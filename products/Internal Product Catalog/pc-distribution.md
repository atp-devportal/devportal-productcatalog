# Product Catalog Distribution APIs

## Overview

Product Catalog data is created and managed through various means (intake APIs/graphical user interface) by Catalog owners. ATPCO also populates the Product Catalog with data that is in ATPCO source systems, such as Amenities, Rules, OSF, and Branded Fares.  

Catalog data needs to be available to subscribers/vendors/retailers/owners on a timely basis, and any updates must be published per their preferences.  

Distribution services continuously collect data updates, prepare it per the receiving organization’s preferences, and notify the organizations when the data is available for their consumption.  

Distribution APIs enable subscribers to request Product Catalog updates by referencing the notification information they have received.  

Here is a list of the Distribution APIs that will be available for the MVP (minimally viable product) release of Product Catalog:  

## Fetch_subs (GET)  

As part of the subscription process, change data is generated and stored in the Distribution database. Product Catalog will provide a reference ID and data summary in a notification sent to eligible subscribers.  

- **Request:** Subscribers will request the subscription data or data pickup information by sending the notification reference ID in a Fetch_subs (GET) request.  
- **Response:** The response from Product Catalog will include the updated data if its size is below a defined threshold. Otherwise, the response will provide an S3 location where the data can be picked up.  

## Fetch_all_adds (GET)  

- **Request:** Subscribers will use a Fetch_all_adds (GET) API to request a data refresh.   
- **Response:** The response from Product Catalog will provide an S3 pickup location for all the data for a given subscription profile as of a specific point in time.  

## Subscription Profile CRUD  

These are the APIs to create and manage subscriber preferences (filters) per their needs. Owning airlines grant Product Catalog access to designated subscribers. Subscribers have the option to adjust their subscription preferences to ensure that the data is loaded efficiently into their systems. The catalog owner designates organizations that are eligible to receive data, including the type of data, the scope of data, and the organization name. Subscribers, in turn, will set their preferences for receiving the data.  

### Subscription Preferences Include:
- **Schedules**
- **Catalog owners**
- **Record types**