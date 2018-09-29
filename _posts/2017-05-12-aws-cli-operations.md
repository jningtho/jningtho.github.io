---
layout: post
title:  "AWS CLI Operations"
date:   2017-04-22 17:12:08 +0530
categories: aws awscli
---

So I have installed `awscli` tool on my macbook or ubuntu. Now what? Where do I go from here. If you've reached this far I'd be wrong to say that you have not created a [FREE TIER](https://aws.amazon.com/free/) account in AWS and are anxious to hop on the bandwagon. Say no more!

### Checklist
* You have created a FREE TIER account in aws
* You have logged in as the root user
* You have also created a _new user_ and have attached _AdministratorAccess policy_.
* Ensure you are logged in a the _new user_ above at all times for all your administrative tasks and not the _root user_.
* Make sure you have completed all the 5 listed tasks on the Identity and Access Management dashboard before proceeding with any activity within your AWS Account.

<img src="assets/img/iam-todo.png">

NOTE: Please make sure to follow _IAM Best Practices_. You may see the [aws  documentation](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#create-iam-users).

### Scenario:
* You have a _new user_  

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}
