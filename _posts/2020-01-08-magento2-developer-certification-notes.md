---
layout: post
title: Magento2 Certification Notes
description: Notes during magneto2 professional developer certification preparation
---
# Magento2 Certified Professional Developer Notes

### How can plugins be skipped?
If the around method does not call the _callable_, it will prevent the execution of all the plugins next in the chain and the original method call.

### You wrote data upgrade patch to delete one category and add another. What possible issues can occur?
Foreign keys are disabled when startSetup() called. See \Magento\Framework\DB\Adapter\Pdo\Mysql::startSetup line 2884

### CLI commands to update magento2 from 2.x.y to 2.x.z in production?
bin/magento maintenance:enable  
bin/magento cache:clean  
composer update magento/product-community-edition 2.x.z  
bin/magento setup:upgrade  
bin/magento maintenance:disable  

### CLI commands to update magento2 from 2.x.y to 2.x.z in development?
composer require magento/product-community-edition 2.x.z --no-update  
composer upgrade  
bin/magento setup:upgrade  

### You do $product->setData('my_new_attribute', 'value'); and get this error: Cannot call getBackend() on non-object. How you would solve this?
Create a new static attribute.

#### Static Attributes
> Static attributes are attributes stored in the main table of an entity - for catalog products, catalog_product_entity. For example, the attribute sku of catalog products is defined as static. Static attributes are always loaded by Magento, and are useful especially if you want to retrieve information quickly or to optimize lookup of data. A drawback of this type of attributes is that you can't have store-specific values, which is one of the advantages of Magento EAV system.
>  
> Even if you define an attribute as static, Magento won't treat it as such unless you have a corresponding column in the main entity table. If the column is not there, Magento treats the attribute as varchar by default and looks for it in the varchar EAV table for the model - for products, catalog_product_entity_varchar.
>
> If you want to use static attributes in your project, you have to do 2 things in your install/upgrade scripts. First, you need to add a column to the main entity table, with the correct column definition. Next, you need to install your attribute using the addAttribute() method, and define your attribute as static. Please refer to the install scripts of Mage_Catalog to better understand how things work in this case.
>
> If you plan to run often queries based on your custom static attributes, consider adding an index on the new column to speed up data fetching.

### How would you add a database trigger?
Add it via schema patch.

### How to solve data patch dependencies?
Use the getDependencies() method and add array with Classes to depend on.  
See \Magento\Framework\Setup\Patch\DataPatchInterface;

### How is the sort order for before-Plugins?
10 before 20, 20 before 30 and so on.

### How is the sort order for after-Plugins?
30 before 20, 20 before 10 and so on.

### Where can you add new layout types?
See view/frontend/layouts.xml and there you need to add a new node.

### What is the use of db_schema_whitelist.json?
See also these documentation: https://devdocs.magento.com/guides/v2.3/extension-dev-guide/declarative-schema/migration-commands.html#create-whitelist
> The db_schema_whitelist.json file is a way of telling Magento which tables and columns it can safely alter using the db_schema.xml file. It was added to preserve backward compatibility and will be removed in a future version when the install/upgrade script be no longer supported.
> 
> In the current dual state where tables and columns can be added/altered/removed either via setup scripts (those located in the Setup folder) or via the new etc/db_schema.xml files, Magento can not know by itself which tables/columns can be safely altered using only the db_schema.xml files. Hence, the db_schema_whitelist.json holds a list of all the DB tables, columns, indexes, constraints, etc that where created via declarative schema and can therefore be safely altered in case it detects any change for those elements in an upgraded db_schema.xml file. Hope it makes more sense now.

### What can be used instead of setting a "custom price" to update product prices?
A price modifier, example see \Magento\CatalogRule\Model\Product\PriceModifier 

### Which layout handle contains instructions for rendering product price?
view/base/layout/catalog_product_prices.xml

### When you rename a column in magento 2.3 with db_schema.xml what to think about?
Use onCreate="migrateDataFrom(entity_id)" and regenerate db whitelist via cli.

### How can you get the vcl configuration file for varnish?
Use the cli command: bin/magento varnish:vcl:generate

### What is the use case for magento vault?
It is storing customer payment tokens, so at further payments, customers do not need to provide their creditcard number again.

### Where you can add a new cron group for your custom functionality?
etc/cron_groups.xml

### Which calculation values are included in Magento\Catalog\Model\Product::getFinalPrice ?
special price, tier price, catalog price rule

### What must be done differently to properly generate a URL in the magento backend?
Generate the URL from an instance of \Magento\Backend\Model\UrlInterface

### Where is the base template file for all Magento HTML requests located?
vendor/magento/module-theme/view/base/templates/root.phtml

### How to set additional options to quote/order item?
Check this code: https://magento.stackexchange.com/questions/210213/cant-retrieve-custom-option-from-order-items/224529#224529

### What minimum attributes are needed for creating a new category with a setup script?
Name, Is Active, Available Product Listing Sort By

### In which XML-File you define new total models (like tax and shipping)?
etc/sales.xml

### What you need for a custom price calculator after you created a new price model?
Make your new price model extend \Magento\Catalog\Model\Product\Type\Price.  
In your product_types.xml module, reference the simple product type, and set a value for the priceModel attribute. 

### Which container contains columns container?
main.content

### Event that is fired after a user added an item to his cart?
sales_quote_add_item
