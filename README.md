# README

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null: false,unique: true|
|name|string|index: true, null: false|
|email|string|null: false|
|password|string|null: false

### Association
- has_many :messages
- has_many :groups, through: :groups_users
- has_many :groups_users

## groups テーブル

|Column|Type|Options|
|------|----|-------|
|id|inteager|null: false, unique: true|
|name|string|index: true, null: false|

### Association
- has_many :messages
- has_many :users, through: :groups_users
- has_many :groups_users

## message テーブル

|Column|Type|Options|
|------|----|-------|
|id|integer|null: false, unique: true|
|body|text|
|image|string
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|foreign_key: true|
|create_time|timestamp|null: false|

### Association
- belongs_to :user
- belongs_to :group

## groups_users テーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user