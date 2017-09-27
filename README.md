# README

 ## rooms table

  |Column|Type|Options|
  |------|------|------|
  |title|string|null: false, index :true|
  |type|string|null: false|
  |price|integer|null: false|
  |location|string|null: false|
  |description|text|null: false|
  |hm_rooms|integer|null: false|
  |hm_bets|integer|null: false|
  |hm_bathrooms|integer|null: false|
  |amenity|string|------|
  |facility|string|------|
  |rules|string|------|
  |meal_time_of_day|string|------|
  |host_id|integer|null: false, foreign_key: true|
  |user_id|integer|null: false, foreign_key: true|
  |room_image_id|integer|foreign_key: true|

### Association

 - belongs_to :host
 - has_many :room_images
 - has_many :users, through: :users_rooms
 - has_many :users_rooms

 ## experiences table

  |Column|Type|Options|
  |------|------|------|
  |title|string|null: false, index :true|
  |type|string|null: false|
  |price|integer|null: false|
  |location|string|null: false|
  |description|text|null: false|
  |category|string|null: false|
  |host_id|integer|null: false, foreign_key: true|
  |user_id|integer|null: false, foreign_key: true|
  |experience_image_id|integer|foreign_key: true|

### Association

 - belongs_to :host
 - has_many :experience_images
 - has_many :users, through: :users_experiences
 - has_many :users_experiences

 ## restaurants table

  |Column|Type|Options|
  |------|------|------|
  |title|string|null: false, index :true|
  |type_of_meal|string|null: false|
  |price|integer|null: false|
  |location|string|null: false|
  |description|text|null: false|
  |cuisine|string|null: false|
  |time_of_day|string|null: false|
  |host_id|integer|null: false, foreign_key: true|
  |user_id|integer|null: false, foreign_key: true|
  |restaurant_image_id|integer|foreign_key: true|

### Association

 - belongs_to :host
 - has_many :restaurant_images
 - has_many :users, through: :users_restaurants
 - has_many :users_restaurants

 ## users table

  |Column|Types|Option|
  |------|------|------|
  |last_name|string|null: false|
  |first_name|string|null: false|
  |gender|string|null: false|
  |birth_month|integer|null: false|
  |birth_day|integer|null: false|
  |birth_year|integer|null: false|
  |email|string|null: false, unique: true|
  |tel|integer|------|
  |currency|string|------|
  |city_country|string|------|
  |description|text|unique: true|


### Association

 - has_many :rooms, through: :users_rooms
 - has_many :users_rooms
 - has_many :experiences, through: :users_experiences
 - has_many :users_experiences
 - has_many :restaurants, through: :users_restaurants
 - has_many :users_restaurants

 ## hosts table

  |Column|Types|Option|
  |------|------|------|
  |last_name|string|null: false|
  |first_name|string|null: false|
  |gender|string|null: false|
  |birth_month|integer|null: false|
  |birth_day|integer|null: false|
  |birth_year|integer|null: false|
  |email|string|null: false, unique: true|
  |tel|integer|null: false, unique: true|
  |currency|string|null: false|
  |city_country|string|null: false|
  |description|text|null: false, unique: true|

### Association

 - has_many :rooms
 - has_many :experiences
 - has_many :restaurants

 ## room_images table

  |Column|Type|Option|
  |------|------|------|
  |title|string|null: false|
  |image_url|text|null: false|
  |room_id|references|null: false, foreign_key: true|

### Association
 - belongs_to :room

 ## experience_images table

  |Column|Type|Option|
  |------|------|------|
  |title|string|null: false|
  |image_url|text|null: false|
  |room_id|references|null: false, foreign_key: true|

### Association
 - belongs_to :experience

 ## restaurant_images table

  |Column|Type|Option|
  |------|------|------|
  |title|string|null: false|
  |image_url|text|null: false|
  |restaurant_id|references|null: false, foreign_key: true|

### Association
 - belongs_to :restaurant

 ## users_rooms table (intermidiate)

 |Column|Type|Option|
 |------|------|------|
 |user_id|references|null: false, foreign_key: true|
 |room_id|references|null: false, foreign_key: true|

### Association
 - belongs_to :user
 - belongs_to :room

 ## users_experiences table (intermidiate)

 |Column|Type|Option|
 |------|------|------|
 |user_id|references|null: false, foreign_key: true|
 |experience_id|references|null: false, foreign_key: true|

### Association
 - belongs_to :user
 - belongs_to :experience

 ## users_restaurants table (intermidiate)

 |Column|Type|Option|
 |------|------|------|
 |user_id|references|null: false, foreign_key: true|
 |restaurant_id|references|null: false, foreign_key: true|

### Association
 - belongs_to :user
 - belongs_to :restaurant
