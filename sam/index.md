---
published: true
layout: default

---
####Updated on October 30, 2015
The SAM team is happy to introduce v4 of the standard API and some updates to the v2 of the Search API.  The updated field references for v4 can be found [here](fields4.html).  We are also announcing that support for v1 and v2 will cease as of this release.  We will continue to support only the latest 2 current versions of the API (v3 and V4).  That being said, v1 and v2 will still be available for use, but we cannot provide resources for ongoing support as we would like to enhance the system for everyone's availablilty and not dwell on outdated versions.  If there are any questions or issues, please visit the [Support and Feedback](https://github.com/GSA/GSA-APIs/issues) to open a ticket.

####Updated on June 26, 2015
The SAM API has a release of v3 of the standard API and release of v2 of the [search](search.html) API.  The updated field references can be found [here](fields3.html).  Another new page which contains a better overview of the changes can be found in our [Versioning](versioning.html) document.

The latest version of our [Data Dictionary](SAM_Functional_Data_Dictionary_v7_Public.pdf) is available for download which will give a deeper look into the SAM system and how it functions.



<h1>Background</h1>
<p>The SAM API is a  RESTful method of retrieving public information about the businesses or  individuals (referred to as &ldquo;entities&rdquo;) within the SAM data set. The entities  publicly available data set can currently be retrieved on an entity-by-entity  basis. The initial SAM API release was introduced in June 2014 and allowed  users of the API to retrieve publicly available entity data. The next iteration  of the API, released in fall 2014, provided the ability to search SAM to find  an entity based on the search criteria submitted.<br />
  In  addition to the entity information, we also provide status and progress  information. This information is also included as part of the front end feature  for the SAM Status Tracker. The status refers to the status of the entity&rsquo;s  registration - whether they are working on their registration, waiting for a  validation from the IRS or the DoD (CAGE), or are active, as an example. The  progress is most relevant for those who are working on their registration; it  indicates whether a user has finished filling out different sections of their  registrations, as well as the progress of their validations with external organizations  such as the IRS or DoD. This should indicate how far along in the process a  user is in completing the work they need to do in order to successful be  registered in SAM.<br />
  Access  to the SAM API is administered through the API.Data.Gov which is an API  management service federal agencies.&nbsp; Consumers  of the SAM data must first register and obtain a key from the site.&nbsp; The key will allow users to access the SAM  APIs.</p>
<h1>SAM getData API</h1>
<p>The SAM getData API has one operation. The  operation will retrieve an entity&rsquo;s public information. Its endpoint is <a href="https://api.data.gov/sam/v1/registrations/">https://api.data.gov/sam/v1/registrations/</a><br />
  Please note: the rate limits for the API are  currently 5,000 calls per 24 hours and 5 calls per 5 seconds. As we go forward  and understand the impact of usage of the API on SAM, we will adjust the limits  accordingly as well as allow for individual users with specific needs to have  customized rate limits appropriate to their use.</p>
<h2>Version 1 (v1)</h2>
<p>The getData v1 SAM API includes:</p>
<ul>
  <li>Added Core Data,  Assertions, and Points of Contact information.&nbsp;  Please note that optional fields that have not been completed by the  registrant are not returned in the API response. </li>
  <ul>
    <li>Fields  from Core Data include:</li>
    <ul>
      <li>activationDate,  businessStartDate, businessTypes, cage, cageRejectionReason, companyDivision,  congressionalDistrict, corporateStructureCode, corporateStructureDescription,  corporateUrl, correspondenceFlag, countryOfIncorporation, creditCardUsage,  divisionNumber, dodaac, doingBusinessAsName, duns, dunsPlus4, expirationDate,  fiscalYearEndCloseDate, hasDelinquentFederalDebt, hasKnownExclusion,  lastUpdateDate, legalBusinessName, mailingAddress, publicDisplay,  purposeOfRegistration, qualifications, registrationDate, samAddress, stateOfIncorporation,  status, statusMessage, submissionDate</li>
    </ul>
    <li>Fields  from Assertions include:</li>
    <ul>
      <li>disasterRelief,  type, geographicalAreas, metropolitanStatisticalArea, county, naics, isPrimary,  naicsCode, naicsName, pscCodes, pscName, pscCode,</li>
    </ul>
    <li>Fields  from Points of Contact include:</li>
    <ul>
      <li>altElectronicBusinessPoc,  altGovtBusinessPoc, altPastPerformancePoc, electronicBusinessPoc,  govtBusinessPoc, pastPerformancePoc</li>
    </ul>
  </ul>
</ul>
<h2>Version 2 (v2)</h2>
<p>The following updates have been applied:</p>
<ul>
  <li>Added Reps and  Certs data; identified as &ldquo;certifications&rdquo; object</li>
  <ul>
    <li>Fields  include from Reps and Certs include:</li>
    <ul>
      <li>farResponses,  dfarResponses, id, answers, answerText, answerId, section</li>
    </ul>
  </ul>
</ul>
<h2>Version 3 (v3)</h2>
<p>The following updates have been applied:</p>
<ul>
  <li>Added FAR  52.204-17, which deals with CAGE Ownership of Offeror Information</li>
  <ul>
    <li>Includes  the addition of Immediate Owner and Highest Level Owner</li>
  </ul>
  <li>Added 2 digit  state code in conjunction with Congressional District code for clarity</li>
  <ul>
    <li>E.g.  congressionalDistrict: &ldquo;DC 98&rdquo; </li>
  </ul>
  <li>Removed answerId  that were sporadically appearing in the certifications object</li>
  <ul>
    <li>Identified  answerId as an optional string and cleared for removal</li>
  </ul>
  <li>Revised field  name for country within the address string to &nbsp;be tagged consistently as &ldquo;countryCode&rdquo;</li>
  <ul>
    <li>SAM  uses the countryCode value that is provided in the GENC <a href="https://nsgreg.nga.mil/doc/view?i=2324">https://nsgreg.nga.mil/doc/view?i=2324</a></li>
  </ul>
  <li>Resolved  instances where an http (error code 500) error is thrown when a batch is ran  with a single one duns being included multiple times within the batch</li>
  <ul>
    <li>No  error is being thrown</li>
  </ul>
  <li>Resolved  instances where an http (error code 500) error is thrown for historical  registrations that are missing a value for congressional district</li>
  <ul>
    <li>The  congressional district string appears as null</li>
  </ul>
  <li>Resolved  instances where an http (error code 500) error is thrown when a DUNS is missing  mandatory data elements</li>
  <ul>
    <li>The  mandatory data elements appear as null</li>
  </ul>
  <li>Resolved an issue  that if the Doing Business As name has a &ldquo;[&ldquo; or &ldquo;]&rdquo; it returns as an array</li>
  <ul>
    <li>doingBusinessAs  now returns as a string, not an array</li>
  </ul>
  <li>Resolved an issue  where Small Business indicator were returning a null for farResponses</li>
  <ul>
    <li>Now  displays a &ldquo;Y&rdquo; or &ldquo;N&rdquo; to indicate Small Business status</li>
  </ul>
</ul>
<h2>Version 4 (v4)</h2>
<p>The following updates have been applied:</p>
<ul>
  <li>Enhanced API getData return by adding 2 modular  options to return either all values (inclusive of &ldquo;null&rdquo; values) or responded  elements</li>
  <ul>
    <li><em>Full</em> -  https://api.data.gov/samdata/v4/registrations/XXXXXXXXX0000?return_values=full</li>
    <li><em>Responded</em> -  https://api.data.gov/samdata/v4/registrations/XXXXXXXXX0000?return_values=responded</li>
  </ul>
  <li>Added Architect-Engineer  Response (SF 330 Part II)</li>
  <ul>
    <li>Nested under  &ldquo;qualifications&rdquo; and &ldquo;acass&rdquo;</li>
  </ul>
  <li>Added  Bonding Information from Disaster Response page. Contains four bonding levels</li>
  <ul>
    <li>Nested  under &ldquo;bondingInformation&rdquo; </li>
  </ul>
  <li>Added  Address Line 2 for every address object</li>
  <ul>
    <li>Address  Line 2 is found under the field element &ldquo;line2&rdquo;</li>
  </ul>
  <li>Revised  52.203-2 data return of the POC. On the front end, there is one text field to  input a first and last name. In the API, there are 2 fields: firstName and  lastName</li>
  <ul>
    <li>firstName  populates the first word while the lastName populates the last word</li>
  </ul>
  <li>Revised  a few fields for DFAR 252.209-7002 to provide more clarity to a user</li>
  <ul>
    <li>&ldquo;name&rdquo;  was changed to &ldquo;controlledEntityName&rdquo;</li>
    <li>&ldquo;mi&rdquo;  was changed to &ldquo;middleInitial&rdquo;</li>
  </ul>
  <li>Revised  all address objects to include fields that were not being returned. Also  revised formatting for consistency throughout the API</li>
  <ul>
    <li>Fields  being returned are now &ldquo;line1&rdquo;, &ldquo;line2&rdquo;, &ldquo;city&rdquo;, &ldquo;countryCode&rdquo;, &ldquo;zip&rdquo;, &ldquo;zipPlus4&rdquo;</li>
  </ul>
  <li>Resolved  an issue for 52.214-14 where the ownerAddress and FacilityAddress was only  returning/copying the last entered facility and addresses.</li>
  <ul>
    <li>Now  returns each distinct facility if the entity has multiple facility addresses</li>
  </ul>
  <li>Resolved  instances where the notes section of a Point of Contact was not being displayed</li>
</ul>
<h1>SAM searchData API</h1>
<p>The SAM Search API has been developed to  mimic the Search functionality that is currently available from the SAM  website. The Search API provides the opportunity to perform a search  transaction in the following two options. Quick Search takes a single search term  provided by the user and compares it to a set of predefined database fields.  Advanced Search allows the user to search by entering a value that is then used  to search a user selected predefined search category. <br />
  Notice that the searchData is through a JSON-based  &ldquo;hypermedia as the engine of application state&rdquo; (HATEOAS with the appropriate  links object within the result set). The intent going forward will be to use  this model to allow for a scalable architecture of IAE&rsquo;s APIs to be built. </p>
<h2>Version 1 (v1)</h2>
<p>The following updates have been applied:</p>
<ul>
  <li>Added Advanced  Search features which allows users to search by specific fields</li>
  <ul>
    <li>Fields  added to the Advanced Search include:</li>
    <ul>
      <li>legalBusinessName,  status, duns, dunsPlus4, hasKnownExclusion, expirationDate, samAddress, cage,  dodaac, hasDelinquentFederalDebt</li>
    </ul>
  </ul>
</ul>
<h2>Version 2 (v2)</h2>
<p>The following updates have been applied:</p>
<ul>
<ul>
  <li>Added ability to  check companies that were added/updated /expired between 2 dates</li>
</ul>
<ul>
<ul>
  <li>Will  use the following format</li>
</ul>
<ul>
<ul>
  <li>expirationDate:[2015-01-01,2015-05-05]</li>
  <li>updateDate:[2015-01-01,2015-05-05]</li>
  <li>createDate:[2015-01-01,2015-05-05]</li>
</ul>



##### Get started
We organized this site into four major areas.

- [API basics](basics.html) introduces you to the operations offered by the API.
- [API calls](console/) gives you a hands-on experience of those operations with an interactive console.
- [Field reference for v4](fields4.html) lists and describes the type of information provided by the API.
- [Feedback](https://github.com/GSA/GSA-APIs/issues) provides a forum for developers to share feedback and report problems.

