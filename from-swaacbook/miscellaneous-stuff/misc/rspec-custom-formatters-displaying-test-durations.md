
# Table of Contents

1.  [RSpec Custom Formatters: Displaying Test Durations](#org721a68a)
    1.  [Creating the custom formatter](#orgd757293)
        1.  [Changing the output](#org0a1d0f3)
    2.  [Using the custom formatter](#org83d78d2)
    3.  [Getting the formatter](#orga40f3ca)
        1.  [`rake` `SPEC_OPTS`](#rake-spec_opts)
        2.  [`.rspec`](#org6c6315a)
        3.  [`spec/spec_helper`](#specspec_helper)
    4.  [Getting the formatter, contributing, and all that](#getting-the-formatter-contributing-and-all-that)


<a id="org721a68a"></a>

# RSpec Custom Formatters: Displaying Test Durations

-   published date: 2013-09-01 13:23
-   keywords: ["howtos", "rspec", "ruby", "swaac"]

The standard documentation formatter for RSpec does not show how long each test executes. This information is available in the HTML formatter, though, so I thought it could be available in others. Turns out this is true.

Inside the formatter, the `example` variable has a method called `execution_result` that is a Hash. One of the hash keys is `:run_time`, which is the milliseconds the test took to run, just what we wanted.


<a id="orgd757293"></a>

## Creating the custom formatter

The simplest thing in our case is to subclass the documentation formatter, and replace the reporting functions. `stopwatch_formatter.rb` does this.


<a id="org0a1d0f3"></a>

### Changing the output

The only two methods of `DocumentationFormatter` we need to look at are:

-   `failure_output`
-   `passed_output`

since these are the only ones that reporting duration on makes sense. (Pending tests don't take any time.)

In this case, I merely copied the methods from the documentation formatter, and added the duration from `example.execution_results[:run_time]` to the output. (I did add a bit of formatting, but that's trivial.)

    require 'rspec/core/formatters/documentation_formatter'
    
    class StopwatchFormatter < RSpec::Core::Formatters::DocumentationFormatter
      DURATION_FORMAT = "%s %-60s | Duration: %7.5f ms"
    
      def failure_output(example, exception)
        failure_color(
          format(
    	DURATION_FORMAT,
    	current_indentation,
    	"#{example.description.strip} (FAILED - #{next_failure_index})",
    	example.execution_result[:run_time]
          )
        )
      end
    
      def passed_output(example)
        success_color(
          format(
    	DURATION_FORMAT,
    	current_indentation,
    	example.description.strip,
    	example.execution_result[:run_time]
          )
        )
      end
    end

Sample output:

<pre><code>
/Users/tamara/.rubies/ruby-2.0.0-p427/bin/ruby -S rspec ./spec/lib/stopwatch_formatter_spec.rb

StopwatchFormatter
  this will pass                                               | Duration: 0.00099 ms
  this will fail (FAILED - 1)                                  | Duration: 0.00010 ms

Failures:

  1) StopwatchFormatter this will fail
     Failure/Error: false.should be_true
       expected: true value
            got: false
     # ./spec/lib/stopwatch_formatter_spec.rb:8:in `block (2 levels) in <top (required)>'

Finished in 0.00146 seconds
2 examples, 1 failure

Failed examples:

rspec ./spec/lib/stopwatch_formatter_spec.rb:7 # StopwatchFormatter this will fail
/Users/tamara/.rubies/ruby-2.0.0-p427/bin/ruby -S rspec ./spec/lib/stopwatch_formatter_spec.rb failed
</code></pre>


<a id="org83d78d2"></a>

## Using the custom formatter

`rspec` needs to load the code for your custom formatter. The easiest thing is to simply require it on the `rspec` command line, and specify the class name as the formatter:

    rspec -r /path/to/stopwatch_formatter.rb --format StopwatchFormatter ...


<a id="orga40f3ca"></a>

## Getting the formatter

You can get `stopwatch_formatter` from rubygems:

    gem install stopwatch_formatter

or put it in your `Gemfile`:

    gem 'stopwatch_formatter', :group => [:development, :test]

and `bundle install` as usual. You can specify to use the stopwatch formatter in a few ways:


<a id="rake-spec_opts"></a>

### `rake` `SPEC_OPTS`

If you use rake, and run rspec from within it, you can simply add the `SPEC_OPTS` variable to your run:

    rake SPEC_OPTS='-f StopwatchFormatter'


<a id="org6c6315a"></a>

### `.rspec`

A more convenient method is to put the formatter inside the `.rspec` file:

    --format StopwatchFormatter

then you can just run:

    rake

(assuming `spec` is one of you default tasks.)


<a id="specspec_helper"></a>

### `spec/spec_helper`

If you want a more permanent solution, you can configure the formatter inside the `spec/spec_helper.rb` file:

    require 'stopwatch_formatter'
    RSpec.configure {|c| c.add_formatter StopwatchFormatter }

This last rather permanently adds the stopwatch formatter to your runs, so if you specify another formatter on the command line or in `.rspec`, you'll end up with that output *and* the stopwatch output, so this isn't really recommended.


<a id="getting-the-formatter-contributing-and-all-that"></a>

## Getting the formatter, contributing, and all that

1.  Fork the github repository at <http://github.com/tamouse/stopwatch_formatter>
2.  Create a *new* branch for your changes.
3.  Commit your changes and push to the branch on your fork. Please rebase.
4.  Issue a pull request via Github.

