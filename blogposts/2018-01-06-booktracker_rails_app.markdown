---
layout: post
title:      "BookTracker Rails App"
date:       2018-01-06 21:02:12 -0500
permalink:  booktracker_rails_app
---


# Lessons learned:
* planning is half the battle
* good planning saves time
* poor planning wastes time 
* be willing to change plans 

You may notice a theme there.  After one full domain model change and multiple tweaks, I finally had a plan that met all of the requirements.  It took a full week of planning combined with trial and error, in addition to input from multiple people before I finally had a working plan.  From there, it was not nearly as hard as I anticipated.

## The plan 
As someone who can never have enough bookshelves, a BookTracker seemed a useful tool.  This app allows a user to log a book in their collection, categorizing it based on one of the preset categories or setting their own, i.e. fitness, programming, leisure, cooking, etc.  

The user can rate the book and add comments to that book log. For someone who starts books but doesn't necessarily finish in one go, they can make a comment such as, 'Up to chapter 4. Putting aside to read xyz book, come back to this one later.'  

As with any Rails app, the user has full CRUD abilities on their book entries.

## Devise and OmniAuth

OmniAuth was a requirement, but I chose to use Devise for login, mainly to gain experience with it.  

## Models, Schema, Validations and Associations

 
```
create_table "book_records", force: :cascade do |t|
    t.integer "user_id"
    t.integer "book_id"
    t.date "date"
    t.string "comments"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
  end

  create_table "books", force: :cascade do |t|
    t.string "title"
    t.string "author"
    t.integer "rating"
    t.integer "category_id"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
  end

  create_table "categories", force: :cascade do |t|
    t.string "name"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
  end

  create_table "users", force: :cascade do |t|
    t.string "email", default: "", null: false
    t.string "encrypted_password", default: "", null: false
    t.string "name"
    t.string "reset_password_token"
    t.datetime "reset_password_sent_at"
    t.datetime "remember_created_at"
    t.integer "sign_in_count", default: 0, null: false
    t.datetime "current_sign_in_at"
    t.datetime "last_sign_in_at"
    t.inet "current_sign_in_ip"
    t.inet "last_sign_in_ip"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
    t.string "provider"
    t.string "uid"
    t.index ["email"], name: "index_users_on_email", unique: true
    t.index ["reset_password_token"], name: "index_users_on_reset_password_token", unique: true
  end
```
	
	
```
	class BookRecord < ApplicationRecord
  belongs_to :user
  belongs_to :book
```


```
class Book < ApplicationRecord
  has_many :book_records
  has_one :users, :through => :book_records
  belongs_to :category

  validates :title, presence: true
  validates :category, presence: true   #is this the right place for this?
  validates :rating, numericality: { only_integer: true, greater_than: 0, less_than_or_equal_to: 5 }, :allow_blank => true
```

```
class Category < ApplicationRecord
  has_many :books

  validates :name, presence: true
```

```
class User < ApplicationRecord
  # Include default devise modules. Others available are:
  # :confirmable, :lockable, :timeoutable and :omniauthable
  devise :database_authenticatable, :registerable,
         :recoverable, :rememberable, :trackable, :validatable,
         :omniauthable, :omniauth_providers => [:facebook]

  has_many :book_records
  has_many :books, :through => :book_records
```

I had minimal required attributes for creating a new book.  As one who can barely remember the title of books I read, let alone the author, I did not want to over-require with validations on the book class.  The only required attributes for creating a new book are title and category.  

## Strengths and Weaknesses 
I am much more area of my weaknesses than my strengths, but I'll give it a fair attempt:
After much refactoring, I think my code is fairly clean and DRY.  
I made use of partials to clean up views and elimiate repetition with forms.
I also used a few before_action statements to eliminate repetition in the controller.

There are many potential features that would be added to this simple app, but it's a great beginning place.  

I utilized some bootrap to go beyond a completely style-less look, but there is much room for improvement on the design side.  

Once I got passed that loved and hated planning stage, this was an enjoyable project.


