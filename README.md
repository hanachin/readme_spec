# ReadmeSpec
[![Build Status](https://travis-ci.org/gong023/readme_spec.svg?branch=master)](https://travis-ci.org/gong023/readme_spec)

Test your spec in README

## Usage

Set you readme file absolute path.

```
# spec_helper.rb
RSpec.configure do |c|
  c.readme_file_path = File.dirname(__FILE__) + '/../README.md'
end
```

Write spec in README.

<pre>
Your awesome description.

Your sample code.

```ruby
class YourClass
  def do_something
    true
  end
end

your_class = YourClass.new
expect(your_class.do_something).to be_true
</pre>

Call `ReadmeSpec.evaluate(binding)` in your test code.

```
expect { ReadmeSpec.evaluate(binding) }.not_to raise_error
```

Readme.evaluate evals your code in README sorrounded by `ruby`. You can keep correct code in README.md

In this repository, below code is tested in `spec/`.

```ruby
a = 1
b = 2
expect(a + b).to be 3
```

If README code is wrong, you can get error message as it is.

```
Failure/Error: it { expect { ReadmeSpec.evaluate(binding) }.not_to raise_error }
  expected no Exception, got #<RSpec::Expectations::ExpectationNotMetError:
  expected #<Fixnum:3> => 1
       got #<Fixnum:7> => 3
```

## Contributing

1. Fork it ( https://github.com/gong023/readme_spec/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
