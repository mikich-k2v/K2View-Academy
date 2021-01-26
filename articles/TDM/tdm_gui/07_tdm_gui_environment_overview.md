# TDM Environments Overview

Every environment must be defined in the TDM to be enabled for TDM tasks. 

Each environment must be defined in the following TDM components:

- Fabric - set the interfaces connection details on each environment. It is also possible to override the Global values on each environment.

  Click to read more about [environment setup in Fabric](/articles/TDM/tdm_implementation/20_tdm_fabric_implementation_environments_setup.md)

- TDM GUI  - set the following information on each environment:

  - [General information] like environment name, contact person, environment type (source, target or both)...
  - [Environment owners] - adding environment owners to setup and maintain the environment.
  - [Environments Products] - attach [TDM Products](05_tdm_gui_product_window.md) to each environment.
  - [Environment Roles] - define roles with permissions on the environment and attach [tester users](02_tdm_gui_user_types.md) to the environment to allow them creating TDM tasks on the environment.
  - [Environment Globals] - override Globals on the environment.
  - [Exclusion Lists] - adding lists of entities to be excluded from the TDM tasks on the environment.

  ## Environments List Window

The **Environments** window displays a list of all Environments defined in the TDM.  Only **Admin users** can create, add or remove environment owners, or delete an environment. The environment owners of the environment can edit the environment. 

Other users can open the Environments for a view.

-   To create a new Environment, click the **New Environment** button.
-   To open a selected Environment, click the environment's **Name**.
-   To delete an environment, click the ![delete](D:/K2View-Academy/articles/TDM/tdm_gui/images/delete_icon.png) icon in the Environment window.



## Environment Window

The Environment window consists of the following sections:

- [General Information](08_environment_window_general_information.md)

- [Execution Summary]

- Environments tabs:

  - [Roles]
  - [Products]
  - [Environment Globals]
  - [Exclusion Lists]

  See an example of an Environment window:

  ![environment](images/tdm_environment_window.png)



  [![Previous](/articles/images/Previous.png)](06_be_product_tdmdb_tables.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](08_environment_window_general_information.md)