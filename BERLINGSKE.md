


Setup step by step:

- Add entry to **composer.json** file

    ````json
    {
        "require": {
            "magento/product-community-edition": "2.1.7",
            "composer/composer": "@alpha",
            "berlingskemedia/bm.m2.module.elasticsuite": "1.0.0"
        }
    }
    ````
    
-  After we install plugin on composer if our elasticsearch host is other than ***ELASTICSEARCH_app*** we need to execute query below.
   
   ```mysql
   INSERT INTO core_config_data VALUES (null, 'default', 0, 'smile_elasticsuite_core_base_settings/es_client/servers', 'ELASTICSEARCH_app:9200');
   ```

- Clear cache
    ```php
    php bin/magento cache:flush
    ```
    
- Execute setup:upgrade
    ```php
    php bin/magento setup:upgrade
    ```   
    
- Execute setup:di:compile
    ```php
    php bin/magento setup:di:compile
    ```   
        
    
- Run reindex
    ```php
    php bin/magento indexer:reindex
    ```   
    
After this steps, module should work properly.