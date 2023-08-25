CreateEventV2

Service Description
===================

*The CreateEvent V2 service is part of the integration flow Customer
Events Retrieval. This is a service for creating ICOMS events. Accepts
all the required fields from the consumer and invokes basic services.
Sends an Error or successful response back to
consumer.

### CreateEvent

### SOAP Headers


  Activity Name    (string)
  
  msgType     (RequestMessageType)
  
  senderURI      (string)
  
  OriginatorURI      (string)
  
  replyToURI        (string)
  
  failureToURI       (string)
  
  Userid           (string)
  
  security           (string)
  
  securityType      (string)
  
  RequestTimestamp     (dateTime)
  
  CommunicationPattern  (string)
  
  CommunicationStyle   (string)
  
  Service             (string)
  
  Version            (string)
  
  BusinessID           (string)
  
  ConversationID       (string)
  
  RequestID           (string)
  
  MessageID           (string)

  ### SOAP BODY

 
  CreateEventRequestCpixType.accountIdentification.siteReference  - A unique service address identifier may only be unique with the combination of service address and site Refrence, Site Reference can be used to describe sysytem and or system instance identifier. Example Value:26

  CreateEventRequestCpixType.accountIdentification.accountNumber -  A unique service address identifier may only be unique with the combination of accountNumber and site Refrence, Account number is a unique identifier representing the customer account . Example Value:104118503

  CreateEventRequestCpixType.event.eventSourceCode          -       This is event source code representing the source of the event.Example Value: NSC,TOC-PROV

  CreateEventRequestCpixType.event.eventTypeCode            -       This is Event Type Code which represents the event specification(type).Example Value: TELESTO, IMPORT

  CreateEventRequestCpixType.event.eventExternalGrouping    -       This is external grouping for an event type.

  CreateEventRequestCpixType.event.eventPatternRecieved      -      This is event pattern received.

  CreateEventRequestCpixType.event.eventData            -           This is event data payload.

  CreateEventRequestCpixType.eventTarget.orderReference      -      ICOMS Work Order Number

  CreateEventRequestCpixType.eventTarget.serviceCategoryCode    -   Service Category Code represents the ICOMS service category which for residential customers tend to be D for High Speed Data(generally broadband), T for Telephony and C for Television.Sample Value-D

  CreateEventRequestCpixType.eventTarget.serviceOccurance      -    Service Occurency

  CreateEventRequestCpixType.eventTarget.serviceCode        -       Service Code, the ICOMS billing code.Sample value:SPOTPRE

  CreateEventRequestCpixType.eventTarget.permiseID          -       ICOMS Premise ID

  CreateEventRequestCpixType.eventTarget.bufferEvent         -      Used to indicate(in ICOMS) that the event can be buffered.NOTE: ICOM default is “YES”. If Event should not be buffered set to “FALSE”

  ### ERROR RESPONSE

  
SYSTEM - 2020 - CRITICAL - Unexpected Error

BUSINESS - 10008 - ERROR - Field Validation Error

SYSTEM - 10003 - CRITICAL - ICOMS - Backend Authentication Error

BUSINESS - 10465 - ERROR - ICOMS - ICOMS Business Exception

SYSTEM - 10466 - CRITICAL - ICOMS - ICOMS System Exception



                                                                   
