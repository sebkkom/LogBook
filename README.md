# LogBook

Storing an events log book.

## Installation

Add this line to your application's Gemfile:

    gem "log_book"

### Create the table

    rails generate guinea_pig:migration
    rake db:migrate

### ActsOnTaggableOn dependency

    rails generate acts_as_taggable_on:migration
    rake db:migrate

## Usage

In any point:

    LogBook.event(<who executes the action>, <over which object>, <text>, <list of tags>)

For example:

    LogBook.event(current_user, item, "Item canceled", [:purchase, :canceled])

## ActiveRecord integration

    class MyModel < ActiveRecord::Base
      log_book_log_book
    end

    MyModel.create!   # => LogBook created
    my_model.save!    # => LogBook created
    my_model.destroy! # => LogBook created

If you want to include _who executes the action_ use the special attribute `log_book_historian`:

    my_model.log_book_historian = current_user
    my_model.save!

## Sate of the art

Beta version but already used in production environments