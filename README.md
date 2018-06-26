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

