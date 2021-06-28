# テーブル設計

## users テーブル

| Column             | Type   | Options                   |
| ------------------ | ------ | ------------------------- |
| nick_name          | string | null: false               |
| email              | string | unique: true, null: false |
| encrypted_password | string | null: false               |
| last_name          | string | null: false               |
| first_name         | string | null: false               |
| last_name_kana     | string | null: false               |
| first_name_kana    | string | null: false               |
| birth_day          | date   | null: false               |

### Association

- has_many :items
- has_many :purchases

## items テーブル

| Column                | Type          | Options           |
| --------------------- | ------------- | ----------------- |
| nick_name             | references    | foreign_key: true |
| name                  | string        | null: false       |
| explanation           | text          | null: false       |
| category_id           | integer       | null: false       |
| condition_id          | integer       | null: false       |
| shipping_fee_id       | integer       | null: false       |
| prefecture_id         | integer       | null: false       |
| scheduled_delivery_id | integer       | null: false       |
| price                 | integer       | null: false       |

### Association

- belongs_to :user
- has_one :destination
- has_one :purchase

##  destinationテーブル

| Column          | Type    | Options     |
| --------------- | ------- | ----------- |
| postal_code     | string  | null: false |
| prefecture_id   | integer | null: false |
| city_id         | integer | null: false |
| address         | string  | null: false |
| building        | string  |             |
| phone_number    | string  | null: false |

### Association

- has_one :purchase


##  purchaseテーブル

| Column      | Type       | Options           |
| ----------- | ---------- | ----------------- |
| user        | references | foreign_key: true |
| item        | references | foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item
- belongs_to :destination


