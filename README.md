# Mouse vs AI: Robust Visual Foraging Challenge

This is the competition website for NeurIPS 2025.

## how to local host
commands for ubuntu 24.04

sudo apt update
sudo apt install ruby-full build-essential zlib1g-dev
gem install --user-install jekyll bundler
bundle config set --local path 'vendor/bundle'
bundle install

after running above commands, you'll have
- .bundle/config - Bundler configuration
- vendor/bundle/ - Directory containing all gem dependencies
- Gemfile.lock - Lock file with exact gem versions

next command runs Jekyll locally automatically at local host 4000
bundle exec jekyll serve
note changes to most files when saved will update the local host automatically but changes to _config.yml you will need to kill and restart Jekyll with the above command.
