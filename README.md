# Objetive-C-Style-Guide
A guide that outlines coding conventions used by CDP2-Mobile Frameworks.

### Coding Practices

* In *switch* statements, brackets are desired around each *case*. If multiple cases are used, they must be on separate lines. *default* should always be the last case.

  ```objective-c
  switch(variable) {
      case firstValue: {
          //some expression
      }
          break;
      case secondValue: {
          //some other expression
      }
          break;
      default:
          break;
  }
  ```

* *NSInteger, NSUinteger* and *CGFLoat* should be used instead of *int, u_int* and *float*. *NSTimeInterval* should be used when dealing with time intervals instead of double.

* When dealing with numbers, be sure to use the right type out of NSInteger, NSUInteger and CGFloat. Using wrong type might not give you a warning but might result into overflow, loss of sign or precision.

* Use right loops for the given requirement. Do not use *for-loop* where *for-in* or enumerator could be used.

* Prefer using *@class* instead of *#import* to import a class if you only need a reference to the class and do not need to call a method or property. It provides performance boost.

* Do no import files in header file(.h) if they are only needed in implementation(.m) file.

* No more ***ivars***. Every property has an *ivar* created for it, automatically.

* No variable should be created outside class scope.

* No ***#define*** for declaring constant variables. Use *const* qualifier instead. For convenience methods also, use inline functions. Use a clear and consistent prefix while declaring constants.

* No method should start with _ or __. Those are reserved for system.

* Property getters should not start with. Use 'get' prefix only for method names that return objects and values indirectly. For example:

  ```objective-c
  - (void)getLineDash:(float *)pattern count:(int *)count phase:(float *)phase;
  ```

* Do not use 'and' in method name to link parameters. It should be used only to link actions. But, no method should have more than one action (SOLID). Hence, 'and' should not be used in method names.

* No more *objectForKey* and *objectAtIndex*. Use subscript convention of Objective-C 2.0.

* No abbreviations inproperty and method names. Be explicit about their purpose.

* Use prefixes when naming classes, protocols, functions, categories, constants and typedef structures. Do not use prefixes when naming methods and properties.

* Use enums to create a group of integer constants. Create float constants with const. Create integer constants with const only if does not belong to any group.

* Do no initialize variables to 0 or nil. Its redundant.

* Avoid *+new* for creating objects.

* Do not use accessors during *-init* and *dealloc* to avoid memory inconsistency. Instead, use *ivar* version of the property.

* User *NS_ENUM* and *NS_ENUM_OPTIONS* instead of *typedef enum* for creating enum.

* Use right initializer for given requirements.

  ```objective-c
  //Use below initializer if list does not need to be mutated
  NSArray *immutableList = @[];
  
  //Use below initializer if list need to be mutated but final size if known
  NSArray *mutableListWithKnownSize = [[NSMutableArray alloc] initWithCapacity:knownCapacity];
  
  //Use below initializer only when list need to be mutated and final size is unknown
  NSArray *mutableListWithUnknownSize = [[NSMutableArray alloc] init];
  ```

  

### Beautification Practices

* Spaces around operators, always. Even ternary operator.

  ```objective-c
  a=b; //❌
  a=b==nil?c:d; //❌
  a = b;  //✅
  a = (b == nil ? c : d); //✅
  ```

* There should **always** be a space between end of method name and the starting bracket. Starting bracket of method definition **must** be in same line.

* Method type (+ or -) **must** be followed by a space.

  ```objective-c
  -(void)someAwesomeMethod{ //❌ Not so awesome
  }
  
  - (void)anotherAwesomeMethod { //✅ Thats the one I'm talking about
  }
  ```

* There should not be a space before or after colons in method name. If the parameter type is a pointer, there should **always** be a space between class name and * operator.

* There should always be exactly two blank lines between method definitions.

* Use pragma marks to group methods by their purpose/inheritence.

* There should **always** be a space between control structure (i.e. if, else etc) and their opening brackets.

* While declaring a property, **nonatmoic** be should be first qualifier, **weak**/**strong**/**assign** and third should be **read**/**write** qualifiers if applicable. Rest should be next in order.

* Try to list imports and properties in alphabetical order.

* Initialization methods should always be on top of all the method declaraions and implementations. Also, declarations and implementations of methods must maintain same order.



Readings and References:

1. https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/CodingGuidelines/CodingGuidelines.html#//apple_ref/doc/uid/10000146-SW1 
2. https://developer.apple.com/library/content/releasenotes/ObjectiveC/ModernizationObjC/AdoptingModernObjective-C/AdoptingModernObjective-C.html#//apple_ref/doc/uid/TP40014150-CH1-SW6 

