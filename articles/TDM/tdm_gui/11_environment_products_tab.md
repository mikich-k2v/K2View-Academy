# Environment Products Tab

A [TDM Product](05_tdm_gui_product_window.md) represents a system or application installed in the source or target environment. Each testing environment must have at least one product. A product can be added, edited or deleted from the environment by an Admin user or the [Environment Owner](08_environment_window_general_information.md#environment-owners) of the environment.  

The environment products are displayed in the **Products tab** of the Environment window:

- To add a new Product to the environment, click the **Add Product** button, populate the product's setting and click the **Add** button.
- To open a selected Product, click the **Name** setting of the product.  Click the **Save Changes** to save the updates. 
- To delete a Product, click the [![be_Example](https://github.com/k2view-academy/K2View-Academy/raw/Academy_6.4_TDM/articles/TDM/tdm_gui/images/delete_icon.png)](https://github.com/k2view-academy/K2View-Academy/blob/Academy_6.4_TDM/articles/TDM/tdm_gui/images/delete_icon.png) icon in the right corner of the Product window.

## Environment Product Window 

The Product Window in the Environment Window holds the following settings:

- **Product Name** -  select a product from the dropdown list of products.
- **Data Center Name** - this is the Data Center where the product is physically located in the environment. For example, ENV1 may have a CRM located in NY and a Billing located in TX. Select a data center from the dropdown list of data centers.

- **Product Version** -  the version of the installed product in the environment. For example, Production environment has CRM  V1  and Dev1 environment has CRM V1.5.  Select a version from the dropdown list of available versions of the product.

  [Click for more information about supporting multiple Product versions via TDM].

  

  Note that the connection details of environment products' data sources (interfaces) are populated and saved in Fabric.

  

   [![Previous](/articles/images/Previous.png)](10_environment_roles_tab.md)[<img align="right" width="60" height="54" src="/articles/images/Next.png">](12_environment_globals_tab.md)