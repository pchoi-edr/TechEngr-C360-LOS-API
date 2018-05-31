# API Introduction

The EDR API Product is a set of application program interfaces designed to provide access to EDR services. Using the APIs you will enable you to create and manage service requests. The EDR API Product provides both RESTful and XML interfaces.

The API product uses OAuth2 authentication to secure the calls from your system.

### API Descriptions

The first API product set available to integration developers is the SRF API Product (Service Request Form)

#### SRF Fields

This endpoint returns a full JSON Schema for the Service Request Form. The schema contains all the details needed for a developer to build robust interfaces to the EDR platform.

#### SRF

The SRF endpoint will create a new DRAFT service request.

#### SRF Status

The Status endpoint returns the details on a existing SRF location and services.

#### SRF Download

Calling the Download endpoint starts the downloading of a specific SRF Asset.

#### SRF Download Assets

The Download Assets endpoint returns a list of downloadable assets for a given SRF
