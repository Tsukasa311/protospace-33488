# テーブル設計

## users テーブル

| Column     | Type    | Option         |
| -----------|---------|----------------|
| email      | string  | null: false    |
| password   | string  | null: false    |
| name       | string  | null: false    |
| profile    | text    | null: false    |
| occupation | text    | null: false    |
| position   | text    | null: false    |

### Association

user has_many :prototypes
user has_many :comments

## prototypes テーブル

| Column     | Type       | Option                         |
| -----------|------------|--------------------------------|
| title      | string     | null: false                    |
| catch_copy | text       | null: false                    |
| concept    | text       | null: false                    |
| user       | references | null: false, foreign_key: true |

### Association

prototype belongs_to user
prototype has_many comments

# comments テーブル

| Column     | Type       | Option                         |
| -----------|------------|--------------------------------|
| text       | text       | null: false                    |
| user       | references | null: false, foreign_key: true |
| prototype  | references | null: false, foreign_key: true |

### Association

comment belongs_to :user
comment belongs_to :prototype