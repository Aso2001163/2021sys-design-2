# DB定義書
## E-R図
[E-R図](https://github.com/Aso2001152/2021sys-design/blob/main/Mypage(E-R%E5%9B%B3).md)

## DBテーブルカラム詳細一覧
### 購入テーブル
|和名|属性名|型|PK|NN|FK|
|----|-----|--|--|--|--|
|オーダーID|order_id|bigint(20)|○|○||
|ユーザーID|user_id|varchar(50)||○|○|
|購入日|purchase_date|date||○||
|総額|total_price|int(11)||○||

### 購入テーブル詳細
|和名|属性名|型|PK|NN|FK|
|----|-----|--|--|--|--|
|オーダー詳細ID|detail_id|bigint(20)|○|○||
|オーダーID|ourder_id|bigint(20)|○|○|○|
|商品コード|item_code|int(11)||○||
|価格|price|int(11)||○||
|数量|num|int(11)||○||

### 顧客テーブル
|和名|属性名|型|PK|NN|FK|
|----|-----|--|--|--|--|
|ユーザーID|user_id|varchar(50)|○|○||
|パスワード|pass|varchar(50)|○|○|○|
|氏名|name|varchar(20)||○||
|メールアドレス|mail|varchar(100)||○||
|削除フラグ|del_flag|int(1)||||
|登録日|reg_date|date||○||

### カテゴリテーブル
|和名|属性名|型|PK|NN|FK|
|----|-----|--|--|--|--|
|カテゴリID|category_id|int(11)|○|○||
|氏名|name|varchar(20)||○||
|登録日|reg_date|date||○||

### 商品テーブル
|和名|属性名|型|PK|NN|FK|
|----|-----|--|--|--|--|
|商品コード|item_code|int(11)|○|○||
|商品名|item_name|varchar(50)||○||
|価格|price|int(11)||○||
|カテゴリID|category_id|int(11)||○|○|
|画像ファイル名|image|varchar(200)||○||
|商品詳細説明|detail|varchar(500)||||
|削除フラグ|del_flag|int(11)||||
|登録日|reg_date|date||○||
