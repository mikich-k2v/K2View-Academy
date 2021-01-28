# Override Sync Mode by Task Execution

When executing a TDM task on an environment, set the sync mode according to the following table:

<table width="900pxl">
<tbody>
<tr>
<td valign="top" width="150pxl">
<p><strong>Override Sync - Env Level</strong></p>
</td>
<td valign="top" width="130pxl">
<p><strong>Override Sync - Task Level&nbsp;</strong></p>
</td>
<td valign="top" width="130pxl">
<p><strong>Task Op Mode</strong></p>
</td>
<td valign="top" width="130pxl">
<p><strong>Task Execution Sync Mode</strong></p>
</td>
<td valign="top" width="380pxl">
<p><strong>Results</strong></p>
</td>
</tr>
<tr>
<td valign="top" width="130pxl">
<p>None</p>
</td>
<td valign="top" width="130pxl">
<p>None</p>
</td>
<td valign="top" width="130pxl">
<p>All</p>
</td>
<td valign="top" width="130pxl">
<p>On</p>
</td>
<td valign="top" width="380pxl">
<p>LUIs are synced according to their sync method.</p>
<p>See <a href="/articles/14_sync_LU_instance/10_sync_behavior_summary.md">Sync Behavior Summary table</a>.</p>
</td>
</tr>
<tr>
<td style="width: 150px;">
<p>None</p>
</td>
<td style="width: 150px;">
<p>Request up-to-date entity</p>
</td>
<td valign="top" width="130pxl">
<p>All</p>
</td>
<td valign="top" width="130pxl">
<p>Force</p>
</td>
<td style="width: 210px;">
<p>LUI are synced from the source.</p>
</td>
</tr>
<tr>
<td valign="top" width="130pxl">
<p>Always sync</p>
</td>
<td valign="top" width="130pxl">
<p>None</p>
</td>
<td valign="top" width="130pxl">
<p>All</p>
</td>
<td valign="top" width="130pxl">
<p>Force</p>
</td>
<td valign="top" width="380pxl">
<p>LUI are synced from the source.</p>
</td>
</tr>
<tr>
<td style="width: 150px;">
<p>Always sync</p>
</td>
<td style="width: 150px;">
<p>Request up-to-date entity</p>
</td>
<td valign="top" width="130pxl">
<p>All</p>
</td>
<td valign="top" width="130pxl">
<p>Force</p>
</td>
<td style="width: 210px;">
<p>LUI are synced from the source.</p>
</td>
</tr>
<tr>
<td style="width: 150px;">
<p>Do not sync</p>
</td>
<td style="width: 150px;">
<p>Request up-to-date entity</p>
</td>
<td valign="top" width="130pxl">
<p>All</p>
</td>
<td valign="top" width="130pxl">
<p>Force</p>
</td>
<td style="width: 210px;">
<p>LUI are synced from the source.</p>
</td>
</tr>
<tr>
<td style="width: 150px;" rowspan="3" valign="top" width="150pxl">
<p>Do not sync</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
</td>
<td style="width: 150px;" rowspan="3" valign="top" width="150pxl">
<p>None</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
</td>
<td valign="top" width="130pxl">
<p>Insert</p>
</td>
<td valign="top" width="130pxl">
<p>Off</p>
</td>
<td valign="top" width="380pxl">
<ul>
<li>First sync, return an error.</li>
<li>If the LUIs exist in Fabric, get the data from Fabric.&nbsp;</li>
</ul>
</td>
</tr>
<tr>
<td valign="top" width="130pxl">
<p>Delete and insert&nbsp;</p>
</td>
<td valign="top" width="130pxl">
<p>On</p>
</td>
<td valign="top" width="380pxl">
<ul>
<li>First sync, return an error.</li>
<li>If the LUIs exist in Fabric:
<ul>
<li>Source LU tables, get the data from Fabric.</li>
<li>Target LU tables, sync the data from the target environment.</li>
</ul>
</li>
</ul>
</td>
</tr>
<tr>
<td valign="top" width="130pxl">
<p>Delete only</p>
</td>
<td valign="top" width="130pxl">
<p>On</p>
</td>
<td valign="top" width="380pxl">
<p>Target LU tables are synced from the target environment.&nbsp;</p>
</td>
</tr>
<tr>
<td style="width: 150px;" rowspan="3" valign="top" width="150pxl">
<p>Do not sync</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
</td>
<td style="width: 150px;"a rowspan="3" valign="top" width="150pxl">
<p>Do not sync source data</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
</td>
<td valign="top" width="130pxl">
<p>Insert</p>
</td>
<td valign="top" width="130pxl">
<p>Off</p>
</td>
<td valign="top" width="380pxl">
<ul>
<li>First sync, return an error.</li>
<li>If the LUIs exist in Fabric, get the data from Fabric.&nbsp;</li>
</ul>
</td>
</tr>
<tr>
<td valign="top" width="130pxl">
<p>Delete and insert&nbsp;</p>
</td>
<td valign="top" width="130pxl">
<p>On</p>
</td>
<td valign="top" width="380pxl">
<ul>
<li>First sync, return an error.</li>
<li>If the LUIs exist in Fabric:
<ul>
<li>Source LU tables, get the data from Fabric.</li>
<li>Target LU tables, get the data from the target environment.</li>
</ul>
</li>
</ul>
</td>
</tr>
<tr>
<td valign="top" width="130pxl">
<p>Delete only</p>
</td>
<td valign="top" width="130pxl">
<p>On</p>
</td>
<td valign="top" width="380pxl">
<p>Target LU tables are synced from the target environment.&nbsp;</p>
</td>
</tr>
<tr>
<td style="width: 150px;" rowspan="3" valign="top" width="150pxl">
<p>None</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
</td>
<td style="width: 150px;" rowspan="3" valign="top" width="150pxl">
<p>Do not sync source data</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
</td>
<td valign="top" width="130pxl">
<p>Insert</p>
</td>
<td valign="top" width="130pxl">
<p>Off</p>
</td>
<td valign="top" width="380pxl">
<ul>
<li>First sync, return an error.</li>
<li>If the LUIs exist in Fabric, get the data from Fabric.&nbsp;</li>
</ul>
</td>
</tr>
<tr>
<td valign="top" width="130pxl">
<p>Delete and insert&nbsp;</p>
</td>
<td valign="top" width="130pxl">
<p>On</p>
</td>
<td valign="top" width="380pxl">
<ul>
<li>First sync, return an error.</li>
<li>If the LUIs exist in Fabric:
<ul>
<li>Source LU tables, get the data from Fabric.</li>
<li>Target LU tables, get the data from the target environment.</li>
</ul>
</li>
</ul>
</td>
</tr>
<tr>
<td valign="top" width="130pxl">
<p>Delete only</p>
</td>
<td valign="top" width="130pxl">
<p>On</p>
</td>
<td valign="top" width="380pxl">
<p>Target LU tables are synced from the target environment.&nbsp;</p>
</td>
</tr>
</tbody>
</table>







  [![Previous](/articles/images/Previous.png)](06_be_product_tdmdb_tables.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">]()
