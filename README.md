# stamp

Format dates (and times, soon) based on examples, not arcane strftime directives.

[![Build Status](http://travis-ci.org/jeremyw/stamp.png)](http://travis-ci.org/jeremyw/stamp)

## Installation

Just `gem install stamp`, or add stamp to your Gemfile and `bundle install`.

## Usage

Date objects get a powerful new method: #stamp. Provide an example date string
with whatever month, day, year, and weekday parts you'd like, and your date
will be formatted accordingly:

```ruby
date = Date.new(2011, 6, 9)
date.stamp("March 1, 1999")         # "June  9, 2011"
date.stamp("Jan 1, 1999")           # "Jun  9, 2011"
date.stamp("Jan 01")                # "Jun 09"
date.stamp("Sunday, May 1, 2000")   # "Thursday, June  9, 2011"
date.stamp("Sun Aug 5")             # "Thu Jun  9"
date.stamp("12/31/99")              # "06/09/11"
date.stamp("DOB: 12/31/2000")       # "DOB: 06/09/2011"
```

### Features

* Abbreviated and full names of months and weekdays are recognized.
* Days with or without a leading zero work instinctively.
* Include any extraneous text you'd like, e.g. "DOB:".

### Disambiguation by value

You can use any month, weekday, day, or year value that makes sense in your
examples, and stamp can often infer your intent based on context, but there
may be times that you need to use unambiguous values to make your intent more
explicit.

For example, "01/09" could refer to January 9, September 1, or
January 2009. More explicit examples include "12/31", "31/12", and "12/99".

Using unambiguous values will also help people who read the code in the
future understand your intent.

### Limitations

* Support for time formatting by example is coming soon. Patches welcome!

Did I mention? Patches welcome!

If you need more obscure formatting options, you can include any valid
[strftime](http://strfti.me) directives in your example string, and they'll
just be passed along:

```ruby
date.stamp("Week #%U, %Y")         # "Week #23, 2011"
````

[Check out http://strfti.me](http://strfti.me) for more ideas.

More coming soon, including time formats by example.

## Contributing to stamp

* Check out the latest master to make sure the feature hasn't been implemented or the bug hasn't been fixed yet
* Check out the issue tracker to make sure someone already hasn't requested it and/or contributed it
* Fork the project
* Run `bundle install`
* Run `rake` to execute the cucumber specs and make sure they all pass
* Start a feature/bugfix branch
* Commit and push until you are happy with your contribution
* Make sure to add tests for it. This is important so I don't break it in a future version unintentionally.
* Please try not to mess with the Rakefile, version, or history. If you want to have your own version, or is otherwise necessary, that is fine, but please isolate to its own commit so I can cherry-pick around it.

## Copyright

Copyright (c) 2011 Jeremy Weiskotten (@doctorzaius). See LICENSE.txt for
further details.
