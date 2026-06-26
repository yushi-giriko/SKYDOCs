Faulted while invoking operation "createorder" on provider "MobileService".
<messages>
<input>
<InvokeMobileService_createOrder_createorder_InputVariable>
<part xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" name="request">
<request xmlns:svcdoc="http://xmlns.oracle.com/Services/Documentation/V1" xmlns:client="http://xmlns.oracle.com/EnterpriseFlows/Industry/Comms/ProcessSoftwareFulfillmentOrderEBFMIP/V1" xmlns:wsdl="http://schemas.xmlsoap.org/wsdl/" xmlns:corecustomerpartyebs="http://xmlns.oracle.com/EnterpriseServices/Core/CustomerParty/V2" xmlns:plnk="http://docs.oasis-open.org/wsbpel/2.0/plnktype" xmlns:inp2="http://TargetNamespace.com/MobileService_createorder_response" xmlns:ebs="http://xmlns.oracle.com/EnterpriseServices/Core/FulfillmentOrder/V1" xmlns:corecom="http://xmlns.oracle.com/EnterpriseObjects/Core/Common/V2" xmlns:ns9="http://xmlns.oracle.com/EnterpriseObjects/Core/Custom/EBO/FulfillmentOrder/V1" xmlns:ns12="http://xmlns.oracle.com/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/MobileService" xmlns:ns5="http://xmlns.oracle.com/EnterpriseObjects/Core/EBO/Validation/V1" xmlns:ns6="http://schemas.xmlsoap.org/ws/2003/03/addressing" xmlns:ns10="http://xmlns.oracle.com/EnterpriseServices/CustomerParty/V2" xmlns:ns7="urn:oasis:names:tc:xacml:2.0:policy:schema:cd:04" xmlns:ns8="http://www.sky.com.br/ArchitectureSchemas" xmlns:ns11="http://xmlns.oracle.com/EnterpriseObjects/Core/Custom/EBO/CustomerParty/V2" xmlns:ns2="http://xmlns.oracle.com/EnterpriseServices/FulfillmentOrder/V1" xmlns:ns4="http://xmlns.oracle.com/EnterpriseObjects/Core/Custom/Common/V2" xmlns:ns3="urn:oasis:names:tc:xacml:2.0:context:schema:cd:04" xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/" xmlns:tns="http://TargetNamespace.com/MobileService_createorder_request" xmlns="http://TargetNamespace.com/MobileService_createorder_request">
<tns:serviceOrder>
<tns:name>CustomerOrderIdentifier</tns:name>
<tns:valueType>string</tns:valueType>
<tns:value>1-56045895145</tns:value>
</tns:serviceOrder>
<tns:serviceOrder>
<tns:name>AccountIdentifier</tns:name>
<tns:valueType>string</tns:valueType>
<tns:value>1520361878</tns:value>
</tns:serviceOrder>
<tns:serviceOrderItem>
<tns:name>operationType</tns:name>
<tns:valueType>string</tns:valueType>
<tns:value>activation</tns:value>
</tns:serviceOrderItem>
<tns:serviceOrderItem>
<tns:name>iccid</tns:name>
<tns:valueType>string</tns:valueType>
<tns:value>8955170220466370751</tns:value>
</tns:serviceOrderItem>
<tns:serviceOrderItem>
<tns:name>ddd</tns:name>
<tns:valueType>string</tns:valueType>
<tns:value>11</tns:value>
</tns:serviceOrderItem>
<tns:serviceOrderItem>
<tns:name>document</tns:name>
<tns:valueType>string</tns:valueType>
<tns:value>26919584000</tns:value>
</tns:serviceOrderItem>
<tns:serviceOrderItem>
<tns:name>planCode</tns:name>
<tns:valueType>string</tns:valueType>
<tns:value>2069</tns:value>
</tns:serviceOrderItem>
</request>
</part>
</InvokeMobileService_createOrder_createorder_InputVariable>
</input>
<fault>
<bpelFault>
<faultType>0</faultType>
<bindingFault xmlns="http://schemas.oracle.com/bpel/extension">
<part name="summary">
<summary>Internal Server Error</summary>
</part>
<part name="detail">
<detail>
{"success":false,"eventId":null,"serviceOrderId":null,"timestamp":"2026-06-26T18:14:31.505293679Z","message":"Ordem ja cadastrada. customerOrder=1-56045895145 account=1520361878"}
</detail>
</part>
<part name="code">
<code>500</code>
</part>
</bindingFault>
</bpelFault>
</fault>
<faultType>
<message>0</message>
</faultType>
</messages>
