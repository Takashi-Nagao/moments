# README



# アプリ名
　　　『　Moments　』



# アプリ詳細
アプリURL
http://54.168.45.251

・実装機能
　　・投稿（表示・作成・保存・削除・編集）機能
　　・ユーザー登録、ログイン機能
　　・投稿検索機能（非同期）
　　・投稿に対するコメント機能(非同期）
　　・画像投稿機能・いいね機能（非同期）

・企画背景（このアプリでできること）
　　私には1歳の息子（双子）がいます。この１年を過去を振り返った時、写真は沢山のあるのですが、その時の感じたことは書き残せていなことに気づきました。そこでその写真を取った時の成長で感じ取ったものを、写真だけでなく文書と共に残せるブログ形式で投稿することで、将来ブログを見返した時により一層思い出深くものになるのではないかと感じ開発することにしました。また子供自身が大きくなった時に親がどんな気持ちで育ててくれていたのかを過去のブログをみて知ることもできるツールになるのでは無いかと思います。

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
