Passo 1: Localizar os dados necessários
Você vai precisar de duas informações que estão no diretório do seu domínio:

A string criptografada da senha:
Abra o arquivo boot.properties do AdminServer (geralmente em .../domains/seu_dominio/servers/AdminServer/security/boot.properties) e copie o valor da linha password. Ela se parece com isso:
password={AES}g2H1sK...=

O caminho da pasta do domínio:
O script precisa saber onde está o arquivo SerializedSystemIni.dat (geralmente fica na raiz da pasta do seu domínio ou dentro de security).

Passo 2: Rodar o Decryptor via WLST
Vá até a pasta de binários do seu domínio para carregar as variáveis de ambiente:

Bash
cd /u01/oracle/user_projects/domains/seu_dominio/bin
source ./setDomainEnv.sh

2. Inicie o WLST em modo interativo (linha de comando do WebLogic):
   ```bash
   wlst.sh
(Aguarde o prompt mudar para wls:/offline>_)

Cole as seguintes linhas de comando no prompt (ajustando os caminhos e a sua string criptografada):

Python
import weblogic.security.internal.SerializedSystemIni
import weblogic.security.internal.encryption.ClearOrEncryptedService

# 1. Defina o caminho exato do seu domínio
domain_path = "/u01/oracle/user_projects/domains/seu_dominio"

# 2. Carrega a chave de criptografia do domínio
encryption_service = weblogic.security.internal.SerializedSystemIni.getEncryptionService(domain_path)
ces = weblogic.security.internal.encryption.ClearOrEncryptedService(encryption_service)

# 3. Cole a string criptografada que você pegou no boot.properties (mantenha as aspas)
senha_criptografada = "{AES}g2H1sK+sua_string_aqui..."

# 4. Executa a descriptografia
print "A SENHA ATUAL E: " + ces.decrypt(senha_criptografada)

4. Assim que você der Enter na última linha, o terminal vai printar a senha em texto aberto.

5. Para sair do WLST, basta digitar:
   ```python
   exit()
