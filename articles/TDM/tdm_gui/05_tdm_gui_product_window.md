# Product Windows

A TDM Product represents a system or application installed in the source or target environment. For example, the UAT1 environment contains CRM and Billing products. Each product can have multiple data sources (interfaces). For example, the Billing product has the Billing and Usage DBs.

A TDM Product contains the following components:

- Product name, a logical name that identifies the product (system). For example, CRM.
- Product versions, the versions of the product as defined in testing environments. For example, Production and Development.

- Logical Units (LUs).

## BE and LU Product Relationship

Each BE and LU combination can be attached to one product only. However, a product can have LUs belonging to different BEs.

The following example displays the relationship between a BE, LU, and Product:

![be-prod-lu](images/be_lu_product_relation.png)



## Products List Window

The **Products** window displays a list of all Products defined in the TDM.  Only **Admin users** can create, edit, or delete a Product. Other users can open Products for view only purposes.

-   To create a new Product, click the **Add Product** button.
-   To open a selected Product, click the Product's **Name**.
-   To delete a Product, click ![delete](images/delete_icon.png) in the right corner of the Product window.

## Product Window

The Product window displays information about a selected Product. It has two main sections: 

- General Information.
- Logical Units.

### General Information

The General Information section has the following settings:

- Name. Populated by the product name.

- Vendor and Description, optional settings.

- Versions, product versions which enable the TDM implementation to support multiple versions of the product.

  -  Each product version may have a different data source structure. For example, a development environment may have new tables and fields that are not in the production environment. 
  - At least one version must be set for a Product. Multiple product versions can also be set. 
  - The relevant product version must be selected when adding a Product to an [Environment].

To add a version to a Product, click ![delete](images/plus_icon_prod_version.png) next to the Product Versions setting and enter the version value which is a logical identifier of the product version. For example 1, 1.5, dev or prod. The values must be aligned to the TDM Fabric implementation. 

  [Click for more information about supporting multiple Product versions via TDM].

### Logical Units

#### How Do I Add an LU to a Product?

Click ![plus](images/plus_icon.png) to open the **Add Logical Unit** dialog box.

  ![add_lu](images/prod_add_lu.png)

- The **Business Entities** setting displays a list of BEs with available LUs that are not attached to any product.

- The **Logical Unit Name** setting displays the list of available LUs that are not attached to any product and belong to the selected BE.

  

#### How Do I Delete an LU from a Product ? 

Click ![be_delete](images/delete_icon.png) to delete the selected LU from the Product.

  [Click for more information about the Product related TDM DB tables](/articles/TDM/tdm_gui/06_be_product_tdmdb_tables.md).

 [![Previous](/articles/images/Previous.png)](04_tdm_gui_business_entity_window.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](06_be_product_tdmdb_tables.md)
