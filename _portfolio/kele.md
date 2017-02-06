---
layout: post
title: Kele API Client
thumbnail-path: "img/Kele.png"
short-description: A ruby command line gem build to access the Bloc.io API

---

{:.center}
![]({{ site.baseurl }}/img/Kele.png)

## Explanation

Kele is a ruby gem that access's Bloc's API.  Bloc's API provides an external facing JSON Web Token authorized gateway to the Bloc application.  

## Problem

Create an application that can access information from bloc.io.  With a students login information, the client should retrieve information like the students profile information, mentor availability, messages, and checkpoint submissions.

## Solution

The solution to this task was to use the HTTParty gem.  This gem has great documentation, and is as simple to use as calling the site you want to access, an HTTP method, and a set of parameters.  For example, to retrieve information about myself, I did the following:

``` ruby
def get_me
  response = self.class.get('https://www.bloc.io/api/v1/users/me', headers: { "authorization": @auth_token })
  JSON.parse(response.body)
end
```

Pretty simple right? This was used in a number of different ways, but the above snippet highlights the basic syntax and setup.  

## Results

I was successful in ultimately extracting information from the API. It was a great exercise in working with a gem I had not used before, and was fun and rewarding seeing information pulled from a site right to my command line.  

## Conclusion
This project was short but sweet. It allowed me to do something I had not done before, and introduced me to the potential of accessing public API.  This was a valuable skill learned and I will likely use it in my future.
