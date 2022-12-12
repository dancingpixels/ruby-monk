# Ruby objects

## Everything is an object

In Ruby, just like in real life, our world is filled with objects.  Everything is an object - integers, characters, text, arrays - everything. To make things happen using Ruby, one always puts oneself in the place of an object and then has conversations with other objects, telling them to do stuff.

Role-playing as an object in your program is an integral part of object-oriented programming.  To know which object you are at the moment, one may use the keyword `self`.

```ruby
self
 => main 
```

if you don't specify which object you are, you automatically play the role  of the `main` object that Ruby provides us by default.

## Talking to objects

One object interacts with another by using what are called  `methods`. More specifically, one object "calls or invokes  the methods" of another object.

In the example below, we call the method `even?` on the object that is the number `2` by placing a period  (`.`) after the object, then adding in the name of the  method we want to invoke.

```ruby
2.even?
 => true 
```

Invoking a method on an object inevitably generates a response.  This response is *always* another object.  Calling the method `next` on the object `1` has it give us the next consecutive value  `2`.

One may also chain method invocations by simply adding more periods  and method names sequentially - each method in the chain is called on  the result of the previous method.  

```ruby
1.next.next
 => 3 
```

## Looking up methods

Ruby objects are happy to tell you what methods they provide, if you call the `methods` method on them.

```ruby
1.methods
```

## Invoking methods with arguments

When talking to an object via its methods, it is possible to give it additional information so it can give you an appropriate response. This additional information is called the _arguments to a method._ The  name _argument_ makes sense if you stop to think about the fact that  methods are the paths of communication between objects.

```ruby
> ['rock','paper','scissors'].index('paper')
 => 1 
```

Here, `index` is the method and `'paper'` the argument.  If there is more than one argument, they can be passed to the method by simply separating them with commas.

```ruby
> 2.between? 1, 3
 => true 
```

## Special Methods

Integer objects list mathematical operators like  `+` and `-` among their methods.  You probably also thought to yourself that invoking the `+` method  like so - `1.+(2)` - to add two numbers would be clumsy - It is, though it works just fine.

```ruby
> 1.+(2) 
=> 3 
```

Ruby as a language aims to be extremely programmer-friendly, so you  can usually safely assume that there is a better way.  Ruby makes an exception in its syntactic rules for commonly used operators so you   don't have to use periods to invoke them on objects.

```ruby
> 1+2
 => 3 
```

There are several other method names that have this special status -  here's a quick summary of the ones you're most likely to run into.

```text
+   -   *   /   =   ==    !=    >   <   >=    <=    []
```

This last method (`[]`) is arguably the most unique in its syntax.  Not only does it not require a period, it also *encloses* the  arguments to itself. 

```ruby
> words = ["foo", "bar", "baz"]
> words[1]
 => "bar" 
```

Even more interesting is that it still works if you use the more  traditional method syntax.

```ruby
words = ["foo", "bar", "baz"]
words.[](1)
=> "bar" 
```

This is a common pattern in Ruby - two different ways to do the same thing where one remains consistent and the other changes the syntax to be more programmer friendly.

# Intro to Strings

## Literal forms

String construction has what is known as a literal form - the interpreter treats anything surrounded with single quotes (`'`) or double quotes(`"`)  as a string. In other words, both `'RubyMonk'` and `"RubyMonk"` will create instances of strings.

All `Strings` are instances of the Ruby `String` class which provides a number of methods to manipulate the string.

## String Length

As a programmer, one of the common things you need to know about a `String` is its length.

```ruby
> 'RubyMonk'.length
 => 8 
```

## String Interpolation

It is essential to be able to replace placeholders within a string with values they represent. In the programming  paradigm, this is called "string interpolation". In Ruby, string interpolation is extremely easy.  

```ruby
a,b = 1, 4
puts "The number #{a} is less than #{b}"
 => "The number 1 is less than 4"  
```

Placeholders aren't just variables. Any valid block of Ruby code you place inside `#{}` will be evaluated and inserted at that location.

Difference between single quote strings & double quote strings:



| Single Quotes                                                | Double Quotes                                                |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Does not support Interpolation                               | Supports Interpolation                                       |
| Does not allow for escape sequences  -   `'\n'` displays the actual escape sequence to the user. | Allows for escape sequences - `“\n”` is interpreted as a new line and appears as a new line when rendered to the user. |

## String Searches

It is conventional in Ruby to have '?' at the end of the method if that method  returns only boolean values. it is not mandated by the syntax, this practice is  highly recommended as it increases the readability of code.

```ruby
"[Luke:] I can’t believe it. [Yoda:] That is why you fail.".include? "Yoda"

"Ruby is a beautiful language".start_with? "Ruby"

"I can't work with any other language but Ruby".end_with? "Ruby"
```

Sometimes we will be required to know the index of a particular character or a sub-string  in a given String and conveniently Ruby provides a method on String that does exactly that.

```ruby
"I am a Rubyist".index "R"
=> 7
```

## Change Case

Ruby provides us with a convenient tool-set to take care of proper  and consistent casing within strings. 

```ruby
puts 'i am in lowercase'.upcase 
```

Similarly, one can convert a string to lower case as well. Ruby  calls this method `downcase`

```ruby
'This is Mixed CASE'.downcase
```

When you  encounter a mixed cased string, [Ruby provides a way to swap the case of every character in it i.e. this method would convert `I Am MixEd` to `i aM mIXeD`.

## Splitting Strings

Splitting strings on a particular word, escape character or white space  to get an array of sub-strings, is an oft-used technique.  The method the Ruby `String` API provides for this is String#split.

Here's an example of splitting a string on space ' ', to get a collection of words in the string.

```ruby
> 'Fear is the path to the dark side'.split(' ')
 => ["Fear", "is", "the", "path", "to", "the", "dark", "side"] 
```

One can effectively manipulate strings by combining String#split and a Regular Expressions. It is possible to similarly split strings on new lines, and parse large amounts of data that is in the form of CSV.

## Concatenating Strings

You can create a new string by adding two strings together in Ruby, just like most other languages.

```ruby
'Ruby' + 'Monk'
```

Ruby often provides more than one way to do the same thing. The literal  and expressive method for String concatenation is `String#concat`.

```ruby
"Ruby".concat("Monk")
```

There's a more widely used alias `<<`.  You can use '<<' just like '+', but in this case the String  object 'Monk' will be appended to the object represented by 'Ruby'  itself.

```ruby
"Ruby" << "Monk"
```

In  the first case of using '+', the original string is not modified, as a  third string 'RubyMonk' is created. This can make a huge difference in  your memory utilization, if you are doing really large scale string  manipulations.

## Replacing a substring

The Ruby String API provides strong support for searching and replacing  within strings. We can search for sub-strings or use Regex.

```ruby
> "I should look into your problem when I get time".sub('I','We')
 => "We should look into your problem when I get time" 
```

The method above only replaced the first occurrence of the term we were  looking for. In order to replace all occurrences we can use a method  called `gsub` which has a global scope.

```ruby
> "I should look into your problem when I get time".gsub('I','We')
 => "We should look into your problem when We get time"
```

Regular Expressions or RegExs are a concise and flexible means for  "matching" particular characters, words, or patterns of characters.  In Ruby you specify a RegEx by putting it between a pair of forward  slashes (`/`).  

An example that replaces all the vowels with the number 1:

```ruby
"RubyMonk".gsub(/[aeiou]/, '1')
 => "R1byM1nk" 
```

## Find a substring using RegEx

The String#match method converts a pattern to a Regexp (if it isn‘t  already one), and then invokes its match method on the target String  object.  Here is how you find the characters from a String which are next to a  whitespace:

```ruby
'RubyMonk Is Pretty Brilliant'.match(/ ./)
 => #<MatchData " I"> 
```

# Conditions and Loops

## Expressions in Ruby

