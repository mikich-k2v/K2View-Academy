# TDM - Fabric Implementation Overview

 Implementation of the TDM  in Fabric involves several steps. The following illustration displays the main ones:

[<img src="images/tdm_fabric_imp_step_1.png" alt="drawing" width="200pxl"/>](04_fabric_tdm_library.md)[<img src="images/tdm_fabric_imp_step_2.png" alt="drawing" width="200pxl"/>](05_tdm_lu_implementation_general.md)[<img src="images/tdm_fabric_imp_step_3.png" alt="drawing" width="200pxl"/>]()[<img src="images/tdm_fabric_imp_step_4.png" alt="drawing" width="200pxl"/>]() [<img src="images/tdm_fabric_imp_step_5.png" alt="drawing" width="200pxl"/>](20_tdm_fabric_implementation_environments_setup.md)

A Fabric TDM project has the following:

- TDM Utilities, TDM Web Services and [TDM LU](04_fabric_tdm_library.md#tdm-lu).
- Logical Units that model TDM entities and their related data to LUs such as Customer, Billing, Ordering, etc.
- Broadway Flows which are defined under each LU to delete or load the entities from the target environment.
- Handling special cases, references, post-execution processes such as sending mail at the end of a task's execution or masking sensitive data.
- Environment setup, defining the source and target environments of the TDM. Setting the connection details of interfaces and the Globals in each environment.

K2view offers a TDM library with TDM utilities as well as TDM Templates for Broadway flows. These utilities must be implemented by the TDM Fabric project. 



[![Previous](/articles/images/Previous.png)](02_tdm_implementation_flow.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](04_fabric_tdm_library.md)



