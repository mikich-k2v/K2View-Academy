# TDM Generic Broadway Flows

The Fabric TDM library includes a set of built-in generic Broadway flows defined for easy adaptation of the TDM generic implementation per the specific data model. 

This article describes which flows should be copied from the TDM library into your TDM project.

<!--check with Taha - what is the process? need to copy or ...?-->

## Shared Objects Flows and Templates

The Broadway folder in the Shared Objects includes the flows that are used across several Logical Units. These flows can be generic or specific. 

The generic flows are the utilities required for the TDM execution. They handle the activities such as setting the global variables and sync mode, loading the reference, handling the errors, populating the execution statistics and more. All these flows must be imported from the TDM library to your project's Shared Objects. They do not require any manual update.

Below are the insights into the structure and functionality of some of the generic flows.

### Initialization

TDM task initialization is performed using the **InitiateTDMLoad.flow** utility which includes several steps, such as:

* Setting the values of the global variables to the session and the sync mode.
* Setting the source environment based on the task source before getting the LUI.
* Getting the LUI from Fabric.
* Setting the target environment as a preparation step for delete and load.

The **InitiateTDMLoad.flow** is performed as a first step of **TDMOrchestrator.flow** task envelop flow.

[Click to learn how to create the TDMOrchestrator.flow](11_tdm_implementation_using_generic_flows.md#step-4---create-the-tdmorchestratorflow-from-template).

### Reference

The TDM library includes a set of utility flows to handle the reference data.

[Click to learn more about TDM reference](/articles/TDM/tdm_gui/24_task_reference_tab.md).

### Load and Delete Generic Flows

The TDM library contains the templates and the generic flows which should be used for creation of a TDM implementation based on your project's data model. The templates are prepared using the Fabric [Templates](/articles/35_templates/01_templates_overview.md) functionality which enables the creation of various project's objects based on a predefined structure rather than creating them from scratch. 

[Click to learn how to create a TDM Implementation using the generic Broadway flows.](11_tdm_implementation_using_generic_flows.md)

### Error Handling and Statistics

The TDM library delivers a generic error handling and statistics gathering mechanism. It is based on the Broadway capabilities tailored per TDM business requirements. 

[Click to learn more about TDM error handling and statistics flows](12_tdm_error_handling_and_statistics.md).



[![Previous](/articles/images/Previous.png)]()[<img align="right" width="60" height="54" src="/articles/images/Next.png">](11_tdm_implementation_using_generic_flows.md)

