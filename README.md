Fluxo Telefonia solo
A proposta de telefonia solo é gerada no salesforce (nesse cenário será informado o iccid), em seguida ele chama o bpelcore, que faz a criação da conta e do pedido, o Maestro pega esse pedido e incia a tramitação, quando ele chega no fluxo do processSoftware ele deverá validar se existe o iccid, se sim devera fazer a ativação na api de "serviceOrder" do Hub que vai por sua vez integrar com a SURF, o Fluxo do ProcessSoftware aguarda o callback, e valida se é um pedido de inclusão de salesforce de tefonia solo, se for ele deverá criar uma OS com uma razão especifica chamando o "CommunicationsWorkOrderEBSPS", para registrar no TOA.
e pedido vai seguir a tramitação no Maestro e será finalizado. uma vez que a OS for gerada pelo TOA, ele vai atualizar o numero da os no item do pedido através do fluxo UpdateFulfillmentOrderOSBPEL.

1. Ajustar o processSoftware para ele criar OS após a Habilitação do a la carte de telefonia paytv do salesforce
2. Ajustar o UpdateFulfillmentOrderOSBPEL para que que ele atualize o item do pedido de telefonia com o numero da OS
3. Ajustes: Ajustar a chamada do createWorkOrder para passar o iccid e ajustar para nao enviar dados de equipamento
4. Alterar o "CommunicationsWorkOrderEBSPS" para nao fazer o callback para o salesforce*



Fluxo PAYTV + telefonia A La Carte
A proposta de Fluxo PAYTV + telefonia A La Carte é gerada no salesforce (nesse cenário não será informado o iccid), em seguida ele chama o bpelcore, que faz a criação da conta e do pedido, o Maestro pega esse pedido e inicia a tramitação, ele vai identificar que existem a necessidade de geração de OS e vai chamar o fluxo o "ProcessHarware", que irá chamar o serviço "CommunicationsWorkOrderEBSPS" para a criação da OS, nesse ponto ele deverá criar os itens de OS dos equipamentos de PAYTV e um item para o Telefonia. Quando a Habilitação ocorrer, ele deve chamar o fluxo do LoadExternal habilitando pelo menos o ponto principal do paytv, antes de habilitar o item de telefonia. O fluxo do "ProcessOSEReturnFulfillmentOrderEBFMIP", vai receber essa OS de telefonia, e chamar o fluxo do ProcessSoftware, que por sua fez ira incluir o produto do BRM e fazer o auto asset.


1. Ajustar o bpel "ProcessOSEReturnFulfillmentOrderEBFMIP", necessário incluir a sub categoria "Telefonia_Plano" nas validações desse fluxo, pois hoje ele só executa o fluxo para itens da categoria "equipamento", al´´em disso remover a chamada ao serviço e inventário quando for telefonia.
2. Ajusta o fluxo do LoadExternal para possibilidar a habilitação sem informar os dados referente ao equipamento
