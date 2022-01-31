---
title: ITK3 Response Codes
keywords: explore Reference
tags: [explore,fhir,error codes]
sidebar: overview_sidebar
permalink: explore_response_codes.html
summary: "Response codes for ITK3 messaging"
---



## Response Code Types ##  
 
There will be two types of response codes:
- Positive Response codes
- Negative Response codes

**Note:** All Negative response codes are deemed to be fatal and no further processing will be carried out on the message. There will be no further response message following the response message that contains the negative response code regardless of what acknowledgement flags are set. 

## The ITK3 Response Codes ##

The ITK3 Response Codes have three prefixes. The codes are returned in response to the handling specification acknowledgement flags in the header of the incoming message. The validation of the incoming message may vary from system to system however the following rules apply to the codes:

**InfAckRequested=true**

- Prefix 1 and 2 (10001 to 20014) should be returned

**BusAckRequested=true**

- Prefix 3 (30001 to 30004) must be returned

<table style="width:100%;max-width: 100%;">
<tr>
<th>Response Code</th>
<th>Type of Response</th>
<th>Display Name</th>
<th>Description</th>
</tr>
<tr>
<td>10001</td>
<td>Negative</td>
<td>Handling Specification Error</td>	
<td>A generic error code which gives a minimum level of assurance that systems can share the minimum information relating to Handling Specification faults.</td>
</tr>
<tr>
<td>10002</td>
<td>Negative</td>
<td>Infrastructure Level Response Value - Processing Error</td>
<td>The handling specification for infrastructure level response is present but cannot be processed. For example, may be unreadable or contain an incorrect value.</td>
</tr>
<tr>
<td>10003</td>
<td>Negative</td>
<td>Business Level Response Value - Processing Error</td>
<td>The handling specification for Business level response is present but cannot be processed. For example, may be unreadable or contain an incorrect value.</td>
</tr>
<tr>
<td>10004</td>
<td>Negative</td>
<td>Message Definition Value – Processing Error</td>	
<td>The handling specification for Message Definition is present but cannot be processed. For example, may be unreadable or contain an incorrect value. This may also be returned when the message type is not supported (known) by the receiving system.</td>
</tr>
<tr>
<td>10005</td>
<td>Negative</td>
<td>Message Definition Version Value – Processing Error</td>	
<td>The handling specification for Message Definition is present but the version is not supported by the receiving system.</td>
</tr>
<tr>
<td>10007</td>
<td>Negative</td>
<td>Sender Reference Value - Processing Error</td>
<td>The handling specification for Sender Reference is present but cannot be processed. For example, may be unreadable, contain an incorrect value or the use of Sender Reference is not supported by receiving system.</td>
</tr>
<tr>
<td>10008</td>
<td>Negative</td>
<td>Handling Specification Business Rule Error</td>
<td>The Handling Specification usage does not match business rules for included Payload. For example, an acknowledgement flag defined as mandatory to contain the value "true" by the Payload specification contains the value "false".</td>
</tr>
<tr>
<td>10009</td>
<td>Negative</td>
<td>Unreadable message received</td>	
<td>A message has been received that is either corrupted or malformed and cannot be read by the receiving system.</td>
</tr>
<tr>
<td>10010</td>
<td>Negative</td>
<td>Recipient Type - Processing Error</td>	
<td>The handling specification for Recipient Type is present but cannot be processed. For example, may be unreadable or contain an incorrect value.</td>
</tr>
<tr>
<td>20001</td>
<td>Negative</td>
<td>Unrecognised Recipient Person</td>	
<td>The person referred to as the recipient in the ITK3 MessageHeader is not recognised.</td>
</tr>
<tr>
<td>20002</td>
<td>Negative</td>
<td>Unrecognised Recipient Organisation</td>	
<td>The organization referred to as the recipient in the ITK3 MessageHeader is not recognised.</td>
</tr>
<tr>
<td>20003</td>
<td>Negative</td>
<td>Unrecognised Sender</td>
<td>The organization or person referred to as the sender in the ITK3 MessageHeader is not recognised. Note: This code should not be used where the domain makes use of the “GP look-up” functionality in MESH.</td>
</tr>
<tr>
<td>20004</td>
<td>Negative</td>
<td>Non-Approved file type received as an attachment</td>	
<td>The Receiving system has received an attached file whose file type is not approved for the business domain.</td>
</tr>
<tr> 
<td>20005</td>
<td>Negative</td>
<td>Unsupported file type received as an attachment</td> 	
<td>The Receiving system has received an attached file which it does not support.</td>
</tr>
<tr>
<td>20006</td>
<td>Negative</td>
<td>ITK3 Header validation failure</td>	
<td>The ITK3 Header resources or elements are not correct or understandable. For example, ITK3 Bundle or ITK3 MessageHeader.</td>
</tr>
<tr>
<td>20007</td>
<td>Negative</td>
<td>Duplicate Message received</td>
<td>Bundle with this message identifier has already been processed. A Payload with this ITK3 MessageHeader identifier has already been received and processed by this recipient.</td>
</tr>
<tr>
<td>20008</td>
<td>Negative</td>	
<td>Duplicate Document received</td>	
<td>Bundle with this document identifier has already been processed. A Payload with this document identifier has already been received and processed by this recipient.</td>
</tr>
<tr>
<td>20009</td>
<td>Negative</td>
<td>Payload validation failure</td>
<td>Payload content validation has failed.</td>
</tr>
<tr>
<td>20010</td>
<td>Negative</td>
<td>Unrecognised Payload Recipient Organisation</td>	
<td>The Recipient Organisation identified in the Payload, is not supported by this End Point (Receiving System).</td>
<tr>
</tr>
<td>20011</td>
<td>Negative</td>
<td>Unrecognised Payload Recipient Person</td>	
<td>The Recipient person identified in the Payload, is not supported by this End Point (Receiving System).</td>
</tr>
<tr>
<td>20012</td>
<td>Negative</td>
<td>Unauthorised Sender</td>	
<td>The Receiving system identified in the Payload is configured to reject messages from unauthorised senders. This code should not be used where the domain makes use of the “GP look-up” functionality in MESH.</td>
</tr>
<tr>
<td>20013</td>
<td>Positive</td>
<td>Success</td>	
<td>The Message has been processed successfully at the infrastructure level. A response will be returned stating the fact. However, the message may still fail after further processing and result in another response if the business acknowledgement request flag has been sent to “true”.</td>
</tr>
<tr>
<td>20014</td>
<td>Negative</td>
<td>Unable to Process Replacement Document</td>
<td>A replacement document was received, but the receiver could not process the new document correctly and has therefore marked the new and original documents as "bad" on its system.</td>	
</tr>
<tr>
<td>20015</td>
<td>Negative</td>
<td>Message too large</td>
<td>Payload is too large to be processed normally by the recipient system and has been rejected to avoid potential for manual intervention and subsequent loss of automated response codes.  The recommended maximum size limit is 5MB.</td>	
</tr>
<tr>
<td>30001</td>
<td>Positive</td>
<td>Patient known here. (e.g. Patient is registered here)</td>
<td></td>	
</tr>
<tr>
<td>30002</td>
<td>Negative</td>	
<td>Patient not known here. (aka ‘patient record not present in system’)</td>
<td></td>
</tr>
<tr>
<td>30003</td>
<td>Negative</td>	
<td>Patient no longer at this clinical setting</td>
<td></td>
</tr>
<tr>
<td>30004</td>
<td>Positive</td>
<td>Patient known here and recently deceased (i.e. patient record current in GP practice system at time of patient’s death and deduction subsequently occurred for this reason)</td>
<td>This response is only applicable for a window of less than 6-months and would start at Date of Death of Patient (or Date of Deduction when reason for this is patient’s death). If an ITK3 payload message is then received at 6 months or beyond, then the response code would revert to a 30003.</td>	
</tr>
<tr>
<td>30005</td>
<td>Positive</td>
<td>Referral open</td>
<td>Referral open.</td>	
</tr>
<tr>
<td>30006</td>
<td>Positive</td>
<td>Referral completed</td>
<td>Referral completed.</td>	
</tr>
<tr>
<td>30007</td>
<td>Negative</td>
<td>Referral escalated back to GP</td>
<td>Referral escalated back to GP.</td>	
</tr>
<tr>
<td>30008</td>
<td>Positive</td>
<td>Signposting to GP (non-urgent)</td>
<td>Patient signposted back to GP. Not a clinically urgent issue.</td>	
</tr>
<tr>
<td>30009</td>
<td>Positive</td>
<td>Clinical escalation to 111/GPOOH</td>
<td>Clinical escalation to 111, UTC or GP Out of Hours once consultation has completed.</td>	
</tr>
<tr>
<td>30010</td>
<td>Positive</td>
<td>Clinical escalation to UTC/A&E or 999</td>
<td>Clinical escalation to 999 or A&E once consultation has completed.</td>	
</tr>
<tr>
<td>30011</td>
<td>Positive</td>
<td>Advised to go elsewhere/self-referral</td>
<td>Patient advised to go elsewhere once consultation has completed.</td>	
</tr>
<tr>
<td>30012</td>
<td>Negative</td>
<td>Unable to contact the patient</td>
<td>Attempted to contact the patient at least three times unsuccessfully.</td>	
</tr>
<tr>
<td>30013</td>
<td>Positive</td>
<td>Closure (service not needed)</td>
<td>Patient advises that the service is no longer needed.</td>	
</tr>
<tr>
<td>30014</td>
<td>Negative</td>
<td>Closure (service not accepted)</td>
<td>Patient does not accept the service being offered.</td>	
</tr>
<tr>
<td>30015</td>
<td>Negative</td>
<td>Closure (duplicate referral)</td>
<td>Duplicate referral.</td>	
</tr>
<tr>
<td>30016</td>
<td>Positive</td>
<td>Referral accepted</td>
<td>Referral accepted.</td>	
</tr>
<tr>
<td>30017</td>
<td>Negative</td>
<td>Referral rejected</td>
<td>Referral rejected.</td>	
</tr>
<tr>
<td>30018</td>
<td>Negative</td>
<td>Did Not Attend</td>
<td>Patient failed to attend the appointment/answer the call.</td>	
</tr>
<tr>
<td>30019</td>
<td>Positive</td>
<td>GP Registration - Application accepted</td>
<td>The registration has been accepted by the GP practice.</td>	
</tr>
<tr>
<td>30020</td>
<td>Negative</td>
<td>GP Registration - Application pending (contact practice)</td>
<td>The registration has not been accepted. The patient needs to contact the GP practice.</td>	
</tr>
<tr>
<td>30021</td>
<td>Negative</td>
<td>GP Registration - Application rejected (patient already registered)</td>
<td>The registration has not been accepted. The patient is already registered at the practice.</td>	
</tr>
<tr>
<td>30022</td>
<td>Negative</td>
<td>GP Registration - Application rejected (at capacity)</td>
<td>The registration has not been accepted. The practice is at capacity and is not currently taking any new registrations.</td>	
</tr>
<tr>
<td>30023</td>
<td>Negative</td>
<td>GP Registration - Application rejected (out of boundary)</td>
<td>The registration has not been accepted. The patient is out of boundary.</td>	
</tr>
<tr>
<td>30024</td>
<td>Negative</td>
<td>GP Registration - Application rejected (Previously removed from this practice)</td>
<td>The registration has not been accepted. The patient has previously been removed from this practice.</td>	
</tr>
<tr>
<td>30025</td>
<td>Negative</td>
<td>GP Registration - Application rejected (Previously removed from another practice)</td>
<td>The registration has not been accepted. The patient has previously been removed from another practice.</td>	
</tr>
</table>	


