# Environment Globals Tab

[Global variables](/articles/08_globals/01_globals_overview.md) defined in Fabric TDM implementation can be overridden on the environment or TDM task level. 

**Examples:**

- A DB Schema Name Global is added and set on the environment level since each environment can have a different DB schema name.
- An Email Global is added and populated by the tester's email on the TDM task level.

A Global can be added, edited or deleted from the environment by an Admin user or the [Environment Owner](08_environment_window_general_information.md#environment-owners) of the environment.  

The environment Globals are displayed in the **Environment Globals tab** of the Environment window:

- To add a new Global to the environment, click the **Add Global** button, populate the Global's setting and click the **Add** button.
- To open a selected Global, click the **Name** setting of the Global.  Click the **Save Changes** to save the updates. 
- To delete a Global from the environment, click the [![be_Example](https://github.com/k2view-academy/K2View-Academy/raw/Academy_6.4_TDM/articles/TDM/tdm_gui/images/delete_icon.png)](https://github.com/k2view-academy/K2View-Academy/blob/Academy_6.4_TDM/articles/TDM/tdm_gui/images/delete_icon.png) icon in the right corner of the Global window. The TDM execution process will take the default value of the Global.

## Environment Global Window 

The Global Window in the Environment Window holds the following settings:

- **Global Name** -  select a Global from the dropdown list of the Globals in the Fabric TDM implementation.
- **Global Value**  - set the value of the Global. A Global variable can have a different value in each environment.\



 [![Previous](/articles/images/Previous.png)](11_environment_products_tab.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">]()

