```startuml
@startuml
!define MASTER_MARK_COLOR Orange 
!define TRANSACTION_MARK_COLOR DeepSkyBlue
!define MAIN_ENTITY #MintCream-MistyRose
skinparam class {
    BackgroundColor Snow
    BorderColor Black
    ArrowColor Black
}
package "ECサイト" as target_system {
    entity "顧客マスタ" as user<<M,MASTER_MARK_COLOR>> {
        + user_id [PK]
        --
          pass
          name
          mail
          del_flag
          reg_date
    }
    entity "購入テーブル" as purchase<<T,TRANSACTION_MARK_COLOR>> {
        + order_id [PK]
        --
        user_id [FK]
        purchase_date
        total_price
    }
    entity "購入詳細テーブル" as purchase_detail<<T,TRANSACTION_MARK_COLOR>> {
        + order_id [PK]
        + detail_id
        --
        item_code [FK]
        price
        num
    }
    entity "商品マスタ" as item<<M,MASTER_MARK_COLOR>> {
        + item_id [PK]
        --
        itemdetail_id [FK]
        item_name
        image
    }
    entity "商品詳細マスタ" as item_detail<<M,MASTER_MARK_COLOR>> {
        + itemdetail_id [PK]
        --
        item_name
        price
        image
        detail
        del_flag
        reg_date
    }
    
    user |o-ri-o{ purchase
    purchase ||-|{ purchase_detail
    purchase_detail }-do-|| item
    item_detail ||-ri-o{ item
@enduml
```
