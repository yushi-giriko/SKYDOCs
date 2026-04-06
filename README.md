<?xml version = '1.0' encoding = 'UTF-8'?>
<xsl:stylesheet version="2.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:corecom="http://xmlns.oracle.com/EnterpriseObjects/Core/Common/V2" xmlns:corecomcust="http://xmlns.oracle.com/EnterpriseObjects/Core/Custom/Common/V2" xmlns:fordcust="http://xmlns.oracle.com/EnterpriseObjects/Core/Custom/EBO/FulfillmentOrder/V1" xmlns:ford="http://xmlns.oracle.com/EnterpriseObjects/Core/EBO/FulfillmentOrder/V1" xmlns:xp20="http://www.oracle.com/XSL/Transform/java/oracle.tip.pc.services.functions.Xpath20" exclude-result-prefixes="xsl xp20">
   <xsl:template match="/">
      <xsl:variable name="AllOrderLines" select="/ford:ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:FulfillmentOrderLine"/>
      <xsl:variable name="LockedInProgressItems" select="$AllOrderLines[corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress']"/>
      <ford:FulfillmentOrderEBO>
         <xsl:for-each select="$LockedInProgressItems[           (             (corecom:InstalledProductReference/corecom:Custom/corecomcust:WorkOrderIndicator = &quot;false&quot;                or (corecom:InstalledProductReference/corecom:Custom/corecomcust:WorkOrderIndicator = &quot;true&quot;                  and ford:Custom/corecomcust:WorkOrderReference/corecom:WorkOrderLineReference/corecom:WorkOrderLineIdentification/corecom:ID)             )             or (xp20:lower-case(string(ford:ServiceActionCode)) = &quot;delete&quot;                  and (substring(corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name=&quot;Modify&quot;]/corecom:Value,1,1) = &quot;S&quot; or not(corecom:ItemReference/corecom:SpecificationGroup/corecom:Specification[corecom:Name=&quot;Modify&quot;]))             )      )      and not(          xp20:lower-case(string(/ford:ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:OrderType)) = &quot;technical support&quot;                and xp20:lower-case(string(ford:ServiceActionCode)) = &quot;delete&quot;                and count($AllOrderLines[xp20:lower-case(string(ford:ServiceActionCode)) = &quot;update&quot;]) > 0           )]">
            <xsl:variable name="CurrentOrderLine" select="."/>
            <xsl:choose>
               <xsl:when test="$CurrentOrderLine/corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'SIM' and ($LockedInProgressItems[corecom:Identification/corecom:ApplicationObjectKey/corecom:ID/text() = $CurrentOrderLine/corecom:RootParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID/text()] or $AllOrderLines[corecom:Identification/corecom:ApplicationObjectKey/corecom:ID/text() = $CurrentOrderLine/corecom:RootParentFulfillmentOrderLineIdentification/corecom:ApplicationObjectKey/corecom:ID/text()]/corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Complete')">
                  <xsl:for-each select="$AllOrderLines[        ford:Custom/fordcust:RootOrderItemId = $CurrentOrderLine/ford:Custom/fordcust:RootOrderItemId]">
                     <xsl:variable name="CurrentHierarchyOrderLine" select="."/>
                     <ford:FulfillmentOrderLine>
                        <corecom:Identification>
                           <corecom:ID>
                              <xsl:value-of select="$CurrentHierarchyOrderLine/corecom:Identification/corecom:ID"/>
                           </corecom:ID>
                        </corecom:Identification>
                     </ford:FulfillmentOrderLine>
                  </xsl:for-each>
                  <ford:FulfillmentOrderLine>
                     <corecom:Identification>
                        <corecom:ID>
                           <xsl:value-of select="$CurrentOrderLine/corecom:Identification/corecom:ID"/>
                        </corecom:ID>
                     </corecom:Identification>
                  </ford:FulfillmentOrderLine>
               </xsl:when>
               <xsl:when test="$CurrentOrderLine/corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory != 'SIM'">
                  <ford:FulfillmentOrderLine>
                     <corecom:Identification>
                        <corecom:ID>
                           <xsl:value-of select="$CurrentOrderLine/corecom:Identification/corecom:ID"/>
                        </corecom:ID>
                     </corecom:Identification>
                  </ford:FulfillmentOrderLine>
               </xsl:when>
            </xsl:choose>
         </xsl:for-each>
      </ford:FulfillmentOrderEBO>
   </xsl:template>
</xsl:stylesheet>



corecom:InstalledProductReference/corecom:Custom/corecomcust:SubCategory = 'Telefonia_Plano' and $Line/ford:ServiceActionCode = 'ADD' AND (corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Locked In Progress' or corecom:InstalledProductReference/corecom:Custom/corecomcust:ActionStatus = 'Pending')
