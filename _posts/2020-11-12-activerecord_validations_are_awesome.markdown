---
layout: post
title:      "ActiveRecord Validations Are Awesome!"
date:       2020-11-12 14:35:53 -0500
permalink:  activerecord_validations_are_awesome
---


When presented with the Sinatra project requirements, none were as intimidating to me as the 'validate user input' one. I felt completely lost on what to do here, the only 'validations' I could imagine up were long and arduous if/else conditionals, but that did not feel ideal. Especially since my Character model had several attributes that I would have to cover, an if/elsif/else statement was just not going to cut it. 

To be honest I don't know if I accidentally slept through the ActiveRecord validations lesson on Learn.co, but while watching a Sinatra project walkthrough on the Learn Instruct site my mind was totally blown when the instructor googled 'ActiveRecord validations' and I was sent to [this page.](https://guides.rubyonrails.org/active_record_validations.html)

ActiveRecord validations are incredible and they do such a good job of making sure the data being sent to your database is actually the kind of data you want to see in there. For example, we learned how to use an if statement when users would signup and create an account. The if/else statment would check if the usernameand password params were empty, which would give an error or redirect to a failure page or back to signup, else the user would be made.

```
post "/signup" do
    if params[:username] == "" || params[:password] == ""
      redirect to '/failure'
    else
      User.create(:username => params[:username], :password => params[:password])
      redirect '/login'
    end
end
```

But now with the power of ActiveRecord validations you can just change your User model with this added in to validates line, and that if/else statement can get out of here!

```
class User < ActiveRecord::Base
   validates :username, :password, presence: true
end
```

![Surprised Keanu](https://i.pinimg.com/originals/e3/ee/d4/e3eed42784106dbf0f372bc1c4e6771e.jpg)

But the magic doesn't end there. In my project I ended up also utilizing length and format validations in my user model. Here are examples of both from the ActiveRecord Validations site:

```
class Person < ApplicationRecord
  validates :name, length: { minimum: 2 }
end
```

```
class Product < ApplicationRecord
  validates :legacy_code, format: { with: /\A[a-zA-Z]+\z/,
    message: "only allows letters" }
end
```

I didn't want users to be able to create usernames or passwords that were single letters or numbers, so length validation helped me to ensure inputs were at least 5 characters long. I also wanted to make sure that a users email was actually structured like a real email, like 'example@email.com', not like 'franksemail@'. So format validations allowed me to use a regex line to gaurantee that familiar email structure. I also used format validations to reject any inputs with any empty spaces. 

Now I know I have any skimmed the surface here on ActiveRecord validations, there is so much more to read up on and use. I also know that there are more validations I could've added to my project before submitting, for example checking that user password includes at least one capital letter, symbol and number. And thats just my user model! I could do a ton or validating with my character model! Anyway, the point is that ActiveRecord validations are awesome, and I can't wait to mess around with them some more after this. 

