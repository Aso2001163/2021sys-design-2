# DB定義書
## E-R図
[E-R図](https://github.com/Aso2001152/2021sys-design/blob/main/Sample_E-R.md)

## DBテーブルカラム詳細一覧
### 購入テーブル(d_purchase)
|属性名|型|PK|NN|FK|
|-----|--|--|--|--|
|order_id|bigint(20)|○|○||
|customer_code|varchar(50)||○||
|purchase_date|date||○||
|total_price|int(11)||○||

### 購入テーブル詳細(d_purchase_detail)
|属性名|型|PK|NN|FK|
|-----|--|--|--|--|
|detail_id|bigint(20)|○|○||
|ourder_id|bigint(20)|○|○|○|
|item_code|int(11)||○||
|price|int(11)||○||
|num|int(11)||○||

### 顧客テーブル(m_customers)
|属性名|型|PK|NN|FK|
|-----|--|--|--|--|
|costomer_code|varchar(50)|○|○||
|pass|varchar(50)|○|○|○|
|name|varchar(20)||○||
|tel|varchar(20)||○||
|mail|varchar(100)||○||
|del_flag|int(1)||||
|reg_date|date||○||

### カテゴリテーブル(m_category)
|属性名|型|PK|NN|FK|
|-----|--|--|--|--|
|category_id|int(11)|○|○||
|name|varchar(20)||○||
|reg_date|date||○||

### 商品テーブル(m_items)
|属性名|型|PK|NN|FK|
|-----|--|--|--|--|
|item_code|int(11)|○|○||
|item_name|varchar(50)||○||
|price|int(11)||○||
|category_id|int(11)||○|○|
|image|varchar(200)||○||
|detail|varchar(500)||||
|del_flag|int(11)||||
|reg_date|date||○||
