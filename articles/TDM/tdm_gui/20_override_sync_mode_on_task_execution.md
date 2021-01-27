# Override Sync Mode by Task Execution

TDM task execution process must to set the Sync mode based on the environment and the task's Override Sync mode and based on the task's operation mode as described in the following table:

<table width="900pxl">
<tbody>
<tr>
<td valign="top" width="150pxl">
<p><strong>Override Sync - Source Environment Level</strong></p>
</td>
<td valign="top" width="130pxl">
<p><strong>Override Sync - Task Level&nbsp;</strong></p>
</td>
<td valign="top" width="130pxl">
<p><strong>Task Operation Mode</strong></p>
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
<p>The LUIs are synced according its sync method.</p>
<p>See <a href="/articles/14_sync_LU_instance/10_sync_behavior_summary.md">Sync Behavior Summary table</a>.</p>
</td>
</tr>
<tr>
<td style="width: 150px;">
<p>None</p>
</td>
<td style="width: 150px;">
<p>Request Up to Date Entity&nbsp;</p>
</td>
<td valign="top" width="130pxl">
<p>All</p>
</td>
<td valign="top" width="130pxl">
<p>Force</p>
</td>
<td style="width: 210px;">
<p>The LUI are synced from the source.</p>
</td>
</tr>
<tr>
<td valign="top" width="130pxl">
<p>Always Sync</p>
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
<p>The LUI are synced from the source.</p>
</td>
</tr>
<tr>
<td style="width: 150px;">
<p>Always Sync</p>
</td>
<td style="width: 150px;">
<p>Request Up to Date Entity&nbsp;</p>
</td>
<td valign="top" width="130pxl">
<p>All</p>
</td>
<td valign="top" width="130pxl">
<p>Force</p>
</td>
<td style="width: 210px;">
<p>The LUI are synced from the source.</p>
</td>
</tr>
<tr>
<td style="width: 150px;">
<p>Do not Sync</p>
</td>
<td style="width: 150px;">
<p>Request Up to Date Entity&nbsp;</p>
</td>
<td valign="top" width="130pxl">
<p>All</p>
</td>
<td valign="top" width="130pxl">
<p>Force</p>
</td>
<td style="width: 210px;">
<p>The LUI are synced from the source.</p>
</td>
</tr>
<tr>
<td style="width: 150px;" rowspan="3" valign="top" width="150pxl">
<p>Do not Sync</p>
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
<li>First sync - return an error.</li>
<li>If the LUIs exist in Fabric - get the data from Fabric.&nbsp;</li>
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
<li>First sync - return an error.</li>
<li>If the LUIs exist in Fabric:
<ul>
<li>Source LU tables - get the data from Fabric.</li>
<li>Target LU tables -&nbsp; sync the data from the target environment.</li>
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
<p>The target LU tables are synced from the target environment.&nbsp;</p>
</td>
</tr>
<tr>
<td style="width: 150px;" rowspan="3" valign="top" width="150pxl">
<p>Do not Sync</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
</td>
<td style="width: 150px;" rowspan="3" valign="top" width="150pxl">
<p>Do not Sync Source Data</p>
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
<li>First sync - return an error.</li>
<li>If the LUIs exist in Fabric - get the data from Fabric.&nbsp;</li>
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
<li>First sync - return an error.</li>
<li>If the LUIs exist in Fabric:
<ul>
<li>Source LU tables - get the data from Fabric.</li>
<li>Target LU tables -&nbsp; get the data from the target environment.</li>
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
<p>The target LU tables are synced from the target environment.&nbsp;</p>
</td>
</tr>
<tr>
<td style="width: 150px;" rowspan="3" valign="top" width="150pxl">
<p>None</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
</td>
<td style="width: 150px;" rowspan="3" valign="top" width="150pxl">
<p>Do not Sync Source Data</p>
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
<li>First sync - return an error.</li>
<li>If the LUIs exist in Fabric - get the data from Fabric.&nbsp;</li>
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
<li>First sync - return an error.</li>
<li>If the LUIs exist in Fabric:
<ul>
<li>Source LU tables - get the data from Fabric.</li>
<li>Target LU tables -&nbsp; get the data from the target environment.</li>
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
<p>The target LU tables are synced from the target environment.&nbsp;</p>
</td>
</tr>
</tbody>
</table>







  [![Previous](/articles/images/Previous.png)](06_be_product_tdmdb_tables.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">]()
