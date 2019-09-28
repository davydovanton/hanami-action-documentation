# Hanami::Action::Documentation

## DoD
* generate documentation for the each action by cli
* map action to route
* grape based DSL
* support swagger and blueprint
* web server with documentations
* plugins system


```ruby
# in the app config:
add_swagger_documentation doc_version: '0.0.1',
                          add_version: true,
                          tags: [
                            { name: 'widgets', description: 'A description of widgets' }
                          ]
```
more here: https://github.com/ruby-grape/grape-swagger#info-

```ruby
module Web
  module Controllers
    module Posts
      class Index
        include Web::Action

        desc "Return super-secret information" do
          summary 'Now this is your summary!' 
          detail 'this will expose all the kittens'
          tags ['orders']
          deprecated true

          headers {
            "XAuthToken" => {
              description: "Valdates your identity",
              required: true
            },
            "XOptionalHeader" => {
              description: "Not really needed",
              required: false
            }
          }

          success { ... }, # or success
          failure [[401, 'KittenBitesError', { ... }]] # or failure
        end

        def call(_params)
          # ...
        end
      end
    end
  end
end
```

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'hanami-action-documentation'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install hanami-action-documentation

## Usage

TODO: Write usage instructions here

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake test` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/[USERNAME]/hanami-action-documentation. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.

## License

The gem is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).

## Code of Conduct

Everyone interacting in the Hanami::Action::Documentation project’s codebases, issue trackers, chat rooms and mailing lists is expected to follow the [code of conduct](https://github.com/[USERNAME]/hanami-action-documentation/blob/master/CODE_OF_CONDUCT.md).
