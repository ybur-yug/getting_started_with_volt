# Getting Started With Volt

## We Need Ruby!

If you are programming, it is generally a very good idea to have a version manager implemented so
that you can easily switch versions of your language of choice. In the case of Ruby there are
several offerings available. We will cover the 3 major options that are available to start. You
obviously only need to pick one of these, and they will all do a sufficient job. These 3 options
are `RVM`, `RbEnv` and `Chruby`.

### RVM

The first step of getting RVM working is to install the mpapis public key.

`gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3`

Now, we can install RVM's stable version and grab Ruby:

`curl -sSL https://get.rvm.io | bash -s stable --ruby`

RVM is now configured for you as a single user. Woo! Now, how to actually use it is the next step.
First, we have to source RVM. So close your terminal, start a new session, and run

`source ~/.rvm/scripts/rvm`

We can verify it works by running:

`type rvm | head -n 1`

Which should output `rvm is a function`.

To find out which rubies we can install, it is as simple as

`rvm list known`

Now, we should install a version of ruby.

`rvm install 2.1`

And you should see something along the lines of:

```BASH
Checking requirements for opensuse.
Requirements installation successful.
Installing Ruby from source to: /home/mpapis/.rvm/rubies/ruby-2.1.1, this may take a while depending on your cpu(s)...
...
Install of ruby-2.1.1 - #complete
Using /home/mpapis/.rvm/gems/ruby-2.1.1
```

And to see if it worked correctly,

```BASH
ruby -v
# => ruby 2.1.1p76 (2014-02-24 revision 45161) [x86_64-linux]

which ruby
#=> /home/mpapis/.rvm/rubies/ruby-2.1.1/bin/ruby
```

And now we are set to actually get rubygems and set up our Volt installation.

### RbEnv
The documentation on RbEnv is quite thorough, and the [README](https://github.com/sstephenson/rbenv) honestly does
much more justice to setting it up than I could.

### Chruby
To install,

```BASH
wget -O chruby-0.3.9.tar.gz https://github.com/postmodern/chruby/archive/v0.3.9.tar.gz
tar -xzvf chruby-0.3.9.tar.gz
cd chruby-0.3.9/
sudo make install
```

Or, on OSX

```BASH
brew install chruby
```

Add this to your `.bashrc` or `.zshrc`

`source /usr/local/share/chruby/chruby.sh`

Now we set a default Ruby.

`chruby ruby-2.1`

and now we are set.


## Installing Volt

Being a standard Ruby Gem, Volt is quite easy to install:

`gem install volt`

And with this, we can now create a project!

`volt new some_project`

This will give us a new directory called `some_project` that is a default Volt app and bundles for us.
![what you should see](http://i.imgur.com/ujb4F0E.gif)


`cd some_project`

And from here if we open up `app/main/views/main/index.html` we can add some clientside Ruby

```RUBY
...
{{ foo = "hello world" }}
<h1>{{ foo }}</h1>
...
```
##### [Source](https://github.com/ybur-yug/getting_started_with_volt/blob/master/some_project/app/main/views/main/index.html#L6)

And if we fire up our server:

`bundle exec volt s`

we can visit `localhost:3000` and see our message proudly displayed.

From here, check out the [documentation](http://docs.voltframework.com) to get up to speed on the
nitty gritty of building isomorphic applications in Ruby.

To dive into some Volt specifics if you feel familiar, check out [Rick Carlino's introduction to Volt tasks and my accompanying asciicast](https://github.com/ybur-yug/volt_task_example)
