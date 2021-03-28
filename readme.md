
## PHP OOP Quiz

Entry for the code challenge for March 2021 set by:

[Howtocodewell](https://codechallenges.howtocodewell.net/)

As specified in the challenge, Markdown is used as the format for the answers.


## Question 1

Is multiple inheritance supported in PHP [yes/no]?

Answer:

For multiple 'class' inheritance, No.


## Question 2

Explain the difference between a class and an object.

An analogy to explain the difference between a class and an object is that a class acts like a blueprint/plan for a physical object.
You use the blueprint/plan which specifies the detail as to how the physical object is composed.
A real-world example is if you want to create a house. You can use a blueprint to create a house. Once the house has been created, you can use the house to live in as it is a physical object, but you cannot live in a blueprint.
Also a single blueprint can be used to make many house objects.  
A class is used as a template to create an object in software. A class can be used to make many objects.

## Question 3

Demonstrate the Singleton pattern.

Answer:

```php
<?php

// This demonstrates a Singleton pattern.
// Works within a console window.

 
class Singleton {

	static private $_instance = NULL;

	private $_setting = '';

	// Ensure construct() and clone() cannot be used by making them private
	private function __construct() {}
	private function __clone() {}

	static function getInstance() {
		if(self::$_instance == NULL) {
			self::$_instance = new Singleton();
		}

		return self::$_instance;
	}

	function set($value) {
		$this->_setting=$value;
	}

	function get() {
		return $this->_setting;
	}

}


// Create the first object
$objOne = Singleton::getInstance();
$objOne->set('This is the only set value');
echo "objOne setting : ". $objOne->get()."\n";

// This won't actually create a brand new instance as both $objOne and $objTwo 
// point to the same instance:
$objTwo = Singleton::getInstance();
echo "objTwo setting : ". $objTwo->get();

// Housekeeping
unset($objOne, $objTwo);
```

## Question 4

Explain why the Singleton pattern is sometimes considered an anti-pattern.

Answer:  

Global variables can break encapsulation and cause problems in larger OOP programs. Because of this, global variables should be kept to a minimum.
Singleton patterns use static variables. Static variables share many of the same characteristics as global variables. Singleton design patterns can act like global variables, which is why they can sometimes be considered as an anti-pattern.

In the book 'Learning PHP Design Patterns', author William Sanders does not include an example of the Singleton design pattern for this purpose.

Eric Gamma, lead author of the 'Design Patterns: Elements of Re-usable Object-Oriented Software' book and member of the 'Gang of Four' is quoted as being in favour of dropping the Singleton pattern. He says that 'Its use is almost always a design smell'.  
[Link](https://www.informit.com/articles/article.aspx?p=1404056)

## Question 5

Explain what an abstract class does?

Answer: 

An abstract class enforces what methods are to be in a child class that inherits from it.
You are free to add your own code within these methods in the child class. What is important is that the methods are present and available for use in the child class.
An abstract class can also contain concrete methods too.



## Question 6

Can an abstract class extend another abstract class [yes/no]?

Answer:

Yes.


## Question 7

Can a PHP interface extend another interface [yes/no]?

Answer:

Yes.


## Question 8

How many interfaces can a PHP class implement?

Answer:

Theoretically an unlimited number, but there must not be a clash of method names.


## Question 9

Explain when you would use an interface instead of an abstract class?

Answer:

When you want to force a developer(or yourself) to create specific methods for a child class. An interface won't allow you to pre-supply any code for these methods, making it a better option than an abstract class, which does allow for code to be pre-supplied. 
An interface will not allow concrete methods, so will allow you to decouple your code from concrete classes. 



## Question 10


Explain the output of the following code:

```php
<?php
final class BaseClass {
   public function test() {
       return "BaseClass::test() called";
   }
}

class ChildClass extends BaseClass {

}

$obj = new ChildClass();
$output = $obj->test();
echo $output;
?>

```

Answer:  

The following error is generated: 

`Class ChildClass may not inherit from final class (BaseClass)`  

This is because BaseClass is defined as a `final` class.
Which means that the class's method may not be overridden and cannot be extended.

Removal of the `final` keyword from the script would allow `ChildClass` to extend the `BaseClass` and return the output:  
`BaseClass::test() called`  
However, as a developer you should be cautious and seek guidance before doing so, as there may be a valid reason as to why the `BaseClass` shouldn't be extended. 

