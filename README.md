[![General Assembly Logo](https://camo.githubusercontent.com/1a91b05b8f4d44b5bbfb83abac2b0996d8e26c92/687474703a2f2f692e696d6775722e636f6d2f6b6538555354712e706e67)](https://generalassemb.ly/education/web-development-immersive)

# Ruby Loops

## Lesson Objectives

- Loops

## Loops

One of the most common things we do as developers is to iterate through data structures.

Whenever we talk about data in Ruby, its important to review how Ruby handles groups of data.

We learned how to iterate over collections in JavaScript using loops. Now we're going to learn the same in Ruby.

### Review JS Loops

<details>
<summary>What loops did we use in JavaScript?</summary>
<code>while</code>, <code>do...while</code>, <code>for</code>
</details>

### Looping with Ruby

In JS if we wanted to print numbers 0 through 3 we would:

```javascript
for(var i = 0; i < 3; i++) {
  console.log(i);
}
// > 0
// > 1
// > 2
```

In Ruby this is much cleaner:

```ruby
3.times { |i| puts i }
# > 0
# > 1
# > 2
```

`times` is a method that takes a _block_.  A block is just a chunk of code that may or may not take arguments.

We also have `.upto` and `.downto` methods for looping.

```ruby
#Initializing the number 
num1 = 8 
num2 = 12 
  
#Prints the number from num1 to num2 
num1.upto(num2){ | i | puts i, " "} 
```

<br>
Lets change it to .downto
<br><br>

But, the closest equivalent to JavaScript's `for` loop is Rubys `for...in` loop

```rb
users = ["Alice", "Bob", "Carol"]
for user in users do
  puts user
end
```

We can also iterate over arrays:

```ruby
arr = [10, 20, 30]

arr.each { |num| num }
# > 10
# > 20
# > 30

arr.map { |num| num / 10 }
# => [1, 2, 3]
```

`each` and `map` also take blocks (just like `forEach` and `map` take callbacks in JS).

### Ruby Map vs Each

What is the difference between map & each? <br><br>

Each is like a more primitive version of map…<br><br>

It gives you every element so you can work with it, but it doesn’t collect the results.<br><br>

Each always returns the original, unchanged object.<br><br>

While map does the same thing, but…<br><br>

It returns a new array with the transformed elements.
<br><br>
<hr>
<br>
For blocks with longer lines or multiple lines, replace `{` and `}` with `do` and `end`

```ruby
arr.map do |num|
  "#{num / 10} is great!"
end
# => ["1 is great!", "2 is great!", "3 is great!"]
```

And we can iterate over hashes:

```ruby
hash = { a: 1, b: 2, c: 3 }
hash.each do |key, val|
  puts "the value of #{key} is #{val}"
end
# > the value of a is 1
# > the value of b is 2
# > the value of c is 3
```

### Other types of Loops in Ruby

#### [while](https://ruby-doc.org/core-2.6.1/doc/syntax/control_expressions_rdoc.html#label-while+Loop)

```rb
input = ""
puts "You must guess the Magic Words to exit the while loop!"
while input != "Magic Words" do
  puts "What are the Magic Words?"
  input = gets.chomp
end
puts "You made it out! Congrats!"
```

#### [until](https://ruby-doc.org/core-2.6.1/doc/syntax/control_expressions_rdoc.html#label-until+Loop)


```rb
input = ""
puts "You must guess the Magic Words to exit the while loop!"
until input == "Magic Words" do
  puts "What are the Magic Words?"
  input = gets.chomp
end
puts "You made it out! Congrats!"
```

#### [loop](https://ruby-doc.org/core-2.6.1/Kernel.html#method-i-loop)

```rb
puts "You must guess the Magic Words to exit the while loop!"
loop do
  puts "What are the Magic Words?"
  input = gets.chomp
  break if input == "Magic Words"
end
puts "You made it out! Congrats!"
```

#### [.times](https://ruby-doc.org/core-2.6.1/Integer.html#method-i-times)

```rb
users = ["Alice", "Bob", "Carol"]
users.length.times do |index|
  puts users[index]  
end
```
> [**Further Reading on Ruby loops**](http://www.tutorialspoint.com/ruby/ruby_loops.htm)


### Labs
### Practice Each (15 minutes)

Use `each` to do the following...

- Say hello to everybody in the below array of names (sample output: `Hello Donald!`).

  ```ruby
  names = [ "Donald", "Daisy", "Huey", "Duey", "Luey" ]
 
names.each do |str| str
  puts "Hello #{str}! "
end
  ```

- Print out the squared values of every number in this numbers array.

  ```ruby
  numbers = [ 1, 3, 9, 11, 100 ]
  numbers = [ 1, 3, 9, 11, 100 ]
numbers.each do |num| num
  puts num*num
end
  ```

- Print out the Celsius values for an array containing Fahrenheit values.

  > Hint: `C = (F - 32) * (5 / 9)`

  ```ruby
  fahrenheit_temps = [ -128.6, 0, 32, 140, 212 ]
  
fahrenheit_temps.each do |num|
  puts  (num.to_f - 32) * 5 / 9
   
end
  ```

- Insert all the values in the `artists` array into the `ninja_turtles` array.

  ```ruby
  artists = [ "Leonardo", "Donatello", "Raphael", "Michelangelo" ]
  ninja_turtles = []

  artists.each do |str|
  ninja_turtles.push(str)
   
end
p ninja_turtles
  ```

- Print out every possible combination of the below ice cream flavors and toppings.

  ```ruby
  flavors = [ "vanilla", "chocolate", "strawberry", "butter pecan", "cookies and cream", "rainbow" ]
  toppings = [ "gummi bears", "hot fudge", "butterscotch", "rainbow sprinkles", "chocolate sprinkles" ]
  
  flavors.each do |str|
  puts "#{str} with #{toppings.sample}"
  puts flavors.product(toppings)
   
end
puts flavors.product(toppings)
  ```
<details>
  <summary>
    Hint
  </summary>
  Use nested enumerable methods or check out <a href="http://apidock.com/ruby/Array/product">product</a>.
</details>

### Map (30 minutes)

#### Explore 1

Run these two snippets separately:

```rb
cart = ["shoes", "watch", "computer"]
uppercase = cart.each do |product|
  caps_product = product.upcase
  puts caps_product
  caps_product
end
puts uppercase.join(", ")
```
with each didnt save change to array
```rb
cart = ["shoes", "watch", "computer"]
uppercase = cart.map do |product|
  caps_product = product.upcase
  puts caps_product
  caps_product
end
puts uppercase.join(", ")
```

How would you explain the difference in the result?
```
with map the change saved to array
```

#### Explore 2

Consider:

```ruby
cart = ["shoes", "watch", "computer"]
uppercase = []
cart.each{|product| uppercase.push(product.upcase) }
puts uppercase.join(", ")
```

```rb
cart = ["shoes", "watch", "computer"]
uppercase = cart.map{|product| product.upcase }
puts uppercase.join(", ")
```

What is the difference in the result of these two snippets?
```
same result
```

#### Explore 3: Bang

Consider:

```rb
cart = ["shoes", "watch", "computer"]
uppercase = cart.map{|product| product.upcase }
puts cart
puts uppercase
```

Below is the same snippet, but with `.map!` instead of `.map`.

What does `!` often indicate in Ruby?
```
here the change happen on new array 
```

```rb
cart = ["shoes", "watch", "computer"]
uppercase = cart.map!{|product| product.upcase }
puts cart
puts uppercase
```

What's the difference between `.map` and `.map!`?
```
here change affect on original array
```

### Practice Map (15 minutes)

Use `map` to do the following...  

1. Create an array that appends "Duck" to everybody in this array of first names

  ```ruby
  first_names = [ "Donald", "Daisy", "Daffy" ]

first_names.map do |str|
newarr = []
  newarr.push("#{str} Duck")
end
  #= ["Donald Duck", "Daisy Duck", "Daffy Duck"]
  ```

2. Create an array containing the squared values of every number in this array.

  ```ruby
  numbers = [ 1, 3, 9, 11, 100 ]

numbers.map do |num|
"#{num * num}"
end
  # => [1, 9, 81, 121, 10000]
  ```

3. Create an array with the Celsius values for these Fahrenheit values.

  > Hint: `C = (F - 32) * (0.555555)`

  ```ruby
  fahrenheit_temps = [ -128.6, 0, 32, 140, 212 ]
 
  fahrenheit_temps.map do |num|
  "#{(num - 32) * 0.555555}"
  end
  #=> [-89.2, -17.8, 0, 60, 100]
  ```
 <br>
 <br>
 <hr>
 
  
  ### Labs - More on Loops (30 minutes)
  
  <hr>
  Note: Think on it and guess what should be the right answer. Make a scanario on paper to check what is the result of each iteration before checking it on your systems.
 <hr>
 <br>

1. choose the correct answer. <br>
While loop checks the condition and the loop keeps on running till the condition is true, it stops when the condition becomes false. <br>
a) True 

--------

2. What is the output of the given code?

```ruby
counter = 1
while counter < 11
  puts counter
  counter = counter + 1
end
```
1. Prints the number from 1 to 10 


--------
3. What is the output of the given code?

```ruby
counter = true
while counter !=false
  puts counter
end
```
<ol type="a">
 
  <li>Infinite loop</li>

</ol>


---------

4. What is the output of the given code?

```ruby
i = 0
while i < 5
  puts i
   i=(i+1)**2
end
```
<ol type="a">
  
  <li>0 1 4</li>
  
</ol>

--------------

5. What is the output of the given code?
```ruby
a=5
b=15
while a&&b
puts a+b
end
```
<ol type="a">
  
  <li>20</li>
  

</ol>

--------------

6. What is the output of the given code?

```ruby
a=5
b=15
while b>a
puts a*(b-a)
while a>b
  a+=1
  b-=1
end
end
```
<ol type="a">
  
  <li>Infinite loop</li>
  

</ol>

---------------------

7. What is the output of the given code?
```ruby
i = 3
while i > 0 do
  print i
  i -= 1
end
```
<ol type="a">
  
  <li>321</li>

</ol>

---------------------

8. What is the output of the given code?
```ruby
i = 50
while i > 25 do
  print 50/i
  i -= 1
end
```
<ol type="a">

  <li>1111111111111111111111111</li>

</ol>

---------------------
9. What is the output of the given code?
```ruby
a = 5
b=10
while a<b do
  puts a*b
  a+=2
  b-=2
  end
```
<ol type="a">
  <li> 50 56</li>

</ol>

---------------------
10. What is the output of the given code?
```ruby
i = 50 
j=55
while i > 25 && j>35 do
  puts 50*j/i
  i -= 1
  j-=2
end
```
<ol type="a"> 
  <li> 55 54 53 52 51 50 48 47 46 45</li>

</ol>


---------------------
11. What is the output of the given code?
```ruby
i = 50 
j=55
while i > 25 && i*j<100 do
  puts (50*j)/i
  i -= 1
  j-=2
end
```
<ol type="a">
  <li>No output</li>

</ol>


---------------------
12. Take inputs from user to make an array. Again take one input from user and search it in the array and delete that element, if found. Iterate over array using for loop.
----------
 p "please enter multiple names : "
input = gets.split(' ')
p "please enter name to deleate it :"
input2 = gets.chomp
input.delete(input2)
puts input
------
  

13. Using (1...101), make two array, one containing all even numbers and other containing all odd numbers.

even = []
odd = []
for i in 0..101

if i.even? then
 even.push(i)
else 
  odd.push(i)
end

end 
p odd
p even

<!-- num1 = 1
num2 = 101
new1 = []
new2 = []
num1.upto(num2){ | i | 
if i.even? then new1.push(i)
else new2.push(i)
end
} 
print new1
print new2 -->
------






