```uml
@startuml

skinparam class {
    BackgroundColor Snow
    BorderColor Black
    ArrowColor Black
}

!define MASTER_MARK_COLOR Orange 
!define TRANSACTION_MARK_COLOR DeepSkyBlue

package "ECサイト" as EC_system {
    entity "顧客マスタ" as customer <m_customers> <<M,MASTER_MARK_COLOR>> {
        + customer_code [PK]
        --
        pass
        name
        address
        credit
        del_flag
        reg_date
    }
    
    entity "購入テーブル" as order <order> <<T,TRANSACTION_MARK_COLOR>> {
        + order_id [PK]
        --
        # customer_code [FK]
        purchase_date
        total_price
    }
    
    entity "購入詳細テーブル" as order_detail  <order_detail> <<T,TRANSACTION_MARK_COLOR>> {
        + detail_id[PK]
        + order_id[PK]
        --
        # item_code [FK]
        price
        num
    }
entity "お知らせテーブル" as d_notice <d_notice> <<T,TRANSACTION_MARK_COLOR>> {
+ notice_code [PK]
--
notice_detail
reg_date
}

entity "お気に入りテーブル" as d_favorite <d_favorite> <<T,TRANSACTION_MARK_COLOR>> {
+ customer_code [PK][FK]
+ item_code [PK][FK]
--
item_name
image
detail
price
}

entity "カートテーブル" as d_cart <d_cart> <<T,TRANSACTION_MARK_COLOR>> {
+ customer_code [PK][FK]
+ item_code [PK][FK]
--
item_name
image
detail
price
num
}

   entity "商品マスタ" as items <m_items> <<M,MASTER_MARK_COLOR>> {
        + item_code [PK]
        --
        item_name
        price
        # category_id [FK]
        image
        detail
        del_flag
        reg_date
    }
    
    entity "カテゴリマスタ" as category <m_category> <<M,MASTER_MARK_COLOR>> {
        + category_id [PK]
        --
        name
        reg_date
    }

entity "管理者マスタ" as master <m_master> <<M,MASTER_MARK_COLOR>> {
+ master_code [PK]
--
pass
name
master_flag
}
}

   d_favorite }o-|| customer
   d_favorite }o-|| items
   d_cart }-|| customer
   d_cart }-o| items
   customer       |o-ri-o{     order
   order          ||-ri-|{     order_detail
   order_detail    }-do-||     items
   items          }o-le-||     category


@enduml
```
