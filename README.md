# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# database設計

## usersテーブル

|Column|Type|Option|
|------|----|------|
|name|string|null:false|
|password|string|null:false|
|email|string|null:false|
|image|string|

### Association
  - has_many comments
  - has_many lists
  - has_many likes

## commentsテーブル

|Column|Type|Option|
|------|----|------|
|content|text|null:false|
|image|string|
|user_id|references|null:false,foreign_key: true|
|list_id|references|null:false,foreign_key: true|

### Association
  - belongs_to user
  - belongs_to list

## listsテーブル
|Column|Type|Option|
|------|----|------|
|content|text|
|image|string|
|target_year|integer|
|budget|integer|

### Association

  - belongs_to user
  - has_many comments
  - has_many likes

## likesテーブル

|Column|Type|Option|
|------|----|------|
|user_id|references|null:false,foreign_key: true|
|list_id|references|null:false,foreign_key: true|

  - belongs_to user
  - belongs_to list