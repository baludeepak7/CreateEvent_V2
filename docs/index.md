**CreateEvent\_V2**

Revision: 1

Middleware Service Specification

Author: **Peter Winnick**

peter.winnick@virginmedia.co.uk

Date: **04/07/16**

Document Version: **1.0**

Status: **Issued**

Document Purpose

The Service Specification document is a subjective document which
describes the interface, operations and implementation of a single
service.

It is produced by the Middleware Solution Designer and is the key input
to the Middleware Development Team.

It also serves the purpose of an as-built reference to describe the
production service and, as such, forms part of the SOA development
deliverables. Every service that is delivered to the SOA platform must
have an accompanying Service Specification which describes the service.

There must at all times be a base-lined version of each Service
Specification which is aligned with the latest production version of the
physical service.

There may also be one or (in the case of parallel development) more
working copies of a Service Specification which have been created as
part of an overall Solution Design for an objective purpose such as a
project. As new versions of a service are delivered to production the
relevant Service Specification would then become the base-lined version
and replace the previous version.

Table of Contents {#table-of-contents .Heading1NC}
=================

1.  Document Control
    ================

    1.  Document Information
        --------------------

  ------------------------------ ----------------------------------------------------
  **Title**                      CreateEvent\_V2 (Middleware Service Specification)
  **Author / (Last saved by)**   Peter Winnick / (Winnick, Peter)
  **Status**                     Issued
  ------------------------------ ----------------------------------------------------

Document History
----------------

  ------------- ------------------------------------------------------------- --------------- ------------------
  **Version**   **Description / Change Comments**                             **Who**         **Date**

  0.1           Initial draft                                                 Peter Winnick   22^nd^ Jul 2015
                                                                                              
                CreateEvent\_V2                                                               
                                                                                              
                Same payload as V1, but restructured for new Fusion service                   

  0.2           Minor updates                                                 Peter Winnick   28^th^ Jul 2015
                                                                                              
                Set business exceptions to ERROR in Mapping sheet                             
                                                                                              
                Updated Business Process diagram                                              
                                                                                              
                Fixed order of attributes in sample requests                                  

  0.3           Added missing ICOMS System Exception (10466)                  Peter Winnick   27^th^ May 2016

  1.0           Fixed Error Category for Error 10003                          Peter Winnick   04^th^ July 2016
                                                                                              
                Raised to Issue 1.0                                                           
  ------------- ------------------------------------------------------------- --------------- ------------------

SOA Governance Approval
-----------------------

***The SOA Governance Authority is required to sign off this service
specification, and ensure that it adheres to SOA standards, before any
further sign off can be sought.***

  ------------ ------------------------ --------------------
  **Name**     **Title / Department**   **Approval (Y/N)**
  Steve King   SOA Governance           
  ------------ ------------------------ --------------------

Where the reviewer is not approving the document explain what changes
are needed.

For Review By
-------------

  ------------------ --------------------------------- --------------------
  **Name**           **Title / Department**            **Approval (Y/N)**
  Steve King         Middleware Solution Design Lead   
  Arpit Shah         Middleware Development Lead       
  Steve King         SOA Governance Representative     
  David Mortimer     Middleware Lead Developer         
  Andrew Zielinski   Middleware Support                
  ------------------ --------------------------------- --------------------

Where the reviewer is not approving the document explain what changes
are needed.

Distribution
------------

Distribution is to the reviewer list above plus the following:

  ---------- ------------------------
  **Name**   **Title / Department**
             
  ---------- ------------------------

References
----------

  ------------------------- -------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Reference**             **Document**                     **Link / Path**
  []{#Ref01 .anchor}Ref01   SOA Principles and Policies      [*SOA Principles and Policies*](http://sharepoint/sites/support/Technology/devsupport/solutiondesign/CCMSD/SOA/Standards/Governance/SOA Principles and Policies.doc)
  []{#Ref02 .anchor}Ref02   SOA Integration Architecture     &lt;David Mortimer&gt;
  Ref03                     SOA Blueprint                    [*SOA Blueprint*](http://sharepoint/sites/support/Technology/devsupport/solutiondesign/CCMSD/SOA/Standards/Governance/SOA Solution Blueprint.doc)
  []{#Ref03 .anchor}Ref04   Master Service Error Code List   [*Master Error List*](http://sharepoint/sites/support/Technology/devsupport/solutiondesign/CCMSD/SOA/Development/Master Service Error Code List.xls)
  ------------------------- -------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------

***Reference any documents that are referred to within this document or
linked to it, including the version number and where the document can be
found. This list shall include all input documents used in its
generation, such as the High Level Design, Detailed Business
Requirements and Detailed Solution Design.***

Contributors to this document
-----------------------------

The following people provided input into this document.

  ------------ --------------------
  **Name**     **Role / Company**
  Steve King   
  ------------ --------------------

Glossary
--------

  ----------- -------------------------------------
  **Term **   **Description**
  Shall       Mandatory
  Should      Highly desirable, but not mandatory
  ----------- -------------------------------------

1.  Introduction
    ============

    1.  Document Purpose
        ----------------

The Service Specification document is a subjective document which
describes the interface, operations and implementation of a single
service.

It also serves the purpose of an as-built reference to describe the
production service and, as such, forms part of the SOA development
deliverables. Every service that is delivered to the SOA platform must
have an accompanying Service Specification which describes the service.

Audience
--------

This document is created for the following audience:

-   Governance Team

-   Design Team

-   Development Team

-   Testing Team

-   Support Team

\
 {#section .ListParagraph}
=

Integration Flow
================

The CreateEvent\_V2 service is part of the integration flow Customer
Events Retrieval. Please refer to the SOA Blueprint document \[Ref04\]
for details of the flow.

\
 {#section-1 .ListParagraph}
=

1.  Service Specification
    =====================

    1.  Service Overview
        ----------------

        1.  ### Function(s)

  -------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Operation Name**   **Function(s)**                                                                                                                                                                     **Limitations**

  CreateEvent          This is a service for creating ICOMS events. Accepts all the required fields from the consumer and invokes basic services. Sends an Error or successful response back to consumer   Whilst discussing the interface with Convergys it was recommended that we do NOT expose the Event Priority attribute but to allow ICOMS to set the priority based on configuration for the event. The priority will be set ‘virtually as soon as the event is created in the queue’.
                                                                                                                                                                                                           
                                                                                                                                                                                                           In addition Convergys stated that we should not expose the Buffer Event via the service and simply allow it to take the default.
                                                                                                                                                                                                           
                                                                                                                                                                                                           However we have a new requirement to expose the Buffer Event, and not always take the default of "YES”
  -------------------- ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Other Details

  -------------------- ------------------------------------------------------------------------------------------------------------- ---------------------- ------------------------------------ ----------------
                                                                                                                                     **Dependencies**       

  **Operation Name**   **Operation Type**                                                                                            **Back end systems**   **Other VM SOA platform services**
                                                                                                                                                            
                       (Basic, Composed, Process)                                                                                                           
                                                                                                                                                            
                       See [*http://kn-soldes-v1/index.php?title=Service\_Type*](http://kn-soldes-v1/index.php?title=Service_Type)                          

  CreateEvent          Basic                                                                                                         ICOMS – AS/400         None
  -------------------- ------------------------------------------------------------------------------------------------------------- ---------------------- ------------------------------------ ----------------

### Service Interface Definition

The WSDL file and any imported XSD files should exist at the following
Sharepoint location:

[*http://kn2-spt-p0002:35606/DEPT/VM/DevMan/SOA/WSDLs%20and%20XSDs/Forms/AllItems.aspx*](http://sharepoint/sites/support/Technology/devsupport/solutiondesign/CCMSD/SOA/WSDLs and XSDs/Forms/AllItems.aspx)

-   CreatEvent\_V2.wsdl

-   CreatEvent\_V2.xsd

-   RequestHeader.2.0.xsd

-   ResponseHeader.3.0.xsd

The following policies must be adhered to:

[*http://kn-soldes-v1/index.php?title=WSDL\_Design\_Policy*](http://kn-soldes-v1/index.php?title=WSDL_Design_Policy)

[*http://kn-soldes-v1/index.php?title=XML\_Schema\_Design\_Policy*](http://kn-soldes-v1/index.php?title=XML_Schema_Design_Policy)

[*http://kn-soldes-v1/index.php?title=XML\_Schema\_Component\_Naming\_Policy*](http://kn-soldes-v1/index.php?title=XML_Schema_Component_Naming_Policy)

[*http://kn-soldes-v1/index.php?title=WSDL\_and\_XSD\_Versioning\_Policy*](http://kn-soldes-v1/index.php?title=WSDL_and_XSD_Versioning_Policy)

### Revision History

*This section tracks each revision of the service. This is different to
the document version number which may be incremented many times during
design and review stages for a particular service revision. The
intention of the section is to clearly document the delta between
revisions of the same service. This will only be used where the service
has been extended in a backward compatible way.*

There must at all times be a base-lined reversion of each Service
Specification which is aligned with the latest production version of the
physical service.

There may also be one or (in the case of parallel development) more
working copies of a Service Specification Versions and Revisions which
have been created as part of an overall Solution Design for an objective
purpose such as a project. As new versions and revisions of a service
are delivered to production the relevant Service Specification would
then become the base-lined version and replace the previous version.

  -------------- ---------------------- --------------------------------------------------------------------------------------------------------------------------
  **Revision**   **Purpose**            **Description of Changes**
  1              { Initial revision }   The CreateEvent\_V2 service has the same interface attributes as CreateEvent, but restructured for a new Fusion service.
  -------------- ---------------------- --------------------------------------------------------------------------------------------------------------------------

1.  Operations
    ----------

    1.  ### CreateEvent

        1.  #### Business Process

The following diagram highlights the business logic associated with the
CreateEvent operation.

![](media/image3.png){width="6.445833333333334in"
height="1.867361111111111in"}

1.  #### Request

    1.  ##### SOAP Header 

![](media/image4.png){width="1.6548611111111111in"
height="8.684722222222222in"}

##### SOAP Body 

![](media/image5.png){width="4.440277777777778in"
height="9.131944444444445in"}

1.  #### Response

    1.  ##### SOAP Header 

![](media/image6.png){width="1.7173611111111111in"
height="8.413194444444445in"}

##### SOAP Body 

![](media/image7.png){width="6.197916666666667in"
height="2.5833333333333335in"}

Fault

![](media/image8.png){width="3.1020833333333333in"
height="7.754861111111111in"}

NOTE: there are no conditions where a fault is returned for a Success
response.

#### Validation Rules

In addition to the schema validation, the following additional
validation shall be performed on the CreateEventRequest which if results
in a failure will result in a fault message returned in the SOAP header.

CreateEventRequest.accountIdentification.siteReference shall be
validated as having a length of 2 characters which contain ONLY numeric
data.

CreateEventRequest. accountIdentification.accountNumber shall be
validated as having a length between 3 and 9 characters which contain
ONLY numeric data.

CreateEventRequest.eventTarget.premiseID shall be validated as having a
length between 1 and 7 characters which contain ONLY numeric data.

#### Errors

{{Document the errors that the operation can throw. Consult the Error
Codes Usage Policy
([*http://kn-soldes-v1/index.php?title=Error\_Codes\_Usage\_Policy*](http://kn-soldes-v1/index.php?title=Error_Codes_Usage_Policy))
for guidance.

All SOA errors can be found in the SOA Master Error List \[Ref04\]. The
following is the errors that are initiated by this service:

  ---------- ---------- -------------- ------------------ ------------------------------
  **type**   **Code**   **Severity**   **sourceSystem**   **Description**
  System     2020       CRITICAL                          Unexpected Error
  Business   10008      ERROR                             Field Validation Error
  System     10003      CRITICAL       ICOMS              Backend Authentication Error
  Business   10465      ERROR          ICOMS              ICOMS Business Exception
  System     10466      CRITICAL       ICOMS              ICOMS System Exception
  ---------- ---------- -------------- ------------------ ------------------------------

1.  ### Sample Test Cases

    1.  #### Test Case 1 – Invoke ‘CreateEvent’ service with correct details

####  {#section-2 .ListParagraph}

##### Purpose of Test

The purpose of the test is to request a new ICOMS event to be created
for the supplied request details.

1.  ##### Request

2.  ##### Expected Response

<!-- -->

1.  #### Test Case 2 – Invoke ‘CreateEvent’ service with invalid premiseID field length 

    1.  ##### Purpose of Test

The purpose of the test is to ensure the validation of the premiseID
field is performed and appropriate error is returned.

1.  ##### Request

2.  ##### Expected Response

#### Test Case 3 – Invoke ‘CreateEvent’ service but ICOMS returns Non zero inline return code.with invalid premiseID field length

####  {#section-3 .ListParagraph}

####  {#section-4 .ListParagraph}

##### Purpose of Test

The purpose of the test is to ensure that the appropriate fault is
returned when ICOMS responds with a non successful inline return code.

1.  ##### Request

2.  ##### Expected Response

<!-- -->

1.  Technical Specification
    =======================

    1.  Operations
        ----------

        1.  ### CreateEvent

            1.  #### Technical Process

![](media/image15.png){width="6.449305555555555in"
height="6.069444444444445in"}

*Validate Message Request Object*

Using the CreateEventRequest, perform the validation described in
“Validation Rules” section above.

For any validation issues, build a failure response using the data
mapping sheet To Response 10008

Operation returns to calling client.

*Prepare and Execute MAC183.INL1374 *

Prepare the MAC183/INL1374 request as described in the Data Mapping
Sheet as described below and execute

If create event request was NOT completed successfully
(MAC00183.0INL1374.INLNRTRNCODE &lt;&gt; 0) then

IF RC &gt; 0 then

*Build ICOMS Business Exception*

> Build a failure response using data mapping sheet ‘To Response 10465’
>
> Operation returns to calling client.

IF RC &lt;0 then

*Build ICOMS System Exception*

> Build a failure response using data mapping sheet ‘To Response 10466
>
> Operation returns to calling client.
>
> Except IF RC = -10050
>
> *Build ICOMS System Exception*
>
> Build a failure response using data mapping sheet ‘To Response 10003
>
> Operation returns to calling client.

If ICOMS Create Event completed was completed successfully then

*Build success response using data mapping sheet Reponse SUCCESS*

Data Mapping Sheet
------------------

[]{#_1526195663 .anchor}

1.  Non-functional requirements
    ===========================

    1.  Security Requirements
        ---------------------

No security requirements have been identified.

Configuration Requirements
--------------------------

No configurations requirements have been identified.

Performance and Capacity Planning Requirements
----------------------------------------------

 {#section-5 .ListParagraph}

The service should be developed to allow the following theoretical loads
but these do not represent the actual expect of usage per consumer.

-   Number of invocations per hour: 100,000

-   Expected peak concurrent service invocations: 60

-   95^th^ Percentile Response Time: 1.0 second.

Troubleshooting
===============

{{Define the possible errors that could occur with a description of
their cause, resolution and how to monitor for the error. As a minimum
this should capture the critical errors which would render the service
unavailable. }}

  ----------------------------------------- --------------------------------------- ------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------
  **Symptom**                               **Cause**                               **Resolution**                                                                                                **Monitoring Method**
  Operation is returning error code 10003   Backend Authentication Error.           Problem with user credentials. Check user and password are correct in request.                                Watch the service log file for any instance of error code 10003.
  Operation is returning error code 10008   Invalid data causing validation error   Likely to be a business error or use of service. Look at logs to determine source and passed data elements.   Watch the service log file for any instance of error code 10008.
  Operation is returning error code 10465   ICOMS Business Exception                Likely to be a business error or use of service. Look at logs to determine source and passed data elements.   Watch the service log file for any instance of error code 10465
  Operation is returning error code 10466   ICOMS System Exception                  ICOMS is returning a System Exception. Look at logs to determine source and poosible issue.                   Watch the service log file for any instance of error code 10466
  ----------------------------------------- --------------------------------------- ------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------
