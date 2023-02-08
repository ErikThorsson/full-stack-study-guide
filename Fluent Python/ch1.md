* He creates a French Deck object using python dunder methods to show how custom classes can act like vanilla python objects.
* This chapter is mostly on the Python Data Model where he goes into under the hood operations and talks about the concept of metaobject protocol. 
    * metaobject protocol (python data model): the properties of objects in general in a specific computer programming language. These are the building blocks of the language itself. The "axioms" you could say.

* Interesting. len() is not a method and uses CPython for speed ("practicality beats purity").
	* The length of the object is read from a field in the C struct. Works with basic objs like str, list, memoryview, etc.
	* __len__ allows you to create a slower method call to work with your custom objects. "A fair compromise".

* Python allows operator overloading.
	* e.g. you can overload the "+" operator to work in custom ways with your objects.

* __repr__ supercedes __str__ if the latter isn't implemented
	* good practice is __repr__ should be as unambiguous as possible for helpful debugging/logging
	* __str__ is more for end users (called by str())

* Python accepts any object in a Boolean context.
	* To determine if a value x is truthy or falsy, applies bool(x), which calls x.__bool__()
		* if __bool__ is not implemented tries to invoke x.__len__() - e.g. in case of empty list. [] == False
		* so we can make custom truthiness for our objects with __bool__

* Collection API
	*  unifies the three essential interfaces that every collection should implement
		*  Iterable to support for, unpacking 
		*  Sized to support len
		*  Container to support in
	*  Sequences, Mappings, and Sets are Collections
		*  Sequences: list, str
		*  Mapping: dict, defaultdict, etc
		*  Set: set and frozenset

* Only Sequences are Reversible since they support arbitrary ordering of their contents while mappings and sets do not.
	*  dict is officially "ordered" in 3.7 but that only means that key insertion is preserved.