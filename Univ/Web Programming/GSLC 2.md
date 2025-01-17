
# Array vs Collection

- Arrays
	In most programming languages, arrays are a data structure where we can store and organize lots of values of the same data type, and we can extract those values by indexing them. Higher level programming languages like python and php (Which laravel uses) can contain values with differing data types in a single array. So in php, we can store numbers, strings, or even functions in a single array.  And there are also different types of arrays in PHP, like indexed arrays which essentially is just a normal array, Associative array, which stores values in a key-value pair, similar to dictionaries in python, multidimensional arrays, etc. However array is limited in that It's very hard to dynamically change the size of the array to either safe space when we don't need lots of space, or we need to increase the space quickly to allocate for more values being stored. Arrays have basic functionalities provided by PHP, but is limited for more complex operations.

- Collections
	Collection is essentially a wrapper for an array, meaning that it does and behaves exactly like an array, with added functionalities that we can utilize in ways we can't really do to an array. Collection is an instance of the `Illuminate\Support\Collection` class in laravel. Collection provides a rich set of methods that can allow us to manipulate data in a more efficient and dynamic way, methods like `map()`, `filter()`, `reduce()`, `pluck()`, and many more. Collections are also considered as objects, so they support method chaining, allowing us to use a more maintainable code when we want to perform multiple operations in a sequence to a certain collection. In conclusion, a collection is a wrapper for an array as a way to compensate the limitations and drawbacks of arrays by providing many methods, allowing us to be able to perform complex operations on data efficiently.


# Implementation

Controller
![[Pasted image 20241129093033.png]]


View
![[Pasted image 20241129093103.png]]

Route
![[Pasted image 20241129093116.png]]

Page
![[Pasted image 20241129093215.png]]

