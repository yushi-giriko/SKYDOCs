<xsl:if test="$TelefoniaPlanoItem">
    <ford:FulfillmentOrderLine>
        <corecom:Identification>
            <corecom:ID>
                <xsl:value-of select="$TelefoniaPlanoItem/corecom:Identification/corecom:ID"/>
            </corecom:ID>
        </corecom:Identification>
    </ford:FulfillmentOrderLine>
</xsl:if>
