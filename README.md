# テーブル設計

## users テーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| nick_name          | string | null: false |
| email              | string | null: false |
| encrypted_password | string | null: false |
| last_name          | string | null: false |
| first_name         | string | null: false |
| last_name_kana     | string | null: false |
| first_name_kana    | string | null: false |
| birth_day          | string | null: false |

### Association

- has_many :items
- has_many :purchases


## items テーブル

| Column             | Type          | Options     |
| ------------------ | ------------- | ----------- |
| item_image         | ActiveStorage |             |
| item_name          | string        | null: false |
| explanation        | text          | null: false 
| category           | string        | null: false |
| condition          | string        | null: false |
| price              | string        | null: false |

### Association

- belongs_to :user
- has_one :destination

##  purchaseテーブル

| Column   | Type   | Options     |
| ------   | -------| ------------|
| card     | string | null: false |
| email    | string | null: false |
| expire   | string | null: false |
| security | string | null: false |

- belongs_to :user

## destinetion テーブル

| Column   | Type   | Options     |
| -------- | -------| ------------|
| name     | string | null: false |
| email    | string | null: false |
| expire   | string | null: false |
| security | string | null: false |

- belongs_to :item