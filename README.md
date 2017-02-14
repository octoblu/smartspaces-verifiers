# smartspaces-verifiers

Smartspaces verifiers are used as flexible way of running tests on complex interactions and relationships between devices and services.

## Types of Verifiers

### Action Verifier (High Level)

High level verifiers are used to verify an end-to-end action. The action should be very single purposed. We should expect that when a state change is performed, or message is sent, that the completed state has the correct transformations.

These verifiers should be able to be run as a worker or manually against a real smartspace.

For example, [Instant Meeting](https://github.com/octoblu/smartspaces-verifier-instant-meeting) and [Room List](https://github.com/octoblu/smartspaces-verifier-room-list) 

### Data Verifier (Low Level)

Low Level verifiers confirm that the relationship between devices are correct, and that the state of a device has the required information.

These verifiers should export a library that can be used in the implemtation of the service that creates, or modifys, the related device, and devices. They should also be able to be fun as a worker or manually against a real smartspace.

For example, [Customer](https://github.com/octoblu/smartspaces-verifier-customer) and [Room](https://github.com/octoblu/smartspaces-verifier-room) 

### Component Verifier (Bridge)

A Component verifier is a bridge between an end component and nearest High, or Low, level test.

Component level verifiers are used to verify that the component does one of these two things:

1. It outputs a correct message, or config, event.
2. It retrieves the required device state, or device lists, in order for it function.

They should match up to the interface used in a "High Level" test, in order to close missing gap of untested code.

These types of verifiers should use a common library between it and the directly related "Low Level" or "High Level" verifier.

## Reporting Errors

### Worker

When running a verfier as a worker, it is important to report to `meshblu-verifier-pingdom`. The verifier pingdom service stores a record of each `pass` and `fail` and will interface to `pingdom` to perform tests over time.

### Library

When running a verifier as a library, it is important to return an Error with `error.errors` and have it returned using "error first" callbacks.

### Manually

When running a verfier manually, it is important use the worker with a "run once" mode and to list all of the errors that failed (`error.errors`).
