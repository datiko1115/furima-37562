# テーブル設計 

## usersテーブル
| Column             | Type   | Options                   | 
| ------------------ | ------ | ------------------------- |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |
| first_name         | string | null: false               |
| last_name          | string | null: false               |
| first_kana         | string | null: false               |
| last_kana          | string | null: false               |
| nickname           | string | null: false               |
| birthday           | date   | null: false               |

### Association
- has_many :items
- has_many :orders

## itemsテーブル
| Column         | Type        | Options                        |
| -------------- | ----------- | ------------------------------ |
| item_name      | string      | null: false                    |
| description    | text        | null: false                    |
| category_id    | integer     | null: false                    |
| price          | integer     | null: false                    |
| condition_id   | integer     | null: false                    |
| recipient_id   | integer     | null: false                    |
| prefecture_id  | integer     | null: false                    |
| shipment_id    | integer     | null: false                    |
| user           | references  | null: false, foreign_key: true |

### Association
- belongs_to :user
- has_one :order

## ordersテーブル
| Column    | Type       | Options                        |
| --------- | ---------- | ------------------------------ |
| user      | references | null: false, foreign_key: true |
| item      | references | null: false, foreign_key: true |

### Association
- belongs_to :user
- belongs_to :item
- has_one :address

## addressesテーブル
| Column         | Type       | Options                        |
| -------------- | ---------- | ------------------------------ |
| postcode       | string     | null: false                    |
| prefecture_id  | integer    | null: false                    |
| city           | string     | null: false                    |
| address        | string     | null: false                    |
| building       | string     |                                |
| phone          | string     | null: false                    |
| order          | references | null: false, foreign_key: true |

### Association
- belongs_to :order