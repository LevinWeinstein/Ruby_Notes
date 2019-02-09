(Detailed notes / copy of Array documentation from Ruby-Doc.org)
# Array
* Arrays are ordered, integer-indexed collections of any object.
* Array indexing starts at 0, as in C or Java.
* A negative index is assumed to be relative to the end of the array
    * that is, an index of -1 indicates the last element of the array, -2 is the next to last element in the array, and so on.
## Creating Arrays
### The literal constructor
*  A new array can be created by using the literal constructor [].
* Arrays can contain different types of objects.
    *  For example, the array below contains an Integer, a String, and a Float
```ruby
ary = [1, "two", 3.0] #=> [1, "two", 3.0]
```
### Array.new
* An array can also be created by expliciatally calling  __::new__ with:
    1. zero arguments,
    2. one argument
        1. The initial size of the array
    2. or two arguments
    1. The initial size of the array
        2. A default object
```ruby
ary = Array.new		#=> []
Array.new(3)		#=> [nil, nil, nil]
Array.new(3, true)	#=> [true, true, true]
```

### Second Argument Warning: copies reference
Note that the second argument populates the array with references to the same object. Therefore, it is only recommended in cases when you need to instantiate arrays with natively immutable objects such as Symbols, numbers, true or false.

### Safe way to make seperate default objects
To create an array with separate objects a block can be passed instead. This method is safe to use with mutable objects such as hashes, strings, or other arrays:
```ruby
Array.new(4) { Hash.new } #=> [{}, {}, {}, {}]
```
This is also a quick way to build up multi-dimensional arrays:
```ruby
empty_table = Array.new(3) { Array.new(3) }
```

### Array() method
* An array can also be created by using the Array() method, provided by Kernel.
* This method tries to call `to_ary`, then `to_a` on its argument.
```ruby
Array({:a => "a", :b => "b"}) #=> [[:a, "a"], [:b, "b"]]
```

## Example Usage
In addition to the methods it mixes in through the __Enumerable__ module, the __Array__ class has proprietary methods for accessing, searching, and otherwise manipulating arrays. 

Some of the more common ones are illustrated below.

## Accessing Elements

### #[], and ::at and ::slice
Elements in an array can be retrieved using the #[] method. It can take a single integer argument (a numeric index), a pair of arguments (start and length), or a range. Negative indices start counting from the end, with -1 being the last element.
```ruby
arr = [1, 2, 3, 4, 5, 6]
arr[2]      #=> 3
arr[100]    #=> nil
arr[-3]     #=> 4
arr[2, 3]   #=> [3, 4, 5] (Goes three elements long, starting at index 2)
arr[1..4]   #=> [2, 3, 4, 5] (Goes from element 2 through element 5)
arr[1..-3]  #=> [2, 3, 4] (Goes from element two through the 3rd to last element)
```
Another way to access a particular array element is by using the __at__ method
```
arr.at(0) #=> 1
```
The __slice__ method works in an identical manner to #[]. (Note: In every single listed way)

### ::fetch
* To raise an error for indices outside of the array bounds
* or to provide a default value for indices outside of the array bounds
* You can use ::fetch.
```ruby
arr = ['a', 'b', 'c', 'd', 'e', 'f']
arr.fetch(3)            #=> "d"
arr.fetch(100)          #=> IndexError: index 100 outside of array bounds: -5...5
arr.fetch(100, "oops") #=> "oops"
```

### Special Methods: ::first and ::last
The special methods first and last will return the first and last elements of an array, respectively.
```ruby
arr.first   #=> a
arr.last    #=> f

arr.first 2 #=> ["a", "b"]
arr.last 2 #=>
```

### ::take and ::drop

[me] Take and drop work the same as First and Last do when they are provided an integer argument, except they don't work at all when not provided an integer argument.

* To return the first _n_ elements of an array, use __take__
```ruby
arr.take(3) #=> ["a", "b", "c"]
```

* __drop__ does the opposite of __take__, by returning the elements after n elements have been dropped.

```ruby
arr.drop(1) #=> ["b", "c", "d", "e", "f"]
```

## Obtaining information about An Array

### ::length, ::count, ::size (all the same)
Arrays keep track of their own length at all times. To query an array about the number of elements it contains, use __length__, __count__, or __size__.
```ruby
browsers = ['Chrome', 'Firefox', 'Safari', 'Opera', 'IE']
browsers.length #=> 5
browsers.count  #=> 5
browsers.size   #=> 5
```

### ::empty? and ::include?
To check whether a particular item is included in the array
```ruby
browsers.include?('Konqueror')  #=> false
```

## Assing Items to Arrays
### `::push` and `#<<`
* Items can be added to the end of an array by using either __push__ or __<<__
    * push can take multiple arguments and push them all
    * << can only take one argument
```ruby
arr = [1, 2, 3, 4]
arr.push 5     #=> [1, 2, 3, 4, 5]
arr << 6       #=> [1, 2, 3, 4, 5, 6]
arr.push 7, 8  #=> [1, 2, 3 ,4 ,5, 6, 7, 8]
arr << 7, 8    #=> SyntaxError: unexpected ',', expecting end-of-input
```

### ::unshift
* __unshift__ will add (a) new item(s) to the beginning of an array.
```ruby
arr.unshift 0       #=> [0, 1, 2, 3, 4, 5, 6]
arr.unshift -3, -2, -1  #=> [-3, -2, -1, 0, 1, 2, 3, 4, 5, 6]
```

### ::insert
* With __insert__ you can add a new element to an array at any position
* You can also insert multiple values at once
```ruby
arr.insert(3, 'apple') #=> [0, 1, 2, 'apple', 3, 4, 5, 6]
arr.insert(3, 'orange', 'pear', 'grapefruit')
#=> [0, 1, 2, "orange", "pear", "grapefruit", "apple", 3, 4, 5, 6]
```

# 
