# PHP Style Guide

## Source Code Layout

 * Use _four spaces_ for each intendation level.
 * Lines should be at most 80 characters long.
 * Keep your methods/functions short and to the point.
 * Use UTF-8 as source file encoding.
 * Leave out the closing PHP tag in pure PHP files.
 * Use Unix Style line endings (`LF`).

### Whitespace

 * Lines should not have any trailing whitespace.
 * Put spaces around operators, such as `+`, `.`, `=`, etc.
 * Put a single space after the control statement and opening parenthesis.
 * You must not put spaces around the expressions inside brackets or parenthesis.
   
     ```php
     <?php
      
     # Bad:
     if ( ! $user ) {
      
     }
      
     $_GET[ "foo" ];
      
     # Good:
     if (!$user) {
      
     }
      
     $_GET["foo"];
     ```
 * Separate multiple classes/functions/methods by exactly one blank line.
   
     ```php
     <?php
    
     # Bad:
     function foo()
     {
     }
     function bar()
     {
     }
    
     # Good:
     function foo()
     {
     }
    
     function bar()
     {
     }
     ```
 * Do _not_ leave excessive numbers of blank lines before closing braces.
     
     ```php
     <?php
       
     # Bad:
     class Foo
     {
         function greet()
         {
             return "Hello!";
         }
       
       
       
         

         
         
         
         
     }
   
     # Good:
     class Foo
     {
         function greet()
         {
             return "Hello!";
         }
     }
     ```

### Braces

 * Put the opening brace on the same line as the `function` keyword when
   defining _anonymous_ functions.

     ```php
     <?php
   
     $power2 = function($number) {
         return $numer * $number;
     };
     ```

 * Put the brace on line by itself after Class, Interface or function 
   definitions (including methods).
   
     ```php
     <?php
   
     class Foo
     {
    	  function greet() 
    	  {
      		  return "Hello World";
    	  }
     }
   
     interface Bar
     {
     }
   
     function str_yadayada()
     {
     }
     ```
 
## Code Style

 * Code must not produce notices with `error_reporting` set to `E_ALL | E_STRICT`.
 * Be open with what you accept as function arguments.
 * Throw an `InvalidArgumentException` when you can't do _anything_ with the argument.
 * Return as early as possible.
   
     ```php
     <?php
    
     function getUser($id)
     {
        if ($user = Cache\get("user:$id")) {
            return $user;
        }
       
        # Do more.
     }
     ```

 * Throw exceptions in _exceptional cases_, that means when it ain't reasonable
   to execute the code that follows.
 * Consider throwing an Exception with a descriptive error message instead of
   returning `false`.
 * When something wasn't found consider returning `null`.
 * Put all of your code in a namespace.
 * Avoid adding new global functions.

## Language

 * Don't use more keywords than necessary.
 * When importing namespaces use _one_ `use` statement with a list of namespace/class names.
 
     ```php
     <?php
    
     use Foo\InvalidArgumentException,
         Foo\Bar\Baz;
     ```

 * Write all language constructs which act like functions (`require`, `include`, `echo`, `print`,…) _with_ parenthesis. They act like functions, so they should look like functions.
   
    ```php
    <?php
   
    # Bad:
    echo "Hello World\n";
   
    # Good:
    echo("Hello World\n");
    ```

### Classes

 * Omit the `public` keyword on public methods, so they are visually more distinct from private/protected methods. 
   
     ```php
     <?php
    
     class Foo
     {
         function greet()
         {
             return "Hello!";
         }
     }
     ```

 * You can omit the `public` keyword from public static properties.
   
     ```php
     <?php
    
     class Foo
     {
         # bad
         public static $foo;
       
         # good
         static $foo;
     }
     ```

 * Group properties by their visibility by writing the visibility keyword once and putting each property on its own line and adding one level of indent.
 
     ```php
     <?php
    
     class Foo
     {
         public
             $foo,
             $bar;
       
         protected
             $baz,
             $boo;
     }
     ```

## Naming

 * Use __U__pperCamelCase for classes, namespaces and interfaces.
 * Use __l__owerCamelCase for methods, _functions_ and variables. 
 * Do not use underscores in function names. Methods are functions, so they should be named using the same rules.
 * Use UPPER_CASE for constants and globals.
 * Avoid class names that end with "Manager".
 * Avoid a "do" prefix in function/method names.
   
     ```php
     <?php
    
     # Bad:
     $tasks->doLast(function() { … });
    
     # Good:
     $tasks->append(function() { … });
     ```

 * Method names should be verbs.
 * Variables which contain collections of objects should be named
   after the type of object they contain, only pluralized.
     
     ```php
     <?php
    
     # Bad:
     $taskList = new TaskList;
    
     # Good:
     $tasks = new TaskList;
     ```

## Documentation

 * Use the documentation style that's used in the rest of the project's code – That is either [phpdoc][] or [Tomdoc][].
 * Use the "#" comment character for inline comments and for Tomdoc doc blocks.
 * Put a single space after the comment character.
 * Document API functions with examples.
 
[phpdoc]: http://phpdoc.org
[tomdoc]: http://tomdoc.org
