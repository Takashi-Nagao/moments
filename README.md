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
|text|string|presence: true|
|image|text||
|user_id|integer||

### Association
- belongs_to :user
- has_many :comments
- has_many :likes, dependent: :destroy
- has_many :liking_users, through: :likes, source: :user

## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer||
|tweet_id|tweet_id||
|text|text||

### Association
- belongs_to :user
- belongs_to :tweet

## likesテーブル
|Column|Type|Options|
|------|----|-------|
|user|integer|null: false|
|tweet|integer|null: false|

### Association  presence: true
- belongs_to :user
- belongs_to :tweet
