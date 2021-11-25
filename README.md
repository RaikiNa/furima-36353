## usersテーブル

|Column                         |Type   |Options                  |
|-------------------------------|-------|-------------------------|
|nickname                       |string |null: false              |
|email                          |string |null: false, unique: true|
|encrypted_password             |string |null: false              |
|first_name                     |string |null: false              |
|last_name                      |string |null: false              |
|first_name_kana                |string |null: false              |
|last_name_kana                 |string |null: false              |
|birthday                       |date   |null: false              |

### Association
- has_many  :items
- has_many  :purchase_records

## itemsテーブル

|Column             |Type      |Options                       |
|-------------------|----------|------------------------------|
|item_name          |string    |null: false                   |
|item_description   |text      |null: false                   |
|category_id        |integer   |null: false                   |
|status_id          |integer   |null: false                   |
|delivery_pay_id    |integer   |null: false                   |
|prefecture_id      |date      |null: false                   |
|send_day_id        |integer   |null: false                   |
|item_price         |integer   |null: false                   |
|user               |references|null: false, foreign_key: true|

### Association
- belongs_to :user
- has_one   :purchase_records

## purchase_recordsテーブル

|Column |Type      |Options                       |
|-------|----------|------------------------------|
|user   |references|null: false, foreign_key: true|
|item   |references|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :item
- has_one    :shipping_address

## shipping_addressesテーブル

|Column               |Type         |Options                       |
|---------------------|-------------|------------------------------|
|postal_code          |string       |null: false                   |
|prefecture           |references   |null: false, foreign_key: true|
|municipalities       |string       |null: false                   |
|house_number         |string       |null: false                   |
|building_name        |string       |                              |
|telephone_number     |string       |null: false                   |
|purchase_recode      |references   |null: false, foreign_key: true|

### Association
- belongs_to :purchase_recode