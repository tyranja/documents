bundler

reads the gemfile
creates gemfile.lock
This lock file is what makes it possible to install the exact same versions on to every machine that runs this application, whether that machine belongs to a developer, a production server, or a CI server.

`bundle install`
    Read the Gemfile (and lock, if it is there)
    Ask RubyGems.org for a list of every version of every gem we want
    If needed, find gem versions allowed by the Gemfile that work together
    If found, write down those versions in the lock for future installs
    Install gems as needed until every gem in the lock is installed

`bundle exec`
    Read the Gemfile (and lock, if it's there)
    If needed, find gem versions allowed by the Gemfile that work together
    If found, write down those versions in the lock for future installs
    Remove any existing gems from the $LOAD_PATH array
    Add each gem version listed in the lock file to the $LOAD_PATH

Best practice is that you run your executable scripts with bundle exec.
In some cases, running executables without bundle exec may work, if the executable happens to be installed in your system and does not pull in any gems that conflict with your bundle.

However, this is unreliable and is the source of considerable pain. Even if it looks like it works, it may not work in the future or on another machine.

https://www.cloudcity.io/blog/2015/07/10/how-bundler-works-a-history-of-ruby-dependency-management/
https://www.viget.com/articles/bundler-best-practices
