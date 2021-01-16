# TDM GUI - User Types

Since the TDM GUI authenticates users via LDAP, all TDM users must be defined in the LDAP application.  

There are three main types of TDM users, each with different permissions for different activities.

Note that all TDM windows can be accessed by all users in View mode. However, only authorized users with the relevant permissions can update TDM definitions.

## Admin 

The Admin can execute all activities in the TDM GUI application. Admins are defined as **admin** in the TDM **config.js**. Their user and password are authenticated via LDAP.

Admins usually also define the [TDM implementation in Fabric](/articles/TDM/tdm_implementation/03_tdm_fabric_implementation_flow.md). They can execute all activities in the TDM GUI and are responsible for the following activities:

- Create, edit or delete [products].
- Create, edit or delete [Business Entities](/articles/TDM/tdm_overview/03_business_entity_overview.md) and attach Logical Units or [post execution processes] to each Business Entity.
- Create, edit or delete [environments].
- Attach environment owners to each environment.
- Define [roles] in each environment and define permissions per role.

## Environment Owner 

The Environment Owner is the owner of a TDM testing environment. Admins can define one or several Environment Owners for each testing environment. 
Environment Owners must be defined in LDAP under a dedicated group of users that can be assigned as Environment Owners. 

The TDM application identifies users with Environment Owners permissions by their LDAP group.

Environment Owners can execute the following activities in their environment:

- Edit details.
- Add or remove [products].
- Add or remove [Globals].
- Add, edit or remove [Exclusion Lists].
- Create, edit or delete [TDM roles] and define permissions per role.
- Attach users to TDM roles.

Note that Environment Owners cannot add or delete an environment and cannot add or remove Environment Owners from the environment.

## Tester User

A Tester can create, extract or load tasks based on their role. 





[![Previous](/articles/images/Previous.png)](01_tdm_gui_overview.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](04_fabric_tdm_library.md)
