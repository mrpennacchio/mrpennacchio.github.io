---
layout: post
title: Blocipedia
thumbnail-path: "img/blocipedia_screen.png"
short-description: Build a production quality SaaS app that allows users to create their own wikis, upgrade memberships, and collaborate with other users.

---

{:.center}
![]({{ site.baseurl }}/img/blocipedia_screen2.png)

## Explanation

Blocipedia is an application that allows users to create public and private Markdown-based wikis.   This project demonstrates the use of CRUD, TDD with Rspec, and integrating gems like Devise, Pundit, Figaro, and Stripe.


## Problem

Create an application that allows users to create wikis that supports Markdown.  Users can sign up for a free account, and upgrade to a premium account. Premium account holders can create private wiki's, as well as add collaborators to a wiki.

## Solution

To allow users to sign up for an account, I used the **devise** gem to accomplish this feature.  It has an easy to follow documentation, and a is a trusted gem in authentication.

Since users could sign up for an account, and then upgrade to a premium account, there had to be some way to distinguish what a each level of membership had authorization to do.  To deal with authorization, I used the **pundit** gem.  Pundit is a great tool for authorization, and has you set up *policy controllers* that establishes certain authorizations.  

In order to create collaborations, I used a join table. This was the most interesting part of the project for me.  While there was a `Collaboration` class, the only information it held was its associations with the `Wiki` and `User` class.  I was able to set up the three classes as follows:

The solution resulted in a relationship between the User class and Wiki class.
{% highlight ruby %}
class User < ApplicationRecord
has_many :wikis, dependent: :destroy
has_many :collaborations
has_many :collaborating_wikis, through: :collaborations, source: :wiki
{% endhighlight %}

{% highlight ruby %}
class Wiki < ApplicationRecord
belongs_to :user
has_many :collaborations
has_many :collaborators, through: :collaborations, source: :user
{% endhighlight %}

{% highlight ruby %}
class Collaboration < ApplicationRecord
  belongs_to :user
  belongs_to :wiki
end
{% endhighlight %}

This type of relationship allowed me to easily append new collaborators, or collaborating wikis onto the join table.  From here I was able to put all of the necessary logic inside of the pre-existing wiki controller, resulting in a more easily managed codebase.

## Results

This project was successful in teaching me further about Ruby on Rails, the use of gems, and allowing me to go further into a MVC structured application.  I believe my solutions to the problems were adequate.  

## Conclusion
Blocipedia allowed me to further explore the power of Ruby on Rails and the proper way of handing relationships and logic.  It also gave me experience in exploring different gems that add power to a site.  
