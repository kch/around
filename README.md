# Around

Redefine existing methods while calling their previous version
by another name. No boilerplate needed.


# Usage

    class Array
      def_around :map, :eval_str do |eval_s=nil, &block|
        !eval_s ^ !block or raise ArgumentError, "Must provide either eval_s or block."
        map_without_eval_str &(block || lambda { |_| eval(eval_s, binding) })
      end
    end
    puts [1,2,3].map("_ * 2")


# API

## `def` methods
* `def_around`
* `class_def_around`
* `eigenclass_def_around`

## `disable` methods
* `around_disable_feature`
* `class_around_disable_feature`
* `eigenclass_around_disable_feature`


# License & Copyright

© 2009 Caio Chassot. Released under the WTFPL.

* http://github.com/kch/around
* http://caiochassot.com
* http://sam.zoy.org/wtfpl
