# chat-space DB設計
## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
|image|text|
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|name|string|null: false|
### Association
- has_many :messages
- has_many :groups, through: groups_users
- has_many :groups_users

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|group_name|string|null: false|

### Association
- has_many :messages
- has_many :users, through: groups_users
- has_many :groups_users

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user
