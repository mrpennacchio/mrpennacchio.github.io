---
layout: post
title: Address-Bloc
thumbnail-path: "img/address-bloc.png"
short-description: A ruby command line gem build to access the Bloc.io API

---

{:.center}
![]({{ site.baseurl }}/img/address-bloc.png)

## Explanation

Address-bloc was a local ruby program that allowed the user to create an address-book on the command line.

## Problem

The address-book should have multiple features including creating new entries, editing entries, imrporting CSV files, and searching for an entry.  This was to be done using TDD.

## Solution

This project was completed using TDD, starting with creating an entry, editing, and viewing all of the entries.  In order to make this app interactive, a menu was created as shown in the picture that allows a user to choose from the menu which action to take.  

The most interesting part for me was the searching for an entry feature. This introduced me to the binary search. It basically breaks an array in half until it finds the item that was searched for.

## Results

The address-book is able to do the intended features. A user can create, read, update, and delete an entry, as well as search or import pre-existing entries.

## Conclusion
This project was my first ruby program and taught me about the importance of red-green TDD, as well as how to set up a ruby program and rub it locally. This project also taught me about the purpose of a Model and Controller and their respective roles in development.
