# Data dictionnary

## PRODUCTS (`product`)
|#|Column Name|Data Type|Characteristics|Description|
|-|-|-|-|-|
|1|id|INT|PRIMARY KEY, NOT NULL, UNSIGNED, AUTO_INCREMENT|Product's id|
|2|name|VARCHAR(64)|NOT NULL|Product's name|
|3|price|DECIMAL(10, 2)|NOT NULL, DEFAULT 0|Product's price|
|4|category_id|entity|NOT NULL|Product's category|
|5|brand_id|entity|NOT NULL|Product's brand|
|6|status|TINYINT(1)|NOT NULL, DEFAULT 0|Product' status (1=available, 2=unavailable)|
|7|picture_hd|VARCHAR(128)|NULL|Product's hd picture URL|
|8|picture_tn|VARCHAR(128)|NULL|Product's thumbnail picture URL|
|9|description|TEXT|NULL|Product's description|
|10|rating|TINYINT(1)|NOT NULL, DEFAULT 0|Product's customers rating|
|11|created_at|TIMESTAMP|NOT NULL, DEFAULT CURRENT_TIMESTAMP|Product's creation datetime|
|12|updated_at|TIMESTAMP|NULL|Product's latest update datetime|

## CATEGORIES (`category`)
|#|Column Name|Data Type|Characteristics|Description|
|-|-|-|-|-|
|1|id|INT|PRIMARY KEY, NOT NULL, UNSIGNED, AUTO_INCREMENT|Category's id|
|2|name|VARCHAR(64)|NOT NULL|Category's name|
|3|created_at|TIMESTAMP|NOT NULL, DEFAULT CURRENT_TIMESTAMP|Category's creation datetime|
|4|updated_at|TIMESTAMP|NULL|Category's latest update datetime|

## BRANDS (`brand`)
|#|Column Name|Data Type|Characteristics|Description|
|-|-|-|-|-|
|1|id|INT|PRIMARY KEY, NOT NULL, UNSIGNED, AUTO_INCREMENT|Brand's id|
|2|name|VARCHAR(64)|NOT NULL|Brand's name|
|3|created_at|TIMESTAMP|NOT NULL, DEFAULT CURRENT_TIMESTAMP|Brand's creation datetime|
|4|updated_at|TIMESTAMP|NULL|Brand's latest update datetime|

## OS (`os`)
|#|Column Name|Data Type|Characteristics|Description|
|-|-|-|-|-|
|1|id|INT|PRIMARY KEY, NOT NULL, UNSIGNED, AUTO_INCREMENT|OS' id|
|2|name|VARCHAR(64)|NOT NULL|OS' name|
|3|logo_hd|VARCHAR(128)|NULL|OS' hd logo URL|
|4|logo_tn|VARCHAR(128)|NULL|OS' thumbnail logo URL|
|5|created_at|TIMESTAMP|NOT NULL, DEFAULT CURRENT_TIMESTAMP|OS' creation datetime|
|6|updated_at|TIMESTAMP|NULL|OS' latest update datetime|

## PRODUCTS SUPPORTED OS (`product_supports_os`) *junction table*
|#|Column Name|Data Type|Characteristics|Description|
|-|-|-|-|-|
|1|product_id|INT|NOT NULL|Product's id|
|2|os_id|INT|NOT NULL|OS' id|

## TAGS (`tag`)
|#|Column Name|Data Type|Characteristics|Description|
|-|-|-|-|-|
|1|id|INT|PRIMARY KEY, NOT NULL, UNSIGNED, AUTO_INCREMENT|Tag's id|
|2|name|VARCHAR(64)|NOT NULL|Tag's name|
|3|created_at|TIMESTAMP|NOT NULL, DEFAULT CURRENT_TIMESTAMP|Tag's creation datetime|
|4|updated_at|TIMESTAMP|NULL|Tag's latest update datetime|

## PRODUCTS ASSOCIATED TAGS (`product_has_tag`) *junction table*
|#|Column Name|Data Type|Characteristics|Description|
|-|-|-|-|-|
|1|product_id|INT|NOT NULL|Product's id|
|2|tag_id|INT|NOT NULL|Tag's id|

## CUSTOMERS (`customer`)
|#|Column Name|Data Type|Characteristics|Description|
|-|-|-|-|-|
|1|id|INT|PRIMARY KEY, NOT NULL, UNSIGNED, AUTO_INCREMENT|Customer's id|
|2|firstname|VARCHAR(64)|NOT NULL|Customer's firstname|
|3|lastname|VARCHAR(64)|NOT NULL|Customer's lastname|
|4|email|VARCHAR(128)|NOT NULL|Customer's email|
|5|password|VARCHAR(64)|NOT NULL|Customer's lastname|
|6|status|TINYINT(1)|NOT NULL, DEFAULT 0|Customer's status (1=active, 2=inactive)|
|7|address_1|VARCHAR(128)|NOT NULL|Customer's address line 1|
|8|address_2|VARCHAR(128)|NOT NULL|Customer's address line 2|
|9|address_3|VARCHAR(128)|NOT NULL|Customer's address line 3|
|10|zip|VARCHAR(64)|NOT NULL|Customer's zip code|
|11|city|VARCHAR(64)|NOT NULL|Customer's city|
|12|state|VARCHAR(64)|NOT NULL|Customer's state|
|13|country|VARCHAR(64)|NOT NULL|Customer's country|
|14|created_at|TIMESTAMP|NOT NULL, DEFAULT CURRENT_TIMESTAMP|Customer's creation datetime|
|15|updated_at|TIMESTAMP|NULL|Customer's latest update datetime|

## ORDERS (`order`)
|#|Column Name|Data Type|Characteristics|Description|
|-|-|-|-|-|
|1|id|INT|PRIMARY KEY, NOT NULL, UNSIGNED, AUTO_INCREMENT|Order's id|
|2|customer_id|INT|NOT NULL|Related customer's id|
|3|amount|DECIMAL(10, 2)|NOT NULL, DEFAULT 0|Order's amount|
|4|status|TINYINT(1)|NOT NULL, DEFAULT 0|Order's status|
|5|created_at|TIMESTAMP|NOT NULL, DEFAULT CURRENT_TIMESTAMP|Customer's creation datetime|
|6|updated_at|TIMESTAMP|NULL|Customer's latest update datetime|

## ORDERS STATUSES (`order-status`)
|#|Column Name|Data Type|Characteristics|Description|
|-|-|-|-|-|
|1|id|INT|PRIMARY KEY, NOT NULL, UNSIGNED, AUTO_INCREMENT|Status' id|
|2|name|VARCHAR(64)|NOT NULL|Status' name|

## ORDERS DETAILS (`order_contains_product`) *junction table*
|#|Column Name|Data Type|Characteristics|Description|
|-|-|-|-|-|
|1|order_id|INT|NOT NULL|Order's id|
|2|product_id|INT|NOT NULL|Product's id|
|3|price|DECIMAL(10, 2)|NOT NULL, DEFAULT 0|Product's price|
|4|discount|DECIMAL(10, 2)|NOT NULL, DEFAULT 0|Product's price discount|
|5|quantity|TINYINT(1)|NOT NULL, DEFAULT 0|Quantity of product's unit|