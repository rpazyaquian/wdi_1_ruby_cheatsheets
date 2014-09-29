# self

`Self` inside a method, it refers to the class instance itself.

Calling `self` will return something like this:

    # SampleClass:0x007fff2b889a00 @instance_variable=value

`Self` is useful if you are calling methods from within methods.

There is also the class-level `self`, which is useful in situations such as this:

    sample_class.about_history  # doesn't make sense, history of an instance???
    SampleClass.about_history  # now this makes sense, history of an entire Class, rather than a single instance of it - maybe a list of all instances created?

In a method name, `self` refers to the class as a whole.

    def self.about_history
      # ...
    end

A class-level variable tracks everything within a certain class.

    @@counter = 0

      def initialize(temp_in_c)
        @temperature = temp_in_c
        @@counter += 1
      end

Instance variable: `@instance_variable`

Class variable: `@@class_variable`

# Classes vs. Modules

Classes create objects.

Modules give those objects more functionality and let them share behavior.

    # inheritance gives us methods that work for both
    # dogs AND birds

    class Dogs < Animal
    end

    class Birds < Animal
    end

    class Animal
      def sleep
      end

      def eat
      end
    end

    class Dinosaurs < Animal
    end

    # pretend all dinosaurs can fly, but remember that dogs can't!
    # how do we give Birds and Dinosaurs the same flyability
    # without extending it to Dogs?

    # what we do is create a module that we mix in wherever we want

    # modules are like extra functionality that we can mix in wherever we want

    module Flying
      def fly
      end
      def land
      end
    end

    class Birds
      include Flying
    end

    class Dinosaurs
      include Flying
    end

    # now birds and dinosaurs can fly, but dogs can't!
    # problem solved

Modules are great for namespacing things.

    module NameOfGame
      class Character
        #methods
      end
    end

    NameOfGame::Character.create  # specifies which Character class

