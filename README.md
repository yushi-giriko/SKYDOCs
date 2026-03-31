<?xml version="1.0" encoding="UTF-8"?>
<!--
//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
  Oracle JDeveloper BPEL Designer 
   
  Created: Mon Sep 24 20:56:50 CST 2012
  Author:  angelica.p.mendoza
  Purpose: Synchronous BPEL Process
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
-->
<process name="ProcessSoftwareFulfillmentOrderBPEL"
         targetNamespace="http://xmlns.oracle.com/SKYNOHS_Fase2_ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderBPEL"
         xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"
         xmlns:client="http://xmlns.oracle.com/SKYNOHS_Fase2_ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderBPEL"
         xmlns:ora="http://schemas.oracle.com/xpath/extension" 
         xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
         xmlns:ns1="http://xmlns.oracle.com/EnterpriseFlows/Industry/Comms/ProcessSoftwareFulfillmentOrderEBFMIP/V1"
         xmlns:bpel="http://docs.oasis-open.org/wsbpel/2.0/process/executable"
         xmlns:xsd="http://www.w3.org/2001/XMLSchema"
         xmlns:ns4="urn:oasis:names:tc:xacml:2.0:context:schema:cd:04" 
         xmlns:xp20="http://www.oracle.com/XSL/Transform/java/oracle.tip.pc.services.functions.Xpath20"
         xmlns:aia="http://www.oracle.com/XSL/Transform/java/oracle.apps.aia.core.xpath.AIAFunctions"
         xmlns:bpws="http://schemas.xmlsoap.org/ws/2003/03/business-process/"
         xmlns:oraext="http://www.oracle.com/XSL/Transform/java/oracle.tip.pc.services.functions.ExtFunc"
         xmlns:dvm="http://www.oracle.com/XSL/Transform/java/oracle.tip.dvm.LookupValue"
         xmlns:hwf="http://xmlns.oracle.com/bpel/workflow/xpath" 
         xmlns:ids="http://xmlns.oracle.com/bpel/services/IdentityService/xpath"
         xmlns:bpm="http://xmlns.oracle.com/bpmn20/extensions"
         xmlns:xdk="http://schemas.oracle.com/bpel/extension/xpath/function/xdk"
         xmlns:xref="http://www.oracle.com/XSL/Transform/java/oracle.tip.xref.xpath.XRefXPathFunctions"
         xmlns:ldap="http://schemas.oracle.com/xpath/extension/ldap"
         xmlns:corecom="http://xmlns.oracle.com/EnterpriseObjects/Core/Common/V2"
         xmlns:corecomcust="http://xmlns.oracle.com/EnterpriseObjects/Core/Custom/Common/V2"
         xmlns:custparty="http://xmlns.oracle.com/EnterpriseObjects/Core/EBO/CustomerParty/V2"
         xmlns:custpartycust="http://xmlns.oracle.com/EnterpriseObjects/Core/Custom/EBO/CustomerParty/V2"
         xmlns:db="http://xmlns.oracle.com/pcbpel/adapter/db/SPWEB/PR_QUERY_PROPOSAL_DATA/"
         xmlns:db2="http://xmlns.oracle.com/pcbpel/adapter/db/SPWEB/PR_QUERY_PROPOSAL_BL/"
         xmlns:ford="http://xmlns.oracle.com/EnterpriseObjects/Core/EBO/FulfillmentOrder/V1"
         xmlns:fordcust="http://xmlns.oracle.com/EnterpriseObjects/Core/Custom/EBO/FulfillmentOrder/V1"
         xmlns:instprod="http://xmlns.oracle.com/EnterpriseObjects/Core/EBO/InstalledProduct/V2"
         xmlns:instprodcust="http://xmlns.oracle.com/EnterpriseObjects/Core/Custom/EBO/InstalledProduct/V2"
         xmlns:trackersvc="http://sky.com.br/maestro/tracker/service"
         xmlns:ns2="http://xmlns.oracle.com/EnterpriseFlows/Industry/Comms/QueryInstalledProductDurationEBF/V1"
         xmlns:ns3="http://xmlns.oracle.com/EnterpriseObjects/Core/EBO/ReceivedPayment/V1"
         xmlns:ns5="http://xmlns.oracle.com/EnterpriseObjects/Core/Custom/EBO/ReceivedPayment/V1"
         xmlns:ns6="http://xmlns.oracle.com/pcbpel/adapter/db/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/QueryProposal_DA"
         xmlns:ns7="http://xmlns.oracle.com/EnterpriseFlows/Industry/Comms/SubscriberControllerEBF/V1"
         xmlns:ns8="http://xmlns.oracle.com/EnterpriseFlows/Industry/Comms/ProcessSoftwareActivationFulfillmentOrderEBFMIP/V1"
         xmlns:ns9="http://xmlns.oracle.com/EnterpriseServices/Core/CustomerParty/V2"
         xmlns:ns10="http://xmlns.oracle.com/EnterpriseServices/Core/Classification/V1"
         xmlns:ns11="http://xmlns.oracle.com/EnterpriseServices/Core/PaymentTerm/V1"
         xmlns:ns12="http://xmlns.oracle.com/pcbpel/adapter/jms/SKYNOHS_Fase2_ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/UpdateSalesOrder"
         xmlns:ns13="http://xmlns.oracle.com/pcbpel/adapter/jms/SKYNOHS_Fase2_ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/BillFulfillmentOrder"
         xmlns:ns14="http://schemas.xmlsoap.org/ws/2003/03/addressing"
         xmlns:ns15="http://www.sky.com.br/ArchitectureSchemas"
         xmlns:ns16="http://www.sky.com.br/ErrorMessage_AS/"
         xmlns:ns17="http://xmlns.oracle.com/AIAAsyncErrorHandlingBPELProcess"
         xmlns:ns18="http://xmlns.oracle.com/EnterpriseServices/Core/ReceivedPayment/V1"
         xmlns:ns19="http://xmlns.oracle.com/pcbpel/adapter/db/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/Query_Proposal_BL_DA"
         xmlns:ns20="http://xmlns.oracle.com/EnterpriseServices/Core/FulfillmentOrder/V1"
         xmlns:ns21="http://xmlns.oracle.com/EnterpriseServices/Core/InventoryTransaction/V1"
         xmlns:ns22="http://xmlns.oracle.com/EnterpriseServices/Core/InstalledProduct/V2"
         xmlns:ns23="http://xmlns.oracle.com/SKYNOHS_Fase2_ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/BPELProcess1"
         xmlns:ns26="http://xmlns.oracle.com/EnterpriseFlows/Industry/Comms/ProcessOSEReturnFulfillmentOrderEBFMIP/V1"
         xmlns:ns27="http://xmlns.oracle.com/pcbpel/adapter/jms/SKYNOHS_Fase2_ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/BillFulfillmentOrderResponse"
         xmlns:ns28="http://xmlns.oracle.com/EnterpriseServices/Core/OverdueCollectionRule/V1"
         xmlns:ns29="http://xmlns.oracle.com/EnterpriseFlows/Industry/Comms/QueryAssessmentInstalledProductListEBF/V1"
         xmlns:ns30="http://xmlns.oracle.com/EnterpriseServices/Core/AccountBalanceAdjustment/V2"
         xmlns:ns31="http://xmlns.oracle.com/EnterpriseObjects/Core/EBO/AccountBalanceAdjustment/V2"
         xmlns:ns32="http://xmlns.oracle.com/BRM/schemas/BusinessOpcodes"
         xmlns:ns24="http://www.sky.com.br/services/IPPVServiceEBS/V1"
         xmlns:ns25="http://www.sky.com.br/message/IPPVServiceEBS/V1"
         xmlns:ns33="http://xmlns.oracle.com/pcbpel/adapter/jms/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/RecurringRechargeJMSAdapter"
         xmlns:ns34="http://xmlns.oracle.com/EnterpriseObjects/Core/EBO/InventoryTransaction/V1"
         xmlns:ui="http://xmlns.oracle.com/soa/designer" xmlns:ess="http://xmlns.oracle.com/scheduler"
         xmlns:ns35="http://xmlns.oracle.com/EnterpriseServices/Core/ProvisioningOrder/V1"
         xmlns:ns41="http://xmlns.oracle.com/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/DisneyStream"
         xmlns:ns42="http://www.sky.com.br/disney/entitlement"
         xmlns:ns36="http://xmlns.oracle.com/pcbpel/adapter/db/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/RELACIONAMENTO_PAI_FILHO"
         xmlns:ns37="http://xmlns.oracle.com/pcbpel/adapter/db/top/RELACIONAMENTO_PAI_FILHO"
         xmlns:ns38="http://www.sky.com.br/service/CommunicationsAccountRelationshipEBS/V1"
         xmlns:ns40="http://www.sky.com.br/Commons/BusinessReturnType/V1"
         xmlns:ns39="http://www.sky.com.br/message/CommunicationsAccountRelationshipEBS/V1"
         xmlns:ns43="http://www.sky.com.br/Commons/HeaderType/V1"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xmlns:ns44="http://xmlns.oracle.com/pcbpel/adapter/db/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/TB_EXTERNAL_PARTNET_EVENT"
         xmlns:ns45="http://xmlns.oracle.com/pcbpel/adapter/db/top/TB_EXTERNAL_PARTNET_EVENT"
         xmlns:ns46="http://xmlns.oracle.com/pcbpel/adapter/db/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/TB_EXTERNAL_PARTNER_EVENT"
         xmlns:ns47="http://xmlns.oracle.com/pcbpel/adapter/db/top/TB_EXTERNAL_PARTNER_EVENT"
         xmlns:ns48="http://xmlns.oracle.com/EnterpriseServices/Core/WorkOrder/V1"
         xmlns:ns49="http://xmlns.oracle.com/EnterpriseObjects/Core/EBO/WorkOrder/V1"
         xmlns:ns50="http://xmlns.oracle.com/EnterpriseObjects/Core/Custom/EBO/WorkOrder/V1"
         xmlns:ns51="http://xmlns.oracle.com/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/HubSvaConnector"
         xmlns:ns52="http://www.sky.com.br/insuranceordermanagement"
         xmlns:ns53="http://www.sky.com.br/camundahubsvarestpostconnector"
         xmlns:ns56="http://xmlns.oracle.com/EnterpriseObjects/Core/Custom/CommonEBO/V1"
         xmlns:ns54="http://xmlns.oracle.com/EnterpriseObjects/Core/EBO/Classification/V1"
         xmlns:ns55="http://xmlns.oracle.com/EnterpriseObjects/Core/CommonEBO/V1" xmlns:ns57="http://www.sky.com.br"
         xmlns:ns59="http://www.sky.com.br/svaservice" 
         xmlns:ns60="http://www.sky.com.br/svalistebm"
         xmlns:ns61="http://xmlns.oracle.com/EnterpriseServices/Core/Location/V1"
         xmlns:ns62="http://xmlns.oracle.com/EnterpriseObjects/Core/Custom/EBO/Location/V1"
         xmlns:ns63="http://xmlns.oracle.com/EnterpriseObjects/Core/EBO/Security/V1"
         xmlns:ns58="http://xmlns.oracle.com/EnterpriseObjects/Core/EBO/Location/V1"
         xmlns:ns64="http://xmlns.oracle.com/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/AmazonApi"
         xmlns:ns65="http://www.sky.com.br/amazon/entitlement"
		 xmlns:ns70="http://xmlns.oracle.com/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/AccountRelationshipAPI"
         xmlns:ns71="http://www.sky.com.br/service/ProcessAccountBalanceHierarchicallyEBF/V1"
         xmlns:ns72="http://www.sky.com.br/service/AccountRelationshipApi/V1"
		 xmlns:ns67="http://xmlns.oracle.com/pcbpel/adapter/db/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/PR_SELECT_LAST_BILL"
         xmlns:ns68="http://xmlns.oracle.com/pcbpel/adapter/db/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/PR_INSERT_TRANSFERENCIA_SALDO"
         xmlns:ns69="http://xmlns.oracle.com/pcbpel/adapter/db/sp/PR_SELECT_LAST_BILL"
         xmlns:ns66="http://xmlns.oracle.com/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/HubMobileAPI"
         xmlns:ns73="http://sky.com.br.com/HubMobileAPI_Operation1_response"
         xmlns:ns74="http://xmlns.oracle.com/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/MobileService"
         xmlns:ns75="http://TargetNamespace.com/MobileService_createorder_response"
         xmlns:ns76="http://xmlns.oracle.com/SKYNOHS_Fase2_ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderBPEL/correlationset">
   <!-- 
    ////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
      PARTNERLINKS                                                      
      List of services participating in this BPEL process               
    ////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
  -->
   <bpelx:annotation>
      <bpelx:analysis>
         <bpelx:property name="propertiesFile">
            <![CDATA[WSDLs/ProcessSoftwareFulfillmentOrderBPEL_properties.wsdl]]>
         </bpelx:property>
      </bpelx:analysis>
   </bpelx:annotation>
   <import namespace="http://www.sky.com.br/amazon/entitlement" location="xsd/rest_model/amazon/AmazonError.xsd"
           importType="http://www.w3.org/2001/XMLSchema"/>
   <import namespace="http://xmlns.oracle.com/EnterpriseServices/Core/FulfillmentOrder/V1"
           location="oramds:/apps/AIAMetaData/AIAComponents/ExtensionServiceLibrary/SOA/EnterpriseBusinessServiceLibrary/Industry/Communications/EBO/FulfillmentOrder/V1/CommunicationsFulfillmentOrderEBSV1Abstract.wsdl"
           importType="http://schemas.xmlsoap.org/wsdl/"/>
   <import namespace="http://www.sky.com.br/service/AccountRelationshipApi/V1"
           location="xsd/rest_model/AccountRelationshipResponseEBM.xsd" importType="http://www.w3.org/2001/XMLSchema"/>
   <import namespace="http://www.sky.com.br/svaservice" location="WSDLs/SvaServiceEBS.wsdl"
           importType="http://schemas.xmlsoap.org/wsdl/"/>
   <import namespace="http://www.sky.com.br/service/CommunicationsAccountRelationshipEBS/V1"
           location="WSDLs/CommunicationsAccountRelationshipEBSAbstract.wsdl"
           importType="http://schemas.xmlsoap.org/wsdl/"/>
   <import namespace="http://www.sky.com.br/message/CommunicationsAccountRelationshipEBS/V1"
           location="xsd/QueryRelationshipResponseEBM.xsd" importType="http://www.w3.org/2001/XMLSchema"/>
   <import namespace="http://xmlns.oracle.com/EnterpriseFlows/Industry/Comms/ProcessSoftwareFulfillmentOrderEBFMIP/V1"
           location="ProcessSoftwareFulfillmentOrderEBFMIPAbstractWrapper.wsdl"
           importType="http://schemas.xmlsoap.org/wsdl/" ui:processWSDL="true"/>
   <import namespace="http://xmlns.oracle.com/EnterpriseServices/Core/InventoryTransaction/V1"
           location="oramds:/apps/AIAMetaData/AIAComponents/ExtensionServiceLibrary/SOA/EnterpriseBusinessServiceLibrary/Industry/Communications/EBO/InventoryTransaction/V1/CommunicationsInventoryTransactionEBSV1Abstract.wsdl"
           importType="http://schemas.xmlsoap.org/wsdl/"/>
   <import namespace="http://xmlns.oracle.com/EnterpriseObjects/Core/EBO/FulfillmentOrder/V1"
           location="oramds:/apps/AIAMetaData/AIAComponents/ExtensionServiceLibrary/SOA/EnterpriseObjectLibrary/Industry/Communications/EBO/FulfillmentOrder/V1/FulfillmentOrderEBM.xsd"
           importType="http://www.w3.org/2001/XMLSchema"/>
   <import namespace="http://xmlns.oracle.com/EnterpriseObjects/Core/EBO/FulfillmentOrder/V1"
           location="oramds:/apps/AIAMetaData/AIAComponents/EnterpriseObjectLibrary/Industry/Communications/EBO/FulfillmentOrder/V1/FulfillmentOrderEBM.xsd"
           importType="http://www.w3.org/2001/XMLSchema"/>
   <import namespace="http://xmlns.oracle.com/EnterpriseFlows/Industry/Comms/ProcessSoftwareFulfillmentOrderEBFMIP/V1" location="oramds:/apps/AIAMetaData/AIAComponents/ExtensionServiceLibrary/SOA/BusinessProcessServiceLibrary/EBF/ProcessSoftwareFulfillmentOrderEBFMIPAbstractV2.wsdl" importType="http://schemas.xmlsoap.org/wsdl/"/>
   <import namespace="http://xmlns.oracle.com/BRM/schemas/BusinessOpcodes" location="oramds:/apps/AIAMetaData/AIAComponents/ApplicationObjectLibrary/BRM/V1/wsdls/BRMCustServices.wsdl" importType="http://schemas.xmlsoap.org/wsdl/"/>
   <import namespace="http://xmlns.oracle.com/EnterpriseServices/Core/AccountBalanceAdjustment/V2" location="oramds:/apps/AIAMetaData/AIAComponents/ExtensionServiceLibrary/SOA/EnterpriseBusinessServiceLibrary/Industry/Communications/EBO/AccountBalanceAdjustment/V2/AccountBalanceAdjustmentEBSV2Abstract.wsdl" importType="http://schemas.xmlsoap.org/wsdl/"/>
   <import namespace="http://xmlns.oracle.com/pcbpel/adapter/jms/SKYNOHS_Fase2_ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/UpdateSalesOrder" location="UpdateSalesOrder.wsdl" importType="http://schemas.xmlsoap.org/wsdl/"/>
   <import namespace="http://xmlns.oracle.com/EnterpriseObjects/Core/EBO/FulfillmentOrder/V1" location="oramds:/apps/AIAMetaData/AIAComponents/EnterpriseObjectLibrary/Industry/Communications/EBO/FulfillmentOrder/V1/FulfillmentOrderEBO.xsd" importType="http://www.w3.org/2001/XMLSchema"/>
   <import namespace="http://xmlns.oracle.com/pcbpel/adapter/db/SPWEB/PR_QUERY_PROPOSAL_DATA/" location="xsd/SPWEB_PR_QUERY_PROPOSAL_DATA.xsd" importType="http://www.w3.org/2001/XMLSchema"/>
   <import namespace="http://xmlns.oracle.com/pcbpel/adapter/db/SPWEB/PR_QUERY_PROPOSAL_BL/" location="xsd/SPWEB_PR_QUERY_PROPOSAL_BL.xsd" importType="http://www.w3.org/2001/XMLSchema"/>
   <import namespace="http://www.sky.com.br/services/IPPVServiceEBS/V1" location="wsdl/IPPVServiceEBSV1Abstract.wsdl" importType="http://schemas.xmlsoap.org/wsdl/"/> 
   
   <partnerLinks>
      <!-- 
      The 'client' role represents the requester of this service. It is 
      used for callback. The location and correlation information associated
      with the client role are automatically set using WS-Addressing.
    -->
      <partnerLink name="processsoftwarefulfillmentorderbpel_client" 
                 partnerLinkType="ns1:ProcessSoftwareFulfillmentOrderBPEL" 
                 partnerRole="ProcessSoftwareFulfillmentOrderEBFMIPResponse" 
                 myRole="ProcessSoftwareFulfillmentOrderEBFMIP"/>
      <partnerLink name="ProcessSoftwareActivationFulfillmentOrderEBFMIP" 
                 partnerLinkType="ns8:ProcessSoftwareActivationFulfillmentOrderEBFMIP" 
                 partnerRole="ProcessSoftwareActivationFulfillmentOrderEBFMIP"/>
      <partnerLink name="BillFulfillmentOrder" 
                 partnerLinkType="ns13:Produce_Message_plt" 
                 partnerRole="Produce_Message_role"/>
      <partnerLink name="ErrorMessage" 
                 partnerLinkType="ns16:ErrorMessage" 
                 partnerRole="ErrorMessage_AS"/>
      <partnerLink name="AIAAsyncErrorHandlingBPELProcess" 
                 partnerLinkType="ns17:AIAAsyncErrorHandlingBPELProcess" 
                 partnerRole="AIAAsyncErrorHandlingBPELProcessProvider"/>
      <partnerLink name="CustomerPartyEBS" 
                 partnerLinkType="ns9:CustomerPartyEBS" 
                 partnerRole="CommunicationsCustomerPartyEBS"/>
      <partnerLink name="ReceivedPaymentEBS" 
                 partnerLinkType="ns18:ReceivedPaymentEBS" 
                 partnerRole="CommunicationsReceivedPaymentEBS"/>
      <partnerLink name="CustomerPartyEBS_SOA" 
                 partnerLinkType="ns9:CustomerPartyEBS_SOA" 
                 partnerRole="CommunicationsCustomerPartyEBS"/>
      <partnerLink name="CommunicationsInstalledProductEBSV2" 
                 partnerLinkType="ns22:CommunicationsInstalledProductEBSV2" 
                 partnerRole="CommunicationsInstalledProductEBS"/>
      <partnerLink name="UpdateSalesOrderCCPSiebelProvABCSImpl" 
                 partnerLinkType="ns20:UpdateSalesOrderCCPSiebelProvABCSImpl" 
                 partnerRole="CommunicationsFulfillmentOrderEBS"/>
      <partnerLink name="ProcessOSEReturnFulfillmentOrder" 
                 partnerLinkType="ns26:ProcessOSEReturnFulfillmentOrder" 
                 partnerRole="ProcessOSEReturnFulfillmentOrderEBFMIP"/>
      <partnerLink name="OverdueCollectionRuleEBS" 
                 partnerLinkType="ns28:OverdueCollectionRuleEBS" 
                 partnerRole="OverdueCollectionRuleEBS"/>
      <partnerLink name="QueryAssessmentInstalledProductListEBF" 
                 partnerLinkType="ns29:QueryAssessmentInstalledProductListEBF" 
                 partnerRole="QueryAssessmentInstalledProductListEBF"/>
      <partnerLink name="CommunicationsPaymentTermEBSV" 
                 partnerLinkType="ns11:CommunicationsPaymentTermEBSV" 
                 partnerRole="CommunicationsPaymentTermEBS"/>
      <partnerLink name="AccountBalanceAdjustmentEBSV2" 
                 partnerLinkType="ns30:AccountBalanceAdjustmentEBSV2" 
                 partnerRole="AccountBalanceAdjustmentEBS"/>
      <partnerLink name="BRMSUBSCRIPTIONService" 
                 partnerLinkType="ns32:BRMSUBSCRIPTIONService_plt" 
                 partnerRole="BRMSUBSCRIPTIONService_role"/>
      <partnerLink name="BRMCUSTService" 
                 partnerLinkType="ns32:BRMCUSTService_plt" 
                 partnerRole="BRMCUSTService_role"/>
      <partnerLink name="QueryInstalledProductDurationEBF" 
                 partnerLinkType="ns2:QueryInstalledProductDurationEBF" 
                 partnerRole="QueryInstalledProductDurationEBF"/>
      <partnerLink name="CommunicationsFulfillmentOrder" 
                 partnerLinkType="ns20:CommunicationsFulfillmentOrder" 
                 partnerRole="CommunicationsFulfillmentOrderEBS"/>
      <partnerLink name="TrackerSourceQueue" 
                 partnerLinkType="trackersvc:ProduceTrackerMessage_plt" 
                 partnerRole="ProduceTrackerMessage_role"/>
      <partnerLink name="QueryProposal_DA" 
                 partnerLinkType="ns6:QueryProposal_DA_plt" 
                 partnerRole="QueryProposal_DA_role"/>
      <partnerLink name="Query_Proposal_BL_DA" 
                 partnerLinkType="ns19:Query_Proposal_BL_DA_plt" 
                 partnerRole="Query_Proposal_BL_DA_role"/>
      <partnerLink name="CommunicationsInventoryTransactionEBSV1" 
                 partnerLinkType="ns21:CommunicationsInventoryTransactionEBSV1" 
                 partnerRole="CommunicationsInventoryTransactionEBS"/>
      <partnerLink name="ChangeCallbackStatus"
                   partnerLinkType="ns24:ChangeCallbackStatus"
                   myRole="IPPVServiceEBSPortType"/>
      <partnerLink name="ChangeCallbackStatus1"
                   partnerLinkType="ns24:ChangeCallbackStatus1"
                   partnerRole="IPPVServiceEBSPortType"/>
      <partnerLink name="RecurringRechargeJMSAdapter"
                   partnerLinkType="ns33:Produce_Message_plt"
                   partnerRole="Produce_Message_role"/>
      <partnerLink name="CommunicationsProvisioningOrderEBS" partnerLinkType="ns35:CommunicationsProvisioningOrderEBS"
                   partnerRole="CommunicationsProvisioningOrderEBS"/>
      <partnerLink name="DisneyStream" partnerLinkType="ns41:DisneyStream" partnerRole="DisneyStreamProvider"/>
      <partnerLink name="RELACIONAMENTO_PAI_FILHO" partnerLinkType="ns36:RELACIONAMENTO_PAI_FILHO_plt"
                   partnerRole="RELACIONAMENTO_PAI_FILHO_role"/>
      <partnerLink name="CommunicationsAccountRelationshipEBS"
                   partnerLinkType="ns38:CommunicationsAccountRelationshipEBS"
                   partnerRole="CommunicationsAccountRelationshipEBSPort"/>
      <partnerLink name="TB_EXTERNAL_PARTNER_EVENT" partnerLinkType="ns46:TB_EXTERNAL_PARTNER_EVENT_plt"
                   partnerRole="TB_EXTERNAL_PARTNER_EVENT_role"/>
      <partnerLink name="CommunicationsWorkOrderEBS" partnerLinkType="ns48:CommunicationsWorkOrderEBS"
                   partnerRole="CommunicationsWorkOrderEBS"/>
      <partnerLink name="HubSvaConnector" partnerLinkType="ns51:HubSvaConnector" partnerRole="HubSvaConnectorProvider"/>
      <partnerLink name="QueryClassificationListCCPSiebelProvABCSImpl"
                   partnerLinkType="ns10:QueryClassificationListCCPSiebelProvABCSImpl"
                   partnerRole="CommunicationsClassificationEBS"/>
      <partnerLink name="CommunicationsLocationEBSV1" partnerLinkType="ns61:CommunicationsLocationEBSV1"
                   partnerRole="CommunicationsLocationEBS"/>
      <partnerLink name="AmazonApi" partnerLinkType="ns64:AmazonApi" partnerRole="AmazonApiProvider"/>
	  <partnerLink name="AccountRelationshipAPI1" partnerLinkType="ns70:AccountRelationshipAPI"
                   partnerRole="AccountRelationshipAPIProvider"/>
      <partnerLink name="ProcessAccountBalanceHierarchicallyEBF"
                   partnerLinkType="ns71:ProcessAccountBalanceHierarchicallyEBF"
                   partnerRole="ProcessAccountBalanceHierarchicallyEBFPort"/>
      <partnerLink name="PR_SELECT_LAST_BILL" partnerLinkType="ns67:PR_SELECT_LAST_BILL_plt"
                   partnerRole="PR_SELECT_LAST_BILL_role"/>
      <partnerLink name="PR_INSERT_TRANSFERENCIA_SALDO" partnerLinkType="ns68:PR_INSERT_TRANSFERENCIA_SALDO_plt"
                   partnerRole="PR_INSERT_TRANSFERENCIA_SALDO_role"/>
      <partnerLink name="UpdateHubMobileCallbackFulfillmentOrder"
                   partnerLinkType="ns1:UpdateHubMobileCallbackFulfillmentOrder_PL"
                   myRole="UpdateHubMobileCallbackFulfillmentOrder_Role"/>
      <partnerLink name="MobileService" partnerLinkType="ns74:MobileService" partnerRole="MobileServiceProvider"/>
   </partnerLinks>
   <!-- 
    ////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
      VARIABLES                                                        
      List of messages and XML documents used within this BPEL process 
    ////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
  -->
   <variables>
      <!-- Reference to the message passed as input during initiation -->
      <variable name="inputVariable" 
				messageType="ns1:ProcessSoftwareFulfillmentOrderRequestMsg"/>
      <!-- Reference to the message that will be returned to the requester-->
      <variable name="outputVariable" 
				messageType="ns1:ProcessSoftwareFulfillmentOrderResponseMsg"/>
      <variable name="D1_flag" 
				type="xsd:string"/>
      <variable name="D2_flag" 
				type="xsd:string"/>
      <variable name="D6_flag" 
				type="xsd:string"/>
      <variable name="curFOL" 
				type="xsd:decimal"/>
      <variable name="PCM_OP_SUBSCRIPTION_SET_DISCOUNT_STATUS_InputVariable" 
				messageType="ns32:PCM_OP_SUBSCRIPTION_SET_DISCOUNT_STATUS_inmsg"/>
      <variable name="PCM_OP_SUBSCRIPTION_SET_DISCOUNT_STATUS_OutputVariable" 
				messageType="ns32:PCM_OP_SUBSCRIPTION_SET_DISCOUNT_STATUS_outmsg"/>
      <variable name="PCM_OP_SUBSCRIPTION_SET_PRODUCT_STATUS_InputVariable" 
				messageType="ns32:PCM_OP_SUBSCRIPTION_SET_PRODUCT_STATUS_inmsg"/>
      <variable name="PCM_OP_SUBSCRIPTION_SET_PRODUCT_STATUS_OutputVariable" 
				messageType="ns32:PCM_OP_SUBSCRIPTION_SET_PRODUCT_STATUS_outmsg"/>
      <variable name="Invoke_A1ProcessSoftwareActivationFulfillmentOrder_InputVariable" 
				messageType="ns8:ProcessSoftwareActivationFulfillmentOrderRequestMsg"/>
      <variable name="Invoke_A1ProcessSoftwareActivationFulfillmentOrder_OutputVariable" 
				messageType="ns8:ProcessSoftwareActivationFulfillmentOrderResponseMsg"/>
      <variable name="Invoke_A3EnableAccountCustomerParty_InputVariable" 
				messageType="ns9:EnableAccountCustomerPartyReqMsg"/>
      <variable name="Invoke_A3EnableAccountCustomerParty_OutputVariable" 
				messageType="ns9:EnableAccountCustomerPartyRespMsg"/>
      <variable name="Invoke_A4UpdateCustomerPartySynchronously_InputVariable" 
				messageType="ns9:UpdateCustomerPartySynchronouslyReqMsg"/>
      <variable name="Invoke_A4UpdateCustomerPartySynchronously_OutputVariable" 
				messageType="ns9:UpdateCustomerPartySynchronouslyRespMsg"/>
      <variable name="Invoke_A6QueryClassificationList_InputVariable" 
				messageType="ns10:QueryClassificationListReqMsg"/>
      <variable name="Invoke_A6QueryClassificationList_OutputVariable" 
				messageType="ns10:QueryClassificationListRespMsg"/>
      <variable name="InvokeA14_BillAccountCustomerParty_InputVariable" 
				messageType="ns9:BillAccountCustomerPartyReqMsg"/>
      <variable name="InvokeA14_BillAccountCustomerParty_OutputVariable" 
				messageType="ns9:BillAccountCustomerPartyRespMsg"/>
      <variable name="Invoke_A10PIPBillFulfillmentOrder_InputVariable" 
				messageType="ns13:Produce_Message_msg"/>
      <variable name="EBMHeader" 
				element="corecom:EBMHeader"/>
      <variable name="queryErrorMessage_InputVariable" 
				messageType="ns16:queryErrorMessageRequest"/>
      <variable name="queryErrorMessage_OutputVariable" 
				messageType="ns16:queryErrorMessageResponse"/>
      <variable name="SystemFaultVar" 
				messageType="bpelx:RuntimeFaultMessage"/>
      <variable name="AIAAsyncErrorHandlingBPELProcessRequestMessage" 
				messageType="ns17:AIAAsyncErrorHandlingBPELProcessRequestMessage"/>
      <variable name="EBM_HEADER" 
				element="corecom:EBMHeader"/>
      <variable name="InvokeA15_CreateReceivedPaymentSynchronously_InputVariable" 
				messageType="ns18:CreateReceivedPaymentSynchronouslyReqMsg"/>
      <variable name="InvokeA15_CreateReceivedPaymentSynchronously_OutputVariable" 
				messageType="ns18:CreateReceivedPaymentSynchronouslyRespMsg"/>
      <variable name="curFulfillmentOrderLine" 
				element="ford:FulfillmentOrderLine"/>
      <variable name="Invoke_A13UpdateSalesOrderCCPSiebelProvABCSImpl_InputVariable" 
				messageType="ns20:UpdateFulfillmentOrderReqMsg"/>
      <variable name="A5_QueryInstalledProductList_InputVariable" 
				messageType="ns22:QueryInstalledProductListReqMsg"/>
      <variable name="A5_QueryInstalledProductList_OutputVariable" 
				messageType="ns22:QueryInstalledProductListRespMsg"/>
      <variable name="A12_UpdateCustomerPartySynchronously_InputVariable" 
				messageType="ns9:UpdateCustomerPartySynchronouslyReqMsg"/>
      <variable name="A12_UpdateCustomerPartySynchronously_OutputVariable" 
				messageType="ns9:UpdateCustomerPartySynchronouslyRespMsg"/>
      <variable name="A6_UpdateFulfillmentOrder_InputVariable" 
				messageType="ns20:UpdateFulfillmentOrderReqMsg"/>
      <variable name="Title" 
				type="xsd:string"/>
      <variable name="A7_ReschedulingOverDueCollectionRule_InputVariable" 
				messageType="ns28:ReschedulingOverdueCollectionRuleReqMsg"/>
      <variable name="A7_ReschedulingOverDueCollectionRule_OutputVariable" 
				messageType="ns28:ReschedulingOverdueCollectionRuleRespMsg"/>
      <variable name="A8_QueryAssessmentInstalledProductList_InputVariable" 
				messageType="ns29:QueryAssessmentInstalledProductListRequestMsg"/>
      <variable name="A8_QueryAssessmentInstalledProductList_OutputVariable" 
				messageType="ns29:QueryAssessmentInstalledProductListResponseMsg"/>
      <variable name="A9_CreatePaymentTermSynchronouly_InputVariable" 
				messageType="ns11:CreatePaymentTermSynchronouslyReqMsg"/>
      <variable name="A9_CreatePaymentTermSynchronouly_OutputVariable" 
				messageType="ns11:CreatePaymentTermSynchronouslyRespMsg"/>
      <variable name="Invoke_CreateAccountBalanceAdjustment_InputVariable" 
				messageType="ns30:CreateAccountBalanceAdjustmentReqMsg"/>
      <variable name="Invoke_CustomCreateAccountBalanceAdjustment_InputVariable" 
				messageType="ns30:CustomCreateAccountBalanceAdjustmentReqMsg"/>
      <variable name="Invoke_CustomCreateAccountBalanceAdjustment_OutputVariable" 
				messageType="ns30:CustomCreateAccountBalanceAdjustmentRespMsg"/>
      <variable name="ImmediateDiscountItems" 
				element="ford:FulfillmentOrderEBO"/>
      <variable name="currentSystemDateTime" 
				type="xsd:dateTime"/>
      <variable name="A5_Invoke_QueryFulfillmentOrderList_InputVariable" 
				messageType="ns20:QueryFulfillmentOrderListReqMsg"/>
      <variable name="A5_Invoke_QueryFulfillmentOrderList_OutputVariable" 
				messageType="ns20:QueryFulfillmentOrderListRespMsg"/>
      <variable name="isInWarranty" 
				type="xsd:boolean"/>
      <variable name="EntryOrderDateTime" 
				type="xsd:dateTime"/>
      <variable name="CurrentDate" 
				type="xsd:dateTime"/>
      <variable name="EntryOrderProblemCode" 
				type="xsd:integer"/>
      <variable name="EntryOrderDateTimeFormated" 
				type="xsd:string"/>
      <variable name="LastFulfillmentOrderDate" 
				type="xsd:dateTime"/>
      <variable name="CurrentStartDt" 
				type="xsd:dateTime"/>
      <variable name="CurrentStartDtDisney" 
				type="xsd:dateTime"/>
      <variable name="CurrentStartDtFormated" 
				type="xsd:string"/>
      <variable name="CurrentStartDtDisneyFormated" 
				type="xsd:string"/>
      <variable name="CurrentSystemDt" 
				type="xsd:dateTime"/>
      <variable name="CurrentSystemDtFormated" 
				type="xsd:string"/>
      <variable name="LastFulfillmentOrderDateFormated" 
				type="xsd:string"/>
      <variable name="accountCSN" 
				type="xsd:string"/>
      <variable name="orderNumber" 
				type="xsd:string"/>
      <variable name="orderType" 
				type="xsd:string"/>
      <variable name="orderSubType" 
				type="xsd:string"/>
      <variable name="logLevel" 
				type="xsd:string"/>
      <variable name="CurrentFulfillmentOrderPayment" 
				element="ford:FulfillmentOrderPayment"/>
      <variable name="InvokeSubscriberControler_CreateSubscriberCorrelation_InputVariable" 
				messageType="ns7:CreateSubscriberCorrelationRequestMsg"/>
      <variable name="currentOrder_SubID" 
				type="xsd:integer"/>
      <variable name="QueryProposal_BL_Query_Proposal_BL_DA_InputVariable" 
				messageType="ns19:args_in_msg"/>
      <variable name="QueryProposal_BL_Query_Proposal_BL_DA_OutputVariable" 
				messageType="ns19:args_out_msg"/>
      <variable name="ProcessSoftwareActivationFulfillmentOrder_bouquer_InputVariable" 
				messageType="ns8:ProcessSoftwareActivationFulfillmentOrderRequestMsg"/>
      <variable name="ProcessSoftwareActivationFulfillmentOrder_bouquer_OutputVariable" 
				messageType="ns8:ProcessSoftwareActivationFulfillmentOrderResponseMsg"/>
      <variable name="Invoke_QueryCustomerParty_InputVariable" 
				messageType="ns9:QueryCustomerPartyReqMsg"/>
      <variable name="Invoke_QueryCustomerParty_OutputVariable" 
				messageType="ns9:QueryCustomerPartyRespMsg"/>
      <variable name="Invoke_UpdateInventoryTransaction_disassociate_InputVariable" 
				messageType="ns21:UpdateInventoryTransactionReqMsg"/>
      <variable name="Invoke_UpdateInventoryTransaction_Associate_InputVariable" 
				messageType="ns21:UpdateInventoryTransactionReqMsg"/>
      <variable name="Invoke_QueryCustomerPartyEnableCustomerParty_InputVariable" 
				messageType="ns9:QueryCustomerPartyReqMsg"/>
      <variable name="Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable" 
				messageType="ns9:QueryCustomerPartyRespMsg"/>
      <variable name="ProcessSoftwareActivationFulfillmentOrder_Recharge" 
				messageType="ns8:ProcessSoftwareActivationFulfillmentOrderRequestMsg"/>
      <variable name="Variable1"
                messageType="ns24:ChangeCallbackStatusRequestMsg"/>
      <variable name="Invoke_ChangeCallbackStatus_InputVariable"
                messageType="ns24:ChangeCallbackStatusRequestMsg"/>
      <variable name="Invoke_ChangeCallbackStatus_OutputVariable"
                messageType="ns24:ChangeCallbackStatusResponseMsg"/>
      <variable name="skyHeader" messageType="ns24:SkyHeaderMsg"/>
      <variable name="UpdateCustomerParty_UpdateCustomerPartySynchronously_InputVariable"
                messageType="ns9:UpdateCustomerPartySynchronouslyReqMsg"/>
      <variable name="UpdateCustomerParty_UpdateCustomerPartySynchronously_OutputVariable"
                messageType="ns9:UpdateCustomerPartySynchronouslyRespMsg"/>
      <variable name="UpdateCustomerParty_UpdateCustomerPartySynchronously_OutputVariable_1"
                messageType="ns9:UpdateCustomerPartySynchronouslyRespMsg"/>
      <variable name="InvokeRecurringRecharge_InputVariable"
                messageType="ns33:Produce_Message_msg"/>
      <variable name="Invoke_UpdateInventoryTransaction_Reuse_InputVariable"
                messageType="ns21:UpdateInventoryTransactionReqMsg"/>
      <variable name="currentItemToAdjust" element="ford:FulfillmentOrderLine"/>
      <variable name="AssetRelationId" type="xsd:string"/>
      <variable name="DeleteItemReference" element="ford:FulfillmentOrderLine"/>
      <variable name="OrderDate" type="xsd:dateTime"/>
      <variable name="Invoke_ProcessCommand_ProcessCommand_InputVariable" messageType="ns35:ProcessCommandReqMsg"/>
      <variable name="ServiceTimePeriod" type="xsd:string"/>
      <variable name="RechargeProductID" type="xsd:string"/>
      <variable name="RechargeStartDateTime" type="xsd:dateTime"/>
      <variable name="RechargeEndDateTime" type="xsd:dateTime"/>
      <variable name="Invoke_DisneyStream_oppEntitlement_InputVariable" messageType="ns41:oppEntitlement_inputMessage"/>
      <variable name="Invoke_DisneyStream_oppEntitlement_OutputVariable" messageType="ns41:Rest_EmptyMessage"/>
      <variable name="RELACIONAMENTO_PAI_FILHO_Select_InputVariable"
                messageType="ns36:RELACIONAMENTO_PAI_FILHOSelect_inputParameters"/>
      <variable name="RELACIONAMENTO_PAI_FILHO_Select_OutputVariable"
                messageType="ns36:RelacionamentoPaiFilhoCollection_msg"/>
      <variable name="QueryCustomerParty_InputVariable_A1" messageType="ns9:QueryCustomerPartyReqMsg"/>
      <variable name="QueryCustomerParty_OutputVariable_A1" messageType="ns9:QueryCustomerPartyRespMsg"/>
      <variable name="Variable_BillingProfileIdentification" type="xsd:string"/>
      <variable name="InvokeUpdateCustomerPartySynchronouslyFB_InputVariable"
                messageType="ns9:CreateCustomerPartyReqMsg"/>
      <variable name="InvokeUpdateCustomerPartySynchronouslyChild_InputVariable"
                messageType="ns9:UpdateCustomerPartySynchronouslyReqMsg"/>
      <variable name="InvokeUpdateCustomerPartySynchronouslyChild_OutputVariable"
                messageType="ns9:UpdateCustomerPartySynchronouslyRespMsg"/>
      <variable name="QueryCustomerParty_InputVariable_A2" messageType="ns9:QueryCustomerPartyReqMsg"/>
      <variable name="QueryCustomerParty_OutputVariable_A2" messageType="ns9:QueryCustomerPartyRespMsg"/>
      <variable name="UpdateCustomerPartySynchronously_InputVariable_A2"
                messageType="ns9:UpdateCustomerPartySynchronouslyReqMsg"/>
      <variable name="UpdateCustomerPartySynchronously_OutputVariable_A2"
                messageType="ns9:UpdateCustomerPartySynchronouslyRespMsg"/>
      <variable name="QueryCustomerParty_InputVariable_A3" messageType="ns9:QueryCustomerPartyReqMsg"/>
      <variable name="QueryCustomerParty_OutputVariable_A3" messageType="ns9:QueryCustomerPartyRespMsg"/>
      <variable name="CreateParentRelationship_InputVariable" messageType="ns38:CreateParentRelationshipRequestMsg"/>
      <variable name="CreateParentRelationship_OutputVariable" messageType="ns38:CreateParentRelationshipResponseMsg"/>
      <variable name="UpdateCustomerPartySynchronously_InputVariable_Fiber"
                messageType="ns9:UpdateCustomerPartySynchronouslyReqMsg"/>
      <variable name="UpdateCustomerPartySynchronously_OutputVariable_Fiber"
                messageType="ns9:UpdateCustomerPartySynchronouslyRespMsg"/>
      <variable name="TB_EXTERNAL_PARTNET_EVENT_insert_InputVariable"
                messageType="ns46:TbExternalPartnerEventCollection_msg"/>
      <variable name="TB_EXTERNAL_PARTNET_EVENT_insert_OutputVariable"
                messageType="ns46:TbExternalPartnerEventCollection_msg"/>
      <variable name="getVelocidade" type="xsd:string"/>
      <variable name="QueryWorkOrderList_InputVariable" messageType="ns48:QueryWorkOrderListReqMsg"/>
      <variable name="QueryWorkOrderList_OutputVariable" messageType="ns48:QueryWorkOrderListRespMsg"/>
      <variable name="QueryWorkOrderList_InputVariable_QueryOS" messageType="ns48:QueryWorkOrderListReqMsg"/>
      <variable name="QueryWorkOrderList_OutputVariable_QueryOS" messageType="ns48:QueryWorkOrderListRespMsg"/>
      <variable name="QueryCustomerParty_InputVariable_HasOS" messageType="ns9:QueryCustomerPartyReqMsg"/>
      <variable name="QueryCustomerParty_OutputVariable_HasOS" messageType="ns9:QueryCustomerPartyRespMsg"/>
      <variable name="QueryCustomerParty_InputVariable_CurrentAccount" messageType="ns9:QueryCustomerPartyReqMsg"/>
      <variable name="QueryCustomerParty_OutputVariable_CurrentAccount" messageType="ns9:QueryCustomerPartyRespMsg"/>
      <variable name="QueryRelationship_InputVariable" messageType="ns38:QueryRelationshipRequestMsg"/>
      <variable name="QueryRelationship_OutputVariable" messageType="ns38:QueryRelationshipResponseMsg"/>
      <variable name="InvokeUpdateCustomerPartySynchronously_UpdateCustomerPartySynchronously_InputVariable_FlowHasTwoOS"
                messageType="ns9:UpdateCustomerPartySynchronouslyReqMsg"/>
      <variable name="InvokeUpdateCustomerPartySynchronously_UpdateCustomerPartySynchronously_OutputVariable_FlowHasTwoOS"
                messageType="ns9:UpdateCustomerPartySynchronouslyRespMsg"/>
      <variable name="QueryRelationship_InputVariable_CurrentAccount" messageType="ns38:QueryRelationshipRequestMsg"/>
      <variable name="QueryRelationship_OutputVariable_CurrentAccount" messageType="ns38:QueryRelationshipResponseMsg"/>
      <variable name="UpdateCustomerPartySynchronously_InputVariable_FlowOs"
                messageType="ns9:UpdateCustomerPartySynchronouslyReqMsg"/>
      <variable name="UpdateCustomerPartySynchronously_OutputVariable_FlowOs"
                messageType="ns9:UpdateCustomerPartySynchronouslyRespMsg"/>
      <variable name="oppHubSvaConnector_InputVariable" messageType="ns51:oppHubSvaConnector_inputMessage"/>
      <variable name="oppHubSvaConnector_OutputVariable" messageType="ns51:oppHubSvaConnector_outputMessage"/>
      <variable name="QueryCustomerParty_InputVariable_HubSvaConnector" messageType="ns9:QueryCustomerPartyReqMsg"/>
      <variable name="QueryCustomerParty_OutputVariable_HubSvaConnector" messageType="ns9:QueryCustomerPartyRespMsg"/>
      <variable name="QueryClassificationList_InputVariable" messageType="ns10:QueryClassificationListReqMsg"/>
      <variable name="QueryClassificationList_OutputVariable" messageType="ns10:QueryClassificationListRespMsg"/>
	  <variable name="getDueDateValue" type="xsd:string"/>
      <variable name="QueryLocationList_InputVariable" messageType="ns61:QueryLocationListReqMsg"/>
      <variable name="QueryLocationList_OutputVariable" messageType="ns61:QueryLocationListRespMsg"/>
      <variable name="UpdateLocationSynchronously_InputVariable" messageType="ns61:UpdateLocationSynchronouslyReqMsg"/>
      <variable name="UpdateLocationSynchronously_OutputVariable" messageType="ns61:UpdateLocationSynchronouslyRespMsg"/>
      <variable name="Invoke_AmazonStream_Suspend_InputVariable" messageType="ns64:Suspend_inputMessage"/>
      <variable name="Invoke_AmazonStream_Suspend_OutputVariable" messageType="ns64:Suspend_outputMessage"/>
      <variable name="Invoke_AmazonStream_Resume_InputVariable" messageType="ns64:Resume_inputMessage"/>
      <variable name="Invoke_AmazonStream_Resume_OutputVariable" messageType="ns64:Resume_outputMessage"/>
      <variable name="Invoke_AmazonStream_Delete_InputVariable" messageType="ns64:Delete_inputMessage"/>
      <variable name="Invoke_AmazonStream_Delete_OutputVariable" messageType="ns64:Delete_outputMessage"/>
      <variable name="Invoke_AmazonStream_Create_InputVariable" messageType="ns64:Create_inputMessage"/>
      <variable name="Invoke_AmazonStream_Create_OutputVariable" messageType="ns64:Create_outputMessage"/>
      <variable name="Invoke_QueryParty_QueryCustomerParty_InputVariable" messageType="ns9:QueryCustomerPartyReqMsg"/>
      <variable name="Invoke_QueryParty_QueryCustomerParty_OutputVariable" messageType="ns9:QueryCustomerPartyRespMsg"/>
      <variable name="QueryRelationship_InputVariable_ActivationChild" messageType="ns38:QueryRelationshipRequestMsg"/>
      <variable name="QueryRelationship_OutputVariable_ActivationChild"
                messageType="ns38:QueryRelationshipResponseMsg"/>
      <variable name="QueryFulfillmentOrderList_InputVariable_DgoChild"
                messageType="ns20:QueryFulfillmentOrderListReqMsg"/>
      <variable name="QueryFulfillmentOrderList_OutputVariable_DgoChild"
                messageType="ns20:QueryFulfillmentOrderListRespMsg"/>
      <variable name="UpdateFulfillmentOrderSynchronously_InputVariable_DgoChild"
                messageType="ns20:UpdateFulfillmentOrderSynchronouslyReqMsg"/>
      <variable name="UpdateFulfillmentOrderSynchronously_OutputVariable_DgoChild"
                messageType="ns20:UpdateFulfillmentOrderSynchronouslyRespMsg"/>
      <variable name="Invoke_UpdateFulfillmentOrder_IntegrationError_OutputVariable"
                messageType="ns20:UpdateFulfillmentOrderSynchronouslyRespMsg"/>
      <variable name="Invoke_QueryInstalledProductList_OutputVariable"
                messageType="ns22:QueryInstalledProductListRespMsg"/>
      <variable name="UpdateFulfillmentOrderSynchronously_InputVariable"
                messageType="ns20:UpdateFulfillmentOrderSynchronouslyReqMsg"/>
      <variable name="UpdateFulfillmentOrderSynchronously_OutputVariable"
                messageType="ns20:UpdateFulfillmentOrderSynchronouslyRespMsg"/>
      <variable name="ProcessAccountBalanceHierarchically_InputVariable"
                messageType="ns71:ProcessAccountBalanceHierarchicallyRequestMsg"/>
      <variable name="ProcessAccountBalanceHierarchically_OutputVariable"
                messageType="ns71:ProcessAccountBalanceHierarchicallyResponseMsg"/>
      <variable name="AccountRelationshipRequestDTO_InputVariable"
                messageType="ns70:AccountRelationshipRequestDTO_inputMessage"/>
      <variable name="AccountRelationshipRequestDTO_OutputVariable"
                messageType="ns70:AccountRelationshipRequestDTO_outputMessage"/>
      <variable name="PR_SELECT_LAST_BILL_InputVariable" messageType="ns67:args_in_msg"/>
      <variable name="PR_SELECT_LAST_BILL_OutputVariable" messageType="ns67:args_out_msg"/>
      <variable name="PR_INSERT_TRANSFERENCIA_SALDO_InputVariable" messageType="ns68:args_in_msg"/>
      <variable name="QueryCustomerParty_InputVariable_MainChild" messageType="ns9:QueryCustomerPartyReqMsg"/>
      <variable name="QueryCustomerParty_OutputVariable_MainChild" messageType="ns9:QueryCustomerPartyRespMsg"/>
      <variable name="InvokeUpdateFulfillmentOrderMobileError_UpdateFulfillmentOrderSynchronously_InputVariable"
                messageType="ns20:UpdateFulfillmentOrderSynchronouslyReqMsg"/>
      <variable name="InvokeUpdateFulfillmentOrderMobileError_UpdateFulfillmentOrderSynchronously_OutputVariable"
                messageType="ns20:UpdateFulfillmentOrderSynchronouslyRespMsg"/>
      <variable name="OnMessage_UpdateHubMobileCallbackFulfillmentOrder_InputVariable"
                messageType="ns1:UpdateHubMobileCallbackFulfillmentOrderReqMsg"/>
      <variable name="InvokeUpdateCustomerPartyKeywords_UpdateCustomerPartySynchronously_InputVariable"
                messageType="ns9:UpdateCustomerPartySynchronouslyReqMsg"/>
      <variable name="InvokeUpdateCustomerPartyKeywords_UpdateCustomerPartySynchronously_OutputVariable"
                messageType="ns9:UpdateCustomerPartySynchronouslyRespMsg"/>
      <variable name="InvokeMobileService_createOrder_createorder_InputVariable"
                messageType="ns74:createorder_inputMessage"/>
      <variable name="InvokeMobileService_createOrder_createorder_OutputVariable"
                messageType="ns74:createorder_outputMessage"/>
   </variables>
   <correlationSets>
      <correlationSet name="Correlation_Set_csMobile" properties="ns76:Property_mobile"/>
   </correlationSets>
   <faultHandlers>
      <catch faultName="bpelx:remoteFault"
             faultVariable="SystemFaultVar"
             faultMessageType="bpelx:RuntimeFaultMessage">
         <sequence name="Sequence16">
            <if name="If_Error_Code_Must_Be_Handled">
               <condition>($SystemFaultVar.detail/ns8:ArchFaultDetails/ns8:errorCode)=true()</condition>
               <sequence name="Sequence15">
                  <assign name="AssignErrorMessageRequest">
                     <copy>
                        <from>"SOA"</from>
                        <to>$queryErrorMessage_InputVariable.in/ns15:system</to>
                     </copy>
                     <copy ignoreMissingFromData="yes">
                        <from>$SystemFaultVar.code</from>
                        <to>$queryErrorMessage_InputVariable.in/ns15:errorCode</to>
                     </copy>
                     <copy ignoreMissingFromData="yes">
                        <from>ora:parseEscapedXML($SystemFaultVar.detail)</from>
                        <to>$queryErrorMessage_InputVariable.in/ns15:faultDetail</to>
                     </copy>
                     <copy>
                        <from>ora:getCompositeName()</from>
                        <to>$queryErrorMessage_InputVariable.in/ns15:serviceName</to>
                     </copy>
                     <copy>
                        <from>"ProcessSoftwareFulfillmentOrder"</from>
                        <to>$queryErrorMessage_InputVariable.in/ns15:operationName</to>
                     </copy>
                     <copy>
                        <from>"OSB"</from>
                        <to>$queryErrorMessage_InputVariable.in/ns15:providerSystem</to>
                     </copy>
                  </assign>
                  <invoke name="Invoke_ErrorMessage"
                          partnerLink="ErrorMessage"
                          portType="ns16:ErrorMessage_AS"
                          operation="queryErrorMessage"
                          inputVariable="queryErrorMessage_InputVariable"
                          outputVariable="queryErrorMessage_OutputVariable"
                          bpelx:invokeAsDetail="no"/>
                  <assign name="AssignEBM_HEADER">
                     <copy ignoreMissingFromData="yes">
                        <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/corecom:EBMHeader</from>
                        <to>$EBM_HEADER</to>
                     </copy>
                  </assign>
                  <assign name="Assign_AIAAsyncErrorHandlingBPELProcessRequestMessage">
                     <copy>
                        <from>ora:processXSLT('xsl/EBM_to_Fault.xsl', bpws:getVariableData('EBM_HEADER'))</from>
                        <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage</to>
                     </copy>
                     <copy>
                        <from>ora:getFaultAsString()</from>
                        <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage/corecom:FaultNotification/corecom:FaultMessage/corecom:Text</to>
                     </copy>
                     <copy>
                        <from>xp20:current-dateTime()</from>
                        <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage/corecom:FaultNotification/corecom:ReportingDateTime</to>
                     </copy>
                     <copy>
                        <from>ora:getProcessId()</from>
                        <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage/corecom:FaultNotification/corecom:FaultingService/corecom:ID</to>
                     </copy>
                     <copy>
                        <from>'BPEL'</from>
                        <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage/corecom:FaultNotification/corecom:FaultingService/corecom:ImplementationCode</to>
                     </copy>
                     <copy>
                        <from>ora:getInstanceId()</from>
                        <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage/corecom:FaultNotification/corecom:FaultingService/corecom:InstanceID</to>
                     </copy>
                     <copy>
                        <from>ora:getECID()</from>
                        <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage/corecom:FaultNotification/corecom:FaultingService/corecom:ExecutionContextID</to>
                     </copy>
                     <copy>
                        <from>ora:getCompositeInstanceId()</from>
                        <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage/corecom:EBMReference/corecom:EBMID</to>
                     </copy>
                     <copy>
                        <from>ora:getComponentName()</from>
                        <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage/corecom:EBMReference/corecom:EBMName</to>
                     </copy>
                     <copy>
                        <from>"ProcessSoftwareFulfillmentOrderEBFMIP"</from>
                        <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage/corecom:EBMReference/corecom:EBOName</to>
                     </copy>
                     <copy>
                        <from>"Process"</from>
                        <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage/corecom:EBMReference/corecom:VerbCode</to>
                     </copy>
                     <copy>
                        <from>"SOA"</from>
                        <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage/corecom:EBMReference/corecom:SenderReference/corecom:Application/corecom:ID</to>
                     </copy>
                     <copy>
                        <from>"Error"</from>
                        <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage/corecom:FaultNotification/corecom:FaultMessage/corecom:Severity</to>
                     </copy>
                     <copy ignoreMissingFromData="yes">
                        <from>$queryErrorMessage_OutputVariable.out/ns15:errorCode</from>
                        <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage/corecom:FaultNotification/corecom:FaultMessage/corecom:Code</to>
                     </copy>
                     <copy ignoreMissingFromData="yes">
                        <from>$queryErrorMessage_OutputVariable.out/ns15:errorMessage</from>
                        <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage/corecom:FaultNotification/corecom:FaultMessage/corecom:Text</to>
                     </copy>
                  </assign>
                  <invoke name="Invoke_AIAAsyncErrorHandlingBPELProcess"
                          partnerLink="AIAAsyncErrorHandlingBPELProcess"
                          portType="ns17:AIAAsyncErrorHandlingBPELProcess"
                          operation="initiate"
                          inputVariable="AIAAsyncErrorHandlingBPELProcessRequestMessage"
                          bpelx:invokeAsDetail="no"/>
                  <assign name="AssignFault">
                     <copy ignoreMissingFromData="yes">
                        <from>$queryErrorMessage_OutputVariable.out/ns15:errorCode</from>
                        <to>$SystemFaultVar.code</to>
                     </copy>
                     <copy ignoreMissingFromData="yes">
                        <from>$queryErrorMessage_OutputVariable.out/ns15:errorMessage</from>
                        <to>$SystemFaultVar.summary</to>
                     </copy>
                  </assign>
                  <scope name="TrackerProcessErrorScopeRemoteFault" exitOnStandardFault="no">
                     <variables>
                        <variable name="WriteToTrackerQueue_ProduceTrackerMessage_InputVariable"
                                  messageType="trackersvc:ProduceTrackerMessage_msg"/>
                     </variables>
                     <faultHandlers>
                        <catchAll>
                           <empty name="DoNothing"/>
                        </catchAll>
                     </faultHandlers>
                     <if name="If_TrackerLogLevel_greaterThan_0">
                        <condition>$logLevel != '' and $logLevel > '0'</condition>
                        <sequence name="TrackerProcessInputErrorSequence">
                           <assign name="AssignValuesToTrackerVariable">
                              <copy>
                                 <from>concat(
                          ora:getInstanceId(), '||',
                          ora:getComponentName(), '||',
                          ora:getCompositeName(), '||',
                          xp20:current-dateTime(), '||',
                          $orderNumber, '||',
                          $accountCSN, '||',
                          '-1', '||',
                          ora:getECID(), '||',
                          '', '||',
                          $orderType, '||',
                          $orderSubType)</from>
                                 <to>$WriteToTrackerQueue_ProduceTrackerMessage_InputVariable.payload</to>
                              </copy>
                           </assign>
                           <invoke name="WriteToTrackerQueue"
                                   partnerLink="TrackerSourceQueue"
                                   portType="trackersvc:ProduceTrackerMessage_ptt"
                                   operation="ProduceTrackerMessage"
                                   bpelx:invokeAsDetail="no"
                                   inputVariable="WriteToTrackerQueue_ProduceTrackerMessage_InputVariable"/>
                        </sequence>
                     </if>
                  </scope>
               </sequence>
            </if>
            <throw name="Throw1" faultName="bpelx:Fault"
                   faultVariable="SystemFaultVar"/>
         </sequence>
      </catch>
      <catchAll>
         <sequence name="Sequence17">
            <assign name="AssignEBM_HEADER">
               <copy ignoreMissingFromData="yes">
                  <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/corecom:EBMHeader</from>
                  <to>$EBM_HEADER</to>
               </copy>
            </assign>
            <assign name="Assign_AIAAsyncErrorHandlingBPELProcessRequestMessage">
               <copy>
                  <from>ora:processXSLT('xsl/EBM_to_Fault.xsl', bpws:getVariableData('EBM_HEADER'))</from>
                  <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage</to>
               </copy>
               <copy>
                  <from>ora:getFaultAsString()</from>
                  <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage/corecom:FaultNotification/corecom:FaultMessage/corecom:Text</to>
               </copy>
               <copy>
                  <from>xp20:current-dateTime()</from>
                  <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage/corecom:FaultNotification/corecom:ReportingDateTime</to>
               </copy>
               <copy>
                  <from>ora:getProcessId()</from>
                  <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage/corecom:FaultNotification/corecom:FaultingService/corecom:ID</to>
               </copy>
               <copy>
                  <from>'BPEL'</from>
                  <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage/corecom:FaultNotification/corecom:FaultingService/corecom:ImplementationCode</to>
               </copy>
               <copy>
                  <from>ora:getInstanceId()</from>
                  <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage/corecom:FaultNotification/corecom:FaultingService/corecom:InstanceID</to>
               </copy>
               <copy>
                  <from>ora:getECID()</from>
                  <to>$AIAAsyncErrorHandlingBPELProcessRequestMessage.FaultMessage/corecom:FaultNotification/corecom:FaultingService/corecom:ExecutionContextID</to>
               </copy>
            </assign>
            <invoke name="Invoke_AIAAsyncErrorHandlingBPELProcess"
                    bpelx:invokeAsDetail="no"
                    partnerLink="AIAAsyncErrorHandlingBPELProcess"
                    portType="ns17:AIAAsyncErrorHandlingBPELProcess"
                    operation="initiate"
                    inputVariable="AIAAsyncErrorHandlingBPELProcessRequestMessage"/>
            <throw name="Throw2" faultName="bpelx:Fault"
                   faultVariable="SystemFaultVar"/>
            <scope name="TrackerProcessErrorScopeCatchAll" exitOnStandardFault="no">
               <variables>
                  <variable name="WriteToTrackerQueue_ProduceTrackerMessage_InputVariable"
                            messageType="trackersvc:ProduceTrackerMessage_msg"/>
               </variables>
               <faultHandlers>
                  <catchAll>
                     <empty name="DoNothing"/>
                  </catchAll>
               </faultHandlers>
               <if name="If_TrackerLogLevel_greaterThan_0">
                  <condition>$logLevel != '' and $logLevel > '0'</condition>
                  <sequence name="TrackerProcessInputErrorSequence">
                     <assign name="AssignValuesToTrackerVariable">
                        <copy>
                           <from>concat(
                          ora:getInstanceId(), '||',
                          ora:getComponentName(), '||',
                          ora:getCompositeName(), '||',
                          xp20:current-dateTime(), '||',
                          $orderNumber, '||',
                          $accountCSN, '||',
                          '-1', '||',
                          ora:getECID(), '||',
                          '', '||',
                          $orderType, '||',
                          $orderSubType)</from>
                           <to>$WriteToTrackerQueue_ProduceTrackerMessage_InputVariable.payload</to>
                        </copy>
                     </assign>
                     <invoke name="WriteToTrackerQueue"
                             partnerLink="TrackerSourceQueue"
                             portType="trackersvc:ProduceTrackerMessage_ptt"
                             operation="ProduceTrackerMessage"
                             bpelx:invokeAsDetail="no"
                             inputVariable="WriteToTrackerQueue_ProduceTrackerMessage_InputVariable"/>
                  </sequence>
               </if>
            </scope>
         </sequence>
      </catchAll>
   </faultHandlers>
   <!-- 
    ////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
     ORCHESTRATION LOGIC                                               
     Set of activities coordinating the flow of messages across the    
     services integrated within this business process                  
    ////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
  -->
   <sequence name="main">
      <!-- Receive input from requestor. (Note: This maps to operation defined in ProcessSoftwareFulfillmentOrderBPEL.wsdl) -->
      <receive name="receiveInput"
               partnerLink="processsoftwarefulfillmentorderbpel_client"
               portType="ns1:ProcessSoftwareFulfillmentOrderEBFMIP"
               operation="ProcessSoftwareFulfillmentOrder"
               variable="inputVariable"
               createInstance="yes">
         <correlations>
            <correlation set="Correlation_Set_csMobile" initiate="yes"/>
         </correlations>
      </receive>
      <!-- Generate reply to synchronous request -->
      <sequence name="AssignInstanceTitle">
         <assign name="AssignTitle">
            <copy>
               <from>concat('Order - ',$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/corecom:Identification/corecom:ID)</from>
               <to>$Title</to>
            </copy>
         </assign>
         <extensionActivity>
            <bpelx:exec name="SetTitle" language="java">
              <![CDATA[setCompositeInstanceTitle((String) getVariableData("Title"));]]>
            </bpelx:exec>
         </extensionActivity>
      </sequence>
      <flow name="FlowTracker">
         <sequence name="Tracker">
            <scope name="TrackerProcessInputScope" exitOnStandardFault="no">
               <variables>
                  <variable name="WriteToTrackerQueue_ProduceTrackerMessage_InputVariable"
                            messageType="trackersvc:ProduceTrackerMessage_msg"/>
               </variables>
               <faultHandlers>
                  <catchAll>
                     <empty name="DoNothing"/>
                  </catchAll>
               </faultHandlers>
               <sequence>
                  <assign name="AssignTrackerLogLevel">
                     <copy>
                        <from>aia:getSystemProperty("TRACKER.LOG.LEVEL", false())</from>
                        <to>$logLevel</to>
                     </copy>
                  </assign>
                  <if name="If_TrackerLogLevel_greaterThan_0">
                     <condition>$logLevel != '' and $logLevel > '0'</condition>
                     <sequence name="TrackerProcessInputSequence">
                        <assign name="AssignTrackerVariables">
                           <copy>
                              <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/corecom:Identification/corecom:ID</from>
                              <to>$orderNumber</to>
                           </copy>
                           <copy>
                              <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/corecom:CustomerPartyReference/corecom:CustomerPartyAccountIdentification/corecom:ID</from>
                              <to>$accountCSN</to>
                           </copy>
                           <copy ignoreMissingFromData="yes">
                              <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:OrderType</from>
                              <to>$orderType</to>
                           </copy>
                           <copy ignoreMissingFromData="yes">
                              <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode</from>
                              <to>$orderSubType</to>
                           </copy>
                        </assign>
                        <assign name="AssignValuesToTrackerVariable">
                           <copy>
                              <from>concat(
                        ora:getInstanceId(), '||',
                        ora:getComponentName(), '||',
                        ora:getCompositeName(), '||',
                        xp20:current-dateTime(), '||',
                        $orderNumber, '||',
                        $accountCSN, '||',
                        '0', '||',
                        ora:getECID(), '||',
                        '', '||',
                        $orderType, '||',
                        $orderSubType)</from>
                              <to>$WriteToTrackerQueue_ProduceTrackerMessage_InputVariable.payload</to>
                           </copy>
                        </assign>
                        <invoke name="WriteToTrackerQueue"
                                partnerLink="TrackerSourceQueue"
                                portType="trackersvc:ProduceTrackerMessage_ptt"
                                operation="ProduceTrackerMessage"
                                bpelx:invokeAsDetail="no"
                                inputVariable="WriteToTrackerQueue_ProduceTrackerMessage_InputVariable"/>
                     </sequence>
                  </if>
               </sequence>
            </scope>
         </sequence>
         <sequence name="MainFlow">
            <scope name="SCP_Initialize_Variable" exitOnStandardFault="no">
               <assign name="SetIsInWarrantyFalse">
                  <copy>
                     <from>false()</from>
                     <to>$isInWarranty</to>
                  </copy>
               </assign>
            </scope>
            <scope name="Scope_CustomersWordReconnection" exitOnStandardFault="no">
               <if name="If_IsSubtype_CustomersWordReconnection">
                  <documentation>
                     <![CDATA[If_IsSubtype_CustomersWordReconnection]]>
                  </documentation>
                  <condition>contains(xp20:lower-case(string($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode)), "customer's word reconnection")</condition>
                  <sequence name="Sequence92">
                     <sequence name="Sequence_CustomerWordReconnection">
                        <assign name="ProcessSoftware_To_ProcessSoftwareActivationFulfillmentOrder">
                           <bpelx:annotation>
                              <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                           </bpelx:annotation>
                           <copy>
                              <from>ora:doXSLTransformForDoc("xsl/ProcessSoftware_To_ProcessSoftwareActivationFulfillmentOrder.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                              <to variable="ProcessSoftwareActivationFulfillmentOrder_bouquer_InputVariable"
                                  part="ProcessSoftwareActivationFulfillmentOrderEBM"/>
                           </copy>
                        </assign>
                        <invoke name="ProcessSoftwareActivationFulfillmentOrder"
                                partnerLink="ProcessSoftwareActivationFulfillmentOrderEBFMIP"
                                portType="ns8:ProcessSoftwareActivationFulfillmentOrderEBFMIP"
                                operation="ProcessSoftwareActivationFulfillmentOrder"
                                inputVariable="ProcessSoftwareActivationFulfillmentOrder_bouquer_InputVariable"
                                outputVariable="ProcessSoftwareActivationFulfillmentOrder_bouquer_OutputVariable"
                                bpelx:invokeAsDetail="no"/>
                     </sequence>
                     <scope name="Scope_QueryInstalledProducts_CommunicationsInstalledProductEBS">
                        <variables>
                           <variable name="Invoke_QueryInstalledProductList_InputVariable"
                                     messageType="ns22:QueryInstalledProductListReqMsg"/>
                        </variables><sequence name="Sequence93"><assign name="XSL_Invoke_QueryInstalledProducts"
                                                                                               xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
         <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
      </bpelx:annotation>
      <copy>
         <from>ora:doXSLTransformForDoc("xsl/ProcessSoftwareFulfilmentOrderEBMToQueryInstalledProductsEBM_Amazon.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM, "EBMHeader", $EBMHeader)</from>
         <to variable="Invoke_QueryInstalledProductList_InputVariable" part="QueryInstalledProductListEBM"/>
      </copy>
   </assign><invoke name="Invoke_QueryInstalledProducts" partnerLink="CommunicationsInstalledProductEBSV2"
                    portType="ns22:CommunicationsInstalledProductEBS" operation="QueryInstalledProductList"
                    inputVariable="Invoke_QueryInstalledProductList_InputVariable"
                    outputVariable="Invoke_QueryInstalledProductList_OutputVariable" bpelx:invokeAsDetail="no"/>
                           <if name="If_CheckProductAmazon">
                              <documentation>
                                 <![CDATA[Is there product amazon ?]]>
                              </documentation>
                              <condition>count($Invoke_QueryInstalledProductList_OutputVariable.QueryInstalledProductListResponseEBM/instprod:DataArea/instprod:QueryInstalledProductListResponse/instprod:InstalledProductSpecificationGroup[corecom:SpecificationGroup/corecom:Name='Streaming Partner']/corecom:SpecificationGroup/corecom:Specification[corecom:Value='amazonprime'])&gt;0</condition>
                              <scope name="Scope_CustomersWordAmazon">
                                 <variables>
                                    <variable name="Invoke_UpdateFulfillmentOrder_IntegrationError_InputVariable"
                                              messageType="ns20:UpdateFulfillmentOrderSynchronouslyReqMsg"/>
                                    <variable name="x-system-origin" type="xsd:string"/>
                                 </variables>
                                 <faultHandlers>
                                    <catchAll>
                                       <sequence name="Sequence_AmazonStream_Integration_Error_Susp"
                                                 xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                          <assign name="Transformation_ReqUpdateFulfillmentOrder_IntegrationError">
                                             <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
                                                <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                             </bpelx:annotation>
                                             <copy>
                                                <from>ora:doXSLTransformForDoc("xsl/Transformation_ReqUpdateFulfillmentOrder_AmazonIntegrationError.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                                <to variable="Invoke_UpdateFulfillmentOrder_IntegrationError_InputVariable"
                                                    part="UpdateFulfillmentOrderSynchronouslyEBM"/>
                                             </copy>
                                          </assign>
                                          <invoke name="Invoke_UpdateFulfillmentOrder_IntegrationError"
                                                  partnerLink="CommunicationsFulfillmentOrder"
                                                  portType="ns20:CommunicationsFulfillmentOrderEBS"
                                                  operation="UpdateFulfillmentOrderSynchronously"
                                                  inputVariable="Invoke_UpdateFulfillmentOrder_IntegrationError_InputVariable"
                                                  outputVariable="Invoke_UpdateFulfillmentOrder_IntegrationError_OutputVariable"
                                                  xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                                                  bpelx:invokeAsDetail="no"/>
                                       </sequence>
                                    </catchAll>
                                 </faultHandlers>
                                 <sequence name="Sequence94">
                                    <assign name="setXSystemOrigin">
                                       <copy>
                                          <from>'SOA'</from>
                                          <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$x-system-origin</to>
                                       </copy>
                                    </assign>
                                    <if name="If_CheckFlowCustomersWordAmazon">
                                       <documentation>
                                          <![CDATA[Is it bill me ?]]>
                                       </documentation>
                                       <condition>xp20:compare($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderPayment/ford:FulfillmentOrderReceivedPayment/corecom:ReceivedPaymentReference/corecom:Custom/corecomcust:PaymentMethodType/text(), 'Bill Me') = 0</condition>
                                       <scope name="Scope_ResumeAmazon"
                                              xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                          <faultHandlers>
                                             <catch faultName="ns64:ValidationResumeError"
                                                    faultVariable="ValidationResumeError"
                                                    faultElement="ns65:EntitlementErrorResponse">
                                                <empty name="DoNothing"
                                                       xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/>
                                             </catch>
                                          </faultHandlers>
                                          <sequence name="Sequence_Temp.SuspensionReconnection_Amazon">
                                             <assign name="Assign_Invoke_AmazonStream"
                                                     xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                                <copy>
                                                   <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/corecom:Identification/corecom:ID/text()</from>
                                                   <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$Invoke_AmazonStream_Resume_InputVariable.request/ns65:order</to>
                                                </copy>
                                                <copy>
                                                   <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/corecom:CustomerPartyReference/corecom:CustomerPartyAccountIdentification/corecom:ID/text()</from>
                                                   <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$Invoke_AmazonStream_Resume_InputVariable.request/ns65:id</to>
                                                </copy>
                                             </assign>
                                             <invoke name="Invoke_AmazonStream"
                                                     inputVariable="Invoke_AmazonStream_Resume_InputVariable"
                                                     outputVariable="Invoke_AmazonStream_Resume_OutputVariable"
                                                     xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                                                     xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"
                                                     partnerLink="AmazonApi" portType="ns64:AmazonApi_ptt"
                                                     operation="Resume"
                                                     bpelx:invokeAsDetail="no"
                                                     bpelx:inputHeaderVariable="x-system-origin"/>
                                          </sequence>
                                       </scope>
                                       <else>
                                          <documentation>
                                             <![CDATA[Check customer's word return]]>
                                          </documentation>
                                          <if name="If_CheckPayment">
                                             <documentation>
                                                <![CDATA[No payment]]>
                                             </documentation>
                                             <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderPayment/ford:FulfillmentOrderReceivedPayment/corecom:ReceivedPaymentReference/corecom:Custom/corecomcust:PaymentTermReference/corecom:Identification/corecom:ID/text() = '1'</condition>
                                             <scope name="Scope_SuspensionAmazon"
                                                    xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                                <faultHandlers>
                                                   <catch faultName="ns64:ValidationSuspendError"
                                                          faultVariable="ValidationSuspendError"
                                                          faultElement="ns65:EntitlementErrorResponse">
                                                      <empty name="DoNothing"
                                                             xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/>
                                                   </catch>
                                                </faultHandlers>
                                                <sequence name="Sequence_TemporarySuspension_Amazon">
                                                   <assign name="Assign_Invoke_AmazonStream"
                                                           xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                                      <copy>
                                                         <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/corecom:Identification/corecom:ID/text()</from>
                                                         <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$Invoke_AmazonStream_Suspend_InputVariable.request/ns65:order</to>
                                                      </copy>
                                                      <copy>
                                                         <from>'Payment overdue'</from>
                                                         <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$Invoke_AmazonStream_Suspend_InputVariable.request/ns65:reason</to>
                                                      </copy>
                                                      <copy>
                                                         <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/corecom:CustomerPartyReference/corecom:CustomerPartyAccountIdentification/corecom:ID/text()</from>
                                                         <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$Invoke_AmazonStream_Suspend_InputVariable.request/ns65:id</to>
                                                      </copy>
                                                   </assign>
                                                   <invoke name="Invoke_AmazonStream"
                                                           inputVariable="Invoke_AmazonStream_Suspend_InputVariable"
                                                           outputVariable="Invoke_AmazonStream_Suspend_OutputVariable"
                                                           xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                                                           xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"
                                                           partnerLink="AmazonApi" portType="ns64:AmazonApi_ptt"
                                                           operation="Suspend"
                                                           bpelx:invokeAsDetail="no"
                                                           bpelx:inputHeaderVariable="x-system-origin"/>
                                                </sequence>
                                             </scope>
                                             <else>
                                                <empty name="Do_Nothing"/>
                                             </else>
                                          </if>
                                       </else>
                                    </if>
                                 </sequence>
                              </scope>
                              <else><empty name="Do_Nothing"
                                           xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/></else>
                           </if>
                        </sequence></scope>
                  </sequence>
                  <else>
                     <documentation>
                        <![CDATA[No_CustomersWordReconnection]]>
                     </documentation>
                     <sequence name="MainFlow">
                        <sequence name="ScopeChangeCallbackStatusBBVOD">
                           <if name="If_Cancellation_Suspension">
                              <documentation>
                                 <![CDATA[CheckCallbackStatus]]>
                              </documentation>
                              <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Preventive cancellation" or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Voluntary cancellation" or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Postpaid to Prepaid Migration" or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Temporary Suspension" or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Temp. Suspension Reconnection" or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Reactivation" or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Migracao Pre-Pos" </condition>
                              <sequence name="SequenceChangeCallbackStatusBBVOD">
                                 <assign name="Transform_To_Header">
                                    <bpelx:annotation>
                                       <bpelx:pattern patternName="bpelx:transformation"/>
                                    </bpelx:annotation>
                                    <copy>
                                       <from>ora:doXSLTransformForDoc("xsl/Transformation_inputVariable_To_skyHeader.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                       <to variable="skyHeader"
                                           part="skyHeader"/>
                                    </copy>
                                 </assign>
                                 <assign name="Transform_To_Callback">
                                    <bpelx:annotation>
                                       <bpelx:pattern patternName="bpelx:transformation"/>
                                    </bpelx:annotation>
                                    <copy>
                                       <from>ora:doXSLTransformForDoc("xsl/Transformation_input_To_Callback.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                       <to variable="Invoke_ChangeCallbackStatus_InputVariable"
                                           part="parameters"/>
                                    </copy>
                                 </assign>
                                 <invoke name="Invoke_ChangeCallbackStatus"
                                         partnerLink="ChangeCallbackStatus1"
                                         portType="ns24:IPPVServiceEBSPortType"
                                         operation="ChangeCallbackStatus"
                                         inputVariable="Invoke_ChangeCallbackStatus_InputVariable"
                                         outputVariable="Invoke_ChangeCallbackStatus_OutputVariable"
                                         bpelx:inputHeaderVariable="skyHeader"
                                         bpelx:invokeAsDetail="no"
                                         bpelx:headerVariable="skyHeader"/>
                              </sequence>
                              <else>
                                 <empty name="do_Nothing"/>
                              </else>
                           </if>
                        </sequence>
                        <sequence name="Sequence_Amazon_Temporary_Suspension">
                           <scope name="Scope_AmazonSuspendAndResume">
                              <variables>
                                 <variable name="x-system-origin" type="xsd:string"/>
                                 <variable name="Invoke_UpdateFulfillmentOrder_IntegrationError_InputVariable"
                                           messageType="ns20:UpdateFulfillmentOrderSynchronouslyReqMsg"/>
                                 <variable name="Invoke_UpdateFulfillmentOrder_IntegrationError_OutputVariable"
                                           messageType="ns20:UpdateFulfillmentOrderSynchronouslyRespMsg"/>
                              </variables>
                              <faultHandlers>
                                 <catchAll><sequence name="Sequence_AmazonStream_Integration_Error_Susp"
                                                     xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <assign name="Transformation_ReqUpdateFulfillmentOrder_IntegrationError">
         <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
            <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
         </bpelx:annotation>
         <copy>
            <from>ora:doXSLTransformForDoc("xsl/Transformation_ReqUpdateFulfillmentOrder_AmazonIntegrationError.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
            <to variable="Invoke_UpdateFulfillmentOrder_IntegrationError_InputVariable"
                part="UpdateFulfillmentOrderSynchronouslyEBM"/>
         </copy>
      </assign>
      <invoke name="Invoke_UpdateFulfillmentOrder_IntegrationError"
              partnerLink="CommunicationsFulfillmentOrder" portType="ns20:CommunicationsFulfillmentOrderEBS"
              operation="UpdateFulfillmentOrderSynchronously"
              inputVariable="Invoke_UpdateFulfillmentOrder_IntegrationError_InputVariable"
              outputVariable="Invoke_UpdateFulfillmentOrder_IntegrationError_OutputVariable"
              xmlns:bpelx="http://schemas.oracle.com/bpel/extension" bpelx:invokeAsDetail="no"/>
   </sequence></catchAll>
                              </faultHandlers>
                              <sequence name="Sequence87">
                                 <assign name="Assign_setXSystemOrigin">
                                    <copy>
                                       <from>'SOA'</from>
                                       <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$x-system-origin</to>
                                    </copy>
                                 </assign>
                                 <if name="If_Amazon_Temporary_Suspension"
                                     xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                    <documentation>
                                       <![CDATA[Temporary Suspension and Amazon]]>
                                    </documentation>
                                    <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Temporary Suspension" and count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='SUSPEND' and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress']/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Streaming Partner' and (corecom:Value='amazon' or corecom:Value='amazonprime')])&gt;0</condition>
                                    <sequence name="Sequence90">
                                       <scope name="Scope_SuspensionAmazon">
                                          <faultHandlers>
                                             <catch faultName="ns64:ValidationSuspendError"
                                                    faultVariable="ValidationSuspendError"
                                                    faultElement="ns65:EntitlementErrorResponse"><empty name="DoNothing"
                                                                                                        xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/></catch>
                                          </faultHandlers>
                                          <sequence name="Sequence_TemporarySuspension_Amazon">
                                             <assign name="Assign_Invoke_AmazonStream"
                                                     xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                                <copy>
                                                   <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/corecom:Identification/corecom:ID/text()</from>
                                                   <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$Invoke_AmazonStream_Suspend_InputVariable.request/ns65:order</to>
                                                </copy>
                                                <copy>
                                                   <from>'Payment overdue'</from>
                                                   <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$Invoke_AmazonStream_Suspend_InputVariable.request/ns65:reason</to>
                                                </copy>
                                                <copy>
                                                   <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/corecom:CustomerPartyReference/corecom:CustomerPartyAccountIdentification/corecom:ID/text()</from>
                                                   <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$Invoke_AmazonStream_Suspend_InputVariable.request/ns65:id</to>
                                                </copy>
                                             </assign>
                                             <invoke name="Invoke_AmazonStream"
                                                     inputVariable="Invoke_AmazonStream_Suspend_InputVariable"
                                                     outputVariable="Invoke_AmazonStream_Suspend_OutputVariable"
                                                     xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                                                     xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"
                                                     partnerLink="AmazonApi" portType="ns64:AmazonApi_ptt"
                                                     operation="Suspend" bpelx:invokeAsDetail="no"
                                                     bpelx:inputHeaderVariable="x-system-origin"/>
                                          </sequence>
                                       </scope>
                                    </sequence>
                                    <elseif>
                                       <documentation>
                                          <![CDATA[Temp. Suspension Reconnection and Amazon]]>
                                       </documentation>
                                       <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Temp. Suspension Reconnection" and count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='RESUME' and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress']/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Streaming Partner' and (corecom:Value='amazon' or corecom:Value='amazonprime')])&gt;0</condition>
                                       <sequence name="Sequence91">
                                          <scope name="Scope_ResumeAmazon">
                                             <faultHandlers>
                                                <catch faultName="ns64:ValidationResumeError"
                                                       faultVariable="ValidationResumeError"
                                                       faultElement="ns65:EntitlementErrorResponse"><empty name="DoNothing"
                                                                                                           xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/></catch>
                                             </faultHandlers>
                                             <sequence name="Sequence_Temp.SuspensionReconnection_Amazon">
                                                <assign name="Assign_Invoke_AmazonStream"
                                                        xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                                   <copy>
                                                      <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/corecom:Identification/corecom:ID/text()</from>
                                                      <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$Invoke_AmazonStream_Resume_InputVariable.request/ns65:order</to>
                                                   </copy>
                                                   <copy>
                                                      <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/corecom:CustomerPartyReference/corecom:CustomerPartyAccountIdentification/corecom:ID/text()</from>
                                                      <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$Invoke_AmazonStream_Resume_InputVariable.request/ns65:id</to>
                                                   </copy>
                                                </assign>
                                                <invoke name="Invoke_AmazonStream"
                                                        inputVariable="Invoke_AmazonStream_Resume_InputVariable"
                                                        outputVariable="Invoke_AmazonStream_Resume_OutputVariable"
                                                        xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                                                        xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"
                                                        partnerLink="AmazonApi" portType="ns64:AmazonApi_ptt"
                                                        operation="Resume" bpelx:invokeAsDetail="no"
                                                        bpelx:inputHeaderVariable="x-system-origin"/>
                                             </sequence>
                                          </scope>
                                       </sequence>
                                    </elseif>
                                    <else>
                                       <sequence name="Sequence_Nothing">
                                          <empty name="DoNothing"
                                                 xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/>
                                       </sequence>
                                    </else>
                                 </if>
                              </sequence>
                           </scope></sequence>
                        <sequence name="Sequence_Disney_Temporary_Suspension">
                           <scope name="Scope_Disney_Temporary_Suspension">
                              <variables>
                                 <variable name="Invoke_UpdateFulfillmentOrder_IntegrationError_InputVariable"
                                           messageType="ns20:UpdateFulfillmentOrderSynchronouslyReqMsg"/>
                                 <variable name="Invoke_UpdateFulfillmentOrder_IntegrationError_OutputVariable"
                                           messageType="ns20:UpdateFulfillmentOrderSynchronouslyRespMsg"/>
                              </variables>
                              <faultHandlers>
                                 <catchAll><sequence name="Sequence_DisneyStream_Integration_Error_Susp"
                                                     xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <assign name="Transformation_ReqUpdateFulfillmentOrder_IntegrationError">
         <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
            <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
         </bpelx:annotation>
         <copy>
            <from>ora:doXSLTransformForDoc("xsl/Transformation_ReqUpdateFulfillmentOrder_AmazonIntegrationError.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
            <to variable="Invoke_UpdateFulfillmentOrder_IntegrationError_InputVariable"
                part="UpdateFulfillmentOrderSynchronouslyEBM"/>
         </copy>
      </assign>
      <invoke name="Invoke_UpdateFulfillmentOrder_IntegrationError" partnerLink="CommunicationsFulfillmentOrder"
              portType="ns20:CommunicationsFulfillmentOrderEBS" operation="UpdateFulfillmentOrderSynchronously"
              inputVariable="Invoke_UpdateFulfillmentOrder_IntegrationError_InputVariable"
              outputVariable="Invoke_UpdateFulfillmentOrder_IntegrationError_OutputVariable"
              xmlns:bpelx="http://schemas.oracle.com/bpel/extension" bpelx:invokeAsDetail="no"/>
   </sequence></catchAll>
                              </faultHandlers>
                              <if name="If_Disney_Temporary_Suspension">
                                 <documentation>
                                    <![CDATA[Temporary Suspension and Disney]]>
                                 </documentation>
                                 <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Temporary Suspension" and count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='SUSPEND' and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress']/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Streaming Partner' and (corecom:Value='disneyplus' or corecom:Value='starplus')])&gt;0</condition>
                                 <sequence name="Sequence98">
                                    <scope name="Scope_Action_SuspensionDisney">
                                       <faultHandlers>
                                          <catchAll>
                                             <scope name="Scope_Action_SuspensionDisneyError">
                                                <variables>
                                                   <variable name="countErrorDisney" type="xsd:integer"/>
                                                </variables>
                                                <sequence name="Sequence100">
                                                   <assign name="Assign_SetCountRetry">
                                                      <copy>
                                                         <from>1</from>
                                                         <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$countErrorDisney</to>
                                                      </copy>
                                                   </assign>
                                                   <while name="While_RetryActionDisney">
                                                      <bpelx:annotation>
                                                         <bpelx:documentation>
                                                            <![CDATA[Retry de 4 tentativas]]>
                                                         </bpelx:documentation>
                                                      </bpelx:annotation>
                                                      <condition>$countErrorDisney &lt; 5</condition>
                                                      <sequence name="Sequence101">
                                                         <scope name="Scope_Action_SuspensionDisneyErrorRetry">
                                                            <faultHandlers>
                                                               <catchAll>
                                                                  <sequence name="Sequence102">
                                                                     <if name="If_Error_Is_retry">
                                                                        <condition>$countErrorDisney = 4</condition>
                                                                        <throw name="Throw_Error_Disney"
                                                                               faultName="ns41:fault500"/>
                                                                        <else>
                                                                           <assign name="Assign_AddCountRetry">
                                                                              <copy>
                                                                                 <from>$countErrorDisney+1</from>
                                                                                 <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$countErrorDisney</to>
                                                                              </copy>
                                                                           </assign>
                                                                        </else>
                                                                     </if>
                                                                  </sequence>
                                                               </catchAll>
                                                            </faultHandlers>
                                                            <sequence name="Sequence_TemporarySuspension_Disney"
                                                                      xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <assign name="Transformation_Input_Disney_Suspension">
         <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
            <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
         </bpelx:annotation>
         <copy>
            <from>ora:doXSLTransformForDoc("Transformations/Transformation_InputVariable_to_DisneyStream.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
            <to variable="Invoke_DisneyStream_oppEntitlement_InputVariable" part="request"/>
         </copy>
      </assign>
      <invoke name="Invoke_DisneyStream" bpelx:invokeAsDetail="no" partnerLink="DisneyStream"
              portType="ns41:DisneyStream_ptt" operation="oppEntitlement"
              inputVariable="Invoke_DisneyStream_oppEntitlement_InputVariable"
              outputVariable="Invoke_DisneyStream_oppEntitlement_OutputVariable"
              xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
              xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/>
   <assign name="Assign_FinishCountRetry" xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      
   <copy>
         <from>5</from>
         <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$countErrorDisney</to>
      </copy></assign></sequence>
                                                         </scope>
                                                      </sequence>
                                                   </while>
                                                </sequence>
                                             </scope>
                                          </catchAll>
                                       </faultHandlers>
                                       <sequence name="Sequence_TemporarySuspension_Disney">
                                          <assign name="Transformation_Input_Disney_Suspension">
                                             <bpelx:annotation>
                                                <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                             </bpelx:annotation>
                                             <copy>
                                                <from>ora:doXSLTransformForDoc("Transformations/Transformation_InputVariable_to_DisneyStream.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                                <to variable="Invoke_DisneyStream_oppEntitlement_InputVariable"
                                                    part="request"/>
                                             </copy>
                                          </assign>
                                          <invoke name="Invoke_DisneyStream" bpelx:invokeAsDetail="no"
                                                  partnerLink="DisneyStream" portType="ns41:DisneyStream_ptt"
                                                  operation="oppEntitlement"
                                                  inputVariable="Invoke_DisneyStream_oppEntitlement_InputVariable"
                                                  outputVariable="Invoke_DisneyStream_oppEntitlement_OutputVariable"
                                                  xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                                                  xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/>
                                       </sequence>
                                    </scope>
                                 </sequence>
                                 <elseif>
                                    <documentation>
                                       <![CDATA[Temp. Suspension Reconnection and Disney]]>
                                    </documentation>
                                    <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Temp. Suspension Reconnection" and count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='RESUME' and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress']/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Streaming Partner' and (corecom:Value='disneyplus' or corecom:Value='starplus')])&gt;0</condition>
                                    <sequence name="Sequence99">
                                       <scope name="Scope_Action_ReconnectionDisney">
                                          <faultHandlers>
                                             <catchAll>
                                                <sequence name="Sequence107">
                                                   <scope name="Scope_Temp.SuspensionReconnection_DisneyError">
                                                      <variables>
                                                         <variable name="countErrorDisney" type="xsd:integer"/>
                                                      </variables>
                                                      <sequence>
                                                         <assign name="Assign_SetCountRetry">
         <copy>
            <from>1</from>
            <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$countErrorDisney</to>
         </copy>
      </assign>
                                                         <while name="While_RetryActionDisney">
         <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
            <bpelx:documentation>
               <![CDATA[Retry de 4 tentativas]]>
            </bpelx:documentation>
         </bpelx:annotation>
         <condition>$countErrorDisney &lt; 5</condition>
         <sequence name="Sequence101">
            <scope name="Scope_Action_ReconnectionDisneyErrorRetry">
               <faultHandlers>
                  <catchAll>
                     <sequence name="Sequence102">
                        <if name="If_Error_Is_retry">
                           <condition>$countErrorDisney = 4</condition>
                           
                           <sequence>
                                                                                 <throw name="Throw_Error_Disney"
                                                                                        faultName="ns41:fault500"/>
                                                                              </sequence><else>
                              <assign name="Assign_AddCountRetry">
                                 <copy>
                                    <from>$countErrorDisney+1</from>
                                    <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$countErrorDisney</to>
                                 </copy>
                              </assign>
                           </else>
                        </if>
                     </sequence>
                  </catchAll>
               </faultHandlers>
               
            <sequence name="Sequence_Temp.SuspensionReconnection_Disney"
                      xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <assign name="Transformation_Input_Disney_Reconnection"
              xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
         <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
            <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
         </bpelx:annotation>
         <copy>
            <from>ora:doXSLTransformForDoc("Transformations/Transformation_InputVariable_to_DisneyStream.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
            <to variable="Invoke_DisneyStream_oppEntitlement_InputVariable" part="request"/>
         </copy>
      </assign>
      <invoke name="Invoke_DisneyStream" bpelx:invokeAsDetail="no" partnerLink="DisneyStream"
              portType="ns41:DisneyStream_ptt" operation="oppEntitlement"
              inputVariable="Invoke_DisneyStream_oppEntitlement_InputVariable"
              outputVariable="Invoke_DisneyStream_oppEntitlement_OutputVariable"
              xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
              xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/>
   <assign name="Assign_FinishCountRetry" xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      
   <copy>
         <from>5</from>
         <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$countErrorDisney</to>
      </copy></assign></sequence></scope>
         </sequence>
      </while>
                                                      </sequence>
                                                   </scope>
                                                </sequence>
                                             </catchAll>
                                          </faultHandlers>
                                          <sequence name="Sequence_Temp.SuspensionReconnection_Disney">
                                             <assign name="Transformation_Input_Disney_Reconnection"
                                                     xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                                <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
                                                   <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                </bpelx:annotation>
                                                <copy>
                                                   <from>ora:doXSLTransformForDoc("Transformations/Transformation_InputVariable_to_DisneyStream.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                                   <to variable="Invoke_DisneyStream_oppEntitlement_InputVariable"
                                                       part="request"/>
                                                </copy>
                                             </assign>
                                             <invoke name="Invoke_DisneyStream" bpelx:invokeAsDetail="no"
                                                     partnerLink="DisneyStream" portType="ns41:DisneyStream_ptt"
                                                     operation="oppEntitlement"
                                                     inputVariable="Invoke_DisneyStream_oppEntitlement_InputVariable"
                                                     outputVariable="Invoke_DisneyStream_oppEntitlement_OutputVariable"
                                                     xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                                                     xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/>
                                          </sequence>
                                       </scope>
                                    </sequence>
                                 </elseif>
                                 <else>
                                    <sequence name="Sequence_NothingDisney">
                                       <empty name="DoNothing"
                                              xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/>
                                    </sequence>
                                 </else>
                              </if>
                           </scope>
                        </sequence>
                        <sequence name="Sequence54">
	<if name="If_Is_SubTypeCode_Reactivation_And_Equipment_Not_Delete">
		<condition>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Equipamento' and ford:ServiceActionCode != 'DELETE' and $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Reactivation"]) &gt; 0</condition>
		<forEach parallel="no"
		         counterName="ForEach1Counter"
		         name="ForEach1">
			<startCounterValue>1</startCounterValue>
			<finalCounterValue>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Equipamento' and ford:ServiceActionCode != 'DELETE' and $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Reactivation"])</finalCounterValue>
			<scope name="Scope22">
				<sequence name="Sequence55">
					<assign name="ProcessSofwareToUpdateInventoryTransactionReuse">
						<bpelx:annotation>
							<bpelx:pattern patternName="bpelx:transformation"/>
						</bpelx:annotation>
						<copy>
							<from>ora:doXSLTransformForDoc("xsl/ProcessSofwareToUpdateInventoryTransactionReuse.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
							<to variable="Invoke_UpdateInventoryTransaction_Reuse_InputVariable"
							    part="UpdateInventoryTransactionEBM"/>
						</copy>
					</assign>
					<invoke name="Invoke_UpdateInventoryTransaction_Reuse"
					        partnerLink="CommunicationsInventoryTransactionEBSV1"
					        portType="ns21:CommunicationsInventoryTransactionEBS"
					        operation="UpdateInventoryTransaction"
					        inputVariable="Invoke_UpdateInventoryTransaction_Reuse_InputVariable"
             bpelx:invokeAsDetail="no"/>
				</sequence>
			</scope>
		</forEach>
	</if>
</sequence>
                        <scope name="Scope21">
                           <if name="If_Salesforce_inclusion">
                              <documentation>
                                 <![CDATA[yes]]>
                              </documentation>
                              <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:SalesChannelCode='Salesforce' and $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Inclusion" and
(count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = "Complete"]) = 0) </condition>
                              <sequence name="Sequence51">
                                 <assign name="Transform_ProcessSoftware_to_UpdateCustomeParty">
                                    <bpelx:annotation>
                                       <bpelx:pattern patternName="bpelx:transformation"/>
                                    </bpelx:annotation>
                                    <copy>
                                       <from>ora:doXSLTransformForDoc("xsl/Transformation_ProcessSoftware_to_UpdateCustomerParty.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                       <to variable="UpdateCustomerParty_UpdateCustomerPartySynchronously_InputVariable"
                                           part="UpdateCustomerPartySynchronouslyEBM"/>
                                    </copy>
                                 </assign>
                                 <invoke name="UpdateCustomerParty_Account"
                                         partnerLink="CustomerPartyEBS_SOA"
                                         portType="ns9:CommunicationsCustomerPartyEBS"
                                         operation="UpdateCustomerPartySynchronously"
                                         inputVariable="UpdateCustomerParty_UpdateCustomerPartySynchronously_InputVariable"
                                         outputVariable="UpdateCustomerParty_UpdateCustomerPartySynchronously_OutputVariable_1"
                                         bpelx:invokeAsDetail="no"/>
                              </sequence>
                           </if>
                        </scope>
                        <scope name="AdjustImmediateDiscountItens" 
                               exitOnStandardFault="no">
                           <documentation>
                              <![CDATA[This scope adjusts Immediate Discount Itens durations, because one payment was already processed in ProcessCreate flow. If the item is recurring, the remaining duration will be sent to BRM. If is one shot only, the item will not be sent to BRM.]]>
                           </documentation>
                           <sequence>
                              <assign name="AdjustImmediateDiscountItemsAttributes">
                                 <bpelx:annotation>
                                    <bpelx:pattern patternName="bpelx:transformation"/>
                                 </bpelx:annotation>
                                 <copy>
                                    <from>ora:doXSLTransformForDoc("xsl/AdjustImmediateDiscountItens.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                    <to variable="ImmediateDiscountItems"/>
                                 </copy>
                              </assign>
                              <!-- <if name="HasItemsToBeAdjusted"> -->
                                 <!-- <documentation> -->
                                    <!-- <![CDATA[yes]]> -->
                                 <!-- </documentation> -->
                                 <!-- <condition>count($ImmediateDiscountItems/ford:FulfillmentOrderLine) > 0</condition> -->
                                 <!-- <forEach parallel="no"  -->
                                          <!-- counterName="ItemCounter"  -->
                                          <!-- name="ForEachImmediateDiscountItem"> -->
                                    <!-- <startCounterValue>1</startCounterValue> -->
                                    <!-- <finalCounterValue>count($ImmediateDiscountItems/ford:FulfillmentOrderLine)</finalCounterValue> -->
                                    <!-- <scope name="AdjustDurations"> -->
                                       <!-- <variables> -->
                                          <!-- <variable name="CurrentOrderLine" -->
                                                    <!-- type="ford:FulfillmentOrderLineType" /> -->
                                       <!-- </variables> -->
                                       <!-- <sequence name="ProcessCurrentOrderLine"> -->
                                          <!-- <assign name="GetCurrentOrderLineFromInputVariable"> -->
                                             <!-- <copy> -->
                                                <!-- <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ -->
                     <!-- corecom:Identification/corecom:ID = -->
                     <!-- $ImmediateDiscountItems/ford:FulfillmentOrderLine[position() = $ItemCounter]/corecom:Identification/corecom:ID]</from> -->
                                                <!-- <to>$CurrentOrderLine</to> -->
                                             <!-- </copy> -->
                                          <!-- </assign> -->
                                          <!-- <assign name="AdjustItemDuration"> -->
                                             <!-- <copy bpelx:insertMissingToData="yes"> -->
                                                <!-- <from>$ImmediateDiscountItems/ford:FulfillmentOrderLine[position() = $ItemCounter]/corecom:InstalledProductReference/corecom:Custom/corecomcust:Duration</from> -->
                                                <!-- <to>$CurrentOrderLine/corecom:InstalledProductReference/corecom:Custom/corecomcust:Duration</to> -->
                                             <!-- </copy> -->
                                          <!-- </assign> -->
                                          <!-- <assign name="OverrideOrderLineInInputVariable"> -->
                                             <!-- <copy> -->
                                                <!-- <from>$CurrentOrderLine</from> -->
                                                <!-- <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ -->
                     <!-- corecom:Identification/corecom:ID = -->
                     <!-- $ImmediateDiscountItems/ford:FulfillmentOrderLine[position() = $ItemCounter]/corecom:Identification/corecom:ID]</to> -->
                                             <!-- </copy> -->
                                          <!-- </assign> -->
                                       <!-- </sequence> -->
                                    <!-- </scope> -->
                                 <!-- </forEach> -->
                              <!-- </if> -->
                           </sequence>
                        </scope>
                        <sequence name="CalculateEffectiveTimePeriods">
                           <forEach parallel="no" 
                                    counterName="ForEachOne" 
                                    name="ForEachOrderItem">
                              <startCounterValue>1</startCounterValue>
                              <finalCounterValue>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine)</finalCounterValue>
                              <scope name="VerifySettingsOfParentToSetChildDuration" 
                                     exitOnStandardFault="no">
                                 <variables>
                                    <variable name="RootParentOrderLine"
                                              type="xsd:string"/>
                                    <variable name="CurrentOrderLine"
                                              type="ford:FulfillmentOrderLineType"/>
                                    <variable name="InstalledProductReference" 
                                             element="corecom:InstalledProductReference"/>
                                    <variable name="QueryProposal_DA_QueryProposal_DA_InputVariable"
                                              messageType="ns6:args_in_msg"/>
                                    <variable name="QueryProposal_DA_QueryProposal_DA_OutputVariable"
                                              messageType="ns6:args_out_msg"/>
                                 </variables>
                                 <sequence name="VerifySettingsOfParentToSetChildDuration">
                                    <assign name="SettingCurrentOrderLineANDRootParentofThisItem">
                                       <copy>
                                          <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[position() = $ForEachOne]</from>
                                          <to>$CurrentOrderLine</to>
                                       </copy>
                                       <copy>
                                          <from>$CurrentOrderLine/corecom:RootParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID/text()</from>
                                          <to>$RootParentOrderLine</to>
                                       </copy>
                                    </assign>
                                    <if name="AnalyzingTheRootParentOrderLine">
                                       <documentation/>
                                       <condition>($RootParentOrderLine != '') and ($RootParentOrderLine != $CurrentOrderLine/corecom:Identification/corecom:ApplicationObjectKey/corecom:ID) and ($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:Identification/corecom:ApplicationObjectKey/corecom:ID = $RootParentOrderLine]/corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Ofertas' or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:Identification/corecom:ApplicationObjectKey/corecom:ID = $RootParentOrderLine]/corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Recarga' or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:Identification/corecom:ApplicationObjectKey/corecom:ID = $RootParentOrderLine]/corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Ofertas Viva Sky') and ($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:Identification/corecom:ApplicationObjectKey/corecom:ID = $RootParentOrderLine]/corecom:InstalledProductReference/corecom:Custom/corecomcust:Duration != '')</condition>
                                       <sequence name="SetTheSameDuration">
                                          <if name="IfNotUpgradeRecarga">
                                             <documentation>
                                                <![CDATA[IS NOT UPGRADE]]>
                                             </documentation>
                                             <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode !="Upgrade de Recarga"</condition>
                                             <assign name="SetDurationParentToChild">
                                                <copy>
                                                   <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:Identification/corecom:ApplicationObjectKey/corecom:ID = $RootParentOrderLine]/corecom:InstalledProductReference/corecom:Custom/corecomcust:Duration</from>
                                                   <to>$InstalledProductReference/corecom:Custom/corecomcust:Duration</to>
                                                </copy>
                                                <extensionAssignOperation>
                                                   <bpelx:insertAfter>
                                                      <?audit suppress oracle.ide.xml.validation-incomplete?>
                                                      <bpelx:from>$InstalledProductReference/corecom:Custom/corecomcust:Duration</bpelx:from>
                                                      <bpelx:to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[position() = $ForEachOne]/corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable</bpelx:to>
                                                   </bpelx:insertAfter>
                                                </extensionAssignOperation>
                                             </assign>
                                             <else>
                                                <documentation>
                                                   <![CDATA[IS UPGRADE]]>
                                                </documentation>
                                                <sequence>
                                                   <empty name="DoNothing"/>
                                                </sequence>
                                             </else>
                                          </if>
                                       </sequence>
                                    </if>
                                    <sequence name="QueryProposal">
                                       <if name="Verify_SalesChannel_equal_SPW">
                                          <documentation>
                                             <![CDATA[Verify_SalesChannel_equal_SPW]]>
                                          </documentation>
                                          <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:SalesChannelCode='SpeedWeb' and $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[position() = $ForEachOne]/corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Equipamento' and ($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[position() = $ForEachOne]/corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'PayTV' or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[position() = $ForEachOne]/corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Banda Larga')</condition>
                                          <sequence>
                                             <if name="If_A_LA_CARTE_BANDA_LARGA">
                                                <documentation>
                                                   <![CDATA[is_a_lacarte_banda_larga]]>
                                                </documentation>
                                                <condition>($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:Identification/corecom:ApplicationObjectKey/corecom:ID = $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[position() = $ForEachOne]/corecom:ParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID]/corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'A La Carte') and ($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:Identification/corecom:ApplicationObjectKey/corecom:ID = $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[position() = $ForEachOne]/corecom:ParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID]/corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Banda Larga')</condition>
                                                <sequence name="Sequence50">
                                                   <assign name="AssignQueryProposal_BL">
                                                      <copy>
                                                         <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/corecom:CustomerPartyReference/corecom:CustomerPartyAccountIdentification/corecom:ID</from>
                                                         <to>$QueryProposal_BL_Query_Proposal_BL_DA_InputVariable.InputParameters/db2:VA_CUSTOMER</to>
                                                      </copy>
                                                   </assign>
                                                   <invoke name="QueryProposal_BL"
                                                           partnerLink="Query_Proposal_BL_DA"
                                                           portType="ns19:Query_Proposal_BL_DA_ptt"
                                                           operation="Query_Proposal_BL_DA"
                                                           inputVariable="QueryProposal_BL_Query_Proposal_BL_DA_InputVariable"
                                                           outputVariable="QueryProposal_BL_Query_Proposal_BL_DA_OutputVariable"
                                                           bpelx:invokeAsDetail="no"/>
                                                   <assign name="AssignQueryProposal_BL_Response">
                                                      <copy bpelx:insertMissingToData="yes">
                                                         <from>string($QueryProposal_BL_Query_Proposal_BL_DA_OutputVariable.OutputParameters/db2:VA_SMARTCARD)</from>
                                                         <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[$ForEachOne]/corecom:InstalledProductReference/corecom:AlternateTrackingNumber</to>
                                                      </copy>
                                                      <copy bpelx:insertMissingToData="yes">
                                                         <from>string($QueryProposal_BL_Query_Proposal_BL_DA_OutputVariable.OutputParameters/db2:VA_IRD)</from>
                                                         <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[$ForEachOne]/corecom:InstalledProductReference/corecom:SerialNumber</to>
                                                      </copy>
                                                      <copy bpelx:insertMissingToData="yes">
                                                         <from>string($QueryProposal_BL_Query_Proposal_BL_DA_OutputVariable.OutputParameters/db2:VA_DS_IRD)</from>
                                                         <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[$ForEachOne]/corecom:InstalledProductReference/corecom:Custom/corecomcust:ModelDescription</to>
                                                      </copy>
                                                      <copy bpelx:insertMissingToData="yes">
                                                         <from>string($QueryProposal_BL_Query_Proposal_BL_DA_OutputVariable.OutputParameters/db2:VA_NR_OS)</from>
                                                         <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[$ForEachOne]/ford:Custom/corecomcust:WorkOrderReference/corecomcust:WorkOrderIdentification/corecom:ID</to>
                                                      </copy>
                                                   </assign>
                                                </sequence>
                                                <!--<else>
                          <documentation>not_banda_larga</documentation>
                          <sequence>
                            <assign name="AssignQueryProposal">
                              <copy ignoreMissingFromData="yes"
                                    bpelx:insertMissingToData="yes">
                                <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/corecom:CustomerPartyReference/corecom:CustomerPartyAccountIdentification/corecom:ID</from>
                                <to>$QueryProposal_DA_QueryProposal_DA_InputVariable.InputParameters/db:VA_CUSTOMER</to>
                              </copy>
                              <copy ignoreMissingFromData="yes"
                                    bpelx:insertMissingToData="yes">
                                <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[position() = $ForEachOne]/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name = 'No. SmartCard/SimCard']/corecom:Value</from>
                                <to>$QueryProposal_DA_QueryProposal_DA_InputVariable.InputParameters/db:VA_SMARTCARD</to>
                              </copy>
                            </assign>
                            <invoke name="QueryProposal_DA"
                                    partnerLink="QueryProposal_DA"
                                    portType="ns6:QueryProposal_DA_ptt"
                                    operation="QueryProposal_DA"
                                    inputVariable="QueryProposal_DA_QueryProposal_DA_InputVariable"
                                    outputVariable="QueryProposal_DA_QueryProposal_DA_OutputVariable"
                                    bpelx:invokeAsDetail="no"/>
                            <assign name="AssignWorkOrderReference">
                              <copy ignoreMissingFromData="yes"
                                    bpelx:insertMissingToData="yes">
                                <from>$QueryProposal_DA_QueryProposal_DA_OutputVariable.OutputParameters/db:VA_SUBID</from>
                                <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[$ForEachOne]/corecom:InstalledProductReference/corecom:Custom/corecom:ItemReference/corecom:Custom/corecomcust:Equipment/corecomcust:EMMGIdentification/corecom:ID</to>
                              </copy>
                              <copy ignoreMissingFromData="yes"
                                    bpelx:insertMissingToData="yes">
                                <from>$QueryProposal_DA_QueryProposal_DA_OutputVariable.OutputParameters/db:VA_OS</from>
                                <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[$ForEachOne]/ford:Custom/corecomcust:WorkOrderReference/corecomcust:WorkOrderIdentification/corecom:ID</to>
                              </copy>
                            </assign>
                          </sequence>
                        </else> -->
                                             </if>
                                          </sequence>
                                       </if>
                                    </sequence>
                                 </sequence>
                              </scope>
                           </forEach>
                           <assign name="Assign_currentSystemDateTime">
                              <copy>
                                 <from>xp20:current-dateTime()</from>
                                 <to>$currentSystemDateTime</to>
                              </copy>
                           </assign>
                           <if name="IfLockedInProgress_Item">
                              <condition>count( $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress'])>0</condition>
                              <sequence name="Sequence61">
                                 <sequence name="Sequence58">
                                    <forEach parallel="no" counterName="counter" name="ForEachLockedInProgressItem">
                                       <startCounterValue>1</startCounterValue>
                                       <finalCounterValue>count( $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress'])</finalCounterValue>
                                       <scope name="SetLineEffectiveTimePeriod" exitOnStandardFault="no">
                                          <variables>
                                             <variable name="CurrentLockedInProgressLine"
                                                       element="ford:FulfillmentOrderLine"/>
                                          </variables>
                                          <sequence name="CalculateDates">
                                             <assign name="SetCurrentLockedInProgressItem">
                                                <copy bpelx:insertMissingToData="yes">
                                                   <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[
                            corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress'][position() = $counter]</from>
                                                   <to>$CurrentLockedInProgressLine</to>
                                                </copy>
                                             </assign>
                                             <if name="IfActionIsDelete">
                                                <documentation>
                                                   <![CDATA[yes]]>
                                                </documentation>
                                                <condition>$CurrentLockedInProgressLine/ford:ServiceActionCode = "DELETE" and $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode != "Upgrade de Recarga"</condition>
                                                <assign name="SetEffectiveTimePeriod">
                                                   <copy bpelx:insertMissingToData="yes">
                                                      <from>$currentSystemDateTime</from>
                                                      <to>$CurrentLockedInProgressLine/corecom:EffectiveTimePeriod/corecom:EndDateTime</to>
                                                   </copy>
                                                </assign>
                                                <elseif>
                                                   <documentation>
                                                      <![CDATA[UpgradeRecarga]]>
                                                   </documentation>
                                                   <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Upgrade de Recarga"</condition>
                                                   <empty name="DoNothing"/>
                                                </elseif>
                                                <elseif>
                                                   <documentation>
                                                      <![CDATA[ADD]]>
                                                   </documentation>
                                                   <condition>$CurrentLockedInProgressLine/ford:ServiceActionCode = "ADD"</condition>
                                                   <if name="If_RootItemCategoryIsCharge">
                                                      <documentation>
                                                         <![CDATA[yes]]>
                                                      </documentation>
                                                      <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ corecom:Identification/corecom:ApplicationObjectKey/corecom:ID = $CurrentLockedInProgressLine/corecom:RootParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID] /corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Recarga'</condition>
                                                   <scope name="QueryInstalledProductDuration" exitOnStandardFault="no">
                                                         <variables>
                                                            <variable name="QueryInstalledProductDuration_InputVariable"
                                                                      messageType="ns2:QueryInstalledProductDurationRequestMsg"/>
                                                            <variable name="QueryInstalledProductDuration_OutputVariable"
                                                                      messageType="ns2:QueryInstalledProductDurationResponseMsg"/>
                                                            <variable name="RechargeLine"
                                                                      element="ford:FulfillmentOrderLine"/>
                                                         </variables>
                                                         <sequence>
                                                            <assign name="AssignRechargeLine">
                                                               <copy>
                                                                  <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:Identification/corecom:ApplicationObjectKey/corecom:ID = $CurrentLockedInProgressLine/corecom:RootParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID]</from>
                                                                  <to>$RechargeLine</to>
                                                               </copy>
                                                            </assign>
                                                            <assign name="ProcessSoftwareFulfillmentOrderEBM_To_QueryInstalledProductDurationEBM">
                                                               <bpelx:annotation>
                                                                  <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                               </bpelx:annotation>
                                                               <copy>
                                                                  <from>ora:doXSLTransformForDoc("xsl/ProcessSoftwareFulfillmentOrderEBM_To_QueryInstalledProductDurationEBM.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM, "RechargeLine", $RechargeLine)</from>
                                                                  <to variable="QueryInstalledProductDuration_InputVariable"
                                                                      part="QueryInstalledProductDurationEBM"/>
                                                               </copy>
                                                            </assign>
                                                            <invoke name="Invoke_QueryInstalledProductDuration"
                                                                    partnerLink="QueryInstalledProductDurationEBF"
                                                                    portType="ns2:QueryInstalledProductDurationEBF"
                                                                    operation="QueryInstalledProductDuration"
                                                                    inputVariable="QueryInstalledProductDuration_InputVariable"
                                                                    bpelx:invokeAsDetail="no"
                                                                    outputVariable="QueryInstalledProductDuration_OutputVariable"/>
                                                            <assign name="SetEffectiveTimePeriod">
                                                               <copy bpelx:insertMissingToData="yes">
                                                                  <from>$QueryInstalledProductDuration_OutputVariable.QueryInstalledProductDurationResponseEBM/instprod:DataArea/instprod:QueryInstalledProductDurationResponse/corecom:EffectiveTimePeriod/corecom:StartDateTime</from>
                                                                  <to>$CurrentLockedInProgressLine/corecom:EffectiveTimePeriod/corecom:StartDateTime</to>
                                                               </copy>
                                                               <copy bpelx:insertMissingToData="yes">
                                                                  <from>$QueryInstalledProductDuration_OutputVariable.QueryInstalledProductDurationResponseEBM/instprod:DataArea/instprod:QueryInstalledProductDurationResponse/corecom:EffectiveTimePeriod/corecom:EndDateTime</from>
                                                                  <to>$CurrentLockedInProgressLine/corecom:EffectiveTimePeriod/corecom:EndDateTime</to>
                                                               </copy>
                                                            </assign>
                                                         </sequence>
                                                      </scope>
                                                      <else>
                                                         <documentation>
                                                            <![CDATA[no]]>
                                                         </documentation>
                                                         <sequence>
                                                            <assign name="SetEffectiveStartDate">
                                                               <copy bpelx:insertMissingToData="yes">
                                                                  <from>xp20:add-dayTimeDuration-to-dateTime($currentSystemDateTime, concat('P', $CurrentLockedInProgressLine/corecom:ItemReference/corecom:BillingStartCode/text(), 'M'))</from>
                                                                  <to>$CurrentLockedInProgressLine/corecom:EffectiveTimePeriod/corecom:StartDateTime</to>
                                                               </copy>
                                                            </assign>
                                                            <if name="ExistsDuration">
                                                               <documentation>
                                                                  <![CDATA[Exists]]>
                                                               </documentation>
                                                               <condition>$CurrentLockedInProgressLine/corecom:InstalledProductReference/corecom:Custom/corecomcust:Duration != ''</condition>
                                                               <sequence name="ImmediateDiscount">
                                                               <!-- [SUSALM-1726] 30/03/2022 - Michel: Bloco comentado devido a falta de endDate no Siebel, evitando que o desconto fique para sempre no parque do cliente -->
                                                                  <!-- <if name="If_OrderContainsImmediateDiscountItens"> -->
                                                                     <!-- <condition>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Desconto Imediato']/corecom:Value = 'Y']) &gt; 0 and ($CurrentLockedInProgressLine/corecom:InstalledProductReference/corecom:Custom/corecomcust:Duration) &gt;=1</condition> -->
                                                                     <!-- <assign name="SetImmediateDiscountDuration"> -->
                                                                        <!-- <copy bpelx:insertMissingToData="yes"> -->
                                                                           <!-- <from>string(number($CurrentLockedInProgressLine/corecom:InstalledProductReference/corecom:Custom/corecomcust:Duration)-1)</from> -->
                                                                           <!-- <to>$CurrentLockedInProgressLine/corecom:InstalledProductReference/corecom:Custom/corecomcust:Duration</to> -->
                                                                        <!-- </copy> -->
                                                                     <!-- </assign> -->
                                                                  <!-- </if> -->
                                                              <!-- Fim [SUSALM-1726] -->
                                                                  <if name="If_IntegerDuration">
                                                                     <condition>round(number($CurrentLockedInProgressLine/corecom:InstalledProductReference/corecom:Custom/corecomcust:Duration/text())) = number($CurrentLockedInProgressLine/corecom:InstalledProductReference/corecom:Custom/corecomcust:Duration/text())</condition>
                                                                     <assign name="SetEffectiveEndDate">
                                                                        <copy bpelx:insertMissingToData="yes">
                                                                           <from>xp20:add-dayTimeDuration-to-dateTime(
                                            $CurrentLockedInProgressLine/corecom:EffectiveTimePeriod/corecom:StartDateTime, 
                                            concat('P',$CurrentLockedInProgressLine/corecom:InstalledProductReference/corecom:Custom/corecomcust:Duration/text(),'M'))</from>
                                                                           <to>$CurrentLockedInProgressLine/corecom:EffectiveTimePeriod/corecom:EndDateTime</to>
                                                                        </copy>
                                                                     </assign>
                                                                     <else>
                                                                        <assign name="SetEffectiveEndDate">
                                                                           <copy bpelx:insertMissingToData="yes">
                                                                              <from>xp20:add-dayTimeDuration-to-dateTime(
                                            $CurrentLockedInProgressLine/corecom:EffectiveTimePeriod/corecom:StartDateTime, 
                                            concat('P',string(number($CurrentLockedInProgressLine/corecom:InstalledProductReference/corecom:Custom/corecomcust:Duration/text())*30),'D'))</from>
                                                                              <to>$CurrentLockedInProgressLine/corecom:EffectiveTimePeriod/corecom:EndDateTime</to>
                                                                           </copy>
                                                                        </assign>
                                                                     </else>
                                                                  </if>
                                                               </sequence>
                                                               <elseif>
                                                                  <documentation/>
                                                                  <condition>(($CurrentLockedInProgressLine/corecom:InstalledProductReference/corecom:Custom/corecomcust:Category='Pay Per View') or($CurrentLockedInProgressLine/corecom:InstalledProductReference/corecom:Custom/corecomcust:Category='Temporada'))</condition>
                                                                  <assign name="SetEffectiveEndDate">
                                                                     <copy bpelx:insertMissingToData="yes">
                                                                        <from>concat(substring($CurrentLockedInProgressLine/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name = 'ExhibitionEnd']/corecom:Value,1,4),'-',substring($CurrentLockedInProgressLine/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name = 'ExhibitionEnd']/corecom:Value,6,2),'-',substring($CurrentLockedInProgressLine/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name = 'ExhibitionEnd']/corecom:Value,9,2),'T',substring($CurrentLockedInProgressLine/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name = 'ExhibitionEnd']/corecom:Value,12,2),':',substring($CurrentLockedInProgressLine/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name = 'ExhibitionEnd']/corecom:Value,15,2),':',substring($CurrentLockedInProgressLine/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name = 'ExhibitionEnd']/corecom:Value,18,2),'-03:00')</from>
                                                                        <to>$CurrentLockedInProgressLine/corecom:EffectiveTimePeriod/corecom:EndDateTime</to>
                                                                     </copy>
                                                                  </assign>
                                                               </elseif>
                                                            </if>
                                                         </sequence>
                                                      </else>
                                                   </if>
                                                </elseif>
                                             </if>
                                             <assign name="OverrideOrderLineInInputVariable">
                                                <copy>
                                                   <from>$CurrentLockedInProgressLine</from>
                                                   <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[
                        corecom:Identification/corecom:ID = $CurrentLockedInProgressLine/corecom:Identification/corecom:ID]</to>
                                                </copy>
                                             </assign>
                                          </sequence>
                                       </scope>
                                    </forEach>
                                    <if name="If_RechargeCalculator">
                                       <condition>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Recarga' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Pacote Básico']) = 2 and $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = 'Inclusion' and (count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification/corecom:Name = 'Sky Prioridade Ativacao' and corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification/corecom:Value = '2' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Recarga' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Pacote Básico']/corecom:EffectiveTimePeriod/corecom:StartDateTime) > 0)</condition>
                                       <sequence>
                                          <assign name="Assign_ServiceTimePeriod">
                                             <copy>
                                                <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification/corecom:Name = 'Sky Prioridade Ativacao' and corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification/corecom:Value = '1' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Recarga' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Pacote Básico']/ford:FulfillmentOrderSchedule/corecom:ServiceTimePeriod/corecom:Duration</from>
                                                <to>$ServiceTimePeriod</to>
                                             </copy>
                                          </assign>
                                          <assign name="Assign_RechargeProductID">
                                             <copy>
                                                <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification/corecom:Name = 'Sky Prioridade Ativacao' and corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification/corecom:Value = '2' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Recarga' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Pacote Básico']/corecom:Identification/corecom:ApplicationObjectKey/corecom:ID</from>
                                                <to>$RechargeProductID</to>
                                             </copy>
                                          </assign>
                                          <assign name="Assign_Start_End_DateTime">
                                             <copy>
                                                <from>xp20:add-dayTimeDuration-to-dateTime(xp20:add-dayTimeDuration-to-dateTime($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification/corecom:Name = 'Sky Prioridade Ativacao' and corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification/corecom:Value = '2' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Recarga' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Pacote Básico']/corecom:EffectiveTimePeriod/corecom:StartDateTime, 'P1D'),$ServiceTimePeriod)</from>
                                                <to>$RechargeStartDateTime</to>
                                             </copy>
                                             <copy>
                                                <from>xp20:add-dayTimeDuration-to-dateTime($RechargeStartDateTime,$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification/corecom:Name = 'Sky Prioridade Ativacao' and corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification/corecom:Value = '2' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Recarga' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Pacote Básico']/ford:FulfillmentOrderSchedule/corecom:ServiceTimePeriod/corecom:Duration)</from>
                                                <to>$RechargeEndDateTime</to>
                                             </copy>
                                          </assign>
                                          <forEach parallel="no" counterName="foreachCounter" name="Foreach">
                                             <startCounterValue>1</startCounterValue>
                                             <finalCounterValue>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:RootParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID = $RechargeProductID and ford:ServiceActionCode = 'ADD'])</finalCounterValue>
                                             <scope name="Scope23">
                                                <assign name="Assign_date_status">
                                                   <copy>
                                                      <from>$RechargeStartDateTime</from>
                                                      <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:RootParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID = $RechargeProductID and ford:ServiceActionCode = 'ADD'][$foreachCounter]/corecom:EffectiveTimePeriod/corecom:StartDateTime</to>
                                                   </copy>
                                                   <copy>
                                                      <from>$RechargeEndDateTime</from>
                                                      <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:RootParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID = $RechargeProductID and ford:ServiceActionCode = 'ADD'][$foreachCounter]/corecom:EffectiveTimePeriod/corecom:EndDateTime</to>
                                                   </copy>
                                                </assign>
                                             </scope>
                                          </forEach>
                                       </sequence>
                                    </if><sequence name="Sequence48"
                                                   xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <assign name="AssignCurrentDate">
         <copy>
            <from>xp20:current-date()</from>
            <to>$CurrentSystemDt</to>
         </copy>
      </assign>
      <assign name="FormatCurrentDate">
         <copy>
            <from>xp20:format-dateTime(string($CurrentSystemDt),"[Y0001]/[M01]/[D01]")</from>
            <to>$CurrentSystemDtFormated</to>
         </copy>
      </assign>
   </sequence></sequence><scope name="Scope_AmazonStream"
                                xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      
      <variables>
                                       <variable name="Invoke_UpdateFulfillmentOrder_IntegrationError_InputVariable"
                                                 messageType="ns20:UpdateFulfillmentOrderSynchronouslyReqMsg"/>
                                       <variable name="Invoke_UpdateFulfillmentOrder_IntegrationError_OutputVariable"
                                                 messageType="ns20:UpdateFulfillmentOrderSynchronouslyRespMsg"/>
                                       <variable name="x-system-origin" type="xsd:string"/>
                                    </variables><faultHandlers><catchAll>
            <sequence name="Sequence_AmazonStream_Integration_Error">
               <assign name="Transformation_ReqUpdateFulfillmentOrder_IntegrationError">
                  <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
                     <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                  </bpelx:annotation>
                  <copy>
                     <from>ora:doXSLTransformForDoc("xsl/Transformation_ReqUpdateFulfillmentOrder_AmazonIntegrationError.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                     <to variable="Invoke_UpdateFulfillmentOrder_IntegrationError_InputVariable"
                         part="UpdateFulfillmentOrderSynchronouslyEBM"/>
                  </copy>
               </assign>
               <invoke name="Invoke_UpdateFulfillmentOrder_IntegrationError" bpelx:invokeAsDetail="no"
                       partnerLink="CommunicationsFulfillmentOrder" portType="ns20:CommunicationsFulfillmentOrderEBS"
                       operation="UpdateFulfillmentOrderSynchronously"
                       inputVariable="Invoke_UpdateFulfillmentOrder_IntegrationError_InputVariable"
                       outputVariable="Invoke_UpdateFulfillmentOrder_IntegrationError_OutputVariable"
                       xmlns:bpelx="http://schemas.oracle.com/bpel/extension"/>
            </sequence>
         </catchAll>
      </faultHandlers>
                                    <sequence name="Sequence86">
                                       <assign name="Assign_setXSystemOrigin">
                                          <copy>
                                             <from>'SOA'</from>
                                             <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$x-system-origin</to>
                                          </copy>
                                       </assign>
                                       <if name="If_AmazonSkuAddDeleteEqual">
                                          <condition>xp20:compare($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress']/corecom:ItemReference/corecom:SpecificationGroup[corecom:Specification/corecom:Name='Streaming Partner' and corecom:Specification/corecom:Value='amazonprime']/corecom:Specification[corecom:Name='SKU']/corecom:Value/text(), $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='DELETE']/corecom:ItemReference/corecom:SpecificationGroup[corecom:Specification/corecom:Name='Streaming Partner' and corecom:Specification/corecom:Value='amazonprime']/corecom:Specification[corecom:Name='SKU']/corecom:Value/text()) = 0</condition><empty name="Do_Nothing"
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/><else>
                                             <if name="If_IsDeleteAmazonStream">
                                                <condition>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='DELETE']/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Streaming Partner' and corecom:Value='amazonprime']) &gt; 0 and count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD']/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Streaming Partner' and corecom:Value='amazonprime'])=0</condition>
                                                <sequence name="Sequence89">
                                                   <scope name="Scope_AmazonDelete">
                                                      <faultHandlers>
                                                         <catch faultName="ns64:ValidationDeleteError"
                                                                faultVariable="ValidationDeleteError"
                                                                faultElement="ns65:EntitlementErrorResponse"><sequence name="Sequence95"><empty name="DoNothing"
                                                                                                                                                                                xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/></sequence></catch>
                                                      </faultHandlers>
                                                      <sequence name="Sequence_AmazonCancellation">
                                                         <assign name="Assign_Invoke_DeleteAmazonStream"
                                                                 xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                                            <copy>
                                                               <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/corecom:Identification/corecom:ID/text()</from>
                                                               <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$Invoke_AmazonStream_Delete_InputVariable.request/ns65:order</to>
                                                            </copy>
                                                            <copy>
                                                               <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/corecom:CustomerPartyReference/corecom:CustomerPartyAccountIdentification/corecom:ID/text()</from>
                                                               <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$Invoke_AmazonStream_Delete_InputVariable.request/ns65:id</to>
                                                            </copy>
                                                         </assign>
                                                         <invoke name="Invoke_AmazonStream" partnerLink="AmazonApi"
                                                                 portType="ns64:AmazonApi_ptt" operation="Delete"
                                                                 inputVariable="Invoke_AmazonStream_Delete_InputVariable"
                                                                 outputVariable="Invoke_AmazonStream_Delete_OutputVariable"
                                                                 bpelx:invokeAsDetail="no"
                                                                 bpelx:inputHeaderVariable="x-system-origin"/>
                                                      </sequence>
                                                   </scope>
                                                </sequence>
                                                <elseif>
                                                   <condition>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress']/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Streaming Partner' and corecom:Value='amazonprime'])&gt;0</condition>
                                                   <sequence name="Sequence_AmazonAcquisition">
                                                      <assign name="Assign_Input_Invoke_QueryParty">
                                                         <copy>
                                                            <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SKYAccountNumber/text()</from>
                                                            <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$Invoke_QueryParty_QueryCustomerParty_InputVariable.QueryCustomerPartyEBM/custparty:DataArea/custparty:QueryCustomerParty/corecom:Identification/corecom:ID</to>
                                                         </copy>
                                                         <copy>
                                                            <from>"process"</from>
                                                            <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$Invoke_QueryParty_QueryCustomerParty_InputVariable.QueryCustomerPartyEBM/corecom:EBMHeader/corecom:VerbCode</to>
                                                         </copy>
                                                         <copy>
                                                            <from>"PRODUCTION"</from>
                                                            <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$Invoke_QueryParty_QueryCustomerParty_InputVariable.QueryCustomerPartyEBM/corecom:EBMHeader/corecom:MessageProcessingInstruction/corecom:EnvironmentCode</to>
                                                         </copy>
                                                      </assign>
                                                      <invoke name="Invoke_QueryParty"
                                                              partnerLink="CustomerPartyEBS_SOA"
                                                              portType="ns9:CommunicationsCustomerPartyEBS"
                                                              operation="QueryCustomerParty"
                                                              inputVariable="Invoke_QueryParty_QueryCustomerParty_InputVariable"
                                                              outputVariable="Invoke_QueryParty_QueryCustomerParty_OutputVariable"
                                                              bpelx:invokeAsDetail="no"/>
                                                      <if name="If_CheckEmail">
                                                         <documentation>
                                                            <![CDATA[Exist Email]]>
                                                         </documentation>
                                                         <condition>string-length($Invoke_QueryParty_QueryCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/corecom:PartyLocation/corecom:LocationReference/corecom:Custom/corecomcust:EmailCommunication/text()) &gt; 0</condition>
                                                         <assign name="Assign_Email_CreateAmazon">
                                                            <copy>
                                                               <from>$Invoke_QueryParty_QueryCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/corecom:PartyLocation/corecom:LocationReference/corecom:Custom/corecomcust:EmailCommunication/text()</from>
                                                               <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$Invoke_AmazonStream_Create_InputVariable.request/ns65:email</to>
                                                            </copy>
                                                         </assign>
                                                         <else>
                                                            <documentation>
                                                               <![CDATA[Is empty]]>
                                                            </documentation>
                                                            <empty name="DoNothing"/>
                                                         </else>
                                                      </if>
                                                      <if name="If_CheckPhoneNumber">
                                                         <documentation>
                                                            <![CDATA[Exist Phone Number]]>
                                                         </documentation>
                                                         <condition>string-length($Invoke_QueryParty_QueryCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:MobileCommunication/corecom:AreaCode/text()) &gt; 0  and string-length($Invoke_QueryParty_QueryCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:MobileCommunication/corecom:LocalNumber/text()) &gt; 0</condition><assign name="Assign_Email_CreateAmazon"
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      
   <copy>
         <from>concat($Invoke_QueryParty_QueryCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:MobileCommunication/corecom:AreaCode/text(),$Invoke_QueryParty_QueryCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:MobileCommunication/corecom:LocalNumber/text())</from>
         <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$Invoke_AmazonStream_Create_InputVariable.request/ns65:phoneNumber</to>
      </copy></assign><else><empty name="DoNothing" xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/></else>
                                                      </if>
                                                      <scope name="Scope_AmazonCreateRetry">
                                                         <faultHandlers>
                                                            <catch faultName="ns64:ValidationCreateError"
                                                                   faultVariable="ValidationCreateError"
                                                                   faultElement="ns65:EntitlementErrorResponse"><empty name="Do_Nothing"
                                                                                                                       xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/></catch>
                                                            <catch faultName="ns64:InternalCreateError"
                                                                   faultVariable="InternalCreateError"
                                                                   faultElement="ns65:EntitlementErrorResponse">
                                                               <scope name="Scope_AmazonRetry">
                                                                  <variables>
                                                                     <variable name="countAmazonRetry"
                                                                               type="xsd:integer"/>
                                                                  </variables>
                                                                  <sequence name="Sequence_Check_IsRetry">
                                                                     <if name="If_isRetry">
                                                                        <condition>$InternalCreateError/ns65:retry/text() = "true"</condition>
                                                                        <sequence>
                                                                           <assign name="Assign_InitCountAmazonRetry">
                                                                              <copy>
                                                                                 <from>1</from>
                                                                                 <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$countAmazonRetry</to>
                                                                              </copy>
                                                                           </assign>
                                                                           <while name="While_AmazonRetry">
                                                                              <condition>$countAmazonRetry &lt;= 3</condition>
                                                                              <sequence name="Sequence_AmazonAcquisition"
                                                                                        xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                                                                 <scope name="Scope27">
                                                                                    <faultHandlers>
                                                                                       <catch faultName="ns64:ValidationCreateError"
                                                                                              faultVariable="ValidationCreateError"
                                                                                              faultElement="ns65:EntitlementErrorResponse">
                                                                                          <sequence>
                                                                                             <empty name="Do_Nothing"/>
                                                                                          </sequence>
                                                                                       </catch>
                                                                                       <catch faultName="ns64:InternalCreateError"
                                                                                              faultVariable="IntInternalCreateError"
                                                                                              faultElement="ns65:EntitlementErrorResponse">
                                                                                          <sequence name="Sequence84">
                                                                                             <if name="If_intIsRetry">
                                                                                                <condition>$IntInternalCreateError/ns65:retry/text() = "true"</condition>
                                                                                                <assign name="Assign_AddCountAmazonRetry"
                                                                                                        xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                                                                                   <copy>
                                                                                                      <from>$countAmazonRetry + 1</from>
                                                                                                      <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$countAmazonRetry</to>
                                                                                                   </copy>
                                                                                                </assign>
                                                                                                <elseif>
                                                                                                   <documentation>
                                                                                                      <![CDATA[If run thrice up error]]>
                                                                                                   </documentation>
                                                                                                   <condition>$countAmazonRetry = 3</condition><throw name="ThrowAmazonRunThrice"
                                                                                                                                                      faultName="ns64:InternalCreateError"
                                                                                                                                                      faultVariable="IntInternalCreateError"
                                                                                                                                                      xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/></elseif>
                                                                                                <else>
                                                                                                   <sequence name="Sequence85">
                                                                                                      <throw name="ThrowAmazonIntRetry"
                                                                                                             faultName="ns64:InternalCreateError"
                                                                                                             faultVariable="IntInternalCreateError"/>
                                                                                                   </sequence>
                                                                                                </else>
                                                                                             </if>
                                                                                          </sequence>
                                                                                       </catch>
                                                                                    </faultHandlers>
                                                                                    <sequence name="Sequence83"><invoke name="Invoke_AmazonStream"
                                                                                               partnerLink="AmazonApi"
                                                                                               portType="ns64:AmazonApi_ptt"
                                                                                               operation="Create"
                                                                                               inputVariable="Invoke_AmazonStream_Create_InputVariable"
                                                                                               outputVariable="Invoke_AmazonStream_Create_OutputVariable"
                                                                                               xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                    bpelx:invokeAsDetail="no" bpelx:inputHeaderVariable="x-system-origin"/>
                                                                                       <assign name="Assign_AddCountAmazonRetryFinish"
                                                                                               xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                                                                          <copy>
                                                                                             <from>3</from>
                                                                                             <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$countAmazonRetry</to>
                                                                                          </copy>
                                                                                       </assign>
                                                                                    </sequence>
                                                                                 </scope>
                                                                              </sequence>
                                                                           </while>
                                                                        </sequence>
                                                                        <else><throw name="ThrowRetryAmazon"
                                                                                     faultName="ns64:InternalCreateError"
                                                                                     faultVariable="InternalCreateError"
                                                                                     xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/></else>
                                                                     </if>
                                                                  </sequence>
                                                               </scope>
                                                            </catch>
                                                         </faultHandlers>
                                                         <sequence name="Sequence_AmazonCreateRetry">
                                                            <assign name="Assign_Invoke_AmazonStream">
                                                               <copy>
                                                                  <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/corecom:Identification/corecom:ID/text()</from>
                                                                  <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$Invoke_AmazonStream_Create_InputVariable.request/ns65:order</to>
                                                               </copy>
                                                               <copy>
                                                                  <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress']/corecom:ItemReference/corecom:SpecificationGroup[corecom:Specification/corecom:Name='Streaming Partner' and corecom:Specification/corecom:Value='amazonprime']/corecom:Specification[corecom:Name='SKU']/corecom:Value/text()</from>
                                                                  <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$Invoke_AmazonStream_Create_InputVariable.request/ns65:eligibleOfferIds</to>
                                                               </copy>
                                                               <copy>
                                                                  <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/corecom:CustomerPartyReference/corecom:CustomerPartyAccountIdentification/corecom:ID/text()</from>
                                                                  <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$Invoke_AmazonStream_Create_InputVariable.request/ns65:id</to>
                                                               </copy>
                                                            </assign>
                                                            <invoke name="Invoke_AmazonStream"
                                                                    partnerLink="AmazonApi"
                                                                    portType="ns64:AmazonApi_ptt" operation="Create"
                                                                    inputVariable="Invoke_AmazonStream_Create_InputVariable"
                                                                    outputVariable="Invoke_AmazonStream_Create_OutputVariable"
                                                                    bpelx:invokeAsDetail="no"
                                                                    bpelx:inputHeaderVariable="x-system-origin"/>
                                                         </sequence>
                                                      </scope>
                                                   </sequence>
                                                </elseif>
                                                <else>
                                                   <empty name="Do_Nothing"/>
                                                </else>
                                             </if>
                                          </else>
                                       </if>
                                    </sequence>
                                 </scope><scope name="Scope_DisneyStream">
                                    <variables>
                                       <variable name="Invoke_UpdateFulfillmentOrder_IntegrationError_InputVariable"
                                                 messageType="ns20:UpdateFulfillmentOrderSynchronouslyReqMsg"/>
                                       <variable name="Invoke_UpdateFulfillmentOrder_IntegrationError_OutputVariable"
                                                 messageType="ns20:UpdateFulfillmentOrderSynchronouslyRespMsg"/>
                                    </variables>
                                    <faultHandlers>
                                       <catchAll>
                                          <sequence name="Sequence_DisneyStream_Integration_Error">
                                             <assign name="Transformation_ReqUpdateFulfillmentOrder_IntegrationError">
                                                <bpelx:annotation>
                                                   <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                </bpelx:annotation>
                                                <copy>
                                                   <from>ora:doXSLTransformForDoc("xsl/Transformation_ReqUpdateFulfillmentOrder_AmazonIntegrationError.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                                   <to variable="Invoke_UpdateFulfillmentOrder_IntegrationError_InputVariable"
                                                       part="UpdateFulfillmentOrderSynchronouslyEBM"/>
                                                </copy>
                                             </assign>
                                             <invoke name="Invoke_UpdateFulfillmentOrder_IntegrationError"
                                                     bpelx:invokeAsDetail="no"
                                                     partnerLink="CommunicationsFulfillmentOrder"
                                                     portType="ns20:CommunicationsFulfillmentOrderEBS"
                                                     operation="UpdateFulfillmentOrderSynchronously"
                                                     inputVariable="Invoke_UpdateFulfillmentOrder_IntegrationError_InputVariable"
                                                     outputVariable="Invoke_UpdateFulfillmentOrder_IntegrationError_OutputVariable"/>
                                          </sequence>
                                       </catchAll>
                                    </faultHandlers>
                                    <if name="If_IsDeleteDisneyStream">
                                       <condition>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='DELETE']/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Streaming Partner' and (corecom:Value='disneyplus' or corecom:Value='starplus')]) > 0 and count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD']/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Streaming Partner' and (corecom:Value='disneyplus' or corecom:Value='starplus')])=0</condition>
                                       <sequence name="Sequence104">
                                          <scope name="Scope_Action_DisneyCancellation">
                                             <faultHandlers>
                                                <catchAll><scope name="Scope_Action_DisneyCancellationError"
                                                                 xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      
      <variables>
                                                         <variable name="countErrorDisney" type="xsd:integer"/>
                                                      </variables><sequence name="Sequence100">
         <assign name="Assign_SetCountRetry">
            <copy>
               <from>1</from>
               <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$countErrorDisney</to>
            </copy>
         </assign>
         <while name="While_RetryActionDisney">
            <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
               <bpelx:documentation>
                  <![CDATA[Retry de 4 tentativas]]>
               </bpelx:documentation>
            </bpelx:annotation>
            <condition>$countErrorDisney &lt; 5</condition>
            <sequence name="Sequence101">
               <scope name="Scope_Action_DisneyCancellationErrorRetry">
                  <faultHandlers>
                     <catchAll>
                        <sequence name="Sequence102">
                           <if name="If_Error_Is_retry">
                              <condition>$countErrorDisney = 4</condition>
                              <throw name="Throw_Error_Disney" faultName="ns41:fault500"/>
                              <else>
                                 <assign name="Assign_AddCountRetry">
                                    <copy>
                                       <from>$countErrorDisney+1</from>
                                       <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$countErrorDisney</to>
                                    </copy>
                                 </assign>
                              </else>
                           </if>
                        </sequence>
                     </catchAll>
                  </faultHandlers>
                  <sequence name="Sequence_Cancellation_Disney"
                            xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      
      
   <assign name="Transformation_Input_Disney_Delete" xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
         <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
      </bpelx:annotation>
      <copy>
         <from>ora:doXSLTransformForDoc("Transformations/Transformation_InputVariable_to_DisneyStream.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
         <to variable="Invoke_DisneyStream_oppEntitlement_InputVariable" part="request"/>
      </copy>
   </assign><invoke name="Invoke_DisneyStream" bpelx:invokeAsDetail="no" partnerLink="DisneyStream"
                    portType="ns41:DisneyStream_ptt" operation="oppEntitlement"
                    inputVariable="Invoke_DisneyStream_oppEntitlement_InputVariable"
                    outputVariable="Invoke_DisneyStream_oppEntitlement_OutputVariable"
                    xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                    xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/><assign name="Assign_FinishCountRetry" xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      
   <copy>
         <from>5</from>
         <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$countErrorDisney</to>
      </copy></assign></sequence>
               </scope>
            </sequence>
         </while>
      </sequence>
   </scope></catchAll>
                                             </faultHandlers>
                                             <sequence name="Sequence_DisneyCancellation">
                                                <assign name="Transformation_Input_Disney_Delete"
                                                        xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                                   <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
                                                      <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                   </bpelx:annotation>
                                                   <copy>
                                                      <from>ora:doXSLTransformForDoc("Transformations/Transformation_InputVariable_to_DisneyStream.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                                      <to variable="Invoke_DisneyStream_oppEntitlement_InputVariable"
                                                          part="request"/>
                                                   </copy>
                                                </assign>
                                                <invoke name="Invoke_DisneyStream" bpelx:invokeAsDetail="no"
                                                        partnerLink="DisneyStream" portType="ns41:DisneyStream_ptt"
                                                        operation="oppEntitlement"
                                                        inputVariable="Invoke_DisneyStream_oppEntitlement_InputVariable"
                                                        outputVariable="Invoke_DisneyStream_oppEntitlement_OutputVariable"/>
                                             </sequence>
                                          </scope>
                                       </sequence>
                                       <elseif>
                                          <condition>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress']/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Streaming Partner' and (corecom:Value='disneyplus' or corecom:Value='starplus')])&gt;0 and count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine/corecom:InstalledProductReference/corecom:Custom[corecomcust:SubCategory = 'Recarga']) &gt; 0</condition><sequence name="Sequence62"><assign name="AssignStarDate"
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                                <copy ignoreMissingFromData="yes">
                                                   <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Recarga' and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress']/corecom:EffectiveTimePeriod/corecom:StartDateTime</from>
                                                   <to>$CurrentStartDtDisney</to>
                                                </copy>
                                             </assign><assign name="FormatStartDate" xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                                <copy>
                                                   <from>xp20:format-dateTime(string($CurrentStartDtDisney),"[Y0001]/[M01]/[D01]")</from>
                                                   <to>$CurrentStartDtDisneyFormated</to>
                                                </copy>
                                             </assign><if name="If3">
                                                <documentation>
                                                   <![CDATA[Verifica se a recarga futura]]>
                                                </documentation>
                                                <condition>$CurrentStartDtDisneyFormated &lt;= $CurrentSystemDtFormated</condition>
                                                <sequence name="Sequence105">
                                                   <scope name="Scope_DisneyAcquisition_PrePago">
                                                      <faultHandlers>
                                                         <catchAll><scope name="Scope_Action_DisneyAcquisition_PrePagoError"
                                                                          xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      
      <variables>
                                                                  <variable name="countErrorDisney" type="xsd:integer"/>
                                                               </variables><sequence name="Sequence100">
         <assign name="Assign_SetCountRetry">
            <copy>
               <from>1</from>
               <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$countErrorDisney</to>
            </copy>
         </assign>
         <while name="While_RetryActionDisney">
            <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
               <bpelx:documentation>
                  <![CDATA[Retry de 4 tentativas]]>
               </bpelx:documentation>
            </bpelx:annotation>
            <condition>$countErrorDisney &lt; 5</condition>
            <sequence name="Sequence101">
               <scope name="Scope_Action_DisneyAcquisition_PrePagoErrorRetry">
                  <faultHandlers>
                     <catchAll>
                        <sequence name="Sequence102">
                           <if name="If_Error_Is_retry">
                              <condition>$countErrorDisney = 4</condition>
                              <throw name="Throw_Error_Disney" faultName="ns41:fault500"/>
                              <else>
                                 <assign name="Assign_AddCountRetry">
                                    <copy>
                                       <from>$countErrorDisney+1</from>
                                       <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$countErrorDisney</to>
                                    </copy>
                                 </assign>
                              </else>
                           </if>
                        </sequence>
                     </catchAll>
                  </faultHandlers>
                  <sequence name="Sequence_DisneyAcquisition_PrePago_Retry"
                            xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      
      
   <assign name="Transformation_Input_Disney_Acquisition"
           xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
         <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
      </bpelx:annotation>
      <copy>
         <from>ora:doXSLTransformForDoc("Transformations/Transformation_InputVariable_to_DisneyStream.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
         <to variable="Invoke_DisneyStream_oppEntitlement_InputVariable" part="request"/>
      </copy>
   </assign><invoke name="Invoke_DisneyStream" bpelx:invokeAsDetail="no" partnerLink="DisneyStream"
                    portType="ns41:DisneyStream_ptt" operation="oppEntitlement"
                    inputVariable="Invoke_DisneyStream_oppEntitlement_InputVariable"
                    outputVariable="Invoke_DisneyStream_oppEntitlement_OutputVariable"
                    xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                    xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/><assign name="Assign_FinishCountRetry"
                                                                                              xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      
   <copy>
         <from>5</from>
         <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$countErrorDisney</to>
      </copy></assign></sequence>
               </scope>
            </sequence>
         </while>
      </sequence>
   </scope></catchAll>
                                                      </faultHandlers>
                                                      <sequence name="Sequence_DisneyAcquisition_PrePago">
                                                         <assign name="Transformation_Input_Disney_Acquisition"
                                                                 xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                                            <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
                                                               <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                            </bpelx:annotation>
                                                            <copy>
                                                               <from>ora:doXSLTransformForDoc("Transformations/Transformation_InputVariable_to_DisneyStream.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                                               <to variable="Invoke_DisneyStream_oppEntitlement_InputVariable"
                                                                   part="request"/>
                                                            </copy>
                                                         </assign>
                                                         <invoke name="Invoke_DisneyStream" bpelx:invokeAsDetail="no"
                                                                 partnerLink="DisneyStream"
                                                                 portType="ns41:DisneyStream_ptt"
                                                                 operation="oppEntitlement"
                                                                 inputVariable="Invoke_DisneyStream_oppEntitlement_InputVariable"
                                                                 outputVariable="Invoke_DisneyStream_oppEntitlement_OutputVariable"
                                                                 xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                                                                 xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/>
                                                      </sequence>
                                                   </scope>
                                                </sequence>
                                                <else>
                                                   <empty name="Do_Nothing"
                                                          xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/>
                                                </else>
                                             </if></sequence></elseif>
                                       <elseif>
                                          <condition>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress']/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Streaming Partner' and (corecom:Value='disneyplus' or corecom:Value='starplus')])&gt;0</condition><sequence name="Sequence_DisneyAcquisition">
                                             <scope name="Scope29">
                                                <faultHandlers>
                                                   <catchAll><scope name="Scope_Action_DisneyAcquisitionError"
                                                                    xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      
      <variables>
                                                            <variable name="countErrorDisney" type="xsd:integer"/>
                                                         </variables><sequence name="Sequence100">
         <assign name="Assign_SetCountRetry">
            <copy>
               <from>1</from>
               <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$countErrorDisney</to>
            </copy>
         </assign>
         <while name="While_RetryActionDisney">
            <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
               <bpelx:documentation>
                  <![CDATA[Retry de 4 tentativas]]>
               </bpelx:documentation>
            </bpelx:annotation>
            <condition>$countErrorDisney &lt; 5</condition>
            <sequence name="Sequence101">
               <scope name="Scope_Action_DisneyAcquisition_ErrorRetry">
                  <faultHandlers>
                     <catchAll>
                        <sequence name="Sequence102">
                           <if name="If_Error_Is_retry">
                              <condition>$countErrorDisney = 4</condition>
                              <throw name="Throw_Error_Disney" faultName="ns41:fault500"/>
                              <else>
                                 <assign name="Assign_AddCountRetry">
                                    <copy>
                                       <from>$countErrorDisney+1</from>
                                       <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$countErrorDisney</to>
                                    </copy>
                                 </assign>
                              </else>
                           </if>
                        </sequence>
                     </catchAll>
                  </faultHandlers>
                  <sequence name="Sequence_DisneyAcquisition_Retry"
                            xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      
      
   <assign name="Transformation_Input_Disney_Acquisition"
           xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
         <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
      </bpelx:annotation>
      <copy>
         <from>ora:doXSLTransformForDoc("Transformations/Transformation_InputVariable_to_DisneyStream.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
         <to variable="Invoke_DisneyStream_oppEntitlement_InputVariable" part="request"/>
      </copy>
   </assign><invoke name="Invoke_DisneyStream" bpelx:invokeAsDetail="no" partnerLink="DisneyStream"
                    portType="ns41:DisneyStream_ptt" operation="oppEntitlement"
                    inputVariable="Invoke_DisneyStream_oppEntitlement_InputVariable"
                    outputVariable="Invoke_DisneyStream_oppEntitlement_OutputVariable"
                    xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                    xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/><assign name="Assign_FinishCountRetry"
                                                                                              xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      
   <copy>
         <from>5</from>
         <to expressionLanguage="urn:oasis:names:tc:wsbpel:2.0:sublang:xpath1.0">$countErrorDisney</to>
      </copy></assign></sequence>
               </scope>
            </sequence>
         </while>
      </sequence>
   </scope></catchAll>
                                                </faultHandlers>
                                                <sequence>
                                                   <assign name="Transformation_Input_Disney_Acquisition"
                                                           xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                                      <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
                                                         <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                      </bpelx:annotation>
                                                      <copy>
                                                         <from>ora:doXSLTransformForDoc("Transformations/Transformation_InputVariable_to_DisneyStream.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                                         <to variable="Invoke_DisneyStream_oppEntitlement_InputVariable"
                                                             part="request"/>
                                                      </copy>
                                                   </assign>
                                                   <invoke name="Invoke_DisneyStream" bpelx:invokeAsDetail="no"
                                                           partnerLink="DisneyStream" portType="ns41:DisneyStream_ptt"
                                                           operation="oppEntitlement"
                                                           inputVariable="Invoke_DisneyStream_oppEntitlement_InputVariable"
                                                           outputVariable="Invoke_DisneyStream_oppEntitlement_OutputVariable"/>
                                                </sequence>
                                             </scope>
                                          </sequence>
                                       </elseif>
                                       <else>
                                          <empty name="Do_Nothing"/>
                                       </else>
                                    </if>
                                 </scope>
                                 <scope name="Scope_HubSvaConnector">
                                    <variables>
                                       <variable name="HubSvaErrorMessage" type="xsd:string"/>
                                       <variable name="SvaList" messageType="ns59:SvaListRequestMsg"/>
                                    </variables>
                                    <sequence name="Sequence79">
                                       <if name="IfContainsSVA">
                                          <condition>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[(corecom:Name = "Tecnologia" or corecom:Name = "Familia Recarga") and corecom:Value = "SVA"]) &gt; 0 and $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode!="Entrance - Step 6"</condition>
                                          <sequence name="Seq_ContainsSva">
                                             <assign name="Assign_QueryCustomerParty">
                                                <copy ignoreMissingFromData="yes">
                                                   <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SKYAccountNumber</from>
                                                   <to>$QueryCustomerParty_InputVariable_HubSvaConnector.QueryCustomerPartyEBM/custparty:DataArea/custparty:QueryCustomerParty/corecom:Identification/corecom:ID</to>
                                                </copy>
                                             </assign>
                                             <invoke name="Invoke_QueryCustomerParty" bpelx:invokeAsDetail="no"
                                                     partnerLink="CustomerPartyEBS"
                                                     portType="ns9:CommunicationsCustomerPartyEBS"
                                                     operation="QueryCustomerParty"
                                                     inputVariable="QueryCustomerParty_InputVariable_HubSvaConnector"
                                                     outputVariable="QueryCustomerParty_OutputVariable_HubSvaConnector"/>
                                             <assign name="TransformationReqQueryClassificationList">
                                                <bpelx:annotation>
                                                   <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                </bpelx:annotation>
                                                <copy>
                                                   <from>ora:doXSLTransformForDoc("xsl/TransformationReqQueryClassificationList.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                                   <to variable="QueryClassificationList_InputVariable"
                                                       part="QueryClassificationListEBM"/>
                                                </copy>
                                             </assign>
                                             <invoke name="InvokeQueryClassificationList" bpelx:invokeAsDetail="no"
                                                     partnerLink="QueryClassificationListCCPSiebelProvABCSImpl"
                                                     portType="ns10:CommunicationsClassificationEBS"
                                                     operation="QueryClassificationList"
                                                     inputVariable="QueryClassificationList_InputVariable"
                                                     outputVariable="QueryClassificationList_OutputVariable"/>
                                             <assign name="Transform_SvaStructure">
                                                <bpelx:annotation>
                                                   <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                </bpelx:annotation>
                                                                <copy>
                                                   <from>ora:doXSLTransformForDoc("xsl/Transformation_InputToSvaList.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM, "QueryClassificationList_OutputVariable.QueryClassificationListResponseEBM", $QueryClassificationList_OutputVariable.QueryClassificationListResponseEBM)</from>
                                                   <to variable="SvaList" part="parameters"/>
                                                                </copy>
                                                             </assign>
                                             <assign name="Transform_SvaListOrder">
                                                <bpelx:annotation>
                                                                        <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                                     </bpelx:annotation>
                                                                     <copy>
                                                   <from>ora:doXSLTransformForDoc("xsl/Transformation_SvaListOder.xsl", $SvaList.parameters)</from>
                                                   <to variable="SvaList" part="parameters"/>
                                                                     </copy>
                                                                  </assign>
                                             <forEach parallel="no" counterName="ForEachPartnerCounter"
                                                      name="ForEachSvaPartner">
                                                      <startCounterValue>1</startCounterValue>
                                                <finalCounterValue>count($SvaList.parameters/ns60:products/ns60:product[not(ns60:partner/ns60:name/text()=preceding::ns60:partner/ns60:name/text())])</finalCounterValue>
                                                <scope name="Scope_Loop_Partners">
                                                         <variables>
                                                      <variable name="Var_Partner_Name" type="xsd:string"/>
                                                      <variable name="SvaListFiltered"
                                                                messageType="ns59:SvaListRequestMsg"/>
                                                         </variables>
                                                         <faultHandlers>
                                                            <catchAll>
                                                            <sequence name="CatchAllSequence">
                                                            <assign name="Assign_ErrorHandling"
                                                                    xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                                                <copy>
                                                                   <from>ora:getFaultAsString()</from>
                                                                   <to>$HubSvaErrorMessage</to>
                                                                </copy>
                                                             </assign>
                                                            </sequence>
                                                          </catchAll>
                                                         </faultHandlers>
                                                   <sequence name="Seq_ForEachPartner">
                                                      <assign name="Assign_PartnerName">
                                                               <copy>
                                                            <from>$SvaList.parameters/ns60:products/ns60:product[not(ns60:partner/ns60:name/text()=preceding::ns60:partner/ns60:name/text())][$ForEachPartnerCounter]/ns60:partner/ns60:name</from>
                                                            <to>$Var_Partner_Name</to>
                                                               </copy>
                                                            </assign>
                                                      <if name="If_action_is_UpDown">
                                                                     <documentation>
                                                            <![CDATA[UPDOWN]]>
                                                         </documentation>
                                                         <condition>(count($SvaList.parameters/ns60:products/ns60:product[ns60:partner/ns60:name=$Var_Partner_Name and ns60:action='add']) = count($SvaList.parameters/ns60:products/ns60:product[ns60:partner/ns60:name=$Var_Partner_Name and ns60:action='cancel'])) and (count($SvaList.parameters/ns60:products/ns60:product[ns60:partner/ns60:name=$Var_Partner_Name and ns60:action='add']) &gt; 0 and count($SvaList.parameters/ns60:products/ns60:product[ns60:partner/ns60:name=$Var_Partner_Name and ns60:action='cancel']) &gt; 0) </condition>
                                                         <sequence name="Seq_UpDown">
                                                            <assign name="Assign_SvaListFiltered">
                                                               <extensionAssignOperation>
                                                                  <bpelx:copyList ignoreMissingFromData="yes">
                                                                     <bpelx:from>$SvaList.parameters/ns60:products/ns60:product[(ns60:partner/ns60:name=$Var_Partner_Name) and (ns60:action='add' or ns60:action='cancel')]</bpelx:from>
                                                                     <bpelx:to>$SvaListFiltered.parameters/ns60:products/ns60:product</bpelx:to>
                                                                  </bpelx:copyList>
                                                               </extensionAssignOperation>
                                                            </assign>
                                                            <assign name="Transform_UpDown">
                                                                           <bpelx:annotation>
                                                                              <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                                           </bpelx:annotation>
                                                                           <copy>
                                                                  <from>ora:doXSLTransformForDoc("xsl/Transformation_To_HubSvaConnector_UpDown.xsl", $QueryCustomerParty_OutputVariable_HubSvaConnector.QueryCustomerPartyResponseEBM, "SvaListFiltered.parameters", $SvaListFiltered.parameters)</from>
                                                                              <to variable="oppHubSvaConnector_InputVariable"
                                                                                  part="request"/>
                                                                           </copy>
                                                                        </assign>
                                                            <invoke name="HubSvaConnector" bpelx:invokeAsDetail="no"
                                                                                partnerLink="HubSvaConnector"
                                                                                portType="ns51:HubSvaConnector_ptt"
                                                                                operation="oppHubSvaConnector"
                                                                                inputVariable="oppHubSvaConnector_InputVariable"
                                                                    outputVariable="oppHubSvaConnector_OutputVariable"
                                                                    xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                                                                    xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/>
                                                                     </sequence>
                                                         <else>
                                                                        <documentation>
                                                               <![CDATA[ADD_DELETE]]>
                                                                        </documentation>
                                                            <sequence name="Seq_Add_Delete">
                                                               <forEach parallel="no"
                                                                        counterName="ForEachPartnerActionsCounter"
                                                                        name="ForEach_PartnerActions">
                                                                  <startCounterValue>1</startCounterValue>
                                                                  <finalCounterValue>count($SvaList.parameters/ns60:products/ns60:product[ns60:partner/ns60:name=$Var_Partner_Name])</finalCounterValue>
                                                                  <scope name="Scope_Loop_Actions">
                                                                     <sequence name="Seq_Loop_Actions">
                                                                        <assign name="Assign_SvaListFiltered">
                                                                           <copy bpelx:insertMissingToData="yes"
                                                                                 ignoreMissingFromData="yes">
                                                                              <from>$SvaList.parameters/ns60:products/ns60:product[(ns60:partner/ns60:name=$Var_Partner_Name)][$ForEachPartnerActionsCounter]</from>
                                                                              <to>$SvaListFiltered.parameters/ns60:products/ns60:product</to>
                                                                           </copy>
                                                                        </assign>
                                                                        <assign name="Transform_AddDel">
                                                                           <bpelx:annotation>
                                                                                 <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                                              </bpelx:annotation>
                                                                              <copy>
                                                                              <from>ora:doXSLTransformForDoc("xsl/Transformation_To_HubSvaConnector_AddDel.xsl", $QueryCustomerParty_OutputVariable_HubSvaConnector.QueryCustomerPartyResponseEBM, "SvaListFiltered.parameters", $SvaListFiltered.parameters)</from>
                                                                                 <to variable="oppHubSvaConnector_InputVariable"
                                                                                     part="request"/>
                                                                              </copy>
                                                                           </assign>
                                                                           <invoke name="HubSvaConnector"
                                                                                   bpelx:invokeAsDetail="no"
                                                                                   partnerLink="HubSvaConnector"
                                                                                   portType="ns51:HubSvaConnector_ptt"
                                                                                   operation="oppHubSvaConnector"
                                                                                   inputVariable="oppHubSvaConnector_InputVariable"
                                                                                outputVariable="oppHubSvaConnector_OutputVariable"/>
                                                                        </sequence>
                                                                  </scope>
                                                               </forEach>
                                                               </sequence>
                                                         </else>
                                                            </if>
                                                         </sequence>
                                                      </scope>
                                                   </forEach>
                                          </sequence>
                                       </if>
                                    </sequence>
                                 </scope>
                              </sequence>
                           </if>
                        </sequence>
                        <if name="D1_If_Is_there_an_item_to_be_provisioned_with_status_equal_to_LockedInProgress">
                           <condition>(count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = "Locked In Progress" and corecom:InstalledProductReference/corecom:Custom/corecomcust:ProvisioningIndicator = "true"]) > 0) and not($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:SalesChannelCode='SpeedWeb' or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:SalesChannelCode='Salesforce') or ($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Migracao Pos-Pre") or  ($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode='Migracao Pre-Pos')</condition>
                           <scope name="SCP_Invoke_A1ProcessSoftwareActivationFulfillmentOrder" 
                                  exitOnStandardFault="no">
                              <variables>
                                 <variable name="flagModify" type="xsd:string"/>
                                 <variable name="CurrentOrderLine"
                                           element="ford:FulfillmentOrderLine"/>
                              </variables>
                              <sequence name="Software_Activation">
                                 <if name="VerifyIfThereIsAnyHwDeleteModifyS">
                                    <condition>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Equipamento' and ford:ServiceActionCode = 'DELETE' and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress' and substring(corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Modify']/corecom:Value,1,1) = 'S']) > 0</condition>
                                    <forEach parallel="no" 
                                             counterName="modifySCounter" 
                                             name="ModifySForEach">
                                       <startCounterValue>1</startCounterValue>
                                       <finalCounterValue>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Equipamento' and ford:ServiceActionCode = 'DELETE' and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress' and substring(corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Modify']/corecom:Value,1,1) = 'S'])</finalCounterValue>
                                       <scope name="EachEquipamentFlagModifyS">
                                          <sequence name="SequenceEquipamentModifyS">
                                             <assign name="AssignFlagModify">
                                                <copy>
                                                   <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Equipamento' and ford:ServiceActionCode = 'DELETE' and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress' and substring(corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Modify']/corecom:Value,1,1) = 'S'][position() = $modifySCounter]/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Modify']/corecom:Value/text()</from>
                                                   <to>$flagModify</to>
                                                </copy>
                                             </assign>
                                             <if name="VerifyCorrespondent">
                                                <condition>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode = 'ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress' and corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Modify']/corecom:Value = $flagModify])>0</condition>
                                                <assign name="AssignContentOrderLineToTwo">
                                                   <copy>
                                                      <from>2</from>
                                                      <to>$CurrentOrderLine/corecom:Note/corecom:Content</to>
                                                   </copy>
                                                </assign>
                                                <else>
                                                   <assign name="AssignContentOrderLineToOne">
                                                      <copy>
                                                         <from>1</from>
                                                         <to>$CurrentOrderLine/corecom:Note/corecom:Content</to>
                                                      </copy>
                                                   </assign>
                                                </else>
                                             </if>
                                             <assign name="InsertingNoteContent">
                                                <extensionAssignOperation>
                                                   <bpelx:insertBefore>
                                                      <bpelx:from>$CurrentOrderLine/corecom:Note</bpelx:from>
                                                      <bpelx:to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Equipamento' and ford:ServiceActionCode = 'DELETE' and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress' and substring(corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Modify']/corecom:Value,1,1) = 'S'][position() = $modifySCounter]/corecom:Status</bpelx:to>
                                                   </bpelx:insertBefore>
                                                </extensionAssignOperation>
                                             </assign>
                                          </sequence>
                                       </scope>
                                    </forEach>
                                 </if>
                                 <assign name="TransformA1_InputVariable_To_ProcessSoftwareActivationFulfillmentOrder">
                                    <bpelx:annotation>
                                       <bpelx:pattern patternName="bpelx:transformation"/>
                                    </bpelx:annotation>
                                    <copy>
                                       <from>ora:doXSLTransformForDoc("xsl/A1_InputVariable_To_ProcessSoftwareActivationFulfillmentOrder.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                       <to variable="Invoke_A1ProcessSoftwareActivationFulfillmentOrder_InputVariable"
                                           part="ProcessSoftwareActivationFulfillmentOrderEBM"/>
                                    </copy>
                                 </assign>
                                 <if name="If_InclusaoHw_Bko_withoutOS">
                                    <condition>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder[count(ford:FulfillmentOrderLine/corecom:InstalledProductReference/corecom:Custom[lower-case(corecomcust:WorkOrderIndicator) = "true"]) = 0]/ford:Custom[lower-case(fordcust:SubTypeCode)= "inclusão hw"]/fordcust:UpdatedFulfillmentOrder/fordcust:SystemIdentification[lower-case(corecom:ID)="icarebko"]) !=0  or ($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode ="Migracao Pre-Pos")</condition>
                                    <empty name="Not_Remove_Comodato"/>
                                    <else>
                                 <if name="If_HasComodatoItem">
                                    <documentation>
                                             <![CDATA[Yes]]>
                                          </documentation>
                                          <condition>(count($Invoke_A1ProcessSoftwareActivationFulfillmentOrder_InputVariable.ProcessSoftwareActivationFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareActivationFulfillmentOrder/ford:FulfillmentOrderLine[ corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name = "Tipo de Aquisição"]/corecom:Value = "Comodato" and (substring(corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name="Modify"]/corecom:Value,1,1) != "H" and substring(corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name="Modify"]/corecom:Value,1,1) != "M") and (ford:ServiceActionCode = "New" or ford:ServiceActionCode = "ADD")]) &gt; 0) and ( $Invoke_A1ProcessSoftwareActivationFulfillmentOrder_InputVariable.ProcessSoftwareActivationFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareActivationFulfillmentOrder/ford:Custom/fordcust:SubTypeCode != "Technical Assistance Exchange")</condition>
                                    <assign name="Remove_ComodatoItem">
                                       <extensionAssignOperation>
                                          <bpelx:remove>
                                             <bpelx:target>$Invoke_A1ProcessSoftwareActivationFulfillmentOrder_InputVariable.ProcessSoftwareActivationFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareActivationFulfillmentOrder/ford:FulfillmentOrderLine[ corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name = "Tipo de Aquisição"]/corecom:Value = "Comodato" and substring(corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name="Modify"]/corecom:Value,1,1) != "M" and (ford:ServiceActionCode = "New" or ford:ServiceActionCode = "ADD")]</bpelx:target>
                                          </bpelx:remove>
                                       </extensionAssignOperation>
                                    </assign>
                                 </if>
                                    </else>
                                 </if>
                                 <if name="If_HasLivreWithOSE">
                                    <condition>(count($Invoke_A1ProcessSoftwareActivationFulfillmentOrder_InputVariable.ProcessSoftwareActivationFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareActivationFulfillmentOrder/ford:FulfillmentOrderLine[ corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name = "Tipo de Aquisição"]/corecom:Value = "Venda" and substring(corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name="Modify"]/corecom:Value,1,1) != "M" and (ford:ServiceActionCode = "New" or ford:ServiceActionCode = "ADD") and string-length(ford:Custom/corecomcust:WorkOrderReference/corecomcust:WorkOrderIdentification/corecom:ID)>0]) > 0) and ( $Invoke_A1ProcessSoftwareActivationFulfillmentOrder_InputVariable.ProcessSoftwareActivationFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareActivationFulfillmentOrder/ford:Custom/fordcust:SubTypeCode != "Technical Assistance Exchange")</condition>
                                    <sequence name="Sequence68">
                                       <if name="If_Migracao_Pre-Pos">
                                          <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Migracao Pre-Pos"</condition>
                                          <empty name="Not_Remove_Venda"/>
                                          <else>
                                             <assign name="Remove_LivreWithOSEItem">
                                                <extensionAssignOperation>
                                                   <bpelx:remove>
                                                      <bpelx:target>$Invoke_A1ProcessSoftwareActivationFulfillmentOrder_InputVariable.ProcessSoftwareActivationFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareActivationFulfillmentOrder/ford:FulfillmentOrderLine[ corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name = "Tipo de Aquisição"]/corecom:Value = "Venda" and substring(corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name="Modify"]/corecom:Value,1,1) != "M" and (ford:ServiceActionCode = "New" or ford:ServiceActionCode = "ADD") and string-length(ford:Custom/corecomcust:WorkOrderReference/corecomcust:WorkOrderIdentification/corecom:ID)&gt;0]</bpelx:target>
                                                   </bpelx:remove>
                                                </extensionAssignOperation>
                                             </assign>
                                          </else>
                                       </if>
                                    </sequence>
                                 </if>
                                 <sequence name="Sequence48">
                                    <assign name="AssignCurrentDate">
                                       <copy>
                                          <from>xp20:current-date()</from>
                                          <to>$CurrentSystemDt</to>
                                       </copy>
                                    </assign>
                                    <assign name="FormatCurrentDate">
                                       <copy>
                                          <from>xp20:format-dateTime(string($CurrentSystemDt),"[Y0001]/[M01]/[D01]")</from>
                                          <to>$CurrentSystemDtFormated</to>
                                       </copy>
                                    </assign>
                                 </sequence>
                                <if name="If_HasRechargeItemsWithStartDateInTheFuture">
                                    <documentation>
                                       <![CDATA[AND NOT UPGRADE]]>
                                    </documentation>
                                    <condition>count($Invoke_A1ProcessSoftwareActivationFulfillmentOrder_InputVariable.ProcessSoftwareActivationFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareActivationFulfillmentOrder/ford:FulfillmentOrderLine[ corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Recarga']) &gt; 0 and $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode !="Upgrade de Recarga"</condition>
                                    <sequence name="Sequence47">
                                              <assign name="Assign_FulfillmentOrderLine_Recharge">
                                                <extensionAssignOperation>
                                                  <bpelx:copyList>
                                                    <bpelx:from>$Invoke_A1ProcessSoftwareActivationFulfillmentOrder_InputVariable.ProcessSoftwareActivationFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareActivationFulfillmentOrder/ford:FulfillmentOrderLine[ corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Recarga']</bpelx:from>
                                                    <bpelx:to>$ProcessSoftwareActivationFulfillmentOrder_Recharge.ProcessSoftwareActivationFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareActivationFulfillmentOrder/ford:FulfillmentOrderLine</bpelx:to>
                                                  </bpelx:copyList>
                                                </extensionAssignOperation>
                                              </assign>
                                              <forEach parallel="no" counterName="RechargeIndex"
                                               name="ForEachRechargeItem">
                                        <startCounterValue>1</startCounterValue>
                                        <finalCounterValue>count($ProcessSoftwareActivationFulfillmentOrder_Recharge.ProcessSoftwareActivationFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareActivationFulfillmentOrder/ford:FulfillmentOrderLine)</finalCounterValue>
                                        <scope name="RemoveRechargeTree">
                                          <variables>
                                                    <variable name="RechargeItemID"
                                                              type="xsd:string"/>
                                          </variables>
                                          <sequence name="RemoveRechargeTree">
                                          <assign name="AssignStarDate">
                                              <copy ignoreMissingFromData="yes">
                                                <from>$ProcessSoftwareActivationFulfillmentOrder_Recharge.ProcessSoftwareActivationFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareActivationFulfillmentOrder/ford:FulfillmentOrderLine[position() = $RechargeIndex]/corecom:EffectiveTimePeriod/corecom:StartDateTime</from>
                                                <to>$CurrentStartDt</to>
                                              </copy>
                                            </assign>
                                             <!-- Format date of DD/MM/YYYY to YYYY/MM/DD -->
                                            <assign name="FormatStartDate">
                                              <copy>
                                                <from>xp20:format-dateTime(string($CurrentStartDt),"[Y0001]/[M01]/[D01]")</from>
                                                <to>$CurrentStartDtFormated</to>
                                              </copy>
                                            </assign>
                                            <if name="If_StartDateInTheFuture">
                                              <condition>$CurrentStartDtFormated &gt; $CurrentSystemDtFormated</condition>
                                            <assign name="Remove_ItemsWithStartDateInTheFuture">
                                              <copy>
                                                <from>$ProcessSoftwareActivationFulfillmentOrder_Recharge.ProcessSoftwareActivationFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareActivationFulfillmentOrder/ford:FulfillmentOrderLine[position() = $RechargeIndex]/corecom:Identification/corecom:ApplicationObjectKey/corecom:ID</from>
                                                <to>$RechargeItemID</to>
                                              </copy>
                                              <extensionAssignOperation>
                                                <bpelx:remove>
                                                  <bpelx:target>$Invoke_A1ProcessSoftwareActivationFulfillmentOrder_InputVariable.ProcessSoftwareActivationFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareActivationFulfillmentOrder/ford:FulfillmentOrderLine[ corecom:RootParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID = $RechargeItemID]</bpelx:target>
                                                </bpelx:remove>
                                              </extensionAssignOperation>
                                            </assign>
                                            </if>
                                          </sequence>
                                        </scope>
                                      </forEach>
                                    </sequence>
                                  </if>
                                 <if name="If_Upgrade_recarga">
                                    <documentation>
                                       <![CDATA[a logica de upgrade de recarga está no ASAPLESS]]>
                                    </documentation>
                                    <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Upgrade de Recarga"</condition>
                                    <sequence name="Sequence57">
                                       <assign name="Transform_InputVariable_to_ProcessCommand">
                                          <bpelx:annotation>
                                             <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                          </bpelx:annotation>
                                          <copy>
                                             <from>ora:doXSLTransformForDoc("Transformations/Transform_InputVariable_to_ProcessCommand.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                             <to variable="Invoke_ProcessCommand_ProcessCommand_InputVariable"
                                                 part="ProcessCommandEBM"/>
                                          </copy>
                                       </assign>
                                       <invoke name="Invoke_ProcessCommand"
                                               partnerLink="CommunicationsProvisioningOrderEBS"
                                               portType="ns35:CommunicationsProvisioningOrderEBS"
                                               operation="ProcessCommand"
                                               inputVariable="Invoke_ProcessCommand_ProcessCommand_InputVariable"
                                               bpelx:invokeAsDetail="no"/>
                                    </sequence>
                                    <elseif>
                                       <documentation>
                                          <![CDATA[Up/Downgrade is Fiber]]>
                                       </documentation>
                                       <condition>($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Upgrade With Techn. Exchange" or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Upgd. W/o Technology Exchange" or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Dwgd. With Technology Exchange" or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Dwgd. W/o Technology Exchange") and ($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name = 'Tecnologia' and corecom:Value = 'FIBRA'])</condition>
                                       <sequence>
                                          <if name="IfTypeIsUpgrade">
                                             <documentation>
                                                <![CDATA[Upgrade]]>
                                             </documentation>
                                             <condition>substring($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode, 1,3) = 'Upg'</condition>
                                             <sequence name="Sequence69">
                                                <assign name="AssignGetVelocidade">
                                                   <copy ignoreMissingFromData="yes">
                                                      <from>($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode = "ADD" and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = "Internet"]/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name = "Velocidade"]/corecom:Value)</from>
                                                      <to>$getVelocidade</to>
                                                   </copy>
                                                </assign>
                                                <assign name="AssignToTbExternalPartner">
                                                   <copy ignoreMissingFromData="yes">
                                                      <from>'FIBRA'</from>
                                                      <to>$TB_EXTERNAL_PARTNET_EVENT_insert_InputVariable.TbExternalPartnerEventCollection/ns47:TbExternalPartnerEvent/ns47:parceiroNegocio</to>
                                                   </copy>
                                                   <copy ignoreMissingFromData="yes">
                                                      <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SKYAccountNumber</from>
                                                      <to>$TB_EXTERNAL_PARTNET_EVENT_insert_InputVariable.TbExternalPartnerEventCollection/ns47:TbExternalPartnerEvent/ns47:idConta</to>
                                                   </copy>
                                                   <copy ignoreMissingFromData="yes">
                                                      <from>xp20:current-dateTime()</from>
                                                      <to>$TB_EXTERNAL_PARTNET_EVENT_insert_InputVariable.TbExternalPartnerEventCollection/ns47:TbExternalPartnerEvent/ns47:createDate</to>
                                                   </copy>
                                                   <copy ignoreMissingFromData="yes">
                                                      <from>$getVelocidade</from>
                                                      <to>$TB_EXTERNAL_PARTNET_EVENT_insert_InputVariable.TbExternalPartnerEventCollection/ns47:TbExternalPartnerEvent/ns47:nmProduto</to>
                                                   </copy> 
                                                   <copy ignoreMissingFromData="yes">
                                                      <from>'upgrade'</from>
                                                      <to>$TB_EXTERNAL_PARTNET_EVENT_insert_InputVariable.TbExternalPartnerEventCollection/ns47:TbExternalPartnerEvent/ns47:acao</to>
                                                   </copy>
                                                   <copy ignoreMissingFromData="yes">
                                                      <from>'SOA-MST'</from>
                                                      <to>$TB_EXTERNAL_PARTNET_EVENT_insert_InputVariable.TbExternalPartnerEventCollection/ns47:TbExternalPartnerEvent/ns47:sistemaOrigem</to>
                                                   </copy>
                                                   <copy ignoreMissingFromData="yes">
                                                      <from>'0'</from>
                                                      <to>$TB_EXTERNAL_PARTNET_EVENT_insert_InputVariable.TbExternalPartnerEventCollection/ns47:TbExternalPartnerEvent/ns47:numeroTentativas</to>
                                                   </copy>
                                                </assign>
                                             </sequence>
                                             <elseif>
                                                <documentation>
                                                   <![CDATA[Downgrade]]>
                                                </documentation>
                                                <condition>substring($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode, 1,3) = 'Dwg'</condition><sequence name="Sequence70"><assign name="AssignGetVelocidade"
                                                                                             xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                                      <copy ignoreMissingFromData="yes">
                                                         <from>($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode = "ADD" and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = "Internet"]/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name = "Velocidade"]/corecom:Value)</from>
                                                         <to>$getVelocidade</to>
                                                      </copy>
                                                   </assign><assign name="AssignToTbExternalPartner" xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                                      <copy ignoreMissingFromData="yes">
                                                         <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SKYAccountNumber</from>
                                                         <to>$TB_EXTERNAL_PARTNET_EVENT_insert_InputVariable.TbExternalPartnerEventCollection/ns47:TbExternalPartnerEvent/ns47:idConta</to>
                                                      </copy>
                                                      <copy ignoreMissingFromData="yes">
                                                         <from>'FIBRA'</from>
                                                         <to>$TB_EXTERNAL_PARTNET_EVENT_insert_InputVariable.TbExternalPartnerEventCollection/ns47:TbExternalPartnerEvent/ns47:parceiroNegocio</to>
                                                      </copy>
                                                      <copy ignoreMissingFromData="yes">
                                                         <from>xp20:current-dateTime()</from>
                                                         <to>$TB_EXTERNAL_PARTNET_EVENT_insert_InputVariable.TbExternalPartnerEventCollection/ns47:TbExternalPartnerEvent/ns47:createDate</to>
                                                      </copy>
                                                      <copy ignoreMissingFromData="yes">
                                                         <from>$getVelocidade</from>
                                                         <to>$TB_EXTERNAL_PARTNET_EVENT_insert_InputVariable.TbExternalPartnerEventCollection/ns47:TbExternalPartnerEvent/ns47:nmProduto</to>
                                                      </copy>
                                                      <copy ignoreMissingFromData="yes">
                                                         <from>'downgrade'</from>
                                                         <to>$TB_EXTERNAL_PARTNET_EVENT_insert_InputVariable.TbExternalPartnerEventCollection/ns47:TbExternalPartnerEvent/ns47:acao</to>
                                                      </copy>
                                                      <copy ignoreMissingFromData="yes">
                                                         <from>'SOA-MST'</from>
                                                         <to>$TB_EXTERNAL_PARTNET_EVENT_insert_InputVariable.TbExternalPartnerEventCollection/ns47:TbExternalPartnerEvent/ns47:sistemaOrigem</to>
                                                      </copy>
                                                      <copy ignoreMissingFromData="yes">
                                                         <from>'0'</from>
                                                         <to>$TB_EXTERNAL_PARTNET_EVENT_insert_InputVariable.TbExternalPartnerEventCollection/ns47:TbExternalPartnerEvent/ns47:numeroTentativas</to>
                                                      </copy>
                                                   </assign></sequence></elseif>
                                          </if>
                                          <invoke name="Invoke_TB_EXTERNAL_PARTNET_EVENT"
                                                  partnerLink="TB_EXTERNAL_PARTNER_EVENT"
                                                  portType="ns46:TB_EXTERNAL_PARTNER_EVENT_ptt" operation="insert"
                                                  inputVariable="TB_EXTERNAL_PARTNET_EVENT_insert_InputVariable"
                                                  bpelx:invokeAsDetail="no"
                                                  outputVariable="TB_EXTERNAL_PARTNET_EVENT_insert_OutputVariable"/>
                                       </sequence>
                                    </elseif>
                                    <elseif>
                                       <documentation>
                                          <![CDATA[If it's Fiber, it's not called ITSA]]>
                                       </documentation>
                                       <condition>($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name = 'Tecnologia' and corecom:Value = 'FIBRA']) 
										   and ($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Entrance - Step 6" 
										   or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Voluntary cancellation" 
										   or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Reactivation" 
										   or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Temporary Suspension" 
										   or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Temp. Suspension Reconnection" 
										   or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="SW Update" 
										   or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Alteracao Parque" 
										   or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Inclusão HW" 
										   or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Instalação - Ponto Principal" 
										   or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Instalação - Substituição" 
										   or contains(xp20:lower-case(string($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode)), "customer's word reconnection"))
									   </condition>
                                       <empty name="Do_Nothing"/>
                                    </elseif>
                                    <else>
                                       <invoke name="Invoke_A1ProcessSoftwareActivationFulfillmentOrder"
                                               partnerLink="ProcessSoftwareActivationFulfillmentOrderEBFMIP"
                                               portType="ns8:ProcessSoftwareActivationFulfillmentOrderEBFMIP"
                                               operation="ProcessSoftwareActivationFulfillmentOrder"
                                               inputVariable="Invoke_A1ProcessSoftwareActivationFulfillmentOrder_InputVariable"
                                               outputVariable="Invoke_A1ProcessSoftwareActivationFulfillmentOrder_OutputVariable"
                                               bpelx:invokeAsDetail="no"/>
                                    </else>
                                 </if>

                              </sequence>
                           </scope>
                        </if>
                        <if name="If_Inclusion_Hybrid_Client">
                           <documentation>
                              <![CDATA[If_Inclusion_Hybrid_Client]]>
                           </documentation>
                           <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Migracao Pos-Pre" or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode="Migracao Pre-Pos"</condition>
                           <sequence name="Sequence_Inclusion_Hybrid_Client">
                              <forEach parallel="no" 
                                       counterName="ForEachEquipCounter" 
                                       name="ForEachEquip">
                                 <startCounterValue>1</startCounterValue>
                                 <finalCounterValue>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine)</finalCounterValue>
                                 <scope name="ScopeCategoryEqualsEquipment" 
                                        exitOnStandardFault="no">
                                    <if name="IfCategoryEqualsEquipment">
                                       <documentation>
                                          <![CDATA[IfCategoryEqualsEquipment]]>
                                       </documentation>
                                       <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[$ForEachEquipCounter]/corecom:InstalledProductReference/corecom:Custom/corecomcust:Category="Equipamento" and ($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[$ForEachEquipCounter]/corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory="PayTV" or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[$ForEachEquipCounter]/corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory="SIM")</condition>
                                       <sequence name="SequenceCategoryEqualsEquipment">
                                          <sequence name="SequenceCategoryEqualsEquipment">
                                             <assign name="ProcessSofwareToUpdateInventoryTransactionAssociate">
                                                <bpelx:annotation>
                                                   <bpelx:pattern patternName="bpelx:transformation"/>
                                                </bpelx:annotation>
                                                <copy>
                                                   <from>ora:doXSLTransformForDoc("xsl/ProcessSofwareToUpdateInventoryTransactionAssociate.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                                   <to variable="Invoke_UpdateInventoryTransaction_Associate_InputVariable"
                                                       part="UpdateInventoryTransactionEBM"/>
                                                </copy>
                                             </assign>
                                             <invoke name="Invoke_UpdateInventoryTransaction_Associate"
                                                     partnerLink="CommunicationsInventoryTransactionEBSV1"
                                                     portType="ns21:CommunicationsInventoryTransactionEBS"
                                                     operation="UpdateInventoryTransaction"
                                                     inputVariable="Invoke_UpdateInventoryTransaction_Associate_InputVariable"
                                                     bpelx:invokeAsDetail="no"/>
                                          </sequence>
                                       </sequence>
                                    </if>
                                 </scope>
                              </forEach>
                           </sequence>
                        </if>
                        <assign name="Transform_QueryCustomerPartyEnableCustomerParty_InputVariable">
                           <bpelx:annotation>
                              <bpelx:pattern patternName="bpelx:transformation"/>
                           </bpelx:annotation>
                           <copy>
                              <from>ora:doXSLTransformForDoc("xsl/ProcessSoftwareToQueryCustomerParty.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                              <to variable="Invoke_QueryCustomerPartyEnableCustomerParty_InputVariable"
                                  part="QueryCustomerPartyEBM"/>
                           </copy>
                        </assign>
                        <invoke name="Invoke_QueryCustomerPartyEnableCustomerParty_InputVariable"
                                partnerLink="CustomerPartyEBS_SOA"
                                portType="ns9:CommunicationsCustomerPartyEBS"
                                operation="QueryCustomerParty"
                                inputVariable="Invoke_QueryCustomerPartyEnableCustomerParty_InputVariable"
                                outputVariable="Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable"
                                bpelx:invokeAsDetail="no"/>
                        <if name="If_Mobile_add">
                           <documentation>
                              <![CDATA[Yes]]>
                           </documentation>
                           <condition>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode = 'ADD' and (corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Telefonia_Plano' or corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Telefonia_AddOn')]) &gt; 0</condition>
                           <sequence name="Sequence109">
                              <if name="If_Ativacao">
                                 <documentation>
                                    <![CDATA[Ativacao]]>
                                 </documentation>
                                 <condition>(count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Telefonia_Plano'])&gt; 0) </condition>
                                 <assign name="Transformation_Input_to_MobileService_createorder">
                                    <bpelx:annotation>
                                       <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                    </bpelx:annotation>
                                    <copy>
                                       <from>ora:doXSLTransformForDoc("Transformations/Transformation_Input_to_MobileService_createorder.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM, "Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM", $Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM)</from>
                                       <to variable="InvokeMobileService_createOrder_createorder_InputVariable"
                                           part="request"/>
                                    </copy>
                                 </assign>
                                 <else>
                                    <empty name="Empty2"/>
                                 </else>
                              </if>
                              <scope name="Scope30">
                                 <faultHandlers>
                                    <catchAll><sequence name="Sequence111">
                                          <if name="If_valida_a_la_carte">
                                             <documentation>
                                                <![CDATA[mobile a la carte]]>
                                             </documentation>
                                             <condition>(count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'A La Carte' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Telefonia_Plano']) &gt; 0)</condition>
                                             <assign name="Assign_CancelMobileItem">
                                                <copy ignoreMissingFromData="yes">
                                                   <from>'Cancelled'</from>
                                                   <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'A La Carte' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Telefonia_Plano']/corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus</to>
                                                </copy>
                                                <copy>
                                                   <from>1</from>
                                                   <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'A La Carte' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Telefonia_Plano']/ford:ServiceActionCode</to>
                                                </copy>
                                             </assign>
                                             <else>
                                                <documentation>
                                                   <![CDATA[Basico]]>
                                                </documentation>
                                                <sequence name="Sequence112">
                                                   <assign name="TransformationCancelFulfillmentOrder">
                                                      <bpelx:annotation>
                                                         <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                      </bpelx:annotation>
                                                      <copy>
                                                         <from>ora:doXSLTransformForDoc("Transformations/Transformation_CancelaFulfillmentOrder.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                                         <to variable="InvokeUpdateFulfillmentOrderMobileError_UpdateFulfillmentOrderSynchronously_InputVariable"
                                                             part="UpdateFulfillmentOrderSynchronouslyEBM"/>
                                                      </copy>
                                                   </assign>
                                                   <invoke name="InvokeUpdateFulfillmentOrderMobileError"
                                                           bpelx:invokeAsDetail="no"
                                                           partnerLink="CommunicationsFulfillmentOrder"
                                                           portType="ns20:CommunicationsFulfillmentOrderEBS"
                                                           operation="UpdateFulfillmentOrderSynchronously"
                                                           inputVariable="InvokeUpdateFulfillmentOrderMobileError_UpdateFulfillmentOrderSynchronously_InputVariable"
                                                           outputVariable="InvokeUpdateFulfillmentOrderMobileError_UpdateFulfillmentOrderSynchronously_OutputVariable"/>
                                                </sequence>
                                             </else>
                                          </if>
                                       </sequence></catchAll>
                                 </faultHandlers>
                                 <sequence>
                                    <invoke name="InvokeMobileService_createOrder" bpelx:invokeAsDetail="no"
                                            partnerLink="MobileService" portType="ns74:MobileService_ptt"
                                            operation="createorder"
                                            inputVariable="InvokeMobileService_createOrder_createorder_InputVariable"
                                            outputVariable="InvokeMobileService_createOrder_createorder_OutputVariable"/>
                                    <if name="If_Sucesso">
                                       <documentation>
                                          <![CDATA[sim]]>
                                       </documentation>
                                       <condition>$InvokeMobileService_createOrder_createorder_OutputVariable.reply/ns75:success='true'</condition>
                                       <pick name="Pick1">
                                          <onMessage bpelx:name="UpdateHubMobileCallbackFulfillmentOrder"
                                                     variable="OnMessage_UpdateHubMobileCallbackFulfillmentOrder_InputVariable"
                                                     partnerLink="UpdateHubMobileCallbackFulfillmentOrder"
                                                     portType="ns1:UpdateHubMobileCallbackFulfillmentOrder"
                                                     operation="UpdateHubMobileCallbackFulfillmentOrder">
                                             <correlations>
                                                <correlation set="Correlation_Set_csMobile" initiate="no"/>
                                             </correlations>
                                             <if name="If_success">
                                                <documentation>
                                                   <![CDATA[success]]>
                                                </documentation>
                                                <condition>not($OnMessage_UpdateHubMobileCallbackFulfillmentOrder_InputVariable.in/ns1:Error/ns1:Code) orstring-length($OnMessage_UpdateHubMobileCallbackFulfillmentOrder_InputVariable.in/ns1:Error/ns1:Code) = 0 or$OnMessage_UpdateHubMobileCallbackFulfillmentOrder_InputVariable.in/ns1:Error/ns1:Code = '0'</condition>
                                                <sequence name="Sequence113">
                                                   <assign name="Assign_Itens_attributes_Mobile"
                                                           xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                                      <copy ignoreMissingFromData="yes">
                                                         <from>$Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:Keywords[custpartycust:KeywordType = 'SKY_MOBILE_ICCID']/custpartycust:KeywordValue</from>
                                                         <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'A La Carte' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Telefonia_Plano']/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Telefonia iccid']/corecom:Value</to>
                                                      </copy>
                                                      <copy ignoreMissingFromData="yes">
                                                         <from>$Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:Keywords[custpartycust:KeywordType = 'SKY_MOBILE_DDD']/custpartycust:KeywordValue</from>
                                                         <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'A La Carte' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Telefonia_Plano']/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Telefonia DDD']/corecom:Value</to>
                                                      </copy>
                                                      <copy ignoreMissingFromData="yes">
                                                         <from>$OnMessage_UpdateHubMobileCallbackFulfillmentOrder_InputVariable.in/ns1:Attributes/ns1:Attribute[ns1:Key = 'Msisdn']/ns1:Value</from>
                                                         <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'A La Carte' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Telefonia_Plano']/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Telefonia msisdn']/corecom:Value</to>
                                                      </copy>
                                                      <copy ignoreMissingFromData="yes">
                                                         <from>$OnMessage_UpdateHubMobileCallbackFulfillmentOrder_InputVariable.in/ns1:Attributes/ns1:Attribute[ns1:Key = 'Imsi']/ns1:Value</from>
                                                         <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'A La Carte' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Telefonia_Plano']/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name='Telefonia imsi']/corecom:Value</to>
                                                      </copy>
                                                   </assign>
                                                   <if name="If_QueryCustomerParty_empty_Keyword">
                                                      <documentation>
                                                         <![CDATA[nao tem msidn na conta]]>
                                                      </documentation>
                                                      <condition>not($Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:Keywords[custpartycust:KeywordType]/custpartycust:KeywordValue) or string-length($Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:Keywords[custpartycust:KeywordType]/custpartycust:KeywordValue) = 0</condition>
                                                      <sequence>
                                                         <assign name="Transformation_input_UpdateCustomerParty_msisdn">
                                                            <bpelx:annotation>
                                                               <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                            </bpelx:annotation>
                                                            <copy>
                                                               <from>ora:doXSLTransformForDoc("Transformations/Transformation_InvokeUpdateCustomerPartyKeywords_UpdateCustomerPartySynchronously_InputVariable.xsl", $OnMessage_UpdateHubMobileCallbackFulfillmentOrder_InputVariable.in, "Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM", $Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM)</from>
                                                               <to variable="InvokeUpdateCustomerPartyKeywords_UpdateCustomerPartySynchronously_InputVariable"
                                                                   part="UpdateCustomerPartySynchronouslyEBM"/>
                                                            </copy>
                                                         </assign>
                                                         <invoke name="InvokeUpdateCustomerPartyKeywords"
                                                                 bpelx:invokeAsDetail="no"
                                                                 partnerLink="CustomerPartyEBS_SOA"
                                                                 portType="ns9:CommunicationsCustomerPartyEBS"
                                                                 operation="UpdateCustomerPartySynchronously"
                                                                 inputVariable="InvokeUpdateCustomerPartyKeywords_UpdateCustomerPartySynchronously_InputVariable"
                                                                 outputVariable="InvokeUpdateCustomerPartyKeywords_UpdateCustomerPartySynchronously_OutputVariable"/>
                                                         <assign name="Transformation_input_UpdateCustomerParty_imsi">
                                                            <bpelx:annotation>
                                                               <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                            </bpelx:annotation>
                                                            <copy>
                                                               <from>ora:doXSLTransformForDoc("Transformations/Transformation_InvokeUpdateCustomerPartyKeywords_UpdateCustomerPartySynchronously_InputVariable_IMSI.xsl", $Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM, "OnMessage_UpdateHubMobileCallbackFulfillmentOrder_InputVariable.in", $OnMessage_UpdateHubMobileCallbackFulfillmentOrder_InputVariable.in)</from>
                                                               <to variable="InvokeUpdateCustomerPartyKeywords_UpdateCustomerPartySynchronously_InputVariable"
                                                                   part="UpdateCustomerPartySynchronouslyEBM"/>
                                                            </copy>
                                                         </assign>
                                                         <invoke name="InvokeUpdateCustomerPartyKeywords"
                                                                 bpelx:invokeAsDetail="no"
                                                                 partnerLink="CustomerPartyEBS_SOA"
                                                                 portType="ns9:CommunicationsCustomerPartyEBS"
                                                                 operation="UpdateCustomerPartySynchronously"
                                                                 inputVariable="InvokeUpdateCustomerPartyKeywords_UpdateCustomerPartySynchronously_InputVariable"
                                                                 outputVariable="InvokeUpdateCustomerPartyKeywords_UpdateCustomerPartySynchronously_OutputVariable"
                                                                 xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                                                                 xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/>
                                                      </sequence>
                                                   </if>
                                                </sequence>
                                                <else><if name="If_valida_a_la_carte"
                                                          xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <documentation>
         <![CDATA[mobile a la carte]]>
      </documentation>
      <condition>(count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'A La Carte' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Telefonia_Plano']) &gt; 0)</condition>
      <assign name="Assign_CancelMobileItem">
         <copy ignoreMissingFromData="yes">
            <from>'Cancelled'</from>
            <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'A La Carte' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Telefonia_Plano']/corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus</to>
         </copy>
         <copy>
            <from>1</from>
            <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'A La Carte' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Telefonia_Plano']/ford:ServiceActionCode</to>
         </copy>
      </assign>
      <else>
         <documentation>
            <![CDATA[Basico]]>
         </documentation>
         <sequence name="Sequence112">
            <assign name="TransformationCancelFulfillmentOrder">
               <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
                  <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
               </bpelx:annotation>
               <copy>
                  <from>ora:doXSLTransformForDoc("Transformations/Transformation_CancelaFulfillmentOrder.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                  <to variable="InvokeUpdateFulfillmentOrderMobileError_UpdateFulfillmentOrderSynchronously_InputVariable"
                      part="UpdateFulfillmentOrderSynchronouslyEBM"/>
               </copy>
            </assign>
            <invoke name="InvokeUpdateFulfillmentOrderMobileError" bpelx:invokeAsDetail="no"
                    partnerLink="CommunicationsFulfillmentOrder" portType="ns20:CommunicationsFulfillmentOrderEBS"
                    operation="UpdateFulfillmentOrderSynchronously"
                    inputVariable="InvokeUpdateFulfillmentOrderMobileError_UpdateFulfillmentOrderSynchronously_InputVariable"
                    outputVariable="InvokeUpdateFulfillmentOrderMobileError_UpdateFulfillmentOrderSynchronously_OutputVariable"
                    xmlns:bpelx="http://schemas.oracle.com/bpel/extension"/>
         </sequence>
      </else>
   </if></else>
                                             </if>
                                          </onMessage>
                                       </pick>
                                       <else>
                                          <documentation>
                                             <![CDATA[nao]]>
                                          </documentation><if name="If_valida_a_la_carte"
                                                              xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <documentation>
         <![CDATA[mobile a la carte]]>
      </documentation>
      <condition>(count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'A La Carte' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Telefonia_Plano']) &gt; 0)</condition>
      <assign name="Assign_CancelMobileItem">
         <copy ignoreMissingFromData="yes">
            <from>'Cancelled'</from>
            <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'A La Carte' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Telefonia_Plano']/corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus</to>
         </copy>
         <copy>
            <from>1</from>
            <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode='ADD' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'A La Carte' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Telefonia_Plano']/ford:ServiceActionCode</to>
         </copy>
      </assign>
      <else>
         <documentation>
            <![CDATA[Basico]]>
         </documentation>
         <sequence name="Sequence112">
            <assign name="TransformationCancelFulfillmentOrder">
               <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
                  <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
               </bpelx:annotation>
               <copy>
                  <from>ora:doXSLTransformForDoc("Transformations/Transformation_CancelaFulfillmentOrder.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                  <to variable="InvokeUpdateFulfillmentOrderMobileError_UpdateFulfillmentOrderSynchronously_InputVariable"
                      part="UpdateFulfillmentOrderSynchronouslyEBM"/>
               </copy>
            </assign>
            <invoke name="InvokeUpdateFulfillmentOrderMobileError" bpelx:invokeAsDetail="no"
                    partnerLink="CommunicationsFulfillmentOrder" portType="ns20:CommunicationsFulfillmentOrderEBS"
                    operation="UpdateFulfillmentOrderSynchronously"
                    inputVariable="InvokeUpdateFulfillmentOrderMobileError_UpdateFulfillmentOrderSynchronously_InputVariable"
                    outputVariable="InvokeUpdateFulfillmentOrderMobileError_UpdateFulfillmentOrderSynchronously_OutputVariable"
                    xmlns:bpelx="http://schemas.oracle.com/bpel/extension"/>
         </sequence>
      </else>
   </if></else>
                                    </if>
                                 </sequence>
                              </scope>
                           </sequence>
                        </if>
                        <if name="D2_Is_SubType_equal_to_Inclusion_and_AccountType_not_equal_to_SkyLivre_and_there_is_no_item_status_equal_to_Finished">
                           <condition>($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Inclusion" or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Prepaid to Postpaid Migration" or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Reg.>Bus. or Bus.>Reg. Migr.") and not(contains(xp20:lower-case(string($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode)), "inclusion") and count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[contains(xp20:lower-case(string(corecom:InstalledProductReference/corecom:Custom/corecomcust:Category)), "livre")]) > 0) and (count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = "Complete"]) = 0)</condition>
                           <sequence name="Sequence24">
                              <sequence name="Sequence10">
                                 <sequence name="A3_">
                                    <sequence>
                                       <scope name="SCP_EnableAccountCustomerParty" 
                                              exitOnStandardFault="no">
                                          <sequence>
                                             <assign name="TransformA3_InputVariable_To_EnableAccountCustomerParty">
                                                <bpelx:annotation>
                                                   <bpelx:pattern patternName="bpelx:transformation"/>
                                                </bpelx:annotation>
                                                <copy>
                                                   <from>ora:doXSLTransformForDoc("xsl/A3_InputVariable_To_EnableAccountCustomerParty1.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM, "Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM", $Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM)</from>
                                                   <to variable="Invoke_A3EnableAccountCustomerParty_InputVariable"
                                                       part="EnableAccountCustomerPartyEBM"/>
                                                </copy>
                                             </assign>
                                             <invoke name="Invoke_A3EnableAccountCustomerParty"
                                                     partnerLink="CustomerPartyEBS_SOA"
                                                     portType="ns9:CommunicationsCustomerPartyEBS"
                                                     operation="EnableAccountCustomerParty"
                                                     inputVariable="Invoke_A3EnableAccountCustomerParty_InputVariable"
                                                     outputVariable="Invoke_A3EnableAccountCustomerParty_OutputVariable"
                                                     bpelx:invokeAsDetail="no"/>
                                          </sequence>
                                       </scope>
									    <if name="If_HasEnabledAccountWithSuccess">
										<documentation>
                                             <![CDATA[yes]]>
                                          </documentation>
										<condition>($Invoke_A3EnableAccountCustomerParty_OutputVariable.EnableAccountCustomerPartyResponseEBM/corecom:EBMHeader/corecom:Custom/ns15:ResponseHeader/ns15:returnCode = "0")and ($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:SalesChannelCode='Salesforce')</condition>
										<scope name="SCP_Invoke_A4UpdateCustomerPartySynchronously"
											   exitOnStandardFault="no">
										  <sequence>
											<assign name="TransformA4_InputVariable_A3Output_To_UpdateCustomerPartySynchronously">
											  <bpelx:annotation>
												<bpelx:pattern patternName="bpelx:transformation"/>
											  </bpelx:annotation>
											  <copy>
												<from>ora:doXSLTransformForDoc("xsl/A4_InputVariable_A3Output_To_UpdateCustomerPartySync.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM, "Invoke_A3EnableAccountCustomerParty_OutputVariable.EnableAccountCustomerPartyResponseEBM", $Invoke_A3EnableAccountCustomerParty_OutputVariable.EnableAccountCustomerPartyResponseEBM)</from>
												<to variable="Invoke_A4UpdateCustomerPartySynchronously_InputVariable"
													part="UpdateCustomerPartySynchronouslyEBM"/>
											  </copy>
											</assign>
											<invoke name="Invoke_A4UpdateCustomerPartySynchronously"
													inputVariable="Invoke_A4UpdateCustomerPartySynchronously_InputVariable"
													outputVariable="Invoke_A4UpdateCustomerPartySynchronously_OutputVariable"
													partnerLink="CustomerPartyEBS"
													portType="ns9:CommunicationsCustomerPartyEBS"
													operation="UpdateCustomerPartySynchronously"
													bpelx:invokeAsDetail="no"/>
										  </sequence>
										</scope>
									  </if>
                                    </sequence>
                                 </sequence>
                              </sequence>
                           </sequence>
                           <else>
                              <sequence>
                                 <if name="D3_Is_OrderType_equal_to_TechnicalSupport_and_SubType_equal_to_Corrective">
                                    <condition>not($Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom[custpartycust:OrganizationType = "Directv Go"]/custpartycust:Keywords[custpartycust:KeywordType = "Pacote Combo" and custpartycust:KeywordValue = "FILHA"]) and not($Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:Keywords[custpartycust:KeywordType = "Pacote Combo" and custpartycust:KeywordValue = "PAI"]) and ($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode) = "Installation Address Change" or ($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:OrderType) = "Technical Support"</condition>
                                    <sequence name="Sequence26">
                                       <scope name="SCP_A5_Invoke_QueryInstalledProducts" 
                                              exitOnStandardFault="no">
                                          <sequence name="A5_">
                                             <assign name="A5_XformProcessSoftwareFulfilmentOrderEBMToQueryInstalledProductsEBM">
                                                <bpelx:annotation>
                                                   <bpelx:pattern patternName="bpelx:transformation"/>
                                                </bpelx:annotation>
                                                <copy>
                                                   <from>ora:doXSLTransformForDoc("xsl/A5_ProcessSoftwareFulfilmentOrderEBMToQueryInstalledProductsEBM.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM, "EBMHeader", $EBMHeader)</from>
                                                   <to variable="A5_QueryInstalledProductList_InputVariable"
                                                       part="QueryInstalledProductListEBM"/>
                                                </copy>
                                             </assign>
                                             <invoke name="A5_Invoke_QueryInstalledProducts"
                                                     partnerLink="CommunicationsInstalledProductEBSV2"
                                                     portType="ns22:CommunicationsInstalledProductEBS"
                                                     operation="QueryInstalledProductList"
                                                     inputVariable="A5_QueryInstalledProductList_InputVariable"
                                                     outputVariable="A5_QueryInstalledProductList_OutputVariable"
                                                     bpelx:invokeAsDetail="no"/>
                                          </sequence>
                                       </scope>
                                       <scope name="SCP_A5_Invoke_QueryFulfillmentOrderList" 
                                              exitOnStandardFault="no">
                                          <sequence name="Sequence44">
                                             <if name="D3_Results_exists">
                                                <condition>count($A5_QueryInstalledProductList_OutputVariable.QueryInstalledProductListResponseEBM/instprod:DataArea)>0 and $A5_QueryInstalledProductList_OutputVariable.QueryInstalledProductListResponseEBM/corecom:EBMHeader/corecom:Custom/ns15:ResponseHeader/ns15:returnCode = '0'</condition>
                                                <empty/>
                                                <else>
                                                   <sequence>
                                                      <sequence name="Sequence43">
                                                         <assign name="A5_XformProcessSoftwareFulfilmentOrderEBMToQueryFulfillmentOrderListEBM">
                                                            <bpelx:annotation>
                                                               <bpelx:pattern patternName="bpelx:transformation"/>
                                                            </bpelx:annotation>
                                                            <copy>
                                                               <from>ora:doXSLTransformForDoc("xsl/A5_ProcessSoftwareFulfilmentOrderEBMToQueryFulfillmentOrderListEBM.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM, "EBMHeader", $EBMHeader)</from>
                                                               <to variable="A5_Invoke_QueryFulfillmentOrderList_InputVariable"
                                                                   part="QueryFulfillmentOrderListEBM"/>
                                                            </copy>
                                                         </assign>
                                                         <invoke name="A5_Invoke_QueryFulfillmentOrderList"
                                                                 partnerLink="CommunicationsFulfillmentOrder"
                                                                 portType="ns20:CommunicationsFulfillmentOrderEBS"
                                                                 operation="QueryFulfillmentOrderList"
                                                                 inputVariable="A5_Invoke_QueryFulfillmentOrderList_InputVariable"
                                                                 outputVariable="A5_Invoke_QueryFulfillmentOrderList_OutputVariable"
                                                                 bpelx:invokeAsDetail="no"/>
                                                         <scope name="SCP_GetEntryOrderProblemCode" 
                                                                exitOnStandardFault="no">
                                                            <assign name="GetEntryOrderProblemCode">
                                                               <copy>
                                                                  <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = "Serviços" and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = "Visita Avulsa"]/ford:Custom/corecomcust:WorkOrderReference/corecomcust:ProblemCode</from>
                                                                  <to>$EntryOrderProblemCode</to>
                                                               </copy>
                                                            </assign>
                                                         </scope>
                                                         <if name="If1">
                                                            <documentation/>
                                                            <condition>count( $A5_Invoke_QueryFulfillmentOrderList_OutputVariable.QueryFulfillmentOrderListResponseEBM/ford:DataArea[./ford:QueryFulfillmentOrderListResponse/ford:FulfillmentOrderLine/ford:Custom/corecomcust:WorkOrderReference/corecomcust:ProblemCode = $EntryOrderProblemCode] ) > 0</condition>
                                                            <sequence name="Sequence45">
                                                               <scope name="Scope18">
                                                                  <scope name="SCP_ValidateDates" 
                                                                         exitOnStandardFault="no">
                                                                     <sequence name="Sequence46">
                                                                        <assign name="GetEntryOrderDateTime">
                                                                           <copy>
                                                                              <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:OrderDateTime</from>
                                                                              <to>$EntryOrderDateTime</to>
                                                                           </copy>
                                                                        </assign>
                                                                        <assign name="FormatEntryOrderDateTime">
                                                                           <copy>
                                                                              <from>xp20:format-dateTime(string($EntryOrderDateTime),"[D01]/[M01]/[Y0001]")</from>
                                                                              <to>$EntryOrderDateTimeFormated</to>
                                                                           </copy>
                                                                        </assign>
                                                                        <assign name="GetLastFulfillmentOrderDate">
                                                                           <copy>
                                                                              <from>$A5_Invoke_QueryFulfillmentOrderList_OutputVariable.QueryFulfillmentOrderListResponseEBM/ford:DataArea[./ford:QueryFulfillmentOrderListResponse/ford:FulfillmentOrderLine/ford:Custom/corecomcust:WorkOrderReference/corecomcust:ProblemCode = $EntryOrderProblemCode][1]/ford:QueryFulfillmentOrderListResponse/ford:OrderDateTime</from>
                                                                              <to>$LastFulfillmentOrderDate</to>
                                                                           </copy>
                                                                        </assign>
                                                                        <assign name="FormatLastFulfillmentOrderDate">
                                                                           <copy>
                                                                              <from>xp20:format-dateTime(string($LastFulfillmentOrderDate),"[D01]/[M01]/[Y0001]")</from>
                                                                              <to>$LastFulfillmentOrderDateFormated</to>
                                                                           </copy>
                                                                        </assign>
                                                                        <extensionActivity>
                                                                           <bpelx:exec name="ValidateWarrantyDate"
                                                                                       language="java">
                                                                           <![CDATA[try{   
java.lang.String dataOrdemService = (java.lang.String)getVariableData("LastFulfillmentOrderDateFormated");   
java.lang.String dataNovaOrdemStr = (java.lang.String)getVariableData("EntryOrderDateTimeFormated");   
   
java.text.SimpleDateFormat sdf = new java.text.SimpleDateFormat("dd/MM/yyyy");   
   
java.util.Date dataOrdem = sdf.parse(dataOrdemService);   
   
java.util.Date dataNovaOrdem = sdf.parse(dataNovaOrdemStr);  
   
java.util.Calendar c = java.util.Calendar.getInstance();   
   
c.setTime(dataOrdem);   
   
c.add(java.util.Calendar.DAY_OF_YEAR, 90);   
   
boolean isPeriodoVigente = c.getTime().after(dataNovaOrdem);   
   
setVariableData("isInWarranty" ,isPeriodoVigente);   
   
}catch(java.text.ParseException ex){   
       
}]]>
                                                                           </bpelx:exec>
                                                                        </extensionActivity>
                                                                     </sequence>
                                                                  </scope>
                                                               </scope>
                                                            </sequence>
                                                            <else>
                                                               <empty/>
                                                            </else>
                                                         </if>
                                                      </sequence>
                                                      <empty/>
                                                   </sequence>
                                                </else>
                                             </if>
                                          </sequence>
                                       </scope>
                                       <if name="D4_If_ExistPremiumOrPrimeProductSubCategory_Or_IsInWarranty">
                                          <condition>(count($A5_QueryInstalledProductList_OutputVariable.QueryInstalledProductListResponseEBM/instprod:DataArea [instprod:QueryInstalledProductListResponse/instprod:Custom/instprodcust:SubCategory = 'Premium' or instprod:QueryInstalledProductListResponse/instprod:Custom/instprodcust:SubCategory = 'Prime'] )>0 and $A5_QueryInstalledProductList_OutputVariable.QueryInstalledProductListResponseEBM/corecom:EBMHeader/corecom:Custom/ns15:ResponseHeader/ns15:returnCode = '0') or ( $isInWarranty = true()) or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine [corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Equipamento' and corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Banda Larga'] or $Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount[custparty:ClassificationCode = 'H' or custparty:ClassificationCode = 'J']</condition>
                                          <sequence name="Sequence27">
                                             <scope name="SCP_A6_Invoke_UpdateFulfillmentOrder" 
                                                    exitOnStandardFault="no">
                                                <sequence>
                                                   <assign name="A6_XformProcessSoftwareFulfillmentOrderEBMToUpdateFulfillmentOrderEBM">
                                                      <bpelx:annotation>
                                                         <bpelx:pattern patternName="bpelx:transformation"/>
                                                      </bpelx:annotation>
                                                      <copy>
                                                         <from>ora:doXSLTransformForDoc("xsl/A6_ProcessSoftwareFulfillmentOrderEBMToUpdateFulfillmentOrderEBM.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                                         <to variable="A6_UpdateFulfillmentOrder_InputVariable"
                                                             part="UpdateFulfillmentOrderEBM"/>
                                                      </copy>
                                                   </assign>
                                                   <if name="D4_If_OrderItem_SubCategory_Equal_Premiun">
                                                      <documentation>
                                                         <![CDATA[Has_Order_Items]]>
                                                      </documentation>
                                                      <condition>count($A6_UpdateFulfillmentOrder_InputVariable.UpdateFulfillmentOrderEBM/ford:DataArea/ford:UpdateFulfillmentOrder/ford:FulfillmentOrderLine)>0</condition>
                                                      <sequence>
                                                         <invoke name="A6_Invoke_UpdateFulfillmentOrder"
                                                                 partnerLink="UpdateSalesOrderCCPSiebelProvABCSImpl"
                                                                 portType="ns20:CommunicationsFulfillmentOrderEBS"
                                                                 operation="UpdateFulfillmentOrder"
                                                                 inputVariable="A6_UpdateFulfillmentOrder_InputVariable"
                                                                 bpelx:invokeAsDetail="no"/>
                                                         <forEach parallel="no" 
                                                                  counterName="v_count" 
                                                                  name="ForEachOrderLine">
                                                            <startCounterValue>1</startCounterValue>
                                                            <finalCounterValue>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine)</finalCounterValue>
                                                            <scope name="Scope10">
                                                               <sequence name="Sequence30">
                                                                  <if name="If_ServiceCategory">
                                                                     <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[position() = $v_count]/corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable and $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[position() = $v_count]/corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = "Serviços" and $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[position() = $v_count]/corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = "Visita Avulsa"</condition>
                                                                     <assign name="A6_Assign_Billable_false">
                                                                        <copy ignoreMissingFromData="yes">
                                                                           <from>'false'</from>
                                                                           <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[position() = $v_count]/corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable</to>
                                                                        </copy>
                                                                     </assign>
                                                                  </if>
                                                               </sequence>
                                                            </scope>
                                                         </forEach>
                                                      </sequence>
                                                   </if>
                                                </sequence>
                                             </scope>
                                          </sequence>
                                       </if>
                                    </sequence>
                                    <else>
                                       <sequence>
                                          <if name="D5_Is_the_SubType_equal_to_ClientWordReconnection">
                                             <condition>($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode) = "Client Word Reconnection"</condition>
                                             <sequence name="Sequence36">
                                                <scope name="SCP_A7_Invoke_ReschedulingOverDueCollectionRule" 
                                                       exitOnStandardFault="no">
                                                   <sequence name="A7">
                                                      <assign name="A7_XformProcessSoftwareFulfillmentOrderEBMToReschedulingOverDueCollectionRuleEBM">
                                                         <bpelx:annotation>
                                                            <bpelx:pattern patternName="bpelx:transformation"/>
                                                         </bpelx:annotation>
                                                         <copy>
                                                            <from>ora:doXSLTransformForDoc("xsl/A7_inputVariable_To_ReschedulingOverDueCollectionRule.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                                            <to variable="A7_ReschedulingOverDueCollectionRule_InputVariable"
                                                                part="ReschedulingOverdueCollectionRuleEBM"/>
                                                         </copy>
                                                      </assign>
                                                      <invoke name="A7_Invoke_ReschedulingOverDueCollectionRule"
                                                              partnerLink="OverdueCollectionRuleEBS"
                                                              portType="ns28:OverdueCollectionRuleEBS"
                                                              operation="ReschedulingOverdueCollectionRule"
                                                              inputVariable="A7_ReschedulingOverDueCollectionRule_InputVariable"
                                                              bpelx:invokeAsDetail="no"
                                                              outputVariable="A7_ReschedulingOverDueCollectionRule_OutputVariable"/>
                                                   </sequence>
                                                </scope>
                                             </sequence>
                                          </if>
                                       </sequence>
                                    </else>
                                 </if>
                              </sequence>
                           </else>
                        </if>
                        <scope name="Bill_Locked_In_Progress_Order_Lines_Scope" 
                               exitOnStandardFault="no">
                           <variables>
                              <variable name="counterAux" type="xsd:int"/>
                           </variables>
                           <sequence name="Bill_Locked_In_Progress_Order_Lines_Sequence">
                              <assign name="TransformQueryCustomerPartyResponse_To_ProcessSoftwareFulfillmentOrderEBM">
                                 <bpelx:annotation>
                                    <bpelx:pattern patternName="bpelx:transformation"/>
                                 </bpelx:annotation>
                                 <copy>
                                    <from>ora:doXSLTransformForDoc("xsl/QueryCustomerPartyResponse_To_ProcessSoftwareFulfillmentOrderEBM.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM, "Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM", $Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM)</from>
                                    <to variable="inputVariable"
                                        part="ProcessSoftwareFulfillmentOrderEBM"/>
                                 </copy>
                              </assign>
                              <if name="If_Check_Upgrade_Recarga">
                                 <documentation>
                                    <![CDATA[isUpgradeRecarga]]>
                                 </documentation>
                                 <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Upgrade de Recarga"</condition>
                                 <sequence name="Sequence56">
                                    <assign name="Assign_OrderDate">
                                       <copy>
                                          <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:OrderDateTime</from>
                                          <to>$OrderDate</to>
                                       </copy>
                                    </assign>
                                    <sequence name="Sequence54">
                                       <assign name="TransformA10_InputVariable_To_RechargeUpgrade_PIPBillFulfillmentOrder"
                                               xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                          <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
                                             <bpelx:pattern patternName="bpelx:transformation"/>
                                          </bpelx:annotation>
                                          <copy>
                                             <from>ora:doXSLTransformForDoc("xsl/InputVariable_To_RechargeUpgradePIPBillFulfillmentOrder.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                             <to variable="Invoke_A10PIPBillFulfillmentOrder_InputVariable"
                                                 part="body"/>
                                          </copy>
                                       </assign>
                                       <if name="If_Has_NonBillable_And_ServiceActionCode_ADD_or_UPDATE_or_DELETE"
                                           xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <documentation>
         <![CDATA[Yes]]>
      </documentation>
      <condition>count($Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'false' and (ford:ServiceActionCode = 'ADD' or ford:ServiceActionCode = 'UPDATE' or ford:ServiceActionCode = 'DELETE')]) != 0</condition>
      <assign name="RemovingNonBillableFromRequest">
         <extensionAssignOperation>
            <bpelx:remove xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
               <bpelx:target>$Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'false' and (ford:ServiceActionCode = 'ADD' or ford:ServiceActionCode = 'UPDATE' or ford:ServiceActionCode = 'DELETE')]</bpelx:target>
            </bpelx:remove>
         </extensionAssignOperation>
      </assign>
   </if><if name="If_A_Billable_Item_Is_Parent_Of_Non_Billable_Itens_Remove_The_Non_Billable_Itens"
            xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <documentation>
         <![CDATA[Yes]]>
      </documentation>
      <condition>count($Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'false' and (corecom:RootParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID = $Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'true']/corecom:Identification/corecom:ApplicationObjectKey/corecom:ID or corecom:ParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID = $Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'true']/corecom:Identification/corecom:ApplicationObjectKey/corecom:ID)]) &gt; 0</condition>
      <assign name="RemovingNonBillableWhichAreSonOfBillableItem">
         <extensionAssignOperation>
            <bpelx:remove xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
               <bpelx:target>$Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'false' and (corecom:RootParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID = $Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'true']/corecom:Identification/corecom:ApplicationObjectKey/corecom:ID or corecom:ParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID = $Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'true']/corecom:Identification/corecom:ApplicationObjectKey/corecom:ID) ]</bpelx:target>
            </bpelx:remove>
         </extensionAssignOperation>
      </assign>
   </if><forEach parallel="no"
                                                counterName="ForEachItem"
                                                name="ForEach_Item">
                                          <startCounterValue>1</startCounterValue>
                                          <finalCounterValue>count($Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine)</finalCounterValue>
                                          <scope name="Scope22">
                                             <variables>
                                                <variable name="Invoke_AccountBalanceAdjustment_CustomCreateAccountBalanceAdjustment_InputVariable"
                                                          messageType="ns30:CustomCreateAccountBalanceAdjustmentReqMsg"/>
                                                <variable name="Invoke_AccountBalanceAdjustment_CustomCreateAccountBalanceAdjustment_OutputVariable"
                                                          messageType="ns30:CustomCreateAccountBalanceAdjustmentRespMsg"/>
                                                <variable name="Invoke_AccountBalanceAdjustment_CustomCreateAccountBalanceAdjustment_OutputVariable_1"
                                                          messageType="ns30:CustomCreateAccountBalanceAdjustmentRespMsg"/>
                                                <variable name="Invoke_Adjustment_UpdateFulfillmentOrderSynchronously_InputVariable"
                                                          messageType="ns20:UpdateFulfillmentOrderSynchronouslyReqMsg"/>
                                                <variable name="Invoke_Adjustment_UpdateFulfillmentOrderSynchronously_OutputVariable"
                                                          messageType="ns20:UpdateFulfillmentOrderSynchronouslyRespMsg"/>
                                                <variable name="Invoke_Adjustment_UpdateFulfillmentOrderSync_UpdateFulfillmentOrderSynchronously_InputVariable"
                                                          messageType="ns20:UpdateFulfillmentOrderSynchronouslyReqMsg"/>
                                                <variable name="Invoke_Adjustment_UpdateFulfillmentOrderSync_UpdateFulfillmentOrderSynchronously_OutputVariable"
                                                          messageType="ns20:UpdateFulfillmentOrderSynchronouslyRespMsg"/>
                                                <variable name="AdjustmentAmount"
                                                          type="xsd:string"/>
                                             </variables>
                                             <sequence name="Sequence55">
                                                <assign name="Assign_Current_Item_to_Adjust">
                                                   <copy>
                                                      <from>$Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[$ForEachItem]</from>
                                                      <to>$currentItemToAdjust</to>
                                                   </copy>
                                                </assign>
                                                <if name="CheckAdjustmentFlag">
                                                   <condition>$currentItemToAdjust/corecom:OriginalFulfillmentOrderLineReference/corecom:Custom/corecomcust:Status = 'Adjusted'</condition>
                                                   <empty name="AlreadyAdjusted"/>
                                                   <else>
                                                      <assign name="Assign_PendingFlag"
                                                              xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      
   <copy bpelx:insertMissingToData="yes"
         xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
                                                            <from>"Pending"</from>
                                                            <to>$currentItemToAdjust/corecom:OriginalFulfillmentOrderLineReference/corecom:Custom/corecomcust:Status</to>
      </copy></assign>
                                                   </else>
                                                </if><if name="If_Need_Adjustment">
                                                   <documentation/>
                                                   <condition>$currentItemToAdjust/ford:ServiceActionCode = "ADD" and $currentItemToAdjust/corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'true' and $currentItemToAdjust/ford:Custom/fordcust:AssetRelationId != '' and $currentItemToAdjust/corecom:OriginalFulfillmentOrderLineReference/corecom:Custom/corecomcust:Status != 'Adjusted'</condition>
                                                   <sequence>
                                                      <assign name="Assign_AssetRelationId">
                                                         <copy>
                                                            <from>$currentItemToAdjust/ford:Custom/fordcust:AssetRelationId</from>
                                                            <to>$AssetRelationId</to>
                                                         </copy>
                                                      </assign>
                                                      <assign name="Assign_DeleteItemReference">
                                                         <copy>
                                                            <from>$Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[ford:ServiceActionCode = 'DELETE'][ford:Custom/fordcust:AssetRelationId = $AssetRelationId]</from>
                                                            <to>$DeleteItemReference</to>
                                                         </copy>
                                                      </assign>
                                                      <assign name="AssignAdjustmentAmount">
                                                         <copy>
                                                            <from>$currentItemToAdjust/ford:FulfillmentOrderSchedule/ford:TotalAmount</from>
                                                            <to>$AdjustmentAmount</to>
                                                         </copy>
                                                      </assign>
                                                      <if name="If_AdjustmentAmount_Zero">
                                                         <condition>$AdjustmentAmount = 0</condition>
                                                         <empty name="DontAdjustAmount"/>
                                                         <else>
                                                            <sequence>
                                                      <assign name="Transform_CurrentItem_to_AccountBalanceAdjustment">
                                                         <bpelx:annotation>
                                                                     <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                         </bpelx:annotation>
                                                         <copy>
                                                            <from>ora:doXSLTransformForDoc("xsl/Transformation_CurrentItem_to_AccountBalanceAdjustment.xsl", $currentItemToAdjust, "DeleteItemReference", $DeleteItemReference, "OrderDate", $OrderDate, "AdjustmentAmount", $AdjustmentAmount)</from>
                                                            <to variable="Invoke_AccountBalanceAdjustment_CustomCreateAccountBalanceAdjustment_InputVariable"
                                                                part="CustomCreateAccountBalanceAdjustmentEBM"/>
                                                         </copy>
                                                      </assign>
                                                      <invoke name="Invoke_AccountBalanceAdjustment"
                                                              partnerLink="AccountBalanceAdjustmentEBSV2"
                                                              portType="ns30:AccountBalanceAdjustmentEBS"
                                                              operation="CustomCreateAccountBalanceAdjustment"
                                                              inputVariable="Invoke_AccountBalanceAdjustment_CustomCreateAccountBalanceAdjustment_InputVariable"
                                                              outputVariable="Invoke_AccountBalanceAdjustment_CustomCreateAccountBalanceAdjustment_OutputVariable"
                                                              bpelx:invokeAsDetail="no"/>
                                                            </sequence>
                                                         </else>
                                                      </if>
                                                      <if name="If_Adjustment_Sucessful_Or_Amount_0">
                                                         <documentation>
                                                            <![CDATA[Sucessful]]>
                                                         </documentation>
                                                         <condition>($Invoke_AccountBalanceAdjustment_CustomCreateAccountBalanceAdjustment_OutputVariable.CustomCreateAccountBalanceAdjustmentResponseEBM/corecom:EBMHeader/corecom:Custom/ns15:ResponseHeader/ns15:returnCode = 0 and $Invoke_AccountBalanceAdjustment_CustomCreateAccountBalanceAdjustment_OutputVariable.CustomCreateAccountBalanceAdjustmentResponseEBM/corecom:EBMHeader/corecom:Custom/ns15:ResponseHeader/ns15:returnMessage = "Sucesso") or $AdjustmentAmount = 0</condition>
                                                         <sequence>
                                                            <assign name="Assign_AdjustedFlag">
                                                               <copy bpelx:insertMissingToData="yes">
                                                                  <from>"Adjusted"</from>
                                                                  <to>$currentItemToAdjust/corecom:OriginalOrderItemReference/corecom:Custom/corecomcust:Status/@listID</to>
                                                               </copy>
                                                            </assign>
                                                            <assign name="Transform_AdjustedItem_to_UpdateFulfillmentOrder">
                                                               <bpelx:annotation>
                                                                  <bpelx:pattern patternName="bpelx:transformation"/>
                                                               </bpelx:annotation>
                                                               <copy>
                                                                  <from>ora:doXSLTransformForDoc("xsl/Transformation_AdjustedItem_to_UpdateFulfillmentOrderSync.xsl", $currentItemToAdjust, "inputVariable.ProcessSoftwareFulfillmentOrderEBM", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                                                  <to variable="Invoke_Adjustment_UpdateFulfillmentOrderSynchronously_InputVariable"
                                                                      part="UpdateFulfillmentOrderSynchronouslyEBM"/>
                                                               </copy>
                                                            </assign>
                                                            <invoke name="Invoke_UpdateFulfillmentOrderSync"
                                                                    partnerLink="CommunicationsFulfillmentOrder"
                                                                    portType="ns20:CommunicationsFulfillmentOrderEBS"
                                                                    operation="UpdateFulfillmentOrderSynchronously"
                                                                    inputVariable="Invoke_Adjustment_UpdateFulfillmentOrderSynchronously_InputVariable"
                                                                    outputVariable="Invoke_Adjustment_UpdateFulfillmentOrderSynchronously_OutputVariable"
                                                                    bpelx:invokeAsDetail="no"/>
                                                         </sequence>
                                                         
                                                      </if>
                                                   </sequence>
                                                   <else>
                                                      <sequence>
                                                         <empty name="AlreadyAdjusted"/>
                                                      </sequence>
                                                   </else>
                                                </if>
                                             </sequence>
                                          </scope>
                                       </forEach>
                                    </sequence><invoke name="Invoke_A10PIPBillFulfillmentOrder"
                                                       bpelx:invokeAsDetail="no"
                                                       partnerLink="BillFulfillmentOrder"
                                                       portType="ns13:Produce_Message_ptt"
                                                       operation="Produce_Message"
                                                       inputVariable="Invoke_A10PIPBillFulfillmentOrder_InputVariable"
                                                       xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                                                       xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/></sequence>
                                 <else>
                                    <documentation>
                                       <![CDATA[notUpgradeRecarga]]>
                                    </documentation>
                                    <sequence>
                                       <assign name="TransformA10_InputVariable_To_PIPBillFulfillmentOrder">
                                          <bpelx:annotation>
                                             <bpelx:pattern patternName="bpelx:transformation"/>
                                          </bpelx:annotation>
                                          <copy>
                                             <from>ora:doXSLTransformForDoc("xsl/A10_InputVariable_To_PIPBillFulfillmentOrder.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                             <to variable="Invoke_A10PIPBillFulfillmentOrder_InputVariable"
                                                 part="body"/>
                                          </copy>
                                       </assign><if name="IfKeywordValueIsChild"
                                                    xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <condition>($Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:Keywords/custpartycust:KeywordValue = 'FILHA')</condition>
      <sequence name="Sequence81">
         <assign name="AssignKeywords" xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
            
            
            
         <copy ignoreMissingFromData="yes" bpelx:insertMissingToData="yes"
               xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
               <from>$Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:Keywords[custpartycust:KeywordValue  = 'FILHA']/custpartycust:KeywordType</from>
               <to>$Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/corecom:CustomerPartyReference/corecom:Custom/corecomcust:Keywords/corecomcust:KeywordType</to>
            </copy><copy ignoreMissingFromData="yes" bpelx:insertMissingToData="yes"
                         xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
               <from>$Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:Keywords[custpartycust:KeywordValue = 'FILHA']/custpartycust:KeywordValue</from>
               <to>$Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/corecom:CustomerPartyReference/corecom:Custom/corecomcust:Keywords/corecomcust:KeywordValue</to>
            </copy><copy ignoreMissingFromData="yes" bpelx:insertMissingToData="yes"
                         xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
               <from>$Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:Keywords[custpartycust:KeywordValue = 'FILHA']/custpartycust:KeywordID</from>
               <to>$Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/corecom:CustomerPartyReference/corecom:Custom/corecomcust:Keywords/corecomcust:KeywordID</to>
            </copy></assign>
      </sequence>
   </if><if name="If_Check_Has_Itens_Locked_In_Progress_And_Billable_True">
                                          <documentation>
                                             <![CDATA[Has_Itens_Locked_In_Progress_And_Billable_True]]>
                                          </documentation>
                                          <condition>count($Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'true']) != 0</condition>
                                          <sequence name="RemoveAndInvokeBFO">
                                             <!--<if name="If_OrderType_Is_UpGrade_OR_DownGrade">
              <documentation>Order is UP or Downgrade.</documentation>
              <condition>($Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:Custom/fordcust:SubTypeCode = "Upgrade With Techn. Exchange" or $Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:Custom/fordcust:SubTypeCode = "Upgd. W/o Technology Exchange" or $Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:Custom/fordcust:SubTypeCode = "Dwgd. With Technology Exchange" or $Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:Custom/fordcust:SubTypeCode = "Dwgd. W/o Technology Exchange")</condition>
              <sequence name="treatmentUpDownGrade">
                <if name="ExistisHWLockedInProgressFlagModifyM">
                  <documentation>Equipment not completed with flag Modify = M</documentation>
                  <condition>count($Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:RootParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID = $Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name = 'Modify']/corecom:Value = 'M' and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress']/corecom:Identification/corecom:ApplicationObjectKey/corecom:ID and corecom:ParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID !='']) > 0</condition>
                  <assign name="RemovingTaxesFromEquipamentsFlagModify">
                    <extensionAssignOperation>
                      <bpelx:remove>
                        <bpelx:target>$Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:RootParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID = $Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name = 'Modify']/corecom:Value = 'M' and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress']/corecom:Identification/corecom:ApplicationObjectKey/corecom:ID and corecom:ParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID !='']</bpelx:target>
                      </bpelx:remove>
                    </extensionAssignOperation>
                  </assign>
                </if>
              </sequence>
            </if>
             Remoção da validação da flag Modify ='M' para atender as regras de cobrança de taxa de UpDownGrade no dia 18/05/2015. ResponsÃ¡vel: Paulo Egidio.
            
            -->
                                             <if name="If_Has_NonLockedInProgress">
                                                <documentation>
                                                   <![CDATA[Yes]]>
                                                </documentation>
                                                <condition>count($Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus != 'Locked In Progress' or not(exists(corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus))]) != 0</condition>
                                                <assign name="RemovingNonLockedItensFromRequest">
                                                   <extensionAssignOperation>
                                                      <bpelx:remove>
                                                         <bpelx:target>$Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus != "Locked In Progress" or not(exists(corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus))]</bpelx:target>
                                                      </bpelx:remove>
                                                   </extensionAssignOperation>
                                                </assign>
                                             </if>
                                             <if name="If_Has_NonBillable_And_ServiceActionCode_ADD_or_UPDATE_or_DELETE">
                                                <documentation>
                                                   <![CDATA[Yes]]>
                                                </documentation>
                                                <condition>count($Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'false' and (ford:ServiceActionCode = 'ADD' or ford:ServiceActionCode = 'UPDATE' or ford:ServiceActionCode = 'DELETE')]) != 0</condition>
                                                <assign name="RemovingNonBillableFromRequest">
                                                   <extensionAssignOperation>
                                                      <bpelx:remove>
                                                         <bpelx:target>$Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'false' and (ford:ServiceActionCode = 'ADD' or ford:ServiceActionCode = 'UPDATE' or ford:ServiceActionCode = 'DELETE')]</bpelx:target>
                                                      </bpelx:remove>
                                                   </extensionAssignOperation>
                                                </assign>
                                             </if>
                                             <if name="If_A_Billable_Item_Is_Parent_Of_Non_Billable_Itens_Remove_The_Non_Billable_Itens">
                                                <documentation>
                                                   <![CDATA[Yes]]>
                                                </documentation>
                                                <condition>count($Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'false' and (corecom:RootParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID = $Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'true']/corecom:Identification/corecom:ApplicationObjectKey/corecom:ID or corecom:ParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID = $Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'true']/corecom:Identification/corecom:ApplicationObjectKey/corecom:ID)]) &gt; 0</condition>
                                                <assign name="RemovingNonBillableWhichAreSonOfBillableItem">
                                                   <extensionAssignOperation>
                                                      <bpelx:remove>
                                                         <bpelx:target>$Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'false' and (corecom:RootParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID = $Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'true']/corecom:Identification/corecom:ApplicationObjectKey/corecom:ID or corecom:ParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID = $Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'true']/corecom:Identification/corecom:ApplicationObjectKey/corecom:ID) ]</bpelx:target>
                                                      </bpelx:remove>
                                                   </extensionAssignOperation>
                                                </assign>
                                             </if>
                                             <if name="If_Has_Subscription_Total_Amount_0_And_ServiceActionCode_ADD_or_UPDATE">
                                                <documentation>
                                                   <![CDATA[Yes]]>
                                                </documentation>
                                                <condition>count($Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine [corecom:ItemReference/corecom:ClassificationCode[@listID='BillingProductTypeCode' and text()='SUBSCRIPTION'] and ford:FulfillmentOrderSchedule/ford:TotalAmount = '0' and (ford:ServiceActionCode = 'ADD' or ford:ServiceActionCode = 'UPDATE')]) != 0</condition>
                                                <assign name="RemovingSubscriptionTotalAmount0">
                                                   <extensionAssignOperation>
                                                      <bpelx:remove>
                                                         <bpelx:target>$Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:ItemReference/corecom:ClassificationCode[@listID='BillingProductTypeCode' and text()='SUBSCRIPTION'] and ford:FulfillmentOrderSchedule/ford:TotalAmount = '0' and (ford:ServiceActionCode = 'ADD' or ford:ServiceActionCode = 'UPDATE')]</bpelx:target>
                                                      </bpelx:remove>
                                                   </extensionAssignOperation>
                                                </assign>
                                             </if>
                                             <if name="If_Has_Action_None">
                                                <documentation>
                                                   <![CDATA[yes]]>
                                                </documentation>
                                                <condition>count($Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[ford:ServiceActionCode = 'NONE' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'true']) != 0</condition>
                                                <assign name="RemovingActionNone">
                                                   <extensionAssignOperation>
                                                      <bpelx:remove>
                                                         <bpelx:target>$Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[ford:ServiceActionCode = 'NONE' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'true']</bpelx:target>
                                                      </bpelx:remove>
                                                   </extensionAssignOperation>
                                                </assign>
                                             </if>
                                             <if name="IfHasImmediateDiscountItemsWithNoDurationLeft">
                                                <documentation>
                                                   <![CDATA[yes]]>
                                                </documentation>
                                                <condition>count($ImmediateDiscountItems/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Duration = 0]) &gt; 0</condition>
                                                <assign name="RemovingImmediateDiscountItems">
                                                   <extensionAssignOperation>
                                                      <bpelx:remove>
                                                         <bpelx:target>$Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine[corecom:Identification/corecom:ID = $ImmediateDiscountItems/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Duration = 0]/corecom:Identification/corecom:ID]</bpelx:target>
                                                      </bpelx:remove>
                                                   </extensionAssignOperation>
                                                </assign>
                                             </if><assign name="TreatmentOfItensServiceActionCodeDELETE_VerifyIfTheyAreInInstalledProductXREF">
                                                <bpelx:annotation>
                                                   <bpelx:pattern patternName="bpelx:transformation"/>
                                                </bpelx:annotation>
                                                <copy>
                                                   <from>ora:doXSLTransformForDoc("xsl/InvokeA10PIPBillFulfillmentOrder_TreatmentOfSACDelete.xsl", $Invoke_A10PIPBillFulfillmentOrder_InputVariable.body)</from>
                                                   <to variable="Invoke_A10PIPBillFulfillmentOrder_InputVariable"
                                                       part="body"/>
                                                </copy>
                                             </assign>
                                             <scope name="SCP_Invoke_A10PIPBillFulfillmentOrder"
                                                    exitOnStandardFault="no">
                                                <if name="IsThereARealNeedToCallPIPBFO">
                                                   <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode != "Voluntary cancellation" and $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode != "Preventive cancellation" and $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode != "Temporary Suspension" and $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode != "Temp. Suspension Reconnection" and $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode != "Entrance - Step 2" and $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode != "Entrance - Step 6" and count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode = 'DELETE' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Pay Per View'] ) = 0 and count($Invoke_A10PIPBillFulfillmentOrder_InputVariable.body/ford:DataArea/ford:ProcessFulfillmentOrderBilling/ford:FulfillmentOrderLine) &gt; 0</condition>
                                                   <invoke name="Invoke_A10PIPBillFulfillmentOrder"
                                                           bpelx:invokeAsDetail="no"
                                                           partnerLink="BillFulfillmentOrder"
                                                           portType="ns13:Produce_Message_ptt"
                                                           operation="Produce_Message"
                                                           inputVariable="Invoke_A10PIPBillFulfillmentOrder_InputVariable"/>
                                                </if>
                                             </scope>
                                          </sequence>
                                       </if>
                                    </sequence>
                                 </else>
                              </if>
                           </sequence>
                        </scope>
                        <scope name="PPV_Treatment" exitOnStandardFault="no">
                           <sequence name="Cancel_PPV_Transaction">
                              <if name="If_Order_Is_a_PPV_Cancelling">
                                 <documentation>
                                    <![CDATA[Yes_It_Is_a_PPV_Cancelling]]>
                                 </documentation>
                                 <condition>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode = 'DELETE' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Pay Per View']) > 0 and count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode[text()="Entrance - Step 6" or text()="Voluntary cancellation" or text()="Preventive cancellation"])=0</condition>
                                 <sequence>
                                    <forEach parallel="no" 
                                             counterName="ForEachPPVCancelCounter" 
                                             name="ForEachPPVCancel">
                                       <startCounterValue>1</startCounterValue>
                                       <finalCounterValue>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode = 'DELETE' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Pay Per View'])</finalCounterValue>
                                       <scope name="Scope19">
                                          <variables>
                                             <variable name="PPVCancel_currentOrderLine"
                                                       element="ford:FulfillmentOrderLine"/>
                                          </variables>
                                          <sequence>
                                             <assign name="Assign_PPV_Cancel">
                                                <copy>
                                                   <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[ford:ServiceActionCode = 'DELETE' and corecom:InstalledProductReference/corecom:Custom/corecomcust:Category = 'Pay Per View'][position() = $ForEachPPVCancelCounter]</from>
                                                   <to>$PPVCancel_currentOrderLine</to>
                                                </copy>
                                             </assign>
                                             <assign name="ProcessSoftwareFulfillmentOrderEBMToCustomCreateAccountBalanceAdjustmentEBM">
                                                <bpelx:annotation>
                                                   <bpelx:pattern patternName="bpelx:transformation"/>
                                                </bpelx:annotation>
                                                <copy>
                                                   <from>ora:doXSLTransformForDoc("xsl/ProcessSoftwareFulfillmentOrderEBM_To_CustomCreateAccountBalanceAdjustmentEBM.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM, "PPVCancel_currentOrderLine", $PPVCancel_currentOrderLine)</from>
                                                   <to variable="Invoke_CustomCreateAccountBalanceAdjustment_InputVariable"
                                                       part="CustomCreateAccountBalanceAdjustmentEBM"/>
                                                </copy>
                                             </assign>
                                             <invoke name="Invoke_CreateAccountBalanceAdjustment"
                                                     partnerLink="AccountBalanceAdjustmentEBSV2"
                                                     portType="ns30:AccountBalanceAdjustmentEBS"
                                                     operation="CustomCreateAccountBalanceAdjustment"
                                                     inputVariable="Invoke_CustomCreateAccountBalanceAdjustment_InputVariable"
                                                     outputVariable="Invoke_CustomCreateAccountBalanceAdjustment_OutputVariable"
                                                     bpelx:invokeAsDetail="no"/>
                                          </sequence>
                                       </scope>
                                    </forEach>
                                 </sequence>
                              </if>
                           </sequence>
                        </scope>
                        <scope name="Entrance_Step_2_Treatment" 
                               exitOnStandardFault="no">
                           <sequence name="Entrance_Step_2_Treatment">
                              <if name="If_Order_Is_an_Entrance_Step_2">
                                 <documentation>
                                    <![CDATA[Yes_It_Is_an_Entrance_Step_2]]>
                                 </documentation>
                                 <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Entrance - Step 2"</condition>
                                 <forEach parallel="no" 
                                          counterName="counter" 
                                          name="ForEachItemBillable">
                                    <startCounterValue>1</startCounterValue>
                                    <finalCounterValue>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'true'])</finalCounterValue>
                                    <scope name="Item_Is_Billable">
                                       <sequence name="For_Each_Billable">
                                          <assign name="AssignLineCounter">
                                             <copy ignoreMissingFromData="yes"
                                                   bpelx:insertMissingToData="yes">
                                                <from>$counter</from>
                                                <to>$curFOL/value</to>
                                             </copy>
                                          </assign>
                                          <if name="If_TheProductToSuspendExistsOnBRM">
                                             <documentation>
                                                <![CDATA[ProductExistsOnBRM]]>
                                             </documentation>
                                             <condition>string(xref:lookupXRef('oramds:/apps/AIAMetaData/xref/INSTALLEDPRODUCT_ID.xref', 'COMMON', $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'true'][position() = $counter]/corecom:InstalledProductReference/corecom:InstalledProductIdentification/corecom:BusinessComponentID, 'BRM_01', false())) != ""</condition>
                                             <if name="Is_Discount">
                                                <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:Billable = 'true'][position() = $counter]/corecom:ItemReference/corecom:ClassificationCode[@listID = 'BillingProductTypeCode'] = 'DISCOUNT'</condition>
                                                <sequence name="Setting_Discounts_To_Suspended">
                                                   <assign name="ProcessSoftwareFulfillmentOrderEBMToPCM_OP_SUBSCRIPTION_SET_DISCOUNT_STATUS">
                                                      <bpelx:annotation>
                                                         <bpelx:pattern patternName="bpelx:transformation"/>
                                                      </bpelx:annotation>
                                                      <copy>
                                                         <from>ora:doXSLTransformForDoc("xsl/ProcessSoftwareFulfillmentOrderEBM_To_PCM_OP_SUBSCRIPTION_SET_DISCOUNT_STATUS.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM, "curFulfillmentOrderLine", $curFOL)</from>
                                                         <to variable="PCM_OP_SUBSCRIPTION_SET_DISCOUNT_STATUS_InputVariable"
                                                             part="PCM_OP_SUBSCRIPTION_SET_DISCOUNT_STATUS_inputFlist"/>
                                                      </copy>
                                                   </assign>
                                                   <invoke name="Invoke_BRM_PCM_OP_SUBSCRIPTION_SET_DISCOUNT_STATUS"
                                                           inputVariable="PCM_OP_SUBSCRIPTION_SET_DISCOUNT_STATUS_InputVariable"
                                                           outputVariable="PCM_OP_SUBSCRIPTION_SET_DISCOUNT_STATUS_OutputVariable"
                                                           partnerLink="BRMSUBSCRIPTIONService"
                                                           portType="ns32:BRMSUBSCRIPTIONService_ptt"
                                                           operation="PCM_OP_SUBSCRIPTION_SET_DISCOUNT_STATUS"/>
                                                </sequence>
                                                <else>
                                                   <sequence name="Setting_Products_To_Suspended">
                                                      <assign name="ProcessSoftwareFulfillmentOrderEBMToPCM_OP_SUBSCRIPTION_SET_PRODUCT_STATUS">
                                                         <bpelx:annotation>
                                                            <bpelx:pattern patternName="bpelx:transformation"/>
                                                         </bpelx:annotation>
                                                         <copy>
                                                            <from>ora:doXSLTransformForDoc("xsl/ProcessSoftwareFulfillmentOrderEBM_To_PCM_OP_SUBSCRIPTION_SET_PRODUCT_STATUS.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM, "curFulfillmentOrderLine", $curFOL)</from>
                                                            <to variable="PCM_OP_SUBSCRIPTION_SET_PRODUCT_STATUS_InputVariable"
                                                                part="PCM_OP_SUBSCRIPTION_SET_PRODUCT_STATUS_inputFlist"/>
                                                         </copy>
                                                      </assign>
                                                      <invoke name="Invoke_BRM_PCM_OP_SUBSCRIPTION_SET_PRODUCT_STATUS"
                                                              inputVariable="PCM_OP_SUBSCRIPTION_SET_PRODUCT_STATUS_InputVariable"
                                                              outputVariable="PCM_OP_SUBSCRIPTION_SET_PRODUCT_STATUS_OutputVariable"
                                                              partnerLink="BRMSUBSCRIPTIONService"
                                                              portType="ns32:BRMSUBSCRIPTIONService_ptt"
                                                              operation="PCM_OP_SUBSCRIPTION_SET_PRODUCT_STATUS"/>
                                                   </sequence>
                                                </else>
                                             </if>
                                          </if>
                                       </sequence>
                                    </scope>
                                 </forEach>
                              </if>
                           </sequence>
                        </scope>
                        <scope name="Temporary_Suspension_Treatment" 
                               exitOnStandardFault="no">
                           <variables>
                              <variable name="SKY_OP_CUST_POL_TEMP_DEACTIVATE_SERVICES_InputVariable"
                                        messageType="ns32:SKY_OP_CUST_POL_TEMP_DEACTIVATE_SERVICES_inmsg"/>
                              <variable name="SKY_OP_CUST_POL_TEMP_DEACTIVATE_SERVICES_OutputVariable"
                                        messageType="ns32:SKY_OP_CUST_POL_TEMP_DEACTIVATE_SERVICES_outmsg"/>
                           </variables>
                           <sequence name="Temporary_Suspension_Treatment">
                              <if name="If_Order_Is_Temporary_Suspension">
                                 <documentation>
                                    <![CDATA[Yes_It_Is_Temporary_Suspension]]>
                                 </documentation>
                                 <condition>contains(xp20:lower-case(string($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode)), "temporary suspension")</condition>
                                 <sequence name="Call_Temporary_Suspension_BRM">
                                    <assign name="ProcessSoftwareFulfillmentOrderEBMToSKY_OP_CUST_POL_TEMP_DEACTIVATE_SERVICES">
                                       <bpelx:annotation>
                                          <bpelx:pattern patternName="bpelx:transformation"/>
                                       </bpelx:annotation>
                                       <copy>
                                          <from>ora:doXSLTransformForDoc("xsl/ProcessSoftwareFulfillmentOrderEBMToSKY_OP_CUST_POL_TEMP_DEACTIVATE_SERVICES.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                          <to variable="SKY_OP_CUST_POL_TEMP_DEACTIVATE_SERVICES_InputVariable"
                                              part="SKY_OP_CUST_POL_TEMP_DEACTIVATE_SERVICES_inputFlist"/>
                                       </copy>
                                    </assign>
                                    <invoke name="Invoke_SKY_OP_CUST_POL_TEMP_DEACTIVATE_SERVICES"
                                            inputVariable="SKY_OP_CUST_POL_TEMP_DEACTIVATE_SERVICES_InputVariable"
                                            outputVariable="SKY_OP_CUST_POL_TEMP_DEACTIVATE_SERVICES_OutputVariable"
                                            partnerLink="BRMCUSTService"
                                            portType="ns32:BRMCUSTService_ptt"
                                            operation="SKY_OP_CUST_POL_TEMP_DEACTIVATE_SERVICES"/>
                                 </sequence>
                              </if>
                           </sequence>
                        </scope>
                        <scope name="Temporary_Suspension_Reconnection_Treatment" 
                               exitOnStandardFault="no">
                           <variables>
                              <variable name="SKY_OP_CUST_POL_TEMP_REACTIVATE_SERVICES_InputVariable"
                                        messageType="ns32:SKY_OP_CUST_POL_TEMP_REACTIVATE_SERVICES_inmsg"/>
                              <variable name="SKY_OP_CUST_POL_TEMP_REACTIVATE_SERVICES_OutputVariable"
                                        messageType="ns32:SKY_OP_CUST_POL_TEMP_REACTIVATE_SERVICES_outmsg"/>
                           </variables>
                           <sequence name="Temporary_Suspension_Reconnection_Treatment">
                              <if name="If_Order_Is_Temporary_Suspension_Reconnection">
                                 <documentation>
                                    <![CDATA[Yes_It_Is_Temporary_Suspension_Reconnection]]>
                                 </documentation>
                                 <condition>contains(xp20:lower-case(string($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode)), "temp. suspension reconnection")</condition>
                                 <sequence name="Call_Temporary_Suspension_Reconnection_BRM">
                                    <assign name="ProcessSoftwareFulfillmentOrderEBMToSKY_OP_CUST_POL_TEMP_REACTIVATE_SERVICES">
                                       <bpelx:annotation>
                                          <bpelx:pattern patternName="bpelx:transformation"/>
                                       </bpelx:annotation>
                                       <copy>
                                          <from>ora:doXSLTransformForDoc("xsl/ProcessSoftwareFulfillmentOrderEBMToSKY_OP_CUST_POL_TEMP_REACTIVATE_SERVICES.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                          <to variable="SKY_OP_CUST_POL_TEMP_REACTIVATE_SERVICES_InputVariable"
                                              part="SKY_OP_CUST_POL_TEMP_REACTIVATE_SERVICES_inputFlist"/>
                                       </copy>
                                    </assign>
                                    <invoke name="Invoke_SKY_OP_CUST_POL_TEMP_REACTIVATE_SERVICES"
                                            inputVariable="SKY_OP_CUST_POL_TEMP_REACTIVATE_SERVICES_InputVariable"
                                            outputVariable="SKY_OP_CUST_POL_TEMP_REACTIVATE_SERVICES_OutputVariable"
                                            partnerLink="BRMCUSTService"
                                            portType="ns32:BRMCUSTService_ptt"
                                            operation="SKY_OP_CUST_POL_TEMP_REACTIVATE_SERVICES"/>
                                 </sequence>
                              </if>
                           </sequence>
                        </scope>
                        <scope name="ATOrder">
                           <if name="If_IsATOrder">
                              <condition>xp20:lower-case(string($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:OrderType)) = "technical support"</condition>
                              <sequence name="Sequence37">
                                 <forEach parallel="no" 
                                          counterName="V_ItemCounter" 
                                          name="ForEachOrderItem">
                                    <startCounterValue>1</startCounterValue>
                                    <finalCounterValue>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[xp20:lower-case(string(corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus)) != "locked in progress" or xp20:lower-case(string(ford:ServiceActionCode)) = "delete"])</finalCounterValue>
                                    <scope name="Scope15">
                                       <assign name="AssignComplete">
                                          <copy>
                                             <from>'Complete'</from>
                                             <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[xp20:lower-case(string(corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus)) != "locked in progress" or xp20:lower-case(string(ford:ServiceActionCode)) = "delete"][position() = $V_ItemCounter]/corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus</to>
                                          </copy>
                                       </assign>
                                    </scope>
                                 </forEach>
                              </sequence>
                           </if>
                        </scope>
                        <scope name="UpdateOrderAndPerformAutoAsset" exitOnStandardFault="no">
                           <variables>
                              <variable name="ItemsToChangeStatus" element="ford:FulfillmentOrderEBO"/>
                           </variables>
                           <sequence name="Sequence52">
                              <sequence name="A11eA13_UpdateOrderAndPerformAutoAsset">
                                 <assign name="FindItemsToChangeStatus">
                                    <bpelx:annotation>
                                       <bpelx:pattern patternName="bpelx:transformation"/>
                                    </bpelx:annotation>
                                    <copy>
                                       <from>ora:doXSLTransformForDoc("xsl/FindItensToChangeStatus.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                       <to variable="ItemsToChangeStatus"/>
                                    </copy>
                                 </assign>
                                 <if name="If_HasOrderItemsToChangeStatus">
                                    <documentation>
                                       <![CDATA[Has_Order_Items]]>
                                    </documentation>
                                    <condition>count($ItemsToChangeStatus/ford:FulfillmentOrderLine)&gt;0</condition>
                                    <sequence name="Sequence63">
                                       <sequence name="UpdateOrderAndPerformAutoAsset">
                                          <sequence>
                                             <scope name="UpdateCompletionStatus" exitOnStandardFault="no">
                                                <sequence>
                                                   <assign name="TransformA13_InputVariable_To_UpdateSalesOrderCCPSiebelProvABCSImpl">
                                                      <bpelx:annotation>
                                                         <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                      </bpelx:annotation>
                                                      <copy>
                                                         <from>ora:doXSLTransformForDoc("xsl/A13_InputVariable_To_UpdateSalesOrderCCPSiebelProvABCSImpl.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM, "ItemsToChangeStatus", $ItemsToChangeStatus, "Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM", $Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM)</from>
                                                         <to variable="Invoke_A13UpdateSalesOrderCCPSiebelProvABCSImpl_InputVariable"
                                                             part="UpdateFulfillmentOrderEBM"/>
                                                      </copy>
                                                   </assign>
                                                   <!-- <invoke name="Invoke_A13UpdateSalesOrderCCPSiebelProvABCSImpl" inputVariable="Invoke_A13UpdateSalesOrderCCPSiebelProvABCSImpl_InputVariable" partnerLink="UpdateSalesOrderCCPSiebelProvABCSImpl" portType="ns20:CommunicationsFulfillmentOrderEBS" operation="UpdateFulfillmentOrder" bpelx:invokeAsDetail="no" /> -->
                                                </sequence>
                                             </scope>
                                             <if name="If_HasLineLockedWithoutWO">
                                                <documentation>
                                                   <![CDATA[Yes]]>
                                                </documentation>
                                                <condition>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[xp20:lower-case(string(corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus)) = "locked in progress" and not(boolean(corecom:InstalledProductReference/corecom:Custom/corecomcust:WorkOrderIndicator))]) &gt; 0</condition>
                                                <sequence>
                                                   <forEach parallel="no" counterName="LinesToCompleteCounter"
                                                            name="ForEach_LinesToComplete">
                                                      <startCounterValue>1</startCounterValue>
                                                      <finalCounterValue>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[xp20:lower-case(string(corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus)) = "locked in progress" and not(boolean(corecom:InstalledProductReference/corecom:Custom/corecomcust:WorkOrderIndicator))])</finalCounterValue>
                                                      <scope name="Scope13">
                                                         <assign name="A12_Assign_Complete">
                                                            <copy bpelx:insertMissingToData="yes">
                                                               <from>'Complete'</from>
                                                               <to>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[xp20:lower-case(string(corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus)) = "locked in progress" and not(boolean(corecom:InstalledProductReference/corecom:Custom/corecomcust:WorkOrderIndicator))][position() = $LinesToCompleteCounter]/corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus</to>
                                                            </copy>
                                                         </assign>
                                                      </scope>
                                                   </forEach>
                                                </sequence>
                                             </if>
                                          </sequence>
                                       </sequence>
                                    </sequence>
                                 </if>
                              </sequence>
                              <assign name="AssignQueryCustomerParty">
                                 <copy ignoreMissingFromData="yes">
                                    <from>$Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM</from>
                                    <to>$Invoke_QueryCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM</to>
                                 </copy>
                              </assign>
                              <if name="IfSubTypeCodeIsAccountInclusionAndKeywordIsPacoteComboPai">
                                 <condition>($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = 'Account Inclusion') and $Invoke_QueryCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:Keywords[custpartycust:KeywordType = 'Pacote Combo PAI']/custpartycust:KeywordValue</condition>
                                 <sequence>
                                    <assign name="AssignCreateParentRelationship">
                                       <copy>
                                          <from>$Invoke_QueryCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:Keywords[custpartycust:KeywordType = 'Pacote Combo PAI']/custpartycust:KeywordValue</from>
                                          <to>$CreateParentRelationship_InputVariable.parameters/ns39:parentClientId</to>
                                       </copy>
                                       <copy>
                                          <from>''</from>
                                          <to>$CreateParentRelationship_InputVariable.parameters/ns39:childClientId</to>
                                       </copy>
                                       <copy>
                                          <from>'T'</from>
                                          <to>$CreateParentRelationship_InputVariable.parameters/ns39:flagTransferValue</to>
                                       </copy>
                                    </assign>
                                    <invoke name="InvokeCreateParentRelationship" bpelx:invokeAsDetail="no"
                                            partnerLink="CommunicationsAccountRelationshipEBS"
                                            portType="ns38:CommunicationsAccountRelationshipEBSPort"
                                            operation="CreateParentRelationship"
                                            inputVariable="CreateParentRelationship_InputVariable"
                                            outputVariable="CreateParentRelationship_OutputVariable"/>
                                    <assign name="TransformationReqQueryCustomerParty_To_UpdateCustomerPartySynchronously_Fiber">
                                       <bpelx:annotation>
                                          <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                       </bpelx:annotation>
                                       <copy>
                                          <from>ora:doXSLTransformForDoc("xsl/TransformationReqQueryCustomerParty_To_UpdateCustomerPartySynchronously_Fiber.xsl", $Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM)</from>
                                          <to variable="UpdateCustomerPartySynchronously_InputVariable_Fiber"
                                              part="UpdateCustomerPartySynchronouslyEBM"/>
                                       </copy>
                                    </assign>
                                    <invoke name="InvokeUpdateCustomerPartySynchronously" bpelx:invokeAsDetail="no"
                                            partnerLink="CustomerPartyEBS_SOA"
                                            portType="ns9:CommunicationsCustomerPartyEBS"
                                            operation="UpdateCustomerPartySynchronously"
                                            inputVariable="UpdateCustomerPartySynchronously_InputVariable_Fiber"
                                            outputVariable="UpdateCustomerPartySynchronously_OutputVariable_Fiber"/>
                                 </sequence>
                                 <elseif>
                                    <documentation>
                                       <![CDATA[Create hierarchy for parent account]]>
                                    </documentation>
                                    <condition>($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = 'Account Inclusion') and (count($Invoke_QueryCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:Keywords[custpartycust:KeywordType = 'Pacote Combo' and custpartycust:KeywordValue = 'PAI']) &gt; 0)</condition>
                                    <sequence name="Seq_Parent_Customer">
                                       <assign name="AssignCreateParentRelationship">
                                          <copy>
                                             <from>$Invoke_QueryCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/corecom:Identification/corecom:ID</from>
                                             <to>$CreateParentRelationship_InputVariable.parameters/ns39:parentClientId</to>
                                          </copy>
                                          <copy>
                                             <from>''</from>
                                             <to>$CreateParentRelationship_InputVariable.parameters/ns39:childClientId</to>
                                          </copy>
                                             <copy>
                                             <from>'T'</from>
                                             <to>$CreateParentRelationship_InputVariable.parameters/ns39:flagTransferValue</to>
                                          </copy>
                                       </assign>
                                       <invoke name="InvokeCreateParentRelationship" bpelx:invokeAsDetail="no"
                                               partnerLink="CommunicationsAccountRelationshipEBS"
                                               portType="ns38:CommunicationsAccountRelationshipEBSPort"
                                               operation="CreateParentRelationship"
                                               inputVariable="CreateParentRelationship_InputVariable"
                                               outputVariable="CreateParentRelationship_OutputVariable"/>
                                       </sequence>
                                 </elseif>
                                 <else>
                                    <documentation>
                                       <![CDATA[This is not an Account Inclusion order]]>
                                    </documentation>
                                    <empty name="Do_nothing"/>
                                 </else>
                              </if>
                              <if name="IfIsChildAndSubtypeInclusion">
                                 <condition>($Invoke_QueryCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:Keywords[custpartycust:KeywordType = 'Pacote Combo' and custpartycust:KeywordValue = 'FILHA']) and ($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Inclusion")</condition>
                                 <sequence name="Sequence71">
                                    <assign name="TransformationReqQueryWorkOrderList">
                                       <bpelx:annotation>
                                          <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                       </bpelx:annotation>
                                       <copy>
                                          <from>ora:doXSLTransformForDoc("xsl/TransformationReqQueryWorkOrderList.xsl", $Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM)</from>
                                          <to variable="QueryWorkOrderList_InputVariable" part="QueryWorkOrderListEBM"/>
                                       </copy>
                                    </assign>
                                    <invoke name="InvokeQueryWorkOrderList"
                                            partnerLink="CommunicationsWorkOrderEBS"
                                            portType="ns48:CommunicationsWorkOrderEBS" operation="QueryWorkOrderList"
                                            inputVariable="QueryWorkOrderList_InputVariable"
                                            outputVariable="QueryWorkOrderList_OutputVariable"
                                            bpelx:invokeAsDetail="no"/>
                                    <if name="IfHasTwoOs">
                                       <condition>count($QueryWorkOrderList_OutputVariable.QueryWorkOrderListResponseEBM/ns49:DataArea) &gt; 1</condition>
                                       <sequence name="Sequence73">
                                          <assign name="AssignCurrentAccount">
                                             <copy ignoreMissingFromData="no">
                                                <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SKYAccountNumber</from>
                                                <to>$QueryCustomerParty_InputVariable_CurrentAccount.QueryCustomerPartyEBM/custparty:DataArea/custparty:QueryCustomerParty/corecom:Identification/corecom:ID</to>
                                             </copy>
                                          </assign>
                                          <invoke name="InvokeQueryCustomerParty" bpelx:invokeAsDetail="no"
                                                  partnerLink="CustomerPartyEBS_SOA"
                                                  portType="ns9:CommunicationsCustomerPartyEBS"
                                                  operation="QueryCustomerParty"
                                                  inputVariable="QueryCustomerParty_InputVariable_CurrentAccount"
                                                  outputVariable="QueryCustomerParty_OutputVariable_CurrentAccount"/>
                                          <forEach parallel="no" counterName="ForEach3Counter" name="ForEachOsChilds">
                                             <startCounterValue>1</startCounterValue>
                                             <finalCounterValue>count($QueryWorkOrderList_OutputVariable.QueryWorkOrderListResponseEBM/ns49:DataArea)</finalCounterValue>
                                             <scope name="Scope26">
                                                <variables>
                                                   <variable name="QueryWorkOrderListFor"
                                                             messageType="ns48:QueryWorkOrderListRespMsg"/>
                                                </variables>
                                                <sequence name="Sequence74">
                                                   <assign name="AssignStatusCode">
                                                      <copy ignoreMissingFromData="yes">
                                                         <from>$QueryWorkOrderList_OutputVariable.QueryWorkOrderListResponseEBM/ns49:DataArea[$ForEach3Counter]</from>
                                                         <to>$QueryWorkOrderListFor.QueryWorkOrderListResponseEBM/ns49:DataArea</to>
                                                      </copy>
                                                   </assign>
                                                   <if name="NotExecuted">
                                                      <condition>count($QueryWorkOrderListFor.QueryWorkOrderListResponseEBM/ns49:DataArea/ns49:QueryWorkOrderListResponse/corecom:Status[corecom:Code = "Executada" or corecom:Code = "Finalizada"])=0</condition>
                                                      <sequence><assign name="Transformation_QueryWorkOrderListFor"
                                                                          xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
         <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
      </bpelx:annotation>
      <copy>
         <from>ora:doXSLTransformForDoc("xsl/TransformationQueryWorkOrderListFor_To_QueryWorkOrderList.xsl", $QueryWorkOrderListFor.QueryWorkOrderListResponseEBM)</from>
         <to variable="QueryWorkOrderList_InputVariable_QueryOS" part="QueryWorkOrderListEBM"/>
      </copy>
   </assign><invoke name="InvokeQueryWorkOrderList"
                                                                 partnerLink="CommunicationsWorkOrderEBS"
                                                                 portType="ns48:CommunicationsWorkOrderEBS"
                                                                 operation="QueryWorkOrderList"
                                                                 inputVariable="QueryWorkOrderList_InputVariable_QueryOS"
                                                                 outputVariable="QueryWorkOrderList_OutputVariable_QueryOS"
                                                                 bpelx:invokeAsDetail="no"/>
                                                         <assign name="AssignQueryWorkOrderList_To_QueryCustomerParty">
                                                            <copy ignoreMissingFromData="yes">
                                                               <from>$QueryWorkOrderList_OutputVariable_QueryOS.QueryWorkOrderListResponseEBM/ns49:DataArea/ns49:QueryWorkOrderListResponse/corecom:CustomerPartyReference/corecom:PartyIdentification/corecom:ID</from>
                                                               <to>$QueryCustomerParty_InputVariable_HasOS.QueryCustomerPartyEBM/custparty:DataArea/custparty:QueryCustomerParty/corecom:Identification/corecom:ID</to>
                                                            </copy>
                                                         </assign>
                                                         <invoke name="InvokeQueryCustomerParty"
                                                                 bpelx:invokeAsDetail="no"
                                                                 partnerLink="CustomerPartyEBS_SOA"
                                                                 portType="ns9:CommunicationsCustomerPartyEBS"
                                                                 operation="QueryCustomerParty"
                                                                 inputVariable="QueryCustomerParty_InputVariable_HasOS"
                                                                 outputVariable="QueryCustomerParty_OutputVariable_HasOS"/>
							<assign name="AssignGetDueDateValue">
                                                            <copy ignoreMissingFromData="yes">
                                                               <from>$QueryCustomerParty_OutputVariable_CurrentAccount.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:DueDate</from>
                                                               <to>$getDueDateValue</to>
                                                            </copy>
                                                         </assign>
                                                         <assign name="AssignUpdateCustomerParty">
                                                            <copy ignoreMissingFromData="yes">
                                                               <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/corecom:EBMHeader/corecom:Custom/ns15:InteroperabilityHeader/ns15:consumerSystem</from>
                                                               <to>$InvokeUpdateCustomerPartySynchronously_UpdateCustomerPartySynchronously_InputVariable_FlowHasTwoOS.UpdateCustomerPartySynchronouslyEBM/corecom:EBMHeader/corecom:Custom/ns15:InteroperabilityHeader/ns15:consumerSystem</to>
                                                            </copy>
                                                            <copy ignoreMissingFromData="yes">
                                                               <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/corecom:EBMHeader/corecom:Custom/ns15:InteroperabilityHeader/ns15:userId</from>
                                                               <to>$InvokeUpdateCustomerPartySynchronously_UpdateCustomerPartySynchronously_InputVariable_FlowHasTwoOS.UpdateCustomerPartySynchronouslyEBM/corecom:EBMHeader/corecom:Custom/ns15:InteroperabilityHeader/ns15:userId</to>
                                                            </copy>
                                                            <copy ignoreMissingFromData="yes">
                                                               <from>$QueryCustomerParty_OutputVariable_HasOS.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/corecom:Identification/corecom:ID</from>
                                                               <to>$InvokeUpdateCustomerPartySynchronously_UpdateCustomerPartySynchronously_InputVariable_FlowHasTwoOS.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/corecom:Identification/corecom:ID</to>
                                                            </copy>
                                                            <copy ignoreMissingFromData="yes">
                                                               <from>$QueryCustomerParty_OutputVariable_HasOS.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/corecom:Identification/corecom:ID</from>
                                                               <to>$InvokeUpdateCustomerPartySynchronously_UpdateCustomerPartySynchronously_InputVariable_FlowHasTwoOS.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/custparty:CustomerPartyAccount/corecom:Identification/corecom:ID</to>
                                                            </copy>
                                                            <copy ignoreMissingFromData="yes">
                                                               <from>$QueryCustomerParty_OutputVariable_HasOS.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/corecom:BillingProfileIdentification/corecom:ID</from>
                                                               <to>$InvokeUpdateCustomerPartySynchronously_UpdateCustomerPartySynchronously_InputVariable_FlowHasTwoOS.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/custparty:CustomerPartyAccount/corecom:BillingProfileIdentification/corecom:ID</to>
                                                            </copy>
                                                            <copy ignoreMissingFromData="yes">
                                                               <from>$getDueDateValue</from>
                                                               <to>$InvokeUpdateCustomerPartySynchronously_UpdateCustomerPartySynchronously_InputVariable_FlowHasTwoOS.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:DueDate</to>
                                                            </copy>
                                                            <copy ignoreMissingFromData="yes">
                                                               <from>'true'</from>
                                                               <to>$InvokeUpdateCustomerPartySynchronously_UpdateCustomerPartySynchronously_InputVariable_FlowHasTwoOS.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:NotEnterCollectionRuleIndicator</to>
                                                            </copy>
                                                         </assign>
                                                         <invoke name="InvokeUpdateCustomerPartySynchronously"
                                                                 partnerLink="CustomerPartyEBS"
                                                                 portType="ns9:CommunicationsCustomerPartyEBS"
                                                                 operation="UpdateCustomerPartySynchronously"
                                                                 inputVariable="InvokeUpdateCustomerPartySynchronously_UpdateCustomerPartySynchronously_InputVariable_FlowHasTwoOS"
                                                                 outputVariable="InvokeUpdateCustomerPartySynchronously_UpdateCustomerPartySynchronously_OutputVariable_FlowHasTwoOS"
                                                                 xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                                                                 xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"
                                                                 bpelx:invokeAsDetail="no"/>
                                                         <assign name="AssignQueryRelationship">
                                                            <copy ignoreMissingFromData="yes">
                                                               <from>($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SKYAccountNumber)</from>
                                                               <to>$QueryRelationship_InputVariable.parameters/ns39:childClientId</to>
                                                            </copy>
                                                         </assign>
                                                         <invoke name="InvokeQueryRelationship"
                                                                 bpelx:invokeAsDetail="no"
                                                                 partnerLink="CommunicationsAccountRelationshipEBS"
                                                                 portType="ns38:CommunicationsAccountRelationshipEBSPort"
                                                                 operation="QueryRelationship"
                                                                 inputVariable="QueryRelationship_InputVariable"
                                                                 outputVariable="QueryRelationship_OutputVariable"/>
                                                         <assign name="AssignQueryCustomerParty">
                                                            <copy ignoreMissingFromData="yes">
                                                               <from>$QueryRelationship_OutputVariable.parameters/ns39:ParentChildList[1]/ns39:parentClientId</from>
                                                               <to>$QueryCustomerParty_InputVariable_A1.QueryCustomerPartyEBM/custparty:DataArea/custparty:QueryCustomerParty/corecom:Identification/corecom:ID</to>
                                                            </copy>
                                                         </assign>
                                                         <invoke name="QueryCustomerParty"
                                                                 partnerLink="CustomerPartyEBS"
                                                                 portType="ns9:CommunicationsCustomerPartyEBS"
                                                                 operation="QueryCustomerParty"
                                                                 inputVariable="QueryCustomerParty_InputVariable_A1"
                                                                 outputVariable="QueryCustomerParty_OutputVariable_A1"
                                                                 bpelx:invokeAsDetail="no"
                                                                 xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                                                                 xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/>
                                                         <assign name="AssignUpdateCustomerParty">
                                                            <copy ignoreMissingFromData="yes">
                                                               <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/corecom:EBMHeader/corecom:Custom/ns15:InteroperabilityHeader/ns15:consumerSystem</from>
                                                               <to>$UpdateCustomerPartySynchronously_InputVariable_FlowOs.UpdateCustomerPartySynchronouslyEBM/corecom:EBMHeader/corecom:Custom/ns15:InteroperabilityHeader/ns15:consumerSystem</to>
                                                            </copy>
                                                            <copy ignoreMissingFromData="yes">
                                                               <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/corecom:EBMHeader/corecom:Custom/ns15:InteroperabilityHeader/ns15:userId</from>
                                                               <to>$UpdateCustomerPartySynchronously_InputVariable_FlowOs.UpdateCustomerPartySynchronouslyEBM/corecom:EBMHeader/corecom:Custom/ns15:InteroperabilityHeader/ns15:userId</to>
                                                            </copy>
                                                            <copy ignoreMissingFromData="yes">
                                                               <from>$QueryCustomerParty_OutputVariable_A1.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/corecom:Identification/corecom:ID</from>
                                                               <to>$UpdateCustomerPartySynchronously_InputVariable_FlowOs.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/corecom:Identification/corecom:ID</to>
                                                            </copy>
                                                            <copy ignoreMissingFromData="yes">
                                                               <from>$QueryCustomerParty_OutputVariable_A1.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/corecom:Identification/corecom:ID</from>
                                                               <to>$UpdateCustomerPartySynchronously_InputVariable_FlowOs.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/custparty:CustomerPartyAccount/corecom:Identification/corecom:ID</to>
                                                            </copy>
                                                            <copy ignoreMissingFromData="yes">
                                                               <from>$QueryCustomerParty_OutputVariable_A1.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/corecom:BillingProfileIdentification/corecom:ID</from>
                                                               <to>$UpdateCustomerPartySynchronously_InputVariable_FlowOs.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/custparty:CustomerPartyAccount/corecom:BillingProfileIdentification/corecom:ID</to>
                                                            </copy>
                                                            <copy ignoreMissingFromData="yes">
                                                               <from>$QueryCustomerParty_OutputVariable_CurrentAccount.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:DueDate</from>
                                                               <to>$UpdateCustomerPartySynchronously_InputVariable_FlowOs.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:DueDate</to>
                                                            </copy>
                                                         </assign>
                                                         <invoke name="InvokeUpdateCustomerPartySynchronously"
                                                                 partnerLink="CustomerPartyEBS"
                                                                 portType="ns9:CommunicationsCustomerPartyEBS"
                                                                 operation="UpdateCustomerPartySynchronously"
                                                                 inputVariable="UpdateCustomerPartySynchronously_InputVariable_FlowOs"
                                                                 outputVariable="UpdateCustomerPartySynchronously_OutputVariable_FlowOs"
                                                                 xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                                                                 xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"
                                                                 bpelx:invokeAsDetail="no"/>
                                                      </sequence>
                                                      <elseif>
                                                         <documentation>
                                                            <![CDATA[Executed]]>
                                                         </documentation>
                                                         <condition>($QueryWorkOrderListFor.QueryWorkOrderListResponseEBM/ns49:DataArea/ns49:QueryWorkOrderListResponse/corecom:Identification/corecom:ID != $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine/ford:Custom/corecomcust:WorkOrderReference/corecom:WorkOrderLineReference/corecom:WorkOrderLineIdentification/corecom:ID) and ($QueryWorkOrderListFor.QueryWorkOrderListResponseEBM/ns49:DataArea/ns49:QueryWorkOrderListResponse/corecom:Status[corecom:Code = "Executada" or corecom:Code = "Finalizada"])</condition>
                                                         <sequence name="Sequence75">
                                                          <assign name="Transformation_QueryWorkOrderListFor">
                                                          <bpelx:annotation><bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern></bpelx:annotation>
                                                               <copy>
                                                                  <from>ora:doXSLTransformForDoc("xsl/TransformationQueryWorkOrderListFor_To_QueryWorkOrderList.xsl", $QueryWorkOrderListFor.QueryWorkOrderListResponseEBM)</from>
                                                                  <to variable="QueryWorkOrderList_InputVariable_QueryOS"
                                                                      part="QueryWorkOrderListEBM"/>
                                                               </copy>
                                                            </assign><invoke name="InvokeQueryWorkOrderList"
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           partnerLink="CommunicationsWorkOrderEBS"
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           portType="ns48:CommunicationsWorkOrderEBS"
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           operation="QueryWorkOrderList"
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           inputVariable="QueryWorkOrderList_InputVariable_QueryOS"
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           outputVariable="QueryWorkOrderList_OutputVariable_QueryOS"
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           bpelx:invokeAsDetail="no"
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/>
                                                            <assign name="AssignQueryCustomerParty">
                                                               <copy ignoreMissingFromData="yes">
                                                                  <from>$QueryWorkOrderList_OutputVariable_QueryOS.QueryWorkOrderListResponseEBM/ns49:DataArea/ns49:QueryWorkOrderListResponse/corecom:CustomerPartyReference/corecom:PartyIdentification/corecom:ID</from>
                                                                  <to>$QueryCustomerParty_InputVariable_HasOS.QueryCustomerPartyEBM/custparty:DataArea/custparty:QueryCustomerParty/corecom:Identification/corecom:ID</to>
                                                               </copy>
                                                            </assign><invoke name="InvokeQueryCustomerParty"
                                                                                                                     bpelx:invokeAsDetail="no"
                                                                                                                     partnerLink="CustomerPartyEBS_SOA"
                                                                                                                     portType="ns9:CommunicationsCustomerPartyEBS"
                                                                                                                     operation="QueryCustomerParty"
                                                                                                                     inputVariable="QueryCustomerParty_InputVariable_HasOS"
                                                                                                                     outputVariable="QueryCustomerParty_OutputVariable_HasOS"
                                                                                                                     xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                                                                                                                     xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/>
<assign name="AssignGetDueDateValue"                                                                                                                                                                                              xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <copy ignoreMissingFromData="yes">
         <from>$QueryCustomerParty_OutputVariable_CurrentAccount.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:DueDate</from>
         <to>$getDueDateValue</to>
      </copy>
   </assign>
<assign name="AssignUpdateCustomerParty" xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <copy ignoreMissingFromData="yes">
         <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/corecom:EBMHeader/corecom:Custom/ns15:InteroperabilityHeader/ns15:consumerSystem</from>
         <to>$InvokeUpdateCustomerPartySynchronously_UpdateCustomerPartySynchronously_InputVariable_FlowHasTwoOS.UpdateCustomerPartySynchronouslyEBM/corecom:EBMHeader/corecom:Custom/ns15:InteroperabilityHeader/ns15:consumerSystem</to>
      </copy>
      <copy ignoreMissingFromData="yes">
         <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/corecom:EBMHeader/corecom:Custom/ns15:InteroperabilityHeader/ns15:userId</from>
         <to>$InvokeUpdateCustomerPartySynchronously_UpdateCustomerPartySynchronously_InputVariable_FlowHasTwoOS.UpdateCustomerPartySynchronouslyEBM/corecom:EBMHeader/corecom:Custom/ns15:InteroperabilityHeader/ns15:userId</to>
      </copy>
      <copy ignoreMissingFromData="yes">
         <from>$QueryCustomerParty_OutputVariable_HasOS.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/corecom:Identification/corecom:ID</from>
         <to>$InvokeUpdateCustomerPartySynchronously_UpdateCustomerPartySynchronously_InputVariable_FlowHasTwoOS.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/corecom:Identification/corecom:ID</to>
      </copy>
      <copy ignoreMissingFromData="yes">
         <from>$QueryCustomerParty_OutputVariable_HasOS.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/corecom:Identification/corecom:ID</from>
         <to>$InvokeUpdateCustomerPartySynchronously_UpdateCustomerPartySynchronously_InputVariable_FlowHasTwoOS.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/custparty:CustomerPartyAccount/corecom:Identification/corecom:ID</to>
      </copy>
      <copy ignoreMissingFromData="yes">
         <from>$QueryCustomerParty_OutputVariable_HasOS.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/corecom:BillingProfileIdentification/corecom:ID</from>
         <to>$InvokeUpdateCustomerPartySynchronously_UpdateCustomerPartySynchronously_InputVariable_FlowHasTwoOS.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/custparty:CustomerPartyAccount/corecom:BillingProfileIdentification/corecom:ID</to>
      </copy>
      <copy ignoreMissingFromData="yes">
         <from>$getDueDateValue</from>
         <to>$InvokeUpdateCustomerPartySynchronously_UpdateCustomerPartySynchronously_InputVariable_FlowHasTwoOS.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:DueDate</to>
      </copy>
      <copy ignoreMissingFromData="yes">
         <from>'true'</from>
         <to>$InvokeUpdateCustomerPartySynchronously_UpdateCustomerPartySynchronously_InputVariable_FlowHasTwoOS.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:NotEnterCollectionRuleIndicator</to>
      </copy>
   </assign><invoke name="InvokeUpdateCustomerPartySynchronously"
                                                                                                    partnerLink="CustomerPartyEBS"
                                                                                                    portType="ns9:CommunicationsCustomerPartyEBS"
                                                                                                    operation="UpdateCustomerPartySynchronously"
                                                                                                    inputVariable="InvokeUpdateCustomerPartySynchronously_UpdateCustomerPartySynchronously_InputVariable_FlowHasTwoOS"
                                                                                                    outputVariable="InvokeUpdateCustomerPartySynchronously_UpdateCustomerPartySynchronously_OutputVariable_FlowHasTwoOS"
                                                                                                    xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                                                                                                    xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"
                                                                                                    bpelx:invokeAsDetail="no"/><assign name="AssignQueryRelationship"
                                                                                              xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <copy ignoreMissingFromData="yes">
         <from>($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SKYAccountNumber)</from>
         <to>$QueryRelationship_InputVariable.parameters/ns39:childClientId</to>
      </copy>
   </assign><invoke name="InvokeQueryRelationship" bpelx:invokeAsDetail="no"
                    partnerLink="CommunicationsAccountRelationshipEBS"
                    portType="ns38:CommunicationsAccountRelationshipEBSPort" operation="QueryRelationship"
                    inputVariable="QueryRelationship_InputVariable" outputVariable="QueryRelationship_OutputVariable"
                    xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                    xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/><assign name="AssignQueryCustomerParty"
                                                                                              xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <copy ignoreMissingFromData="yes">
         <from>$QueryRelationship_OutputVariable.parameters/ns39:ParentChildList[1]/ns39:parentClientId</from>
         <to>$QueryCustomerParty_InputVariable_A1.QueryCustomerPartyEBM/custparty:DataArea/custparty:QueryCustomerParty/corecom:Identification/corecom:ID</to>
      </copy>
   </assign><invoke name="QueryCustomerParty" partnerLink="CustomerPartyEBS"
                    portType="ns9:CommunicationsCustomerPartyEBS" operation="QueryCustomerParty"
                    inputVariable="QueryCustomerParty_InputVariable_A1"
                    outputVariable="QueryCustomerParty_OutputVariable_A1" bpelx:invokeAsDetail="no"
                    xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                    xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/><assign name="AssignUpdateCustomerParty"
                                                                                              xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
                                                               <copy ignoreMissingFromData="yes">
                                                                  <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/corecom:EBMHeader/corecom:Custom/ns15:InteroperabilityHeader/ns15:consumerSystem</from>
                                                                  <to>$UpdateCustomerPartySynchronously_InputVariable_FlowOs.UpdateCustomerPartySynchronouslyEBM/corecom:EBMHeader/corecom:Custom/ns15:InteroperabilityHeader/ns15:consumerSystem</to>
                                                               </copy>
                                                               <copy ignoreMissingFromData="yes">
                                                                  <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/corecom:EBMHeader/corecom:Custom/ns15:InteroperabilityHeader/ns15:userId</from>
                                                                  <to>$UpdateCustomerPartySynchronously_InputVariable_FlowOs.UpdateCustomerPartySynchronouslyEBM/corecom:EBMHeader/corecom:Custom/ns15:InteroperabilityHeader/ns15:userId</to>
                                                               </copy>
                                                               <copy ignoreMissingFromData="yes">
                                                                  <from>$QueryCustomerParty_OutputVariable_A1.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/corecom:Identification/corecom:ID</from>
                                                                  <to>$UpdateCustomerPartySynchronously_InputVariable_FlowOs.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/corecom:Identification/corecom:ID</to>
                                                               </copy>
                                                               <copy ignoreMissingFromData="yes">
                                                                  <from>$QueryCustomerParty_OutputVariable_A1.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/corecom:Identification/corecom:ID</from>
                                                                  <to>$UpdateCustomerPartySynchronously_InputVariable_FlowOs.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/custparty:CustomerPartyAccount/corecom:Identification/corecom:ID</to>
                                                               </copy>
                                                               <copy ignoreMissingFromData="yes">
                                                                  <from>$QueryCustomerParty_OutputVariable_A1.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/corecom:BillingProfileIdentification/corecom:ID</from>
                                                                  <to>$UpdateCustomerPartySynchronously_InputVariable_FlowOs.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/custparty:CustomerPartyAccount/corecom:BillingProfileIdentification/corecom:ID</to>
                                                               </copy>
                                                               <copy ignoreMissingFromData="yes">
                                                                  <from>$QueryCustomerParty_OutputVariable_CurrentAccount.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:DueDate</from>
                                                                  <to>$UpdateCustomerPartySynchronously_InputVariable_FlowOs.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:DueDate</to>
                                                               </copy>
                                                            </assign><invoke name="InvokeUpdateCustomerPartySynchronously" partnerLink="CustomerPartyEBS"
                    portType="ns9:CommunicationsCustomerPartyEBS" operation="UpdateCustomerPartySynchronously"
                    inputVariable="UpdateCustomerPartySynchronously_InputVariable_FlowOs"
                    outputVariable="UpdateCustomerPartySynchronously_OutputVariable_FlowOs"
                    xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                    xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable" bpelx:invokeAsDetail="no"/></sequence></elseif>
                                                   </if>
                                                </sequence>
                                             </scope>
                                          </forEach></sequence>
                                       <else>
                                          <sequence>
                                             <assign name="AssignCdMainChild">
                                                <copy>
                                                   <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SKYAccountNumber</from>
                                                   <to>$RELACIONAMENTO_PAI_FILHO_Select_InputVariable.RELACIONAMENTO_PAI_FILHOSelect_inputParameters/ns37:cd_Cliente_Filho</to>
                                                </copy>
                                             </assign>
                                             <invoke name="Invoke_RELACIONAMENTO_PAI_FILHO" bpelx:invokeAsDetail="no"
                                                     partnerLink="RELACIONAMENTO_PAI_FILHO"
                                                     portType="ns36:RELACIONAMENTO_PAI_FILHO_ptt"
                                                     operation="RELACIONAMENTO_PAI_FILHOSelect"
                                                     inputVariable="RELACIONAMENTO_PAI_FILHO_Select_InputVariable"
                                                     outputVariable="RELACIONAMENTO_PAI_FILHO_Select_OutputVariable"/>
                                             <forEach parallel="no" counterName="ForEach2Counter" name="ForEach2">
                                                <startCounterValue>1</startCounterValue>
                                                <finalCounterValue>count($RELACIONAMENTO_PAI_FILHO_Select_OutputVariable.RelacionamentoPaiFilhoCollection/ns37:RelacionamentoPaiFilho/ns37:cdClienteFilho)</finalCounterValue>
                                                <scope name="Scope25">
                                                   <variables>
                                                      <variable name="RelacionamentoPaiFilhoCollectionFor"
                                                                messageType="ns36:RelacionamentoPaiFilhoCollection_msg"/>
                                                   </variables>
                                                   <sequence>
                                                      <assign name="AssignChildAccounts">
                                                         <copy ignoreMissingFromData="yes">
                                                            <from>$RELACIONAMENTO_PAI_FILHO_Select_OutputVariable.RelacionamentoPaiFilhoCollection/ns37:RelacionamentoPaiFilho[$ForEach2Counter]</from>
                                                            <to>$RelacionamentoPaiFilhoCollectionFor.RelacionamentoPaiFilhoCollection/ns37:RelacionamentoPaiFilho</to>
                                                         </copy>
                                                      </assign>
                                                      <if name="IfChildClientCodeIsDifferent">
                                                         <condition>($RelacionamentoPaiFilhoCollectionFor.RelacionamentoPaiFilhoCollection/ns37:RelacionamentoPaiFilho/ns37:cdClienteFilho != $Invoke_QueryCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/corecom:Identification/corecom:ID) and ($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/corecom:WorkerReference/corecom:WorkerIdentification/corecom:ID != "MIGRADOR")</condition>
                                                         <sequence name="Sequence67">
                                                            <assign name="TransformationReqRelacionamentoPaiFilhoToChild">
                                                               <bpelx:annotation>
                                                                  <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                               </bpelx:annotation>
                                                               <copy>
                                                                  <from>ora:doXSLTransformForDoc("xsl/TransformationReqRelacionamentoPaiFilhoToChild.xsl", $RelacionamentoPaiFilhoCollectionFor.RelacionamentoPaiFilhoCollection)</from>
                                                                  <to variable="QueryCustomerParty_InputVariable_A1"
                                                                      part="QueryCustomerPartyEBM"/>
                                                               </copy>
                                                            </assign>
                                                            <invoke name="QueryCustomerParty"
                                                                    partnerLink="CustomerPartyEBS"
                                                                    portType="ns9:CommunicationsCustomerPartyEBS"
                                                                    operation="QueryCustomerParty"
                                                                    inputVariable="QueryCustomerParty_InputVariable_A1"
                                                                    outputVariable="QueryCustomerParty_OutputVariable_A1"
                                                                    bpelx:invokeAsDetail="no"
                                                                    xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                                                                    xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/>
                                                            <assign name="AssignReqUpdateCustomerPartySynchronouslyToChild">
                                                               <copy ignoreMissingFromData="yes">
                                                                  <from>' '</from>
                                                                  <to>$InvokeUpdateCustomerPartySynchronouslyChild_InputVariable.UpdateCustomerPartySynchronouslyEBM/corecom:EBMHeader/corecom:Custom/ns15:InteroperabilityHeader/ns15:consumerSystem</to>
                                                               </copy>
                                                               <copy ignoreMissingFromData="yes">
                                                                  <from>' '</from>
                                                                  <to>$InvokeUpdateCustomerPartySynchronouslyChild_InputVariable.UpdateCustomerPartySynchronouslyEBM/corecom:EBMHeader/corecom:Custom/ns15:InteroperabilityHeader/ns15:userId</to>
                                                               </copy>
                                                               <copy ignoreMissingFromData="yes">
                                                                  <from>$RELACIONAMENTO_PAI_FILHO_Select_OutputVariable.RelacionamentoPaiFilhoCollection/ns37:RelacionamentoPaiFilho[$ForEach2Counter]/ns37:cdClienteFilho</from>
                                                                  <to>$InvokeUpdateCustomerPartySynchronouslyChild_InputVariable.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/custparty:CustomerPartyAccount/corecom:Identification/corecom:ID</to>
                                                               </copy>
                                                               <copy ignoreMissingFromData="yes">
                                                                  <from>$QueryCustomerParty_OutputVariable_A1.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/corecom:BillingProfileIdentification/corecom:ID</from>
                                                                  <to>$InvokeUpdateCustomerPartySynchronouslyChild_InputVariable.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/custparty:CustomerPartyAccount/corecom:BillingProfileIdentification/corecom:ID</to>
                                                               </copy>
                                                               <copy ignoreMissingFromData="yes">
                                                                  <from>xp20:day-from-dateTime(xp20:current-dateTime ( ))</from>
                                                                  <to>$InvokeUpdateCustomerPartySynchronouslyChild_InputVariable.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:DueDate</to>
                                                               </copy>
                                                               <copy ignoreMissingFromData="yes">
                                                                  <from>'true'</from>
                                                                  <to>$InvokeUpdateCustomerPartySynchronouslyChild_InputVariable.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:NotEnterCollectionRuleIndicator</to>
                                                               </copy>
                                                            </assign>
                                                            <invoke name="InvokeUpdateCustomerPartySynchronouslyChild"
                                                                    partnerLink="CustomerPartyEBS"
                                                                    portType="ns9:CommunicationsCustomerPartyEBS"
                                                                    operation="UpdateCustomerPartySynchronously"
                                                                    inputVariable="InvokeUpdateCustomerPartySynchronouslyChild_InputVariable"
                                                                    outputVariable="InvokeUpdateCustomerPartySynchronouslyChild_OutputVariable"
                                                                    bpelx:invokeAsDetail="no"/>
                                                            <assign name="TransformationReqRelacionamentoPaiFilhoToParent">
                                                               <bpelx:annotation>
                                                                  <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                               </bpelx:annotation>
                                                               <copy>
                                                                  <from>ora:doXSLTransformForDoc("xsl/TransformationReqRelacionamentoPaiFilhoToParent.xsl", $RELACIONAMENTO_PAI_FILHO_Select_OutputVariable.RelacionamentoPaiFilhoCollection)</from>
                                                                  <to variable="QueryCustomerParty_InputVariable_A1"
                                                                      part="QueryCustomerPartyEBM"/>
                                                               </copy>
                                                            </assign>
                                                            <invoke name="QueryCustomerParty"
                                                                    partnerLink="CustomerPartyEBS"
                                                                    portType="ns9:CommunicationsCustomerPartyEBS"
                                                                    operation="QueryCustomerParty"
                                                                    inputVariable="QueryCustomerParty_InputVariable_A1"
                                                                    outputVariable="QueryCustomerParty_OutputVariable_A1"
                                                                    bpelx:invokeAsDetail="no"/>
                                                            <assign name="TransformationReqQueryCustomerParty_To_UpdateCustomerPartySynchronously">
                                                               <bpelx:annotation>
                                                                  <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                               </bpelx:annotation>
                                                               <copy>
                                                                  <from>ora:doXSLTransformForDoc("xsl/TransformationReqQueryCustomerParty_To_UpdateCustomerPartySynchronously.xsl", $RELACIONAMENTO_PAI_FILHO_Select_OutputVariable.RelacionamentoPaiFilhoCollection, "QueryCustomerParty_OutputVariable_A1.QueryCustomerPartyResponseEBM", $QueryCustomerParty_OutputVariable_A1.QueryCustomerPartyResponseEBM, "Invoke_QueryCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM", $Invoke_QueryCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM)</from>
                                                                  <to variable="UpdateCustomerParty_UpdateCustomerPartySynchronously_InputVariable"
                                                                      part="UpdateCustomerPartySynchronouslyEBM"/>
                                                               </copy>
                                                            </assign>
                                                            <assign name="BillingProfileIdentification">
                                                               <copy ignoreMissingFromData="yes">
                                                                  <from>$QueryCustomerParty_OutputVariable_A1.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/corecom:BillingProfileIdentification/corecom:ID</from>
                                                                  <to>$UpdateCustomerParty_UpdateCustomerPartySynchronously_InputVariable.UpdateCustomerPartySynchronouslyEBM/custparty:DataArea/custparty:UpdateCustomerPartySynchronously/custparty:CustomerPartyAccount/corecom:BillingProfileIdentification/corecom:ID</to>
                                                               </copy>
                                                            </assign>
                                                            <invoke name="InvokeUpdateCustomerPartySynchronously"
                                                                    bpelx:invokeAsDetail="no"
                                                                    partnerLink="CustomerPartyEBS"
                                                                    portType="ns9:CommunicationsCustomerPartyEBS"
                                                                    operation="UpdateCustomerPartySynchronously"
                                                                    inputVariable="UpdateCustomerParty_UpdateCustomerPartySynchronously_InputVariable"
                                                                    outputVariable="UpdateCustomerParty_UpdateCustomerPartySynchronously_OutputVariable"/>                                                       
      <if name="IfIsFiberChild" xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <condition>($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name = 'Tecnologia' and corecom:Value = 'FIBRA'])</condition>
      <sequence>
         <assign name="Transformation_InputParameters_To_QueryRelationship">
            <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
               <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
            </bpelx:annotation>
            <copy>
               <from>ora:doXSLTransformForDoc("xsl/Transformation_InputParameters_To_QueryRelationship.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
               <to variable="QueryRelationship_InputVariable_ActivationChild" part="parameters"/>
            </copy>
         </assign>
         <invoke name="InvokeQueryRelationship"
                 partnerLink="CommunicationsAccountRelationshipEBS"
                 portType="ns38:CommunicationsAccountRelationshipEBSPort" operation="QueryRelationship"
                 inputVariable="QueryRelationship_InputVariable_ActivationChild"
                 outputVariable="QueryRelationship_OutputVariable_ActivationChild"
                 xmlns:bpelx="http://schemas.oracle.com/bpel/extension" bpelx:invokeAsDetail="no"/>
         <forEach parallel="no" counterName="ForEachChildsActivationCounter" name="ForEachChildsActivation">
            <startCounterValue>1</startCounterValue>
            <finalCounterValue>count($QueryRelationship_OutputVariable_ActivationChild.parameters/ns39:ParentChildList)</finalCounterValue>
            <scope name="ScopeHabilitarSKYMais">
               <variables>
                  <variable name="QueryRelationshipFor" messageType="ns38:QueryRelationshipResponseMsg"/>
               </variables>
               <sequence name="Sequence87">
                  <assign name="AssignChildActivation">
                     <copy ignoreMissingFromData="yes">
                        <from>$QueryRelationship_OutputVariable_ActivationChild.parameters/ns39:ParentChildList[$ForEachChildsActivationCounter]</from>
                        <to>$QueryRelationshipFor.parameters/ns39:ParentChildList</to>
                     </copy>
                  </assign>
                  <if name="IfIsSKYMaisChild">
                     <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SKYAccountNumber != $QueryRelationshipFor.parameters/ns39:ParentChildList/ns39:childClientId</condition>
                     <sequence>
                        <assign name="Transformation_QueryCustomerParty_To_QueryFulfillmentOrderList">
                           <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
                              <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                           </bpelx:annotation>
                           <copy>
                              <from>ora:doXSLTransformForDoc("xsl/Transformation_QueryRelationship_To_QueryFulfillmentOrderList.xsl", $QueryRelationshipFor.parameters)</from>
                              <to variable="QueryFulfillmentOrderList_InputVariable_DgoChild"
                                  part="QueryFulfillmentOrderListEBM"/>
                           </copy>
                        </assign>
                        <invoke name="InvokeQueryFulfillmentOrderList"
                                partnerLink="CommunicationsFulfillmentOrder"
                                portType="ns20:CommunicationsFulfillmentOrderEBS" operation="QueryFulfillmentOrderList"
                                inputVariable="QueryFulfillmentOrderList_InputVariable_DgoChild"
                                outputVariable="QueryFulfillmentOrderList_OutputVariable_DgoChild"
                                xmlns:bpelx="http://schemas.oracle.com/bpel/extension" bpelx:invokeAsDetail="no"/>
                        <sequence name="Sequence83">
                           <forEach parallel="no" counterName="ForEachOrdersCounter" name="ForEachOrdes">
                              <startCounterValue>1</startCounterValue>
                              <finalCounterValue>count($QueryFulfillmentOrderList_OutputVariable_DgoChild.QueryFulfillmentOrderListResponseEBM/ford:DataArea)</finalCounterValue>
                              <scope name="Scope27">
                                 <variables>
                                    <variable name="QueryFulfillmentOrderListFor"
                                              messageType="ns20:QueryFulfillmentOrderListRespMsg"/>
                                 </variables>
                                 <sequence name="Sequence84">
                                    <assign name="AssignOrders">
                                       <copy ignoreMissingFromData="yes">
                                          <from>$QueryFulfillmentOrderList_OutputVariable_DgoChild.QueryFulfillmentOrderListResponseEBM/ford:DataArea[$ForEachOrdersCounter]</from>
                                          <to>$QueryFulfillmentOrderListFor.QueryFulfillmentOrderListResponseEBM/ford:DataArea</to>
                                       </copy>
                                    </assign>
                                    <if name="IfSubTypeCodeIsAwaitingFiberActivation">
                                       <condition>($QueryFulfillmentOrderListFor.QueryFulfillmentOrderListResponseEBM/ford:DataArea/ford:QueryFulfillmentOrderListResponse/corecom:Status[corecom:Code = 'Awaiting Fiber Activation'])</condition>
                                       <sequence name="Sequence85">
                                          <assign name="Transformation_QueryFulfillmentOrder_To_UpdateFulfillmentOrderSynchronously">
                                             <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
                                                <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                             </bpelx:annotation>
                                             <copy>
                                                <from>ora:doXSLTransformForDoc("xsl/Transformation_QueryFulfillmentOrder_To_UpdateFulfillmentOrderSynchronously.xsl", $QueryFulfillmentOrderListFor.QueryFulfillmentOrderListResponseEBM)</from>
                                                <to variable="UpdateFulfillmentOrderSynchronously_InputVariable_DgoChild"
                                                    part="UpdateFulfillmentOrderSynchronouslyEBM"/>
                                             </copy>
                                          </assign>
                                          <invoke name="InvokeUpdateFulfillmentOrderSynchronously" partnerLink="CommunicationsFulfillmentOrder"
                                                  portType="ns20:CommunicationsFulfillmentOrderEBS"
                                                  operation="UpdateFulfillmentOrderSynchronously"
                                                  inputVariable="UpdateFulfillmentOrderSynchronously_InputVariable_DgoChild"
                                                  outputVariable="UpdateFulfillmentOrderSynchronously_OutputVariable_DgoChild"
                                                  xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                                                  bpelx:invokeAsDetail="no"/>
                                       </sequence>
                                       <else>
                                          <empty name="Do_Nothing"/>
                                       </else>
                                    </if>
                                 </sequence>
                              </scope>
                           </forEach>
                        </sequence>
                     </sequence>
                  </if>
               </sequence>
            </scope>
         </forEach>
      </sequence>
      <else>
         <empty name="Do_Nothing"/>
      </else>
   </if>
   </sequence>
                                                      </if>
                                                   </sequence>
                                                </scope>
                                             </forEach>
                                          </sequence>
                                       </else>
                                    </if>
                                 </sequence>
                                 <elseif>
                                    <documentation>
                                       <![CDATA[It's Installation Address Change and Dad or Child DGO]]>
                                    </documentation>
                                    <condition>($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Installation Address Change" and ($Invoke_QueryCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:Keywords[custpartycust:KeywordType = 'Pacote Combo' and custpartycust:KeywordValue = "PAI"] or $Invoke_QueryCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom[custpartycust:OrganizationType = "Directv Go"]/custpartycust:Keywords[custpartycust:KeywordType = 'Pacote Combo' and custpartycust:KeywordValue = "FILHA"]))</condition>
                                    <sequence name="Sequence82">
                                       <assign name="InputParameters_To_QueryLocationList">
                                          <bpelx:annotation>
                                             <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                          </bpelx:annotation>
                                          <copy>
                                             <from>ora:doXSLTransformForDoc("xsl/InputParameters_To_QueryLocationList.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                             <to variable="QueryLocationList_InputVariable"
                                                 part="QueryLocationListEBM"/>
                                          </copy>
                                       </assign>
                                       <invoke name="InvokeQueryLocationList" bpelx:invokeAsDetail="no"
                                               partnerLink="CommunicationsLocationEBSV1"
                                               portType="ns61:CommunicationsLocationEBS" operation="QueryLocationList"
                                               inputVariable="QueryLocationList_InputVariable"
                                               outputVariable="QueryLocationList_OutputVariable"/>
                                       <if name="IfIsWithSucess">
                                          <condition>$QueryLocationList_OutputVariable.QueryLocationListResponseEBM/corecom:EBMHeader/corecom:Custom/ns15:ResponseHeader/ns15:returnCode = 0</condition>
                                          <sequence>
                                             <assign name="InputParameters_To_UpdateLocationSynchronously">
                                                <bpelx:annotation>
                                                   <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                </bpelx:annotation>
                                                <copy>
                                                   <from>ora:doXSLTransformForDoc("xsl/InputParameters_To_UpdateLocationSynchronously.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM, "QueryLocationList_OutputVariable.QueryLocationListResponseEBM", $QueryLocationList_OutputVariable.QueryLocationListResponseEBM)</from>
                                                   <to variable="UpdateLocationSynchronously_InputVariable"
                                                       part="UpdateLocationSynchronouslyEBM"/>
                                                </copy>
                                             </assign>
                                             <invoke name="InvokeUpdateLocationSynchronously"
                                                     partnerLink="CommunicationsLocationEBSV1"
                                                     portType="ns61:CommunicationsLocationEBS"
                                                     operation="UpdateLocationSynchronously"
                                                     inputVariable="UpdateLocationSynchronously_InputVariable"
                                                     outputVariable="UpdateLocationSynchronously_OutputVariable"
                                                     bpelx:invokeAsDetail="no"/>
                                          </sequence>
                                          <else>
                                             <empty name="Do_Nothing"/>
                                          </else>
                                       </if>
                                    </sequence>
                                 </elseif>
                                 <elseif>
                                    <documentation>
                                       <![CDATA[Fiber child reactivation]]>
                                    </documentation>
                                    <condition>($Invoke_QueryCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:Keywords[custpartycust:KeywordType = 'Pacote Combo' and custpartycust:KeywordValue = 'FILHA']) and ($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Reactivation")</condition>
                                    <sequence name="Seq_Fiber_Child_Reactivation">
                                    <assign name="TransformationReqQueryWorkOrderList">
                                       <bpelx:annotation>
                                          <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                       </bpelx:annotation>
                                       <copy>
                                          <from>ora:doXSLTransformForDoc("xsl/TransformationReqQueryWorkOrderList.xsl", $Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM)</from>
                                          <to variable="QueryWorkOrderList_InputVariable" part="QueryWorkOrderListEBM"/>
                                       </copy>
                                    </assign>
                                    <invoke name="InvokeQueryWorkOrderList"
                                            partnerLink="CommunicationsWorkOrderEBS"
                                            portType="ns48:CommunicationsWorkOrderEBS" operation="QueryWorkOrderList"
                                            inputVariable="QueryWorkOrderList_InputVariable"
                                            outputVariable="QueryWorkOrderList_OutputVariable"
                                            bpelx:invokeAsDetail="no"/>
                                       <if name="If_has_one_work_order_or_less">
                                          <documentation>
                                             <![CDATA[Has one work order or less]]>
                                          </documentation>
                                          <condition>count($QueryWorkOrderList_OutputVariable.QueryWorkOrderListResponseEBM/ns49:DataArea) &lt;= 1</condition>
                                          <sequence name="Seq_Has_One_WorkOrderOrLess">
                                            <assign name="AssignCdMainChild">
                                                <copy>
                                                   <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SKYAccountNumber</from>
                                                   <to>$RELACIONAMENTO_PAI_FILHO_Select_InputVariable.RELACIONAMENTO_PAI_FILHOSelect_inputParameters/ns37:cd_Cliente_Filho</to>
                                                </copy>
                                             </assign>
                                             <invoke name="Invoke_RELACIONAMENTO_PAI_FILHO" bpelx:invokeAsDetail="no"
                                                     partnerLink="RELACIONAMENTO_PAI_FILHO"
                                                     portType="ns36:RELACIONAMENTO_PAI_FILHO_ptt"
                                                     operation="RELACIONAMENTO_PAI_FILHOSelect"
                                                     inputVariable="RELACIONAMENTO_PAI_FILHO_Select_InputVariable"
                                                     outputVariable="RELACIONAMENTO_PAI_FILHO_Select_OutputVariable"/>
                                             <forEach parallel="no" counterName="ForEach2Counter" name="ForEach2">
                                                <startCounterValue>1</startCounterValue>
                                                <finalCounterValue>count($RELACIONAMENTO_PAI_FILHO_Select_OutputVariable.RelacionamentoPaiFilhoCollection/ns37:RelacionamentoPaiFilho/ns37:cdClienteFilho)</finalCounterValue>
                                                <scope name="Scope28">
                                                  <variables>
                                                    <variable name="RelacionamentoPaiFilhoCollectionFor" messageType="ns36:RelacionamentoPaiFilhoCollection_msg"/>
                                                  </variables>
                                                   <sequence name="Sequence96">
                                                      <assign name="AssignChildAccounts">
                                                         <copy ignoreMissingFromData="yes">
                                                            <from>$RELACIONAMENTO_PAI_FILHO_Select_OutputVariable.RelacionamentoPaiFilhoCollection/ns37:RelacionamentoPaiFilho[$ForEach2Counter]</from>
                                                            <to>$RelacionamentoPaiFilhoCollectionFor.RelacionamentoPaiFilhoCollection/ns37:RelacionamentoPaiFilho</to>
                                                         </copy>
                                                      </assign>
                                                      <if name="IfChildClientCodeIsDifferent">
                                                         <condition>($RelacionamentoPaiFilhoCollectionFor.RelacionamentoPaiFilhoCollection/ns37:RelacionamentoPaiFilho/ns37:cdClienteFilho != $Invoke_QueryCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/corecom:Identification/corecom:ID) and ($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/corecom:WorkerReference/corecom:WorkerIdentification/corecom:ID != "MIGRADOR")</condition>
                                                         <if name="IfIsFiberChild">
                                                            <condition>($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine/corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name = 'Tecnologia' and corecom:Value = 'FIBRA'])</condition>
                                                            <sequence>
                                                              <assign name="Transformation_InputParameters_To_QueryRelationship">
                                                                <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
                                                                  <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                                </bpelx:annotation>
                                                                <copy>
                                                                  <from>ora:doXSLTransformForDoc("xsl/Transformation_InputParameters_To_QueryRelationship.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                                                  <to variable="QueryRelationship_InputVariable_ActivationChild" part="parameters"/>
                                                                </copy>
                                                              </assign>
                                                              <invoke name="InvokeQueryRelationship"
                                                                      partnerLink="CommunicationsAccountRelationshipEBS"
                                                                      portType="ns38:CommunicationsAccountRelationshipEBSPort" operation="QueryRelationship"
                                                                      inputVariable="QueryRelationship_InputVariable_ActivationChild"
                                                                      outputVariable="QueryRelationship_OutputVariable_ActivationChild"
                                                                      xmlns:bpelx="http://schemas.oracle.com/bpel/extension" bpelx:invokeAsDetail="no"/>
                                                               <forEach parallel="no" counterName="ForEachChildsActivationCounter" name="ForEachChildsActivation">
                                                               <startCounterValue>1</startCounterValue>
                                                               <finalCounterValue>count($QueryRelationship_OutputVariable_ActivationChild.parameters/ns39:ParentChildList)</finalCounterValue>
                                                                  <scope name="ScopeHabilitarSKYMais">
                                                                     <variables>
                                                                        <variable name="QueryRelationshipFor" messageType="ns38:QueryRelationshipResponseMsg"/>
                                                                     </variables>
                                                                     <sequence>
                                                                        <assign name="AssignChildActivation">
                                                                           <copy ignoreMissingFromData="yes">
                                                                              <from>$QueryRelationship_OutputVariable_ActivationChild.parameters/ns39:ParentChildList[$ForEachChildsActivationCounter]</from>
                                                                              <to>$QueryRelationshipFor.parameters/ns39:ParentChildList</to>
                                                                           </copy>
                                                                        </assign>
                                                                        <if name="IfIsSKYMaisChild">
                                                                           <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SKYAccountNumber != $QueryRelationshipFor.parameters/ns39:ParentChildList/ns39:childClientId</condition>
                                                                           <sequence name="Sequence83">
                                                                              <assign name="Transformation_QueryCustomerParty_To_QueryFulfillmentOrderList">
                                                                                 <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
                                                                                    <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                                                 </bpelx:annotation>
                                                                                 <copy>
                                                                                    <from>ora:doXSLTransformForDoc("xsl/Transformation_QueryRelationship_To_QueryFulfillmentOrderList.xsl", $QueryRelationshipFor.parameters)</from>
                                                                                    <to variable="QueryFulfillmentOrderList_InputVariable_DgoChild"
                                                                                        part="QueryFulfillmentOrderListEBM"/>
                                                                                 </copy>
                                                                              </assign>
                                                                              <invoke name="InvokeQueryFulfillmentOrderList"
                                                                                      partnerLink="CommunicationsFulfillmentOrder"
                                                                                      portType="ns20:CommunicationsFulfillmentOrderEBS" operation="QueryFulfillmentOrderList"
                                                                                      inputVariable="QueryFulfillmentOrderList_InputVariable_DgoChild"
                                                                                      outputVariable="QueryFulfillmentOrderList_OutputVariable_DgoChild"
                                                                                      xmlns:bpelx="http://schemas.oracle.com/bpel/extension" bpelx:invokeAsDetail="no"/>
                                                                              <forEach parallel="no" counterName="ForEachOrdersCounter" name="ForEachOrdes">
                                                                                 <startCounterValue>1</startCounterValue>
                                                                                 <finalCounterValue>count($QueryFulfillmentOrderList_OutputVariable_DgoChild.QueryFulfillmentOrderListResponseEBM/ford:DataArea)</finalCounterValue>
                                                                                 <scope name="Scope27">
                                                                                    <variables>
                                                                                       <variable name="QueryFulfillmentOrderListFor"
                                                                                                 messageType="ns20:QueryFulfillmentOrderListRespMsg"/>
                                                                                    </variables>
                                                                                    <sequence name="Sequence84">
                                                                                       <assign name="AssignOrders">
                                                                                          <copy ignoreMissingFromData="yes">
                                                                                             <from>$QueryFulfillmentOrderList_OutputVariable_DgoChild.QueryFulfillmentOrderListResponseEBM/ford:DataArea[$ForEachOrdersCounter]</from>
                                                                                             <to>$QueryFulfillmentOrderListFor.QueryFulfillmentOrderListResponseEBM/ford:DataArea</to>
                                                                                          </copy>
                                                                                       </assign>
                                                                                       <if name="IfSubTypeCodeIsAwaitingFiberActivation">
                                                                                          <condition>($QueryFulfillmentOrderListFor.QueryFulfillmentOrderListResponseEBM/ford:DataArea/ford:QueryFulfillmentOrderListResponse/corecom:Status[corecom:Code = 'Awaiting Fiber Activation'])</condition>
                                                                                          <sequence name="Sequence85">
                                                                                             <assign name="Transformation_QueryFulfillmentOrder_To_UpdateFulfillmentOrderSynchronously">
                                                                                                <bpelx:annotation xmlns:bpelx="http://schemas.oracle.com/bpel/extension">
                                                                                                   <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                                                                </bpelx:annotation>
                                                                                                <copy>
                                                                                                   <from>ora:doXSLTransformForDoc("xsl/Transformation_QueryFulfillmentOrder_To_UpdateFulfillmentOrderSynchronously.xsl", $QueryFulfillmentOrderListFor.QueryFulfillmentOrderListResponseEBM)</from>
                                                                                                   <to variable="UpdateFulfillmentOrderSynchronously_InputVariable_DgoChild"
                                                                                                       part="UpdateFulfillmentOrderSynchronouslyEBM"/>
                                                                                                </copy>
                                                                                             </assign>
                                                                                             <invoke name="InvokeUpdateFulfillmentOrderSynchronously" partnerLink="CommunicationsFulfillmentOrder"
                                                                                                     portType="ns20:CommunicationsFulfillmentOrderEBS"
                                                                                                     operation="UpdateFulfillmentOrderSynchronously"
                                                                                                     inputVariable="UpdateFulfillmentOrderSynchronously_InputVariable_DgoChild"
                                                                                                     outputVariable="UpdateFulfillmentOrderSynchronously_OutputVariable_DgoChild"
                                                                                                     xmlns:bpelx="http://schemas.oracle.com/bpel/extension"
                                                                                                     bpelx:invokeAsDetail="no"/>
                                                                                          </sequence>
                                                                                          <else>
                                                                                             <empty name="Do_Nothing"/>
                                                                                          </else>
                                                                                       </if>
                                                                                    </sequence>
                                                                                 </scope>
                                                                              </forEach>
                                                                           </sequence>
                                                                        </if>
                                                                     </sequence>
                                                                  </scope>
                                                               </forEach>
                                                            </sequence>
                                                         </if>
                                                      </if>
                                                   </sequence>
                                                </scope>
                                             </forEach>
                                          </sequence>
                                          <else>
                                             <documentation>
                                                <![CDATA[Do Nothing]]>
                                             </documentation>
                                             <sequence name="Sequence97">
                                                <empty name="Do_Nothing"/>
                                             </sequence>
                                          </else>
                                       </if>
                                    </sequence>
                                 </elseif>
                              </if>
                              <scope name="ScopeTransferenciadeSaldo">
                                 <if name="IfSubtype_Is_Account_Inclusion_And_Parent_Account">
                                    <condition>($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = 'Account Inclusion') and ($Invoke_QueryCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:Keywords[custpartycust:KeywordType = "Pacote Combo" and custpartycust:KeywordValue = "PAI"])</condition>
                                    <sequence name="Sequence83">
                                       <assign name="TransformationInputParameters_To_AccountRelationshipDTO">
                                          <bpelx:annotation>
                                             <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                          </bpelx:annotation>
                                          <copy>
                                             <from>ora:doXSLTransformForDoc("xsl/TransformationInputParameters_To_AccountRelationshipDTO.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                             <to variable="AccountRelationshipRequestDTO_InputVariable" part="request"/>
                                          </copy>
                                       </assign>
                                       <invoke name="InvokeAccountRelationshipAPI" bpelx:invokeAsDetail="no"
                                               partnerLink="AccountRelationshipAPI1"
                                               portType="ns70:AccountRelationshipAPI_ptt"
                                               operation="AccountRelationshipRequestDTO"
                                               inputVariable="AccountRelationshipRequestDTO_InputVariable"
                                               outputVariable="AccountRelationshipRequestDTO_OutputVariable"/>
                                       <if name="IfCodeIsError">
                                          <condition>$AccountRelationshipRequestDTO_OutputVariable.reply/ns72:message != ""</condition>
                                          <empty name="Continue"/>
                                          <else>
                                             <documentation>
                                                <![CDATA[Sucessful]]>
                                             </documentation>
                                             <sequence>
                                                <assign name="Transformation_InputParameters_To_UpdateFulfillmentOrderSynchronously">
                                                   <bpelx:annotation>
                                                      <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                   </bpelx:annotation>
                                                   <copy>
                                                      <from>ora:doXSLTransformForDoc("xsl/Transformation_InputParameters_To_UpdateFulfillmentOrderSynchronously.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM, "curFulfillmentOrderLine", $curFulfillmentOrderLine)</from>
                                                      <to variable="UpdateFulfillmentOrderSynchronously_InputVariable"
                                                          part="UpdateFulfillmentOrderSynchronouslyEBM"/>
                                                   </copy>
                                                </assign>
                                                <invoke name="InvokeCommunicationsFulfillmentOrder"
                                                        bpelx:invokeAsDetail="no"
                                                        partnerLink="CommunicationsFulfillmentOrder"
                                                        portType="ns20:CommunicationsFulfillmentOrderEBS"
                                                        operation="UpdateFulfillmentOrderSynchronously"
                                                        inputVariable="UpdateFulfillmentOrderSynchronously_InputVariable"
                                                        outputVariable="UpdateFulfillmentOrderSynchronously_OutputVariable"/>
                                                <forEach parallel="no" counterName="ForEachChildCounter"
                                                         name="ForEachChildType">
                                                   <startCounterValue>1</startCounterValue>
                                                   <finalCounterValue>count($AccountRelationshipRequestDTO_OutputVariable.reply/ns72:child)</finalCounterValue>
                                                   <scope name="Scope27">
                                                      <variables>
                                                         <variable name="AccountRelationshipResponseFor"
                                                                   element="ns72:AccountRelationshipResponseEBM"/>
                                                      </variables>
                                                      <sequence>
                                                         <assign name="AssignChildType">
                                                            <copy ignoreMissingFromData="yes">
                                                               <from>$AccountRelationshipRequestDTO_OutputVariable.reply/ns72:child[$ForEachChildCounter]</from>
                                                               <to>$AccountRelationshipResponseFor/ns72:child</to>
                                                            </copy>
                                                         </assign>
                                                         <assign name="Transformation_AccountRelationship_To_QueryCustomerParty.xsl">
                                                            <bpelx:annotation>
                                                               <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                            </bpelx:annotation>
                                                            <copy>
                                                               <from>ora:doXSLTransformForDoc("xsl/Transformation_AccountRelationship_To_QueryCustomerParty.xsl", $AccountRelationshipResponseFor)</from>
                                                               <to variable="QueryCustomerParty_InputVariable_MainChild"
                                                                   part="QueryCustomerPartyEBM"/>
                                                            </copy>
                                                         </assign> 
                                                         <invoke name="InvokeQueryCustomerParty"
                                                                 bpelx:invokeAsDetail="no"
                                                                 partnerLink="CustomerPartyEBS"
                                                                 portType="ns9:CommunicationsCustomerPartyEBS"
                                                                 operation="QueryCustomerParty"
                                                                 inputVariable="QueryCustomerParty_InputVariable_MainChild"
                                                                 outputVariable="QueryCustomerParty_OutputVariable_MainChild"/>
                                                         <if name="IfKeywordMainChild">
                                                            <condition>($QueryCustomerParty_OutputVariable_MainChild.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:Keywords[custpartycust:KeywordType = 'Pacote Combo' and custpartycust:KeywordValue = 'FILHA PRINCIPAL']) and ($AccountRelationshipRequestDTO_OutputVariable.reply/ns72:child[$ForEachChildCounter]/ns72:transfer = 'T' or $AccountRelationshipRequestDTO_OutputVariable.reply/ns72:child[$ForEachChildCounter]/ns72:transfer = 'S')</condition>
                                                            <sequence>
                                                               <assign name="Transformation_InputParameters_To_ProcessAccountBalanceHierarchically">
                                                                  <copy ignoreMissingFromData="yes">
                                                                     <from>'SOA'</from>
                                                                     <to>$ProcessAccountBalanceHierarchically_InputVariable.ProcessAccountBalanceHierarchicallyEBM/ns71:EBMHeader/ns43:consumerSystem</to>
                                                                  </copy>
                                                                  <copy ignoreMissingFromData="yes">
                                                                     <from>'SOA'</from>
                                                                     <to>$ProcessAccountBalanceHierarchically_InputVariable.ProcessAccountBalanceHierarchicallyEBM/ns71:EBMHeader/ns43:userId</to>
                                                                  </copy>
                                                                  <copy ignoreMissingFromData="yes">
                                                                     <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SKYAccountNumber</from>
                                                                     <to>$ProcessAccountBalanceHierarchically_InputVariable.ProcessAccountBalanceHierarchicallyEBM/ns71:parentAccountID</to>
                                                                  </copy>
                                                                  <copy ignoreMissingFromData="yes">
                                                                     <from>$AccountRelationshipResponseFor/ns72:child/ns72:account</from>
                                                                     <to>$ProcessAccountBalanceHierarchically_InputVariable.ProcessAccountBalanceHierarchicallyEBM/ns71:childAccountID</to>
                                                                  </copy>
                                                                  <copy ignoreMissingFromData="yes">
                                                                     <from>$AccountRelationshipResponseFor/ns72:child/ns72:type</from>
                                                                     <to>$ProcessAccountBalanceHierarchically_InputVariable.ProcessAccountBalanceHierarchicallyEBM/ns71:typeChild</to>
                                                                  </copy>
                                                               </assign>
                                                               <invoke name="InvokeProcessAccountBalanceHierarchicallyEBF"
                                                                       bpelx:invokeAsDetail="no"
                                                                       partnerLink="ProcessAccountBalanceHierarchicallyEBF"
                                                                       portType="ns71:ProcessAccountBalanceHierarchicallyEBFPort"
                                                                       operation="ProcessAccountBalanceHierarchically"
                                                                       inputVariable="ProcessAccountBalanceHierarchically_InputVariable"
                                                                       outputVariable="ProcessAccountBalanceHierarchically_OutputVariable"/>
                                                               <if name="If_P_VALOR_Is_Not_Empty">
                                                                  <condition>$ProcessAccountBalanceHierarchically_OutputVariable.ProcessAccountBalanceHierarchicallyEBM/ns71:P_VALOR != 0</condition>
                                                                  <sequence>
                                                                     <if name="If_P_POID_PAG_PAI_Is_Empty">
                                                                        <condition>$ProcessAccountBalanceHierarchically_OutputVariable.ProcessAccountBalanceHierarchicallyEBM/ns71:P_POID_PAG_PAI = 0</condition>
                                                                        <sequence>
                                                                           <assign name="Transformation_InputParameters_To_PR_SELECT_LAST_BILL">
                                                                              <bpelx:annotation>
                                                                                 <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                                              </bpelx:annotation>
                                                                              <copy>
                                                                                 <from>ora:doXSLTransformForDoc("xsl/Transformation_InputParameters_To_PR_SELECT_LAST_BILL.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                                                                 <to variable="PR_SELECT_LAST_BILL_InputVariable"
                                                                                     part="InputParameters"/>
                                                                              </copy>
                                                                           </assign>
                                                                           <invoke name="Invoke_PR_SELECT_LAST_BILL"
                                                                                   bpelx:invokeAsDetail="no"
                                                                                   partnerLink="PR_SELECT_LAST_BILL"
                                                                                   portType="ns67:PR_SELECT_LAST_BILL_ptt"
                                                                                   operation="PR_SELECT_LAST_BILL"
                                                                                   inputVariable="PR_SELECT_LAST_BILL_InputVariable"
                                                                                   outputVariable="PR_SELECT_LAST_BILL_OutputVariable"/>
                                                                        </sequence>
                                                                     </if>
                                                                     <assign name="Transformation_InputParameters_To_PR_INSERT_TRANSFERENCIA_SALDO">
                                                                        <bpelx:annotation>
                                                                           <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                                        </bpelx:annotation>
                                                                        <copy>
                                                                           <from>ora:doXSLTransformForDoc("xsl/Transformation_InputParameters_To_PR_INSERT_TRANSFERENCIA_SALDO.xsl", $ProcessAccountBalanceHierarchically_OutputVariable.ProcessAccountBalanceHierarchicallyEBM, "PR_SELECT_LAST_BILL_OutputVariable.OutputParameters", $PR_SELECT_LAST_BILL_OutputVariable.OutputParameters)</from>
                                                                           <to variable="PR_INSERT_TRANSFERENCIA_SALDO_InputVariable"
                                                                               part="InputParameters"/>
                                                                        </copy>
                                                                     </assign>
                                                                     <invoke name="Invoke_PR_INSERT_TRANSFERENCIA_SALDO"
                                                                             bpelx:invokeAsDetail="no"
                                                                             partnerLink="PR_INSERT_TRANSFERENCIA_SALDO"
                                                                             portType="ns68:PR_INSERT_TRANSFERENCIA_SALDO_ptt"
                                                                             operation="PR_INSERT_TRANSFERENCIA_SALDO"
                                                                             inputVariable="PR_INSERT_TRANSFERENCIA_SALDO_InputVariable"/>
                                                                  </sequence>
                                                                  <else>
                                                                     <empty name="Do_Nothing"
                                                                            xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable"/>
                                                                  </else>
                                                               </if>
                                                            </sequence>
                                                            <else>
                                                               <empty name="Do_Nothing"/>
                                                            </else>
                                                         </if>
                                                      </sequence>
                                                   </scope>
                                                </forEach>
                                             </sequence>
                                          </else>
                                       </if>
                                    </sequence>
                                    <else>
                                       <empty name="Do_Nothing"/>
                                    </else>
                                 </if>
                              </scope>
                           </sequence>
                        </scope>
                        <if name="IfOrderHasNoHardwareOrIsLastHardware">
                           <documentation>
                              <![CDATA[If there is no hardware or is last hardware being processed, the order status should be set to complete]]>
                           </documentation>
                           <condition>count( $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder /ford:FulfillmentOrderLine[ corecom:InstalledProductReference/corecom:Custom/corecomcust:WorkOrderIndicator = 'true']) = 0 or ( $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder /corecom:Status/corecom:Code = 'Locked In Progress' and count( $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder /ford:FulfillmentOrderLine[( (corecom:InstalledProductReference/corecom:Custom/corecomcust:WorkOrderIndicator = 'true' and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Pending') or (corecom:InstalledProductReference/corecom:Custom/corecomcust:WorkOrderIndicator = 'true' and not(corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus)))]) = 0 )</condition>
                           <scope name="SetOrderStatusToComplete" 
                                  exitOnStandardFault="no">
                              <variables>
                                 <variable name="Invoke_UpdateFulfillmentOrder_InputVariable"
                                           messageType="ns20:UpdateFulfillmentOrderReqMsg"/>
                              </variables>
                              <sequence name="SetOrderStatusToComplete">
                                 <assign name="Tranform_UpdateFulfillmentOrder">
                                    <bpelx:annotation>
                                       <bpelx:pattern patternName="bpelx:transformation"/>
                                    </bpelx:annotation>
                                    <copy>
                                       <from>ora:doXSLTransformForDoc("xsl/UpdateFulfillmentOrder_OrderStatusComplete.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM, "Invoke_A13UpdateSalesOrderCCPSiebelProvABCSImpl_InputVariable.UpdateFulfillmentOrderEBM", $Invoke_A13UpdateSalesOrderCCPSiebelProvABCSImpl_InputVariable.UpdateFulfillmentOrderEBM)</from>
                                       <to variable="Invoke_UpdateFulfillmentOrder_InputVariable"
                                           part="UpdateFulfillmentOrderEBM"/>
                                    </copy>
                                 </assign>
                                 <invoke name="Invoke_UpdateFulfillmentOrder"
                                         partnerLink="UpdateSalesOrderCCPSiebelProvABCSImpl"
                                         portType="ns20:CommunicationsFulfillmentOrderEBS"
                                         operation="UpdateFulfillmentOrder"
                                         inputVariable="Invoke_UpdateFulfillmentOrder_InputVariable"
                                         bpelx:invokeAsDetail="no"/>
                              </sequence>
                           </scope>
                              <elseif>
                                 <condition>count($Invoke_A13UpdateSalesOrderCCPSiebelProvABCSImpl_InputVariable.UpdateFulfillmentOrderEBM/ford:DataArea/ford:UpdateFulfillmentOrder/ford:FulfillmentOrderLine)>0</condition>
                                 <sequence name="Invoke_ItemsToChangeStatus">
                                     <invoke name="Invoke_A13UpdateSalesOrderCCPSiebelProvABCSImpl"
                                             inputVariable="Invoke_A13UpdateSalesOrderCCPSiebelProvABCSImpl_InputVariable"
                                             partnerLink="UpdateSalesOrderCCPSiebelProvABCSImpl"
                                             portType="ns20:CommunicationsFulfillmentOrderEBS"
                                             operation="UpdateFulfillmentOrder"
                                             bpelx:invokeAsDetail="no"/>
                                 </sequence>
                              </elseif>
                        </if>
                        <scope name="ScopeRecurringRecharge"
                               exitOnStandardFault="no">
                           <if name="If2">
                              <documentation>
                                 <![CDATA[CheckRecurringRecharge]]>
                              </documentation>
                              <condition>$Invoke_QueryCustomerPartyEnableCustomerParty_OutputVariable.QueryCustomerPartyResponseEBM/custparty:DataArea/custparty:QueryCustomerPartyResponse/custparty:CustomerPartyAccount/custparty:Custom/custpartycust:Keywords[custpartycust:KeywordType = 'Recarga Programada']/custpartycust:KeywordValue = 'CADASTRADO' and $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:SalesChannelCode = 'Salesforce'</condition>
                              <sequence name="Sequence53">
                                 <assign name="TransformRecurringRecharge">
                                    <bpelx:annotation>
                                       <bpelx:pattern patternName="bpelx:transformation"/>
                                    </bpelx:annotation>
                                    <copy>
                                       <from>ora:doXSLTransformForDoc("xsl/TransformationReqToRecurringRecharge.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                                       <to variable="InvokeRecurringRecharge_InputVariable"
                                           part="body"/>
                                    </copy>
                                 </assign>
                                 <invoke name="InvokeRecurringRecharge"
                                         bpelx:invokeAsDetail="no"
                                         partnerLink="RecurringRechargeJMSAdapter"
                                         portType="ns33:Produce_Message_ptt"
                                         operation="Produce_Message"
                                         inputVariable="InvokeRecurringRecharge_InputVariable"/>
                              </sequence>
                           </if>
                        </scope>
                        <if name="If_OrderItem_Not_Completed">
                           <documentation>
                              <![CDATA[Has_Order_Items]]>
                           </documentation>
                           <condition>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus != 'Complete']) > 0 or count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine) = 0</condition>
                           <sequence name="Do_Nothing">
                              <empty name="Do_Not_Have_Anything_to_Send"/>
                           </sequence>
                           <else>
                              <documentation>
                                 <![CDATA[Does_Not_Have_Order_Items]]>
                              </documentation>
                              <scope name="SCP_A12_Invoke_UpdateCustomerPartySynchronously" 
                                     exitOnStandardFault="no">
                                 <sequence name="A12_">
                                    <assign name="A12_XformProcessSoftwareFulfillmentOrderEBMToUpdateCustomerPartySynchronouslyEBM">
                                       <bpelx:annotation>
                                          <bpelx:pattern patternName="bpelx:transformation"/>
                                       </bpelx:annotation>
                                       <copy>
                                          <from>ora:doXSLTransformForDoc("xsl/A12_ProcessSoftwareFulfillmentOrderEBMToUpdateCustomerPartySynchronouslyEBM.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM, "EBMHeader", $EBMHeader)</from>
                                          <to variable="A12_UpdateCustomerPartySynchronously_InputVariable"
                                              part="UpdateCustomerPartySynchronouslyEBM"/>
                                       </copy>
                                    </assign>
                                    <invoke name="A12_Invoke_UpdateCustomerPartySynchronously"
                                            partnerLink="CustomerPartyEBS"
                                            portType="ns9:CommunicationsCustomerPartyEBS"
                                            operation="UpdateCustomerPartySynchronously"
                                            inputVariable="A12_UpdateCustomerPartySynchronously_InputVariable"
                                            bpelx:invokeAsDetail="no"
                                            outputVariable="A12_UpdateCustomerPartySynchronously_OutputVariable"/>
                                 </sequence>
                              </scope>
                           </else>
                        </if>
                        <if name="D9_Has_To_Check_For_Pending_Payments">
                           <documentation>
                              <![CDATA[yes]]>
                           </documentation>
                           <condition>(not($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Inclusion") and not($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Prepaid to Postpaid Migration"))or $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:MigrationAccountType = "Sky Livre"</condition>
                           <if name="IfOrderHasNoHardwareOrIsLastHardware">
                              <condition>count( $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder /ford:FulfillmentOrderLine[ corecom:InstalledProductReference/corecom:Custom/corecomcust:WorkOrderIndicator = 'true']) = 0 or ( $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder /corecom:Status/corecom:Code = 'Locked In Progress' and count( $inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder /ford:FulfillmentOrderLine[( (corecom:InstalledProductReference/corecom:Custom/corecomcust:WorkOrderIndicator = 'true' and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Pending') or (corecom:InstalledProductReference/corecom:Custom/corecomcust:WorkOrderIndicator = 'true' and not(corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus)))]) = 0 )</condition>
                              <sequence name="Sequence59">
                                 
                                 <forEach parallel="no" counterName="D10_ctr" name="ForEachOrderPayment_D10">
                                    <startCounterValue>1</startCounterValue>
                                    <finalCounterValue>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderPayment)</finalCounterValue>
                                    <scope name="SCP_InvokeA15_CreateReceivedPaymentSynchronously"
                                           exitOnStandardFault="no">
                                       <sequence name="Sequence19">
                                          <assign name="Assign_ForEachCtr_To_ItemIndex">
                                             <copy>
                                                <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderPayment[$D10_ctr]</from>
                                                <to>$CurrentFulfillmentOrderPayment</to>
                                             </copy>
                                          </assign>
                                          <if name="D10_Is_there_any_payment_which_has_not_been_registered_in_BRM">
                                             <condition>(string-length($CurrentFulfillmentOrderPayment/ford:FulfillmentOrderReceivedPayment/corecom:ReceivedPaymentReference/corecom:Custom/corecomcust:PaymentReceiptDate) != 0)</condition>
                                             <sequence name="Sequence18">
                                                <assign name="Transform_A15_InputVariable_To_CreateReceivedPaymentSynchronously">
                                                   <bpelx:annotation>
                                                      <bpelx:pattern patternName="bpelx:transformation"></bpelx:pattern>
                                                   </bpelx:annotation>
                                                   <copy>
                                                      <from>ora:doXSLTransformForDoc("xsl/A15_InputVariable_To_CreateReceivedPaymentSync2.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM, "CurrentFulfillmentOrderPayment", $CurrentFulfillmentOrderPayment)</from>
                                                      <to variable="InvokeA15_CreateReceivedPaymentSynchronously_InputVariable"
                                                          part="CreateReceivedPaymentSynchronouslyEBM"/>
                                                   </copy>
                                                </assign>
                                                <assign name="AssignCurrentDate">
                                                   <copy>
                                                      <from>xp20:current-dateTime()</from>
                                                      <to>$CurrentDate</to>
                                                   </copy>
                                                </assign>
                                                <invoke name="InvokeA15_CreateReceivedPaymentSynchronously"
                                                        partnerLink="ReceivedPaymentEBS"
                                                        portType="ns18:CommunicationsReceivedPaymentEBS"
                                                        operation="CreateReceivedPaymentSynchronously"
                                                        inputVariable="InvokeA15_CreateReceivedPaymentSynchronously_InputVariable"
                                                        outputVariable="InvokeA15_CreateReceivedPaymentSynchronously_OutputVariable"
                                                        bpelx:invokeAsDetail="no"/>
                                             </sequence>
                                          </if>
                                       </sequence>
                                    </scope>
                                 </forEach>
                    </sequence>
                           </if>
                        </if>
                     </sequence>
                  </else>
               </if>
            </scope>
            <!--if name="D6_IsThereAnySoftwareDelete">
      <condition>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[
                            corecom:InstalledProductReference/corecom:Custom/corecomcust:Category != "Equipamento"
                            and ford:ServiceActionCode = "DELETE"
                            and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = "Locked In Progress"]) > 0
                  and not($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Prepaid to Postpaid Migration")
                  and not($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Postpaid to Prepaid Migration")
                  and not($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Postpaid BB > Prepaid Migr.")
                  and not($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Reg.>Bus. or Bus.>Reg. Migr.")
                  and not($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Upgrade With Techn. Exchange")
                  and not($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Upgd. W/o Technology Exchange")
                  and not($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Dwgd. With Technology Exchange")
                  and not($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Dwgd. W/o Technology Exchange")</condition>
      <forEach parallel="no" counterName="ForEach_Counter"
               name="ForEach_SoftwareDelete">
        <startCounterValue>1</startCounterValue>
        <finalCounterValue>count($inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[
                                    corecom:InstalledProductReference/corecom:Custom/corecomcust:Category != "Equipamento"
                                    and ford:ServiceActionCode = "DELETE"
                                    and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = "Locked In Progress"])</finalCounterValue>
        <scope name="Scope16">
          <variables>
            <variable name="v_currentOrderLine"
                      element="ford:FulfillmentOrderLine"/>
          </variables>
          <if name="IsNotSeason">
            <documentation>Season penalties will be calculated internally in BRM</documentation>
            <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine/corecom:InstalledProductReference/corecom:Custom/corecomcust:Category != "Temporada"</condition>
          <sequence name="Sequence41">
            <assign name="Assign_CurrentOrderLine">
              <copy>
                  <from>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine[
                            corecom:InstalledProductReference/corecom:Custom/corecomcust:Category != "Equipamento" 
                            and ford:ServiceActionCode = "DELETE" 
                            and corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = "Locked In Progress"][position() = $ForEach_Counter]</from>
                <to>$v_currentOrderLine</to>
              </copy>
            </assign>
            <assign name="A8_XformProcessSoftwareFulfilmentOrderEBMToQueryAssessmentInstalledProductListEBM">
              <bpelx:annotation>
                <bpelx:pattern patternName="bpelx:transformation"/>
              </bpelx:annotation>
              <copy>
                <from>ora:doXSLTransformForDoc("xsl/A8_InputVariableEBMToQueryAssessmentInstalledProductListEBM.xsl", $v_currentOrderLine, "inputVariable.ProcessSoftwareFulfillmentOrderEBM", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                <to variable="A8_QueryAssessmentInstalledProductList_InputVariable"
                    part="QueryAssessmentInstalledProductListEBM"/>
              </copy>
            </assign>
            <invoke name="A8_Invoke_QueryAssessmentInstalledProductList"
                    partnerLink="QueryAssessmentInstalledProductListEBF"
                    portType="ns29:QueryAssessmentInstalledProductListEBF"
                    operation="QueryAssessmentInstalledProductList"
                    inputVariable="A8_QueryAssessmentInstalledProductList_InputVariable"
                    bpelx:invokeAsDetail="no"
                    outputVariable="A8_QueryAssessmentInstalledProductList_OutputVariable"/>
            <if name="If_HasAmount">
              <condition>count($A8_QueryAssessmentInstalledProductList_OutputVariable.QueryAssessmentInstalledProductListResponseEBM/instprod:DataArea/instprod:QueryAssessmentInstalledProductListResponse/instprod:InstalledProductPrice/corecom:Price/corecom:Amount) > 0 and number($A8_QueryAssessmentInstalledProductList_OutputVariable.QueryAssessmentInstalledProductListResponseEBM/instprod:DataArea/instprod:QueryAssessmentInstalledProductListResponse/instprod:InstalledProductPrice/corecom:Price/corecom:Amount) > 0</condition>
              <sequence name="Sequence42">
                <assign name="A9_XformProcessSoftwareFulfillmentOrderEBMToCreatePaymentTermSynchronoulyEBM">
                  <bpelx:annotation>
                    <bpelx:pattern patternName="bpelx:transformation"/>
                  </bpelx:annotation>
                  <copy>
                    <from>ora:doXSLTransformForDoc("xsl/A9_inputVariableToCreatePaymentTermSynchronously.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM, "A8_QueryAssessmentInstalledProductList_OutputVariable.QueryAssessmentInstalledProductListResponseEBM", $A8_QueryAssessmentInstalledProductList_OutputVariable.QueryAssessmentInstalledProductListResponseEBM, "v_currentOrderLine", $v_currentOrderLine)</from>
                    <to variable="A9_CreatePaymentTermSynchronouly_InputVariable"
                        part="CreatePaymentTermSynchronouslyEBM"/>
                  </copy>
                </assign>
                <invoke name="A9_Invoke_CreatePaymentTermSynchronouly"
                        partnerLink="CommunicationsPaymentTermEBSV"
                        portType="ns11:CommunicationsPaymentTermEBS"
                        operation="CreatePaymentTermSynchronously"
                        inputVariable="A9_CreatePaymentTermSynchronouly_InputVariable"
                        bpelx:invokeAsDetail="no"
                        outputVariable="A9_CreatePaymentTermSynchronouly_OutputVariable"/>
              </sequence>
            </if>
          </sequence>
    </if>
      </scope>
    </forEach>
    </if-->
            <assign name="Set_SuccessMessage">
               <bpelx:annotation>
                  <bpelx:pattern patternName="bpelx:transformation"/>
               </bpelx:annotation>
               <copy>
                  <from>ora:doXSLTransformForDoc("xsl/Set_SuccessMessage.xsl", $inputVariable.ProcessSoftwareFulfillmentOrderEBM)</from>
                  <to variable="outputVariable"
                      part="ProcessSoftwareFulfillmentOrderEBM"/>
               </copy>
            </assign>
            <invoke name="replyOutput"
                    partnerLink="processsoftwarefulfillmentorderbpel_client"
                    portType="ns1:ProcessSoftwareFulfillmentOrderResponse"
                    operation="CallbackResponse"
                    inputVariable="outputVariable"/>
            <scope name="TrackerProcessOutputScope" exitOnStandardFault="no">
               <variables>
                  <variable name="WriteToTrackerQueue_ProduceTrackerMessage_InputVariable"
                            messageType="trackersvc:ProduceTrackerMessage_msg"/>
               </variables>
               <faultHandlers>
                  <catchAll>
                     <empty name="DoNothing"/>
                  </catchAll>
               </faultHandlers>
               <if name="If_TrackerLogLevel_greaterThan_0">
                  <condition>$logLevel != '' and $logLevel > '0'</condition>
                  <sequence name="TrackerProcessOutputSequence">
                     <assign name="AssignValuesToTrackerVariable">
                        <copy>
                           <from>concat(
                            ora:getInstanceId(), '||',
                            ora:getComponentName(), '||',
                            ora:getCompositeName(), '||',
                            xp20:current-dateTime(), '||',
                            $orderNumber, '||',
                            $accountCSN, '||',
                            '1', '||',
                            ora:getECID(), '||',
                            '', '||',
                            $orderType, '||',
                            $orderSubType)</from>
                           <to>$WriteToTrackerQueue_ProduceTrackerMessage_InputVariable.payload</to>
                        </copy>
                     </assign>
                     <invoke name="WriteToTrackerQueue"
                             partnerLink="TrackerSourceQueue"
                             portType="trackersvc:ProduceTrackerMessage_ptt"
                             operation="ProduceTrackerMessage"
                             bpelx:invokeAsDetail="no"
                             inputVariable="WriteToTrackerQueue_ProduceTrackerMessage_InputVariable"/>
                  </sequence>
               </if>
            </scope>
         </sequence>
      </flow>
      </sequence>
</process>






erro:


<bpelFault><faultType>0</faultType><runtimeFault xmlns="http://schemas.oracle.com/bpel/extension"><part name="summary"><summary>Cannot find property alias.
cannot find the property alias "{http://xmlns.oracle.com/SKYNOHS_Fase2_ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderBPEL/correlationset}mobile", message type "{http://xmlns.oracle.com/EnterpriseFlows/Industry/Comms/ProcessSoftwareFulfillmentOrderEBFMIP/V1}ProcessSoftwareFulfillmentOrderRequestMsg"
The property alias named in the error message was not defined in the BPEL/WSDL source.
Check the BPEL/WSDL source to ensure that the property alias named in the error message has been defined.
</summary></part><part name="detail"><detail>ORABPEL-03812

Cannot find property alias.
cannot find the property alias "{http://xmlns.oracle.com/SKYNOHS_Fase2_ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderBPEL/correlationset}mobile", message type "{http://xmlns.oracle.com/EnterpriseFlows/Industry/Comms/ProcessSoftwareFulfillmentOrderEBFMIP/V1}ProcessSoftwareFulfillmentOrderRequestMsg"
The property alias named in the error message was not defined in the BPEL/WSDL source.
Check the BPEL/WSDL source to ensure that the property alias named in the error message has been defined.

	at com.collaxa.cube.engine.ext.bpel.common.BPELWMPHelper.initiateCorrelationSet(BPELWMPHelper.java:1961)
	at com.collaxa.cube.engine.ext.common.EntryReceiveHandler.handleInputMessage(EntryReceiveHandler.java:210)
	at com.collaxa.cube.engine.ext.common.EntryReceiveHandler.handle(EntryReceiveHandler.java:83)
	at com.collaxa.cube.engine.ext.bpel.common.wmp.BPELEntryReceiveWMP.__executeStatements(BPELEntryReceiveWMP.java:99)
	at com.collaxa.cube.engine.ext.bpel.common.wmp.BaseBPELActivityWMP.perform(BaseBPELActivityWMP.java:188)
	at com.collaxa.cube.engine.CubeEngine.performActivity(CubeEngine.java:2924)
	at com.collaxa.cube.engine.CubeEngine._handleWorkItem(CubeEngine.java:1267)
	at com.collaxa.cube.engine.CubeEngine.handleWorkItem(CubeEngine.java:1162)
	at com.collaxa.cube.engine.dispatch.message.instance.PerformMessageHandler.handleLocal(PerformMessageHandler.java:106)
	at com.collaxa.cube.engine.dispatch.DispatchHelper.handleLocalMessage(DispatchHelper.java:308)
	at com.collaxa.cube.engine.dispatch.DispatchHelper.sendMemory(DispatchHelper.java:387)
	at com.collaxa.cube.engine.CubeEngine.endRequest(CubeEngine.java:4955)
	at com.collaxa.cube.engine.CubeEngine.endRequest(CubeEngine.java:4879)
	at com.collaxa.cube.engine.CubeEngine._createAndInvoke(CubeEngine.java:756)
	at com.collaxa.cube.engine.CubeEngine.createAndInvoke(CubeEngine.java:591)
	at com.collaxa.cube.engine.ejb.impl.CubeEngineBean.createAndInvoke(CubeEngineBean.java:126)
	at com.collaxa.cube.engine.ejb.impl.CubeEngineBean.syncCreateAndInvokeParticipate(CubeEngineBean.java:219)
	at com.collaxa.cube.engine.ejb.impl.bpel.BPELEngineBean_51369e_ICubeEngineLocalBeanImpl.__WL_invoke(Unknown Source)
	at weblogic.ejb.container.internal.SessionLocalMethodInvoker.invoke(SessionLocalMethodInvoker.java:33)
	at com.collaxa.cube.engine.ejb.impl.bpel.BPELEngineBean_51369e_ICubeEngineLocalBeanImpl.syncCreateAndInvokeParticipate(Unknown Source)
	at com.collaxa.cube.engine.delivery.DeliveryHandler.callCreateAndInvoke(DeliveryHandler.java:987)
	at com.collaxa.cube.engine.delivery.DeliveryHandler.initialPostAnyType(DeliveryHandler.java:475)
	at com.collaxa.cube.engine.delivery.DeliveryHandler.initialPost(DeliveryHandler.java:361)
	at com.collaxa.cube.engine.delivery.DeliveryHandler.post(DeliveryHandler.java:120)
	at com.collaxa.cube.engine.ejb.impl.CubeDeliveryBean.post(CubeDeliveryBean.java:672)
	at com.collaxa.cube.engine.ejb.impl.bpel.BPELDeliveryBean_5k948i_ICubeDeliveryLocalBeanImpl.__WL_invoke(Unknown Source)
	at weblogic.ejb.container.internal.SessionLocalMethodInvoker.invoke(SessionLocalMethodInvoker.java:33)
	at com.collaxa.cube.engine.ejb.impl.bpel.BPELDeliveryBean_5k948i_ICubeDeliveryLocalBeanImpl.post(Unknown Source)
	at oracle.fabric.CubeServiceEngine.post(CubeServiceEngine.java:618)
	at oracle.integration.platform.blocks.mesh.AsynchronousMessageHandler.doPost(AsynchronousMessageHandler.java:144)
	at oracle.integration.platform.blocks.mesh.MessageRouter.post(MessageRouter.java:233)
	at oracle.integration.platform.blocks.mesh.MeshImpl.post(MeshImpl.java:418)
	at sun.reflect.GeneratedMethodAccessor1436.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at org.springframework.aop.support.AopUtils.invokeJoinpointUsingReflection(AopUtils.java:318)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.invokeJoinpoint(ReflectiveMethodInvocation.java:183)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:150)
	at oracle.integration.platform.metrics.PhaseEventAspect.invoke(PhaseEventAspect.java:59)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:172)
	at org.springframework.aop.framework.JdkDynamicAopProxy.invoke(JdkDynamicAopProxy.java:202)
	at com.sun.proxy.$Proxy394.post(Unknown Source)
	at oracle.integration.platform.blocks.soap.WebServiceEntryBindingComponent.doMessageProcessing(WebServiceEntryBindingComponent.java:2342)
	at oracle.integration.platform.blocks.soap.WebServiceEntryBindingComponent.processIncomingMessage(WebServiceEntryBindingComponent.java:1403)
	at oracle.integration.platform.blocks.soap.FabricProvider.processMessage(FabricProvider.java:113)
	at oracle.j2ee.ws.server.provider.ProviderProcessor.doEndpointProcessing(ProviderProcessor.java:1319)
	at oracle.j2ee.ws.server.WebServiceProcessor.invokeEndpointImplementation(WebServiceProcessor.java:1380)
	at oracle.j2ee.ws.server.provider.ProviderProcessor.doRequestProcessingPhaseTwo(ProviderProcessor.java:705)
	at oracle.j2ee.ws.server.WebServiceProcessor.doRequestProcessing(WebServiceProcessor.java:693)
	at oracle.j2ee.ws.server.WebServiceProcessor.processRequest(WebServiceProcessor.java:251)
	at oracle.j2ee.ws.server.WebServiceProcessor.doService(WebServiceProcessor.java:215)
	at oracle.j2ee.ws.server.WebServiceServlet.doService(WebServiceServlet.java:687)
	at oracle.j2ee.ws.server.WebServiceServlet.doPost(WebServiceServlet.java:525)
	at oracle.integration.platform.blocks.soap.FabricProviderServlet.doPost(FabricProviderServlet.java:788)
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:751)
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:844)
	at weblogic.servlet.internal.StubSecurityHelper$ServletServiceAction.run(StubSecurityHelper.java:280)
	at weblogic.servlet.internal.StubSecurityHelper$ServletServiceAction.run(StubSecurityHelper.java:254)
	at weblogic.servlet.internal.StubSecurityHelper.invokeServlet(StubSecurityHelper.java:136)
	at weblogic.servlet.internal.ServletStubImpl.execute(ServletStubImpl.java:346)
	at weblogic.servlet.internal.TailFilter.doFilter(TailFilter.java:25)
	at weblogic.servlet.internal.FilterChainImpl.doFilter(FilterChainImpl.java:79)
	at oracle.security.jps.ee.http.JpsAbsFilter$1.run(JpsAbsFilter.java:137)
	at java.security.AccessController.doPrivileged(Native Method)
	at oracle.security.jps.util.JpsSubject.doAsPrivileged(JpsSubject.java:315)
	at oracle.security.jps.ee.util.JpsPlatformUtil.runJaasMode(JpsPlatformUtil.java:460)
	at oracle.security.jps.ee.http.JpsAbsFilter.runJaasMode(JpsAbsFilter.java:120)
	at oracle.security.jps.ee.http.JpsAbsFilter.doFilter(JpsAbsFilter.java:217)
	at oracle.security.jps.ee.http.JpsFilter.doFilter(JpsFilter.java:81)
	at weblogic.servlet.internal.FilterChainImpl.doFilter(FilterChainImpl.java:79)
	at oracle.dms.servlet.DMSServletFilter.doFilter(DMSServletFilter.java:220)
	at weblogic.servlet.internal.FilterChainImpl.doFilter(FilterChainImpl.java:79)
	at weblogic.servlet.internal.WebAppServletContext$ServletInvocationAction.wrapRun(WebAppServletContext.java:3436)
	at weblogic.servlet.internal.WebAppServletContext$ServletInvocationAction.run(WebAppServletContext.java:3402)
	at weblogic.security.acl.internal.AuthenticatedSubject.doAs(AuthenticatedSubject.java:321)
	at weblogic.security.service.SecurityManager.runAs(SecurityManager.java:120)
	at weblogic.servlet.provider.WlsSubjectHandle.run(WlsSubjectHandle.java:57)
	at weblogic.servlet.internal.WebAppServletContext.doSecuredExecute(WebAppServletContext.java:2285)
	at weblogic.servlet.internal.WebAppServletContext.securedExecute(WebAppServletContext.java:2201)
	at weblogic.servlet.internal.WebAppServletContext.execute(WebAppServletContext.java:2179)
	at weblogic.servlet.internal.ServletRequestImpl.run(ServletRequestImpl.java:1572)
	at weblogic.servlet.provider.ContainerSupportProviderImpl$WlsRequestExecutor.run(ContainerSupportProviderImpl.java:255)
	at weblogic.work.ExecuteThread.execute(ExecuteThread.java:311)
	at weblogic.work.ExecuteThread.run(ExecuteThread.java:263)
</detail></part><part name="code"><code>com.collaxa.cube.engine.delivery.DeliveryCorrelationException</code></part></runtimeFault></bpelFault>
