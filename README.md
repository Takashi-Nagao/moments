# README

# Moments DB設計

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false, unique: true|
|email|string|null: false, unique: true|
|password|string|null: false, unique: true|

### Association


## tweetsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string||
|text|string||
|image|text||
