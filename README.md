# README

# Moments DB設計

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false, unique: true|
|email|string|null: false, unique: true|
|password|string|null: false, unique: true|

### Association
- has_many :tweets, dependent: :destroy
- has_many :comments
- has_many :likes, dependent: :destroy
- has_many :like_tweets, through: :likes, source: :tweet


## tweetsテーブル
|Column|Type|Options|
|------|----|-------|
|text|string||
|image|text||
|user_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :user
- has_many :comments
- has_many :likes, dependent: :destroy
- has_many :liking_users, through: :likes, source: :user

## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false|
|tweet_id|tweet_id|null: false|
|text|text|null: false|

### Association
- belongs_to :user
- belongs_to :tweet

## likesテーブル
|Column|Type|Options|
|------|----|-------|
|user|integer|null: false, foreign_key: true|
|tweet|integer|null: false, foreign_key: true|

### Association  presence: true
- belongs_to :user
- belongs_to :tweet
