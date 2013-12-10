# SubclassJS

## Simple JavaScript Inheritance

 * Originally from the [blog](http://ejohn.org/blog/simple-javascript-inheritance/) and the book: ["Secrets of the JavaScript Ninja"](http://amzn.to/17f0RS8) by [John Resig](http://ejohn.org/)

 * Extended to support getters & setters

## Usage

*__Install [5 min fork](http://5minfork.com/) browser extension to see this example directly on GitHub without even downloading anything!__*

	var Person = Object.subClass({

		init: function( isDancing ) {
			this.dancing = isDancing;
		},

		// Ninja will inherit this property
		set name( newName ) {
			this._name = newName;
		},

		// Ninja will inherit this property
		get name() {
			return this._name;
		},

		dance: function() {
			return this.dancing;
		}
	});

	var Ninja = Person.subClass({

		init: function() {
			this._super( false );
		},

		dance: function() {
			// Ninja-specific stuff here
			return this._super();
		},

		swingSword: function() {
			return true;
		}
	});

	var person = new Person( true );
	person.name = "Rukia";
	assert( person.dance(), person.name + " is dancing." );

	var ninja = new Ninja();
	assert( ninja.swingSword(), "The sword is swinging." );
	ninja.name = "Ichigo Kurosaki";
	assert( !ninja.dance(), ninja.name + " is not dancing." );

	assert( person instanceof Person, "Person is a Person." );
	assert( ninja instanceof Ninja && ninja instanceof Person, "Ninja is a Ninja and a Person." );


## Copyright and license

Copyright © 2013 [Miroslav Hibler](http://miro.hibler.me)

Licensed under the [**MIT**](http://miro.mit-license.org) license.
