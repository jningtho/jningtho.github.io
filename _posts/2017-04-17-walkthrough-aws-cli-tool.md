---
layout: post
comments: true
title:  "Installing AWS CLI Tool"
date:   2017-04-19 13:12:08 +0530
categories: aws
tags: aws cli awscli
---
In this post, I will walk through installing `awscli` a command line tool to interact with the AWS Services in your account. The installation guide in [AWS cli documentation](https://docs.aws.amazon.com/cli/latest/userguide/installing.html) is very elaborate however I'll take the direct approach with the installation steps on macOS and Linux machines(ubuntu).

## Pre-reqs:
The primary distribution method for the AWS CLI on Linux, Windows, and macOS is `pip`, a package manager for Python that provides an easy way to install, upgrade, and remove Python packages and their dependencies.
* Python 2 version 2.6.5+ or Python 3 version 3.3+
* `pip` Python package manager

## macOS Installing `awscli tool` in 3 simple steps.

1.The latest version of Mac OS X, High Sierra, comes with Python 2.7 out of the box. Perhaps [this document](https://docs.python-guide.org/starting/install/osx/) can give you a granular detail. Check for python version in the terminal and the output should be something like below.

{% highlight shell%}
$ python --version
Python 2.7.15 #=> output
{% endhighlight %}

NOTE: It is recommended to install Python 3.6 to get the latest libraries. [Refer here](https://wsvincent.com/install-python3-mac/)

2.Install `pip` using curl as provided by Python Packaging Authority,

{% highlight shell%}
$ curl -O https://bootstrap.pypa.io/get-pip.py
$ python3 get-pip.py --user
{% endhighlight %}

```shell
#=> Verify pip3 version
$ pip3 --version
pip 18.0 from /usr/local/lib/python3.7/site-packages/pip (python 3.7) #=>output.
```

3.Use `pip` to install the latest version of 'awscli'
```shell
$ pip3 install awscli --upgrade --user
```

Check for correct installation with the command below
```shell
$ aws --version
aws-cli/1.16.20 Python/3.7.0 Darwin/17.7.0 botocore/1.12.10 #=>output.
```

Another easy method is installing via `[Homebrew]`(https://brew.sh/) also known as the 'Missing Package Manager for macOS'. You may refer the step-by-step walkthrough [here](http://certglobal.com/aws-cli-tools-1/)


## ubuntu
The installation method on Ubuntu is more or less similar except it uses `apt` package manager tool for [Ubuntu](https://help.ubuntu.com/lts/serverguide/apt.html.en). Similar fashion, install Python if not already installed.

1.Install `[Python 3 +]`(https://docs.aws.amazon.com/cli/latest/userguide/awscli-install-linux-python.html)

2.Install `pip`
```shell
$ curl -O https://bootstrap.pypa.io/get-pip.py
$ python get-pip.py --user
```
3.Install latest version of `awscli`
```shell
$ pip install awscli --upgrade --user
```

To upgrade to the latest version, run the installation command again, run the same command as step 3

Confirm `awscli` installed successfully
```shell
$ aws --version
aws-cli/1.11.84 Python/3.6.2 Linux/4.4.0-59-generic botocore/1.5.47
```

Simple wasn't it? If in doubt to modify your path variable, please refer '[aws documentation]'(https://docs.aws.amazon.com/cli/latest/userguide/awscli-install-linux.html#awscli-install-linux-pip)


Voila! You are now ready to configure your AWS  Profile using the Secret Key and Secret Access ID.
