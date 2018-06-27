# API Introduction

EDR's Loan Origination System APIs are a set of application
programming interfaces designed to provide access to EDR services.

The APIs enable you to use your own custom software to create and
manage service requests within Collateral 360, so you can seamlessly
integrate Collateral 360's industry-leading features into your own
familiar due diligence and workflow control software. Using EDR's
APIs can help you achieve time and cost savings, increase efficiency,
and reduce troublesome manual data entry errors between different
systems.

# Business Workflow Overview

The purpose of the LOS APIs is to facilitate the management of
service requests via custom client applications. As a user of
Collateral 360, you or your organization may wish to use your
own software to accomplish or automate common tasks normally
performed through the Collateral 360 Web application's user
interface. The LOS APIs are a starting point for achieving
this goal.

Lending institutions that use Collateral 360 to manage their
real property due diligence processes typically begin by
creating a draft service request via Collateral 360's
service request form (SRF). While in the "draft" status, a
service request is allowed to be incomplete, since a draft
represents work-in-progress. Depending on your institution's
settings in Collateral 360, draft service requests may only
be visible to their authors until the service request is
marked as no longer being in draft status.

A service request typically contains some or all of the
following data:

* Basic loan information (principal, purpose, _etc._).
  
* Details about the borrowers.
  
* A list of real property offered as collateral.
  
* Tasks that must be accomplished to complete the underwriting
  and funding decision-making processes.
  
* Records of the individuals responsible for completing the
  aforementioned tasks.

(Lending institutions may optionally organize their service
requests into separate _cabinets_, which are simply named
groups of service requests that are logically grouped in
some meaningful way.)

For each collateral location, a set of _services_ can be
requested (the aggregated collection of services requested
for all collateral properties is from where the name _service
request_ is derived). Each service represents a task that
must be performed for the property in order to proceed towards
completion of all necessary due diligence. Lending insitutions
can customize the list of services, so these will vary between
different users of Collateral 360. However, accomplishing a
services usually results in some form of documentation, such as
a report, affidavit, contract, or other paperwork. These
documents are typically uploaded into Collateral 360 as digital
files, and can then be downloaded and reviewed by any individual
who has been granted permission to do so.

Each service always belongs to a broad category. For example,
services related to environmental due diligence may reside in
the "Environmental" category, while those related to appraising
a property's condition may be in the "Appraisal" category.

> The preceding workflow describes the components of Collateral
> 360 that are covered by the LOS API, and should provide a
> general understanding of the terminology and purpose of the
> API requests described in this document. A broader description
> of the other features and processes supported by Collateral 360
> is not within the scope of this document.

# Technical Overview

EDR's APIs are made available over TLS-encrypted HTTPS. Client
authentication is performed using OAuth2.

The API protocol itself is formatted as JSON, and uses a consistent
envelope structure for most calls (to facilitate centralization of
envelope construction and parsing).

## API Endpoint Descriptions

The first set of APIs available to integration developers is the
Draft SRF API product. These APIs are designed to manage the creation
and editing of service request form data prior to the point where
the data are finalized and ready to be acted on.

At this point in the due diligence process, information on-hand may
be incomplete or in flux, and decisions on exactly what services
need to be performed on real estate collateral are not yet finalized.
Accordingly, the Draft SRF APIs allow incomplete data to be recorded
as it is obtained from borrowers or other sources.

Available API endpoints are as follow:

### SRF Fields

This endpoint returns a full representation of all draft SRF data
fields available for entry and modification by the API. The fields
are provided in the JSON Schema format, which is documented here:

    http://json-schema.org/

### SRF

The SRF endpoint allows you to create a new draft service request
form, or update an existing one.

### SRF Status

The Status endpoint returns basic details about an existing service
request. Data are available at the following levels:
* Information about a service request.
* The real property used as collateral in a service request.
* The services to be performed on each collateral property.

### SRF Download Assets

This endpoint returns a list of downloadable assets for a given SRF.

### SRF Download

Invoking this enpoint downloads a specific SRF Asset.

