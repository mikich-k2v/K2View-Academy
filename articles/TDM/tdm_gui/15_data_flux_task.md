# TDM Data Flux Tasks

The Data Flux mode enables users to keep versions (backups) of data during functional tests and reload the to the latest saved version on the target environment when needed:

A User can create an Extract task and execute it multiple times to create different versions (backups) of the entities and save each version in Fabric.  Then the user can get the one of the extracted version and reload it into the testing environment if the testing environment gets corrupted by the functional tests. 

This functionality is useful when a tester runs a complex testing calendar on their testing environment. Taking backups of their entities' data every X steps or every X time enables the tester to reload the latest backup on their environment and repair its data if something goes wrong and the data gets corrupted by the functional tests. This way the tester does not have to go back to the original state of their environment and loose the updates, made by the testing calendar. 

Note that the testing environment is often used as a source and target environment on Data Flux tasks. Therefore, the [environment type](/articles/TDM/tdm_gui/08_environment_window_general_information.md#environment-type) must be set to **Both** to enable the Data Flux on a given environment.



## How do I Create a Data Flux Task ?

Check the **Entity Versioning** setting in the **General tab** of the task window.



## Who Can Create a Data Flux Task ?

The following users can create a Data Flux task:

1. Admin users
2. Environment owner users can create a Data Flux task on their environment
3. Other users (testers) can create a TDM task on the environments they are attached to by a [role](/articles/TDM/tdm_gui/10_environment_roles_tab.md) which has an **Entity Versioning permission**.



## TDM Task Types and Modes - Summary Table

<table width="900pxl">
<tbody>
<tr>
<td valign="top" width="150pxl">
<p><strong>Task Type</strong></p>
</td>
<td valign="top" width="150pxl">
<p><strong>Entity Versioning</strong></p>
</td>
<td valign="top" width="600pxl">
<p><strong>Description</strong></p>
</td>
</tr>
<tr>
<td valign="top" width="150pxl">
<p>Extract</p>
</td>
<td valign="top" width="150pxl">
<p>true</p>
</td>
<td valign="top" width="600pxl">
<p>Extract the data of the selected entities from the source environment and save it as a separate version in the Fabric.</p>
<p>The extract gets the execution datetime and each entity gets the following instance ID in Fabric:</p>
<p>&lt;Source env name&gt;_&lt;entity id&gt;_&lt;task title&gt;_&lt;datetime&gt;</p>
<p>For example, ENV1_100_extractTest3_20210218082453</p>
<p>Since the execution datetime is concatenated to the LUI, each task execution creates a different set of LUIs.&nbsp;</p>
</td>
</tr>
<tr>
<td valign="top" width="150pxl">
<p>Extract</p>
</td>
<td valign="top" width="150pxl">
<p>false</p>
</td>
<td valign="top" width="600pxl">
<p>Extract the data of the selected entities from the source environment and save it in the Fabric.</p>
<p>Each entity is kept in Fabric with the following instance:</p>
<p>&lt;Source env name&gt;_&lt;entity id&gt;</p>
<p>For example, ENV1_100</p>
<p>Note that each task execution may update the LUIs in Fabric.</p>
</td>
</tr>
<tr>
<td valign="top" width="150pxl">
<p>Load</p>
</td>
<td valign="top" width="150pxl">
<p>true</p>
</td>
<td valign="top" width="600pxl">
<p>Load a selected version created on the task's LUs and source environment, into the selected target environment. The required entities will be deleted from the target and reloaded based on the selected version.</p>
</td>
</tr>
<tr>
<td valign="top" width="150pxl">
<p>Load</p>
</td>
<td valign="top" width="150pxl">
<p>false</p>
</td>
<td valign="top" width="600pxl">
<p>Regular TDM load task.&nbsp; Get a list of entities from a source environment and copy them into the target environment.</p>
</td>
</tr>
</tbody>
</table>





 [![Previous](/articles/images/Previous.png)](14_task_overview.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](16_extract_task.md)

