# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation


# データベース設計

## messagesテーブル
|Colume|Type|Options|
|content|string||
|image|string||
|user_id|integer|null: false, foreign_key: user_id|
|group_id|integer|null: false, foreign_key: group_id|
### アソシエーション
belongs_to :group
belongs_to :user


## groups_usersテーブル
|Colume|Type|Options|
|group_id|null: false, foreign_key: true|
|user_id|null: false, foreign_key: true|
### アソシエーション
belongs_to :group
belongs_to :user


## groupsテーブル
|Colume|Type|Options|
|name|string|null: false|
### アソシエーション
has_many :messages
has_many :groups, through: groups_users
has_many :groups_users


## usersテーブル
|Colume|Type|Options|
|name|string|null: false, index: true|
|email|string|null: false, unique: true|
### アソシエーション
has_many: messages
has_many: groups, through: groups_users
has_many: groups_users


* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...
