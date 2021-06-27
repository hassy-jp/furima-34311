# テーブル設計

## users テーブル

| Column             | Type   | Options      |
| ------------------ | ------ | ------------ |
| nick_name          | string | null: false  |
| email              | string | unique: true |
| encrypted_password | string | null: false  |
| last_name          | string | null: false  |
| first_name         | string | null: false  |
| last_name_kana     | string | null: false  |
| first_name_kana    | string | null: false  |
| birth_day          | string | null: false  |

### Association

- has_many :items
- has_many :destination


## items テーブル

| Column                | Type          | Options     |
| --------------------- | ------------- | ----------- |
| item_name             | string        | null: false |
| explanation           | text          | null: false |
| category_id           | integer       | null: false |
| condition_id          | integer       | null: false |
| shipping-fee_id       | integer       | null: false |
| prefecture_id         | integer       | null: false |
| scheduled-delivery_id | integer       | null: false |
| price                 | integer       | null: false |

### Association

- belongs_to :user
- has_one :destination

##  destinationテーブル

| Column      | Type       | Options                        |
| ----------- | ---------- | ------------------------------ |
| user        | references | null: false, foreign_key: true |
| item        | references | null: false, foreign_key: true |
| postal-code | string     | null: false                    |
| prefecture  | string     | null: false                    |
| city        | string     | null: false                    |
| address     | string     | null: false                    |
| building    | string     | null: false                    |
| phone-number| string     | null: false                    |

### Association

- belongs_to :user
- belongs_to :item

