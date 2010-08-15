# Around

Redefine existing methods while calling their previous version by another
name.

Similar to Rails's `alias_method_chain`, but without all the boilerplate.


# Usage

    require 'around'

    Array.def_around(:map, :eval_str) do |eval_s = nil, &block|
      !eval_s ^ !block or raise ArgumentError, "Must provide either eval_s or block."
      block ||= lambda { |_| eval(eval_s, binding) }
      map_without_eval_str &block
    end

    puts [1, 2, 3].map("_ * 2").join(", ")  # => 2, 4, 6


# API

## `def` methods
* `def_around`
* `class_def_around`
* `singleton_class_def_around`

## `disable` methods
* `around_disable_feature`
* `class_around_disable_feature`
* `singleton_class_around_disable_feature`


# License & Copyright

© 2009 Caio Chassot. Released under the WTFPL.

* <http://github.com/kch/around>
* <http://caiochassot.com>
* <http://sam.zoy.org/wtfpl>
