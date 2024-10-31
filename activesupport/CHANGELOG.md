*   `ActiveSupport::BroadcastLogger` now correctly supports `with_level`, which has been
    [available in Ruby's Logger](https://docs.ruby-lang.org/en/3.3/Logger.html#method-i-with_level).

    Previously, the behavior was for `#method_missing` to forward `with_logger` to _each_ of its broadcast loggers,
    which could cause the block to be invoked multiple times when broadcasting to multiple loggers.

    *meagar*

*   `ActiveSupport::CurrentAttributes#attributes` now will return a new hash object on each call.

    Previously, the same hash object was returned each time that method was called.

    *fatkodima*

*   `ActiveSupport::JSON.encode` supports CIDR notation.

    Previously:

    ```ruby
    ActiveSupport::JSON.encode(IPAddr.new("172.16.0.0/24")) # => "\"172.16.0.0\""
    ```

    After this change:

    ```ruby
    ActiveSupport::JSON.encode(IPAddr.new("172.16.0.0/24")) # => "\"172.16.0.0/24\""
    ```

    *Taketo Takashima*

Please check [8-0-stable](https://github.com/rails/rails/blob/8-0-stable/activesupport/CHANGELOG.md) for previous changes.
