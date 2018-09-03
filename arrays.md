# Arrays

## Declaration:
* You can declare an array of HP characters like so:
```ruby
students = ["Harry Potter", "Ron Weasley", "Hermione Granger", "Draco Malfoy]
```

* You can declare an empty array like so:
```ruby
# The Literal Constructor
my_array = []

# The Class Constructor
my_array = Array.new
```


## Array Methods:
* Arrays are actually a class of data structure in Ruby
   * (Not merely a block of allocated memory for a series of primitives like in Java, C++, or C)
### The methods are:

1. The shovel method
    * adds an item to the end of an array
```ruby 
    dogs = ["biggy", "snowwy"]
    dogs << ["bijou"]
    dogs #=> ["biggy", "snowwy", "bijou"]
```

2. The .push Method
    * adds a variable amount of items to the end of an array.
    * can be used just like shovel, but you can list as many items as you'd like, instead of just one.
```ruby
    items = ["bacon", "eggs"]   
    items.push("lettuce", "tomato", "avocado")
    items.inspect #=> "[\"bacon\", \"eggs\", \"lettuce\", \"tomato\", \"avocado\"]
```

3. The .unshift Method
    * adds an item to the front of the array.
    * this makes sense due to the fact that shift removes an item from the front of the array.
    * like pop, this can handle multiple elements at once.
```ruby
    count = [1, 2, 3]
    count.unshift(0)
    count #=> [0, 1, 2, 3]
    count.unshift(-2, -1)
    count #=> [-2, -1, 0, 1, 2, 3]
```

4. The .pop Method
    * removes an item from the end of an array.
    * returns that item.
    * works in accordance with push, in the same way specified by a Stack adt.
    * returns nil if no items in array when called.
    * a number of elements to pop can be specified
        * if the number is greater than the length of the array, <br /> all elements will be popped successfully.

```ruby
    count = []
    count.pop #=> nil
    
    count.push    2,3,4
    count #=>    [2,3,4]

    count.pop #=>  4
    count     #=> []
``` 

5. The .shift Method
    * removes items from the front of the array
    * returns those items, just like pop.
    * also returns nil if the array is empty, just like pop.
    * a number of elements to shift can be specified
        * if the number is greater than the length of the array, <br /> all elements will be shifted successfully.
```ruby
    count = []
    count.shift #=> nil

    count.push      2,3,4
    count      #=> [2,3,4]

    count.shift #=> 2
    count       #=>[3, 4]
```


