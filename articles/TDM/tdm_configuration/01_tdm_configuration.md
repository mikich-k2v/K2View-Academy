# TDM Configuration

The TDM configuration consists of the following:

- [TDM GUI Configuration](#tdm-gui-configuration)
- TDM DB - General Parameters

## TDM GUI Configuration

The main configuration file of the TDM GUI is the **config.js** file. This file is located under the ~/TDM/k2vtdmbe directory of the TDM server.

### Config.js File

<table width="900pxl">
<tbody>
<tr>
<td valign="top" width="200pxl"><strong>Section Name</strong></td>
<td valign="top" width="200pxl"><strong>Attribute Name</strong></td>
<td valign="top" width="300pxl"><strong>Description</strong></td>
<td valign="top" width="200pxl"><strong>Default Value</strong></td>
</tr>
</tbody>
<tbody>
<tr>
<td valign="top" width="200pxl">N/A</td>
<td valign="top" width="200pxl">secret</td>
<td valign="top" width="300pxl">&nbsp;</td>
<td valign="top" width="200pxl">hello</td>
</tr>
<tr>
<td valign="top" width="200pxl">N/A</td>
<td valign="top" width="200pxl">sessionTimeout</td>
<td valign="top" width="300pxl">The number of seconds till an idle session expires.</td>
<td valign="top" width="200pxl">3600</td>
</tr>
<tr>
<td valign="top" width="200pxl">N/A</td>
<td valign="top" width="200pxl">https</td>
<td valign="top" width="300pxl">Configures the connection mode of the TDM GUI: http or https. To connect the TDM GUI in https mode set this parameter to true and set the <strong>url</strong> of the constants.js to https.</td>
<td valign="top" width="200pxl">false</td>
</tr>
<tr>
<td valign="top" width="200pxl">N/A</td>
<td valign="top" width="200pxl">fluxMode</td>
<td valign="top" width="300pxl">Set to false to disable the creation and execution of <a href="/articles/TDM/tdm_gui/16_extract_task.md">Extract tasks</a> and <a href="/articles/TDM/tdm_gui/15_data_flux_task.md">Load Data Flux tasks</a>.</td>
<td valign="top" width="200pxl">true</td>
</tr>
<tr>
<td valign="top" width="200pxl">adminUsers</td>
<td valign="top" width="200pxl">uid, displayName</td>
<td valign="top" width="300pxl">Defines the list of admin users in the TDM GUI. Note that each user including the admin user must be defined in the LDAP system as well.</td>
<td valign="top" width="200pxl">&nbsp;</td>
</tr>
<tr>
<td valign="top" width="200pxl">postgres</td>
<td valign="top" width="200pxl">user</td>
<td valign="top" width="300pxl">The connection details of the <a href="/articles/TDM/tdm_architecture/02_tdm_database.md">TDM PostgreSQL DB</a>.</td>
<td valign="top" width="200pxl">tdm</td>
</tr>
<tr>
<td valign="top" width="200pxl">postgres</td>
<td valign="top" width="200pxl">pass</td>
<td valign="top" width="200pxl">The connection details of the <a href="/articles/TDM/tdm_architecture/02_tdm_database.md">TDM PostgreSQL DB</a>.</td>
<td valign="top" width="200pxl">tdm</td>
</tr>
<tr>
<td valign="top" width="200pxl">postgres</td>
<td valign="top" width="200pxl">host</td>
<td valign="top" width="200pxl">The connection details of the <a href="/articles/TDM/tdm_architecture/02_tdm_database.md">TDM PostgreSQL DB</a>. Edit the host and populate it by the IP address of the TDM DB.</td>
<td valign="top" width="200pxl">&nbsp;</td>
</tr>
<tr>
<td valign="top" width="200pxl">postgres</td>
<td valign="top" width="200pxl">port</td>
<td valign="top" width="200pxl">The connection details of the <a href="/articles/TDM/tdm_architecture/02_tdm_database.md">TDM PostgreSQL DB</a>.</td>
<td valign="top" width="200pxl">5432</td>
</tr>
<tr>
<td valign="top" width="200pxl">postgres</td>
<td valign="top" width="200pxl">database</td>
<td valign="top" width="200pxl">The connection details of the <a href="/articles/TDM/tdm_architecture/02_tdm_database.md">TDM PostgreSQL DB</a>.</td>
<td valign="top" width="200pxl">TDMDB</td>
</tr>
<tr>
<td valign="top" width="200pxl">postgres</td>
<td valign="top" width="200pxl">schema</td>
<td valign="top" width="200pxl">The connection details of the <a href="/articles/TDM/tdm_architecture/02_tdm_database.md">TDM PostgreSQL DB</a>.</td>
<td valign="top" width="200pxl">public</td>
</tr>
<tr>
<td valign="top" width="200pxl">postgres</td>
<td valign="top" width="200pxl">ssl</td>
<td valign="top" width="200pxl">Set to true to set an SSL connection to the TDM DB.</td>
<td valign="top" width="200pxl">false</td>
</tr>
<tr>
<td valign="top" width="200pxl">debug</td>
<td valign="top" width="200pxl">level</td>
<td valign="top" width="200pxl">The TDM GUI debug level can be set to <strong>error</strong>, <strong>warn</strong> or <strong>info</strong>.</td>
<td valign="top" width="200pxl">info</td>
</tr>
<tr>
<td valign="top" width="200pxl">debug</td>
<td valign="top" width="200pxl">outputType</td>
<td valign="top" width="200pxl">Set the debug output type to <strong>console</strong> or <strong>file</strong>.</td>
<td valign="top" width="200pxl">console</td>
</tr>
<tr>
<td valign="top" width="200pxl">debug</td>
<td valign="top" width="200pxl">status</td>
<td valign="top" width="200pxl">Set to <strong>off</strong> to disable the debug messages.</td>
<td valign="top" width="200pxl">on</td>
</tr>
<tr>
<td valign="top" width="200pxl">ldap</td>
<td valign="top" width="200pxl">ssl</td>
<td valign="top" width="200pxl">Set to <strong>true</strong> to connect the LDAP in a secured mode (LDAPS).</td>
<td valign="top" width="200pxl">false</td>
</tr>
<tr>
<td valign="top" width="200pxl">ldap</td>
<td valign="top" width="200pxl">MC_AD</td>
<td valign="top" width="200pxl">Set to <strong>true</strong> to connect the Microsoft Active Directory as LDAP system</td>
<td valign="top" width="200pxl">false</td>
</tr>
<tr>
<td valign="top" width="200pxl">ldap</td>
<td valign="top" width="200pxl">urlString</td>
<td valign="top" width="200pxl">The LDAP's URL. Set the IP address and port of the LDAP system. Set the port to <strong>636</strong> to connect the LDAP in a secure mode (LDAPS). Note that the TDM server contains also an LDAP sever for the TDM development and testing. Populate the URL by the TDM server IP address to invoke the development LDAP server.</td>
<td valign="top" width="200pxl">ldap://62.90.46.136:10389</td>
</tr>
<tr>
<td valign="top" width="200pxl">ldap</td>
<td valign="top" width="200pxl">adminDN</td>
<td valign="top" width="200pxl">&nbsp;</td>
<td valign="top" width="200pxl">uid=tdmldap,ou=users,ou=system</td>
</tr>
<tr>
<td valign="top" width="200pxl">ldap</td>
<td valign="top" width="200pxl">adminPassword</td>
<td valign="top" width="200pxl">The LDAP password. Use the default password to connect the development LDAP.</td>
<td valign="top" width="200pxl">Q1w2e3r4t5</td>
</tr>
<tr>
<td valign="top" width="200pxl">ldap</td>
<td valign="top" width="200pxl">ownersDN</td>
<td valign="top" width="200pxl">Use the default value to connect the development LDAP.</td>
<td valign="top" width="200pxl">ou=k2venvownerg,ou=system</td>
</tr>
<tr>
<td valign="top" width="200pxl">ldap</td>
<td valign="top" width="200pxl">testersDN</td>
<td valign="top" width="200pxl">Use the default value to connect the development LDAP.</td>
<td valign="top" width="200pxl">ou=k2vtestg,ou=system</td>
</tr>
<tr>
<td valign="top" width="200pxl">ldap</td>
<td valign="top" width="200pxl">ownersGroupName</td>
<td valign="top" width="200pxl">The group name of the environment owners users. Use the default value to connect the development LDAP.</td>
<td valign="top" width="200pxl">k2venvownerg</td>
</tr>
<tr>
<td valign="top" width="200pxl">ldap</td>
<td valign="top" width="200pxl">testersGroupName</td>
<td valign="top" width="200pxl">The group name of the testers users. Use the default value to connect the development LDAP.</td>
<td valign="top" width="200pxl">k2vtestg</td>
</tr>
<tr>
<td valign="top" width="200pxl">ldap</td>
<td valign="top" width="200pxl">baseCN</td>
<td valign="top" width="200pxl">The the value as follows to connect the Microsoft Active Directory: CN=Users,DC=k2vfabric,DC=local</td>
<td valign="top" width="200pxl">DC=training,DC=k2view,DC=com</td>
</tr>
<tr>
<td valign="top" width="200pxl">fabricWsUrl</td>
<td valign="top" width="200pxl">url</td>
<td valign="top" width="200pxl">Edit the URL and set the IP address of Fabric. Create the [tdm-WS token] in Fabric and grant it permissions on all Fabric Web-Services.</td>
<td valign="top" width="200pxl">http://62.90.46.136:3213/ws?format=json&amp;token=tdm-WS</td>
</tr>
<tr>
<td valign="top" width="200pxl">fabricWsUrl</td>
<td valign="top" width="200pxl">List of Fabric APIs invoked by the TDM GUI</td>
<td valign="top" width="200pxl">&nbsp;</td>
<td valign="top" width="200pxl">&nbsp;</td>
</tr>
<tr>
<td valign="top" width="200pxl">fabricWsUrlFormatHTML</td>
<td valign="top" width="200pxl">url</td>
<td valign="top" width="200pxl">Edit the URL and set the IP address of Fabric. Create the [tdm-WS token] in Fabric and grant it permissions on all Fabric Web-Services.</td>
<td valign="top" width="200pxl">http://62.90.46.136:3213/ws?format=json&amp;token=tdm-WS</td>
</tr>
<tr>
<td valign="top" width="200pxl">retentionPeriod</td>
<td valign="top" width="200pxl">maxRetentionPeriod</td>
<td valign="top" width="200pxl">Maximum <a href="/articles/TDM/tdm_gui/16_extract_task.md#retention-period">retention period</a> in days to define on Extract tasks.</td>
<td valign="top" width="200pxl">90</td>
</tr>
<tr>
<td valign="top" width="200pxl">retentionPeriod</td>
<td valign="top" width="200pxl">defaultPeriod</td>
<td valign="top" width="200pxl">The default retention period of Extract task.</td>
<td valign="top" width="200pxl">"unit" : "Days", "value": 5</td>
</tr>
<tr>
<td valign="top" width="200pxl">availableOptions</td>
<td valign="top" width="200pxl">name, units</td>
<td valign="top" width="200pxl">The available options to set the retention period on Extract tasks.</td>
<td valign="top" width="200pxl">&nbsp;</td>
</tr>
</table>



### Constants.js File

The constants.js configuration file is used by the TDM GUI and located under ~/TDM//k2vtdmfe/app/js/constants directory.

Edit the **url** attribute of **BE_BASE_URL** as follows:

- Edit the IP address to the TDM server IP address.

- Replace the **http** by **https** to connect the TDM GUI in https mode.

  

## TDM DB - General Parameters

The [tdm_general_parameters](/articles/TDM/tdm_architecture/02_tdm_database.md#tdm_general_parameters) TDM DB table holds the following parameters:

- [TDM Clean-up](/articles/TDM/tdm_architecture/06_tdmdb_cleanup_process.md) parameters. These parameters are automatically created in **tdm_general_parameters** by the TDMDB creation scripts.

- [LUI separator](/articles/TDM/tdm_implementation/01_tdm_set_instance_per_env_and_version.md#tdm-separator) parameters:

  - By default, the LUI separator is set to underscore. However, a different separator must be set on the LUIs if the source entity ID can contain underscore. 
  - For example, if the source Customer ID is 123_4, then the separator of the LUI must be different than underscore to enable the TDM process to parse the LUI correctly and get the correct Customer ID.
  - The **param_name** of the LUI separator is **iid_separator**.  The **param_value** needs to be populated by the String set as a separator.  
  - Note that the iid_separator setting impacts on all the project's LUs.

  

  **Example**:

  - Insert the following record to tdm_general_parameters to set the separator to @ : 

    ```sql
  	insert into tdm_general_parameters (param_name, param_value) values ('iid_separator', '@');
  	```
  	
  - The LUI of Customer 123_4 and environment ENV1 is **ENV1@123_4**.