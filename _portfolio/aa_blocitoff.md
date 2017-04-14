---
layout: post
title: Blocitoff
thumbnail-path: "img/Blocitoff_sign_in.png"
short-description: A self destructing to-do list. Items not marked complete are deleted after 7 days.

---

{:.center}
![]({{ site.baseurl }}/img/Blocitoff_item_list.png)

## Explanation
Blocitoff is a self destructing to-do list built with Ruby on Rails. The project includes TDD, a rake task, as well as Ajax.


## Problem
Create a to do list app. A user should be able to create and delete a task, as well as have it removed after 7 days if not marked as complete.

## Solution
The biggest challenge for me in this was using Ajax.  Prior to this project I had not used Ajax, so it was new territory for me.  While I had used rails before for a destroy action, I had never incorporated JavaScript into this.  I knew that I wanted an Ajax request to fire when I clicked the checkmark, marking an item as complete.  The following code demonstrates my solution for making this happen. I used jQuery.  

{% highlight JavaScript %}
// ajax request to delete item
$('.complete-icon').bind('ajax:success', function() {
   $(this).closest('li').fadeOut("slow", "swing", function() { //speed, style, callback after ajax
     var count = <%= current_user.items.count %>;
     $('.to-do-count').html(count--); //callback to change the current_user.item.count
   });
});
{% endhighlight %}

The corresponding controller action
{% highlight Ruby %}
def destroy
   @items = Item.find(params[:id])
   @items.destroy
   respond_to do |format|
     format.html { redirect_to root_path, notice: "Item Completed" }
     format.js {flash.now[:notice] = "Item Completed"}
   end
   {% endhighlight %}


   My destroy action was asynchronously executing, but I had to find a way to give some solid user feedback that their action had worked in the form of a flash notice.  I wanted this to happen as the user deleted an item.  I created file holding my flash notice configurations, and called upon it in my destroy.js.erb file.  The resulting code looks like this:

{% highlight JavaScript %}
   // flash alert after ajax request
   <% flash.each do |type, message| %>
     $("#flash_messages_partial").html('<div class="alert alert-warning"><button type="button" class="close" data-dismiss="alert">&times;</button><%= flash[:notice] %></div>')
   <% end %>
{% endhighlight %}


## Results
In the end, my project was a success as it allowed a user to make to-do items as well as mark them as complete using Ajax.  I also think that this project is more aesthetically pleasing than my others, as it incorporates flat colors and minimalist design practices.  It has primary colors to draw the user's attention to what's important on the page, with the rest black and white.  
