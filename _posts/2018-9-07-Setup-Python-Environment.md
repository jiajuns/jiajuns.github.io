---
layout: post
title: Setup Python Environment
---

If you start your new job as a software developer, what you need to do on day 1 is to set up your environment. The developing environment can mean a lot of things for an experienced developer. But since you are a newbee, I guess your boss's minimal expectation is **to let the codebase run on your machine**.

The original post can be found [here](https://github.com/asavpatel92/pretaining-to-be-professional-101)

Pick python distribution
---
There are two popular choices: [Python](https://www.python.org/) and [Anaconda](https://www.anaconda.com/). From my personal experiences, if you use linux or MacOS, take [Python](https://www.python.org/); if you use windows, take [Anaconda](https://www.anaconda.com/).

If you use linux or MacOS, you can solve everything in terminal, install [Python](https://www.python.org/), it is light weight and nothing hiden inside. Therefore, I recommend you just build things from it.

If you are on the darkside, sometimes things can become very tricky. If you don`t want to get your hands dirty, [Anaconda](https://www.anaconda.com/) can make things easier.

**BUTTT** for linux and MacOS user you don't need to do anything!!! because you already have python in your system. You might ask, what if your project is built on `Python 3.6` but your system is `Python 2.7`. Don't worry please wait I will tell you what to do.

To verify your installation works, do the following in terminal or cygwin  or whatever.
{% highlight python %}
python
{% endhighlight %}
it will print out
{% highlight python %}
Python 3.6.6 (default, Jun 28 2018, 04:42:43)
[GCC 5.4.0 20160609] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
{% endhighlight %}

or
{% highlight python %}
which python
{% endhighlight %}

it will print out
{% highlight python %}
/usr/bin/python
{% endhighlight %}

If you see things similiar to those, you are good for the next step.


Don`t put stuff in root environment
---
After setting up python, you cannot resist to run the codebase or any project you find online. Then you realise it requires many packages. For example you receive this error:

{% highlight python %}
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ModuleNotFoundError: No module named 'pytorch'
{% endhighlight %}

This error means, you need to install a package called `pytorch`. However, **do not do this for your root environment**. Your python root environment is fresh and clean after you just installed it on your machine.

To create a **virtual environment** is what a professional developer will do.

### 1. Plain Python ([virtualenv](https://virtualenv.pypa.io/en/stable/userguide/))
If you use plain Python, below are the instructions for you!

* First install virtualenv
{% highlight python %}
pip install virtualenv
{% endhighlight %}

* Create a `python3` virtualenv called `test_env`
{% highlight python %}
virtualenv -p python3 test_env
{% endhighlight %}

* Use this virtualenv `test_env`
{% highlight python %}
source test_env/bin/activate
{% endhighlight %}

Then you will see something like this:
{% highlight python %}
(test_env) jiajuns@jiajuns-desktop:~$
{% endhighlight %}

Now, you are in your `test_env` environment. When you run `python` in this mode, you are not using your root python. The benfit will show up when you are working with different project and each of them has unique environment. Also if you f**k up your environment, you can just delete it and create it again. Image what will happen if your root environment broke, that is the real pain.

### 2. Anaconda
Anaconda has create tools to create conda environment, which works like `virtualenv`. This [link](https://conda.io/docs/user-guide/tasks/manage-environments.html) has detail instruction.

* Create a `python3` conda env called `test_env`
{% highlight python %}
conda create -n test_env python=3.6
{% endhighlight %}

use this conda environment `test_env`
{% highlight python %}
source activate test_env
{% endhighlight %}
or
{% highlight python %}
activate test_env
{% endhighlight %}

Now you have known how to create an environment using virtualenv or conda

Put library to your virtual environment
---
The most popular choice is `pip`

Linux user:
{% highlight python %}
sudo apt-get install python-pip
{% endhighlight %}

MacOS user:
{% highlight python %}
sudo easy_install pip
{% endhighlight %}

Windows user:

Download [get-pip.py](https://bootstrap.pypa.io/get-pip.py) to a folder on your computer. Open a command prompt window and navigate to the folder containing get-pip.py. Then run
{% highlight python %}
python get-pip.py
{% endhighlight %}

Once you have `pip` ready, you can install any package by
{% highlight python %}
pip install [package]
{% endhighlight %}

If you have anaconda, you can use conda to install package
{% highlight python %}
conda install [package]
{% endhighlight %}

However!
---
For a well maintained project, other developer has prepared something to make your life easier. It is generally called environment file. If the team is using `virtualenv`, the file usually named as `requirements.txt`. [Here](https://github.com/BlueRiverTechnology/ts-datacart) is an example. You can create the environment by:

{% highlight python %}
virtualenv -p python3 brtenv
pip install -r requirements.txt
{% endhighlight %}

On the other hand, some team use `conda` to manage environment, the file usually named as `environment.yml`. [Here](https://github.com/BlueRiverTechnology/ts-standcount-model) is an example. You can create the environment by:

{% highlight python %}
conda env create -f environment.yml
{% endhighlight %}

Great! you have finished your first step!