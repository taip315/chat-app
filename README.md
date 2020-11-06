# テーブル設計

## users テーブル

| Column   | Type    | Options     |
| -------- | ------- | ----------  |
| name     | string  | null: false |
| email    | string  | null: false |
| password | string  | null: false |

### Association

_ has_many :room_users
_ has_many :rooms, through: room_users
_ has_many :messages


## rooms テーブル

| Column   | Type    | Options     |
| -------- | ------- | ----------  |
| name     | string  | null: false |

### Association

_ has_many :room_users
_ has_many :users, through: room_users
_ has_many :messages


## room_users テーブル

| Column   | Type        | Options                       |
| -------- | ----------- | ----------------------------  |
| user     | references  | null: false, foreign_key:true |
| room     | references  | null: false, foreign_key:true |

### Association

_ belongs_to :room
_ belongs_to :user

## messages テーブル
| Column   | Type        | Options                       |
| -------- | ----------- | ----------------------------  |
| content  | string      |                               |
| user     | references  | null: false, foreign_key:true |
| room     | references  | null: false, foreign_key:true | 

### Association

- belongs_to :room
- belongs_to :user