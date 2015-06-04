# smartdevs-indexer
Optimations for Magento catalog_product_index_eav performance

This module increase the performance during full reindexing of catalog_product_index_eav. 
The idea behind was to reduce the write load to MySQL Innodb transactionlog. Another reason for creating this module was to reclaim used table space inside the innodb buffer pool. The Regular way Magento uses the indexing uses full deletes to tables which is produced heavy IO based load. Also the transaction log grows fast. This module is fixing some queries and uses table rotation for full reindex. Update on save uses tempoary tables of mysql instead of deleting all rows in tmp tables in an transaction.

Keep in Mind that this solution can have side effects and only works with mysql. 
Its tested against Magento 1.9 and working in Production. 
