# TDM Generic Broadway Flows

### Overview

The Fabric TDM library includes a set of built-in generic Broadway flows defined for easy adaptation of the TDM generic implementation per the specific data model. This article describes which flows should be copied from the TDM library into your TDM project.

### Shared Objects Broadway Flows

The Broadway folder in the Shared Objects includes the flows that are used across several Logical Units. These flows can be generic or specific. 

The generic flows are the utilities required for the TDM execution. They handle the activities such as setting the global variables and sync mode, handling the errors, populating the execution statistics and more. All these flows must be copied from the TDM folder of the TDM library under the Shared Objects to your  project. They do not require any manual update.

### TDM_LIBRARY LU Broadway Flows

TDM_LIBRARY LU contains the template flows which are used for the creation of a TDM implementation based on your project's data model. They are prepared using the Fabric [Templates](/articles/35_templates/01_templates_overview.md) functionality which enable the creation of various project's objects based on a predefined structure rather than creating them from scratch. 

The following templates and flows must be copied from the TDM library to the Logical Unit of your TDM project:

**Templates:**

- tdmLoadAllTables.flow.template
- tdmLoadTable.flow.template
- TDMOrchestrator.flow.template

**Flows:**

- createLoadAllTablesFlow.flow 
- createLoadTableFlows.flow 
- createLoadTableToTargetFlow.flow







