# ER図

```mermaid
---
title: "メダコレデータベース"
---
erDiagram
    user ||--o{ user_album: ""
    user_album }o--|| album: ""
    album ||--o{ medal: ""
    album ||--o{ tag: ""
    medal }|--|| purchase_location: ""
    medal ||--o{ medal_tag: ""
    album ||--o{ purchase_location: ""
    medal_tag }o--|| tag: ""

  user {
    int user_id PK "ユーザーID"
    varchar user_name "ユーザー名"
    varchar user_image_path "ユーザー画像"
    varchar email UK "メールアドレス"
    varchar hashed_password "パスワード (ハッシュ化)"
    timestamp created_at "作成日時"
    timestamp updated_at "更新日時"
  }

  user_album {
    int user_id PK "ユーザーID"
    int album_id PK "アルバムID"
    timestamp created_at "作成日時"
    timestamp updated_at "更新日時"
  }

  album {
    int album_id PK "アルバムID"
    char album_share_key UK "アルバム共有キー"
    varchar album_name "アルバム名"
    timestamp created_at "作成日時"
    timestamp updated_at "更新日時"
  }

  medal {
    int medal_id PK "メダルID"
    int album_id FK "アルバムID"
    varchar medal_name "メダル名"
    varchar medal_image_path "メダル画像"
    int purchase_location_id FK "購入場所ID"
    timestamp purchase_date "購入日時"
    text memo "メモ"
    timestamp created_at "作成日時"
    timestamp updated_at "更新日時"
  }

  medal_tag {
    int medal_id PK,FK "メダルID"
    int tag_id PK,FK "タグID"
    timestamp created_at "作成日時"
    timestamp updated_at "更新日時"
  }

  tag {
    int tag_id PK "タグID"
    int album_id FK "アルバムID"
    varchar tag_name "タグ名"
    timestamp created_at "作成日時"
    timestamp updated_at "更新日時"
  }

  purchase_location {
    int purchase_location_id PK "購入場所ID"
    int album_id FK "アルバムID"
    varchar purchase_location_name "購入場所名"
    timestamp created_at "作成日時"
    timestamp updated_at "更新日時"
  }
```