## usersテーブル

|Column                         |Type   |Options                  |
|-------------------------------|-------|-------------------------|
|nickname                       |string |null: false              |
|email                          |string |null: false, unique: true|
|encrypted_password             |string |null: false              |
|encrypted_password_confirmation|string |null: false              |
|first_name                     |string |null: false              |
|last_name                      |string |null: false              |
|first_name_kana                |string |null: false              |
|last_name_kana                 |string |null: false              |
|birthday_year                  |integer|null: false              |
|birthday_month                 |integer|null: false              |
|birthday_day                  |integer|null: false              |

### Association
- has_many  :items
- has_many  :purchase_recode

## itemsテーブル

|Column          |Type      |Options                       |
|----------------|----------|------------------------------|
|item_name       |string    |null: false                   |
|item_description|text      |null: false                   |
|item_category   |integer   |null: false                   |
|item_status     |integer   |null: false                   |
|delivery_pay    |integer   |null: false                   |
|send_prefecture |integer   |null: false                   |
|send_day        |integer   |null: false                   |
|item_price      |integer   |null: false                   |
|user_id         |references|null: false, foreign_key: true|

### Association
- belongs_to :user
- has_one   :purchase_recode

## purchase_recodeテーブル

|Column  |Type      |Options                       |
|--------|----------|------------------------------|
|user_id |references|null: false, foreign_key: true|
|item_id |references|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :item
- has_one    :shipping_address

## shipping_address

|Column               |Type      |Options    |
|---------------------|----------|-----------|
|postal_code          |string    |null: false|
|prefecture           |integer   |null: false|
|municipalities       |string    |null: false|
|house_number         |string    |null: false|
|building_name        |string    |           |
|telephone_number     |string    |null: false|


### Association
- belongs_to :purchase_recode