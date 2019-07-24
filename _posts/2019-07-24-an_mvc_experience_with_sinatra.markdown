---
layout: post
title:      "An MVC Experience With Sinatra"
date:       2019-07-24 22:47:29 +0000
permalink:  an_mvc_experience_with_sinatra
---


The content of your blog post goes here. As far as app architectural concepts, I can’t imagine any concept being more intuitive than MVC(Model-View-Controller), especial applied in frameworks like Sinatra. Now, this not to suggest that  all or even most frameworks that use the MVC architecture are necessarily easy for beginners(e.g. Angular), but their intuitive nature does make them rather encouraging for those diving into the world of app development. And few MVC framework seem more enjoyable or accommodating to new developers like Sinatra. 
So, here are is a review of my experience when building a simple content management app on Sinatra. 
.
**SQLIte**

I am  not proficient on the technical mechanics of SQLite 3, but I know it’s a simpler RDMBS which has its benefits when need to build something quick and simple.  However, the simplicity also makes it less powerful relative to its more traditional counter parts like SQL Server and MySQl.  I also found that the later are more accommodated by platforms like Heroku, AWS S3, and Firebase. 
  
**Active Record- ORM**
 
Active Record was the ORM(Object Relational Mapper) used on this project. For those not familiar with ORMs, they effectively act as the bridge between the database and the application. They are necessary to connect objects of different types. For example, in this app Active Record connects a Ruby Class, “User” with an SQL Table “Users”.

``class User < ActiveRecord::Base
    
     has_secure_password 
     has_many :items
end

class CreateUsers < ActiveRecord::Migration[5.2]
  def change
    create_table :users do |t|
      t.string :email
    end
  end
end``


** Frontend**

The templating engine on this project was ERB. Though it maybe do to the simplicity of my app, but I thought it was great. I understand that  many experienced developers prefer to use  HAML.

And of course I used  Bootstrap as the frontend library. 
 

**Sinatra**

So, what about the thing that connects these pieces together? Sinatra. Okay, in all fairness my experience with MVC frameworks does not dictate that I would be a good judge of Sinatra…but I thought it was super utilitarian. I thought it was simple and efficient, which  I believe was the intent of the Sinatra builders anyway.  Sure, I’ve been told that it is relatively limited relative to other frameworks, or as a friend put it; “Sinatra is a toolbox, Ruby on Rails is a Home Depot.”  Nonetheless, Sinatra has awesome features. My favorite being the design and display of error messages. Error messages were clear, precise, and they came back with tracebacks. It made fixing code so efficient. And for beginners, clean error logs translate to less time on Stack Overflow.

So, that’s pretty much my two cents on my MVC/Sinatra  experience. 





