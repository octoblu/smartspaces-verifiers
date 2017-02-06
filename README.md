# smartspaces-verifiers

Smartspaces verifiers are used as flexible way of running tests on complex interactions and relationships between devices and services.

## Types of Verifiers

### High Level

High level verifiers are used to verify an end-to-end action. The action should be very single purposed. We should expect that when a state change is performed, or message is sent, that the completed state has the correct transformations.

These verifiers should be able to be run as a worker or manually against a real smartspace.

For example, [Instant Meeting](https://github.com/octoblu/smartspaces-verifer-instant-meeting). 

### Low Level

Low Level verifiers confirm that the relationship between devices are correct, and that the state of a device has the required information.

These verifiers should export a library that can be used in the implemtation of the service that creates, or modifys, the related device, and devices. They should also be able to be fun as a worker or manually against a real smartspace.

For example, [Customer](https://github.com/octoblu/smartspaces-verifer-customer). 

### Component Level

Component level verifiers are used to verify that the component does one of these two things:

1. It outputs a correct message, or config, event.
2. It retrieves the required device state, or device lists, in order for it function.

They should match up to the interface used in a "High Level" test.

These types of verifiers should use a common library between it and the directly related "Low Level" or "High Level" verifier.
