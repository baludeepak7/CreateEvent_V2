CreateEventV2

Service Description
===================

*The CreateEvent V2 service is part of the integration flow Customer
Events Retrieval. This is a service for creating ICOMS events. Accepts
all the required fields from the consumer and invokes basic services.
Sends an Error or successful response back to
consumer.*[[]{#scroll-bookmark-2064 .anchor}]{#_Toc256000916 .anchor}

### CreateEvent

### SOAP Headers

**Header Name**        **Type**
  ---------------------- --------------------
  Activity Name          string
  msgType                RequestMessageType
  senderURI              string
  OriginatorURI          string
  replyToURI             string
  failureToURI           string
  Userid                 string
  security               string
  securityType           string
  RequestTimestamp       dateTime
  CommunicationPattern   string
  CommunicationStyle     string
  Service                string
  Version                string
  BusinessID             string
  ConversationID         string
  RequestID              string
  MessageID              string
