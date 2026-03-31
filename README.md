<?xml version="1.0" encoding="UTF-8"?>
<definitions
    name="ProcessSoftwareFulfillmentOrderBPEL_properties"
    targetNamespace="http://xmlns.oracle.com/SKYNOHS_Fase2_ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderBPEL/correlationset"
    xmlns="http://schemas.xmlsoap.org/wsdl/"
    xmlns:plnk="http://docs.oasis-open.org/wsbpel/2.0/plnktype"
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"
    xmlns:tns="http://xmlns.oracle.com/SKYNOHS_Fase2_ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderEBFMIP/ProcessSoftwareFulfillmentOrderBPEL/correlationset"
    xmlns:ns1="http://xmlns.oracle.com/EnterpriseFlows/Industry/Comms/ProcessSoftwareFulfillmentOrderEBFMIP/V1"
    xmlns:ford="http://xmlns.oracle.com/EnterpriseObjects/Core/EBO/FulfillmentOrder/V1"
    xmlns:corecom="http://xmlns.oracle.com/EnterpriseObjects/Core/Common/V2">

    <plnk:property name="Property_mobile" type="xsd:string"/>

    <plnk:propertyAlias
        propertyName="tns:Property_mobile"
        messageType="ns1:ProcessSoftwareFulfillmentOrderRequestMsg"
        part="payload">
        <plnk:query><![CDATA[
            /ford:ProcessSoftwareFulfillmentOrderEBM
            /ford:DataArea
            /ford:ProcessSoftwareFulfillmentOrder
            /corecom:Identification
            /corecom:ID
        ]]></plnk:query>
    </plnk:propertyAlias>

</definitions>
