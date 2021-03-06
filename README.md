# Redshift::Rails [![Gem Version](https://badge.fury.io/rb/redshift-rails.svg)](https://badge.fury.io/rb/redshift-rails) [![Build Status](https://travis-ci.org/dakatsuka/redshift-rails.svg?branch=master)](https://travis-ci.org/dakatsuka/redshift-rails)

The library provides the railtie that allows redshift-client into Rails >= 4.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'redshift-rails'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install redshift-rails

## Usage

Set your redshift url to `$REDSHIFT_URL`:

```
$ export REDSHIFT_URL="redshift://user:password@*****.region.redshift.amazonaws.com:5439/dbname"
```

or create `config/redshift.yml`:

```yaml
# config/redshift.yml

development:
  host: *****.region.redshift.amazonaws.com
  port: 5439
  user: user
  password: password
  dbname: dbname
```

You can call `Redshift::Client` at anywhere.

```ruby
class HealthController < ApplicationConttoller
  def index
    render json: Redshift::Client.connection.exec("SELECT NOW()").first
  end
end
```

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake rspec` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/dakatsuka/redshift-rails. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](contributor-covenant.org) code of conduct.

## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

