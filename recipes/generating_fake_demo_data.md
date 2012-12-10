# Generating fake demo data
If you need to generate data for demo please don't do it as "Name0", "Name1", .... Instead you should use fake data generators such as [forgery](https://github.com/sevenwire/forgery).

## Installing
Just add it to Gemfile:
```ruby
group :development do
  gem 'forgery'
end
```

## Examples of usage
Generate title for blog post:
```ruby
> Forgery(:lorem_ipsum).words(4, random: true).capitalize
=> "Purus sit amet nulla"
```

Generate user name and email:
```ruby
> Forgery(:name).full_name
=> "Shawn Smith"
> Forgery(:email).address
=> "pwagner@teklist.org"
```

Generate credit card number:
```ruby
> Forgery(:credit_card).number(type: 'Visa')
=> "4532443581421162"
```

See additional information about usage in official [README](https://github.com/sevenwire/forgery#forgery), [wiki](https://github.com/sevenwire/forgery/wiki) or in [code base](https://github.com/sevenwire/forgery/tree/master/lib/forgery/forgery).

## Notes
Code of [forgery](https://github.com/sevenwire/forgery) is easy to read and understand. Feel free to explore and contribute. It especially need documentation improvements.
