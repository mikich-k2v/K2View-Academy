# Environment Exclusion Lists Tab

A tester may need to lock the copied entities on the testing environment and avoid re-loading these entities from the source environment by other users, till the completion of the functional tests.

To lock a list of entities,  a tester needs to ask the Admin user or the Environment Owner to add the required entities to an exclusion list of the environment.  The exclusion list holds the entities that are not allowed to be deleted or loaded into the environment for a given BE. 

**Example:**

- Define an exclusion list on ENV1 for Customer BE. Populate the exclusion list by 1,2,3. 
- As a result, customers 1, 2, and 3 cannot be copied to ENV1 by the TDM. 

An exclusion list can be added, edited or deleted from the environment by an Admin user or the [Environment Owner](08_environment_window_general_information.md#environment-owners) of the environment.  

The environment exclusion lists are displayed in the **Exclusion Lists tab** of the Environment window:

- To add a new exclusion list to the environment, click the **Add Exclusion List** button, populate the exclusion list's setting and click the **Add** button.
- To open a selected exclusion list, click the **Exclusion List** setting of the exclusion list.  Click the **Save Changes** to save the updates. 
- To delete an exclusion list from the environment, click the [![be_Example](https://github.com/k2view-academy/K2View-Academy/raw/Academy_6.4_TDM/articles/TDM/tdm_gui/images/delete_icon.png)](https://github.com/k2view-academy/K2View-Academy/blob/Academy_6.4_TDM/articles/TDM/tdm_gui/images/delete_icon.png) icon in the right corner of the exclusion list window. 

## Environment Global Window 

The Exclusion List Window in the Environment Window holds the following settings:

- **Business Entity** -  the entity type of the excluded entities. Select a BE from the dropdown list of the BEs that are related to the 
- **Requested by** -  the user id of the user who asks for the lock. It can be populated by admin users, environment owners of the environment, or the testers of the environment. Note that you can create **one exclusion list per environment, BE, and Requested by combination**. If a tester already has an exclusion list and asks to add entities to the exclusion list, you need to update the existing list.
- **Exclusion list** - the list of the excluded entities, separated by a comma. 



 [![Previous](/articles/images/Previous.png)](12_environment_globals_tab)[<img align="right" width="60" height="54" src="/articles/images/Next.png">]()

