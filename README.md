# doc_cache

doc_cache allows you to cache raw text fragments to the "cloud" to be retrieved
asyncronously later by JavaScript.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'doc_cache'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install doc_cache

If you're using Rails, add the following to your asset manifest:

```
#= require 'doc_cache'
```

## Usage

In an ERB file:

``` erb
<%= DocCache.cache ['your_key', @some_object.id] do %>
  <div>
    I'm cached! Hello from <%= @some_object.name %>
  </div>
<% end %>
```

If the key has never been accessed before, the server will render it as normal
and return the outputted HTML. If the cache has been warmed, the server returns
a `<span>` tag with an identifier. Example:

```
<span class="doc_cache_fragment" data-fragment-id="eyJhBGci0iJIUz..."></span>
```

The included JavaScript code will parse every fragment when the document is
ready and load them asyncronously into the page.

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake spec` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/[USERNAME]/doc_cache.

## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
