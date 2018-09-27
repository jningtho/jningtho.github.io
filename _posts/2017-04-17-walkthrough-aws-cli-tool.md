---
layout: post
comments: true
title:  "Installing AWS CLI Tool"
date:   2017-04-19 13:12:08 +0530
categories: aws
tags: aws cli awscli
---
In this post, I will walk through installing `awscli` a command line tool to interact with the AWS Services in your account. The installation guide in [AWS cli documentation](https://docs.aws.amazon.com/cli/latest/userguide/installing.html) is very elaborate however I'll take the direct approach with the installation steps on macOS and Linux machines(ubuntu).

##Pre-reqs:
The primary distribution method for the AWS CLI on Linux, Windows, and macOS is `pip`, a package manager for Python that provides an easy way to install, upgrade, and remove Python packages and their dependencies.
* Python 2 version 2.6.5+ or Python 3 version 3.3+
* `pip` Python package manager

##MAC
Insatalling in 3 simple steps

1. The latest version of Mac OS X, High Sierra, comes with Python 2.7 out of the box. Perhaps [this document](https://docs.python-guide.org/starting/install/osx/) can give you a granular detail. Check for python version in the terminal and the output should be something like below.

{% highlight shell%}
$ python --version
Python 2.7.15 #=> output
{% endhighlight %}

NOTE: It is recommended to install Python 3.6 to get the latest libraries. [Refer here](https://wsvincent.com/install-python3-mac/)

2. Install `pip` using curl as provided by Python Packaging Authority,

{% highlight shell%}
$ curl -O https://bootstrap.pypa.io/get-pip.py
$ python3 get-pip.py --user
{% endhighlight %}

```shell
#=> Verify pip3 version
$ pip3 --version
pip 18.0 from /usr/local/lib/python3.7/site-packages/pip (python 3.7) #=>output as below
```
3. Use `pip` to install the latest version of 'awscli'
```shell
$ pip3 install awscli --upgrade --user
```

Check for correct installation with the command below
```shell
$ aws --version
aws-cli/1.16.20 Python/3.7.0 Darwin/17.7.0 botocore/1.12.10 #=>output should give you something like this.
```

Voila! You are ready to configure your AWS  Profile using the Secret Key and Secret Access ID.





Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
