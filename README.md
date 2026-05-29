eu tenho esse scope que eu criei:

<scope name="Scope31">
                                             <faultHandlers>
                                                <catchAll>
                                                   <if name="If_Portabilidade"
                                                       xmlns="http://docs.oasis-open.org/wsbpel/2.0/process/executable">
      <documentation>
         
      <![CDATA[Portabilidade]]></documentation>
      <condition>$inputVariable.ProcessSoftwareFulfillmentOrderEBM/ford:DataArea/ford:ProcessSoftwareFulfillmentOrder/ford:Custom/fordcust:SubTypeCode = "Telefonia Portabilidade"</condition>
      
      <sequence>
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
                                                         <invoke name="InvokeUpdateFulfillmentOrderMobileError"
                                                                 bpelx:invokeAsDetail="no"
                                                                 partnerLink="CommunicationsFulfillmentOrder"
                                                                 portType="ns20:CommunicationsFulfillmentOrderEBS"
                                                                 operation="UpdateFulfillmentOrderSynchronously"
                                                                 inputVariable="InvokeUpdateFulfillmentOrderMobileError_UpdateFulfillmentOrderSynchronously_InputVariable"
                                                                 outputVariable="InvokeUpdateFulfillmentOrderMobileError_UpdateFulfillmentOrderSynchronously_OutputVariable"
                                                                 xmlns:bpelx="http://schemas.oracle.com/bpel/extension"/>
                                                      </sequence>
   </if>
                                                </catchAll>
                                             </faultHandlers>
                                             <invoke name="InvokeMobileService_createOrder" bpelx:invokeAsDetail="no"
                                                     partnerLink="MobileService" portType="ns74:MobileService_ptt"
                                                     operation="createorder"
                                                     inputVariable="InvokeMobileService_createOrder_createorder_InputVariable"
                                                     outputVariable="InvokeMobileService_createOrder_createorder_OutputVariable"/>
                                          </scope>
										  
										  
										  
										  
mas alem disso eu tenho esse fault policies:


<faultPolicies xmlns="http://schemas.oracle.com/bpel/faultpolicy" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
   <faultPolicy version="2.1.3" id="ConnectionFaults">
      <Conditions>
         <faultName xmlns:bpelx="http://schemas.oracle.com/bpel/extension" name="bpelx:remoteFault">
            <condition>
               <action ref="java-fault-handler"/>
            </condition>
         </faultName>
      </Conditions>
      <Actions>
         <Action id="sky-default-retry-hi">
            <retry>
               <retryCount>7</retryCount>
               <retryInterval>60</retryInterval>
               <exponentialBackoff/>
               <retryFailureAction ref="ora-human-intervention"/>
            </retry>
         </Action>
         <Action id="ora-retry">
            <retry>
               <retryCount>7</retryCount>
               <retryInterval>60</retryInterval>
               <exponentialBackoff/>
               <retryFailureAction ref="aia-ora-java"/>
               <retrySuccessAction ref="aia-ora-java"/>
            </retry>
         </Action>
         <Action id="aia-ora-retry">
            <retry>
               <retryCount>7</retryCount>
               <retryInterval>60</retryInterval>
               <exponentialBackoff/>
               <retryFailureAction ref="aia-ora-java"/>
               <retrySuccessAction ref="aia-ora-java"/>
            </retry>
         </Action>
         <Action id="ora-replay-scope">
            <replayScope/>
         </Action>
         <Action id="ora-rethrow-fault">
            <rethrowFault/>
         </Action>
         <Action id="ora-human-intervention">
            <humanIntervention/>
         </Action>
         <Action id="ora-terminate">
            <abort/>
         </Action>
         <Action id="aia-ora-java">
            <javaAction className="oracle.apps.aia.core.eh.CompositeJavaAction" defaultAction="ora-rethrow-fault">
               <returnValue value="REPLAY" ref="ora-terminate"/>
               <returnValue value="RETHROW" ref="ora-rethrow-fault"/>
               <returnValue value="ABORT" ref="ora-terminate"/>
               <returnValue value="RETRY" ref="aia-ora-retry"/>
               <returnValue value="MANUAL" ref="ora-human-intervention"/>
            </javaAction>
         </Action>
         <Action id="aia-no-action">
            <javaAction className="oracle.apps.aia.core.eh.CompositeJavaNoAction" defaultAction="ora-rethrow-fault">
               <returnValue value="REPLAY" ref="ora-terminate"/>
               <returnValue value="RETHROW" ref="ora-rethrow-fault"/>
               <returnValue value="ABORT" ref="ora-terminate"/>
               <returnValue value="RETRY" ref="aia-ora-retry"/>
               <returnValue value="MANUAL" ref="ora-human-intervention"/>
            </javaAction>
         </Action>
         <Action id="java-fault-handler">
            <javaAction className="br.com.sky.faultpolicy.CustomFaultHandler" defaultAction="sky-default-retry-hi" propertySet="properties">
               <returnValue value="RETRY" ref="ora-retry-custom"/>
               <returnValue value="NOTFOUND" ref="sky-default-retry-hi"/>
               <returnValue value="RECOVER" ref="ora-human-intervention"/>
               <returnValue value="TERMINATE" ref="ora-terminate"/>
            </javaAction>
         </Action>
         <Action id="java-fault-handler-recover">
            <javaAction className="br.com.sky.faultpolicy.CustomFaultHandler" defaultAction="sky-default-retry-hi" propertySet="properties-recover">
               <returnValue value="RECOVER" ref="ora-human-intervention"/>
               <returnValue value="TERMINATE" ref="ora-terminate"/>
            </javaAction>
         </Action>
         <Action id="ora-retry-custom">
            <retry>
               <retryCount>7</retryCount>
               <retryInterval>60</retryInterval>
               <exponentialBackoff/>
               <retryFailureAction ref="java-fault-handler-recover"/>
               <retrySuccessAction ref="ora-terminate"/>
            </retry>
         </Action>
      </Actions>
      <Properties>
         <propertySet name="properties">
            <property name="level">retry</property>
            <property name="partNamePayload">ProcessSoftwareFulfillmentOrderEBM</property>
            <property name="tagOrderNumberPayload">//ProcessSoftwareFulfillmentOrderEBM/DataArea/ProcessSoftwareFulfillmentOrder/Identification/ID</property>
            <property name="tagOrderTypePayload">//ProcessSoftwareFulfillmentOrderEBM/DataArea/ProcessSoftwareFulfillmentOrder/Custom/OrderType</property>
            <property name="tagOrderSubTypePayload">//ProcessSoftwareFulfillmentOrderEBM/DataArea/ProcessSoftwareFulfillmentOrder/Custom/SubTypeCode</property>
            <property name="partNameFaultCode">detail</property>
            <property name="tagFaultCode">//ArchFaultDetails/errorCode</property>
            <property name="partNameFaultDetail">detail</property>
            <property name="tagFaultDetail">//ArchFaultDetails/FaultDetails/faultBody/Body/Fault/faultstring**//ArchFaultDetails/errorDetails/Body/CreatePaymentTermSynchronouslyResponseEBM/EBMHeader/Custom/ResponseHeader/returnMessage**//ArchFaultDetails/Fault/fault/fault/reason**//detail</property>
            <property name="partNameFaultCodeSiebel">detail</property>
            <property name="tagFaultCodeSiebel">//ArchFaultDetails/errorDetails/detail/siebdetail/errorstack/error/errorcode</property>
            <property name="partNameFaultDetailSiebel">detail</property>
            <property name="tagFaultDetailSiebel">//ArchFaultDetails/errorDetails/detail/siebdetail/errorstack/error/errormsg</property>
         </propertySet>
         <propertySet name="properties-recover">
            <property name="level">recovery</property>
            <property name="partNamePayload">ProcessSoftwareFulfillmentOrderEBM</property>
            <property name="tagOrderNumberPayload">//ProcessSoftwareFulfillmentOrderEBM/DataArea/ProcessSoftwareFulfillmentOrder/Identification/ID</property>
            <property name="tagOrderTypePayload">//ProcessSoftwareFulfillmentOrderEBM/DataArea/ProcessSoftwareFulfillmentOrder/Custom/OrderType</property>
            <property name="tagOrderSubTypePayload">//ProcessSoftwareFulfillmentOrderEBM/DataArea/ProcessSoftwareFulfillmentOrder/Custom/SubTypeCode</property>
            <property name="partNameFaultCode">detail</property>
            <property name="tagFaultCode">//ArchFaultDetails/errorCode</property>
            <property name="partNameFaultDetail">detail</property>
            <property name="tagFaultDetail">//ArchFaultDetails/FaultDetails/faultBody/Body/Fault/faultstring**//ArchFaultDetails/errorDetails/Body/CreatePaymentTermSynchronouslyResponseEBM/EBMHeader/Custom/ResponseHeader/returnMessage**//ArchFaultDetails/Fault/fault/fault/reason**//detail</property>
            <property name="partNameFaultCodeSiebel">detail</property>
            <property name="tagFaultCodeSiebel">//ArchFaultDetails/errorDetails/detail/siebdetail/errorstack/error/errorcode</property>
            <property name="partNameFaultDetailSiebel">detail</property>
            <property name="tagFaultDetailSiebel">//ArchFaultDetails/errorDetails/detail/siebdetail/errorstack/error/errormsg</property>
         </propertySet>
      </Properties>
   </faultPolicy>
   <faultPolicy version="1.0" id="SKY_SYNC_POLICY" xmlns:env="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.oracle.com/bpel/faultpolicy" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <Conditions>
         <faultName>
            <condition>
               <action ref="sky-default-retry-hi"/>
            </condition>
         </faultName>
      </Conditions>
      <Actions>
         <Action id="sky-default-retry-hi">
            <retry>
               <retryCount>4</retryCount>
               <retryInterval>20</retryInterval>
               <exponentialBackoff>2</exponentialBackoff>
               <retryFailureAction ref="ora-human-intervention"/>
            </retry>
         </Action>
         <Action id="ora-human-intervention">
            <humanIntervention/>
         </Action>
      </Actions>
   </faultPolicy>
   <faultPolicy version="1.0" id="PARTNER_MOBILE_POLICY" xmlns:env="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.oracle.com/bpel/faultpolicy" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <Conditions>
         <faultName>
            <condition>
               <action ref="sky-mobile-retry-hi"/>
            </condition>
         </faultName>
      </Conditions>
      <Actions>
         <Action id="sky-mobile-retry-hi">
            <retry>
               <retryCount>4</retryCount>
               <retryInterval>20</retryInterval>
               <exponentialBackoff>2</exponentialBackoff>
               <retryFailureAction ref="ora-rethrow-fault"/>
            </retry>
         </Action>
         <Action id="ora-rethrow-fault">
            <rethrowFault/>
         </Action>
      </Actions>
   </faultPolicy>
</faultPolicies>


e tenho esse fault binding:
<?xml version='1.0' encoding='UTF-8'?>
<faultPolicyBindings version="3.0" xmlns="http://schemas.oracle.com/bpel/faultpolicy" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
   <composite faultPolicy="ConnectionFaults"/>
   <component faultPolicy="ConnectionFaults">
      <name>ProcessCreateFulfillmentOrderEBFMIPBPEL</name>
      <name>ProcessSoftwareActivationFulfillmentOrderBPEL</name>
      <name>ProcessCommandNewSubscriberProvisioningOrderBPEL</name>
      <name>ProcessCommandCancelSignalProvisioningOrderBPEL</name>
      <name>ProcessCommandProductChangeProvisioningOrderBPEL</name>
      <name>ProcessCommandChangeAddressProvisioningOrderBPEL</name>
      <name>CancelCoreFulfillmentOrderEBFMIPBPEL</name>
      <name>CancelOrderItemFulfillmentOrderEBFMIP</name>
      <name>ProcessHardwareActivationFulfillmentOrderEBFMIP</name>
      <name>ProcessSoftwareFulfillmentOrderBPEL</name>
      <name>ProcessCoreFulfillmentOrderEBFMIPBPEL</name>
      <name>ProcessHardwareFulfillmentOrderEBFMIPBPEL</name>
      <name>ProcessOSEReturnFulfillmentOrderEBFMIPBPEL</name>
      <name>BillCustomer</name>
      <name>PosCreateFulfillmentBPELProcess</name>
      <name>CommunicationsCustomerInteractionBPEL</name>
      <name>CancelCoreFulfillmentOrderAsyncBpelProcess</name>
   </component>
   <reference faultPolicy="PARTNER_MOBILE_POLICY">
      <name>MobileService</name>
   </reference>
</faultPolicyBindings>
