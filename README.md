# dominus

> Lean DOM Manipulation

# Install

Using Bower

```shell
bower install -S dominus
```

Using `npm`

```shell
npm install -S dominus
```

Dominus is like jQuery, minus the cruft. Dominus uses [`Sizzle`][1] as its selector engine of choice, so you rest assured that the best part of jQuery is also available from Dominus.

# API

Just like with jQuery, Dominus exposes a rich API that's chainable to the best of its ability. The biggest difference with jQuery at this level is that the `Dominus` wrapper is a real array. These arrays have been modified to include a few other properties in their prototype, but they don't change the native DOM array. [See `poser` for more details on that one.][3] All of this means you can `.map`, `.forEach`, `.filter`, and all of that good stuff that you're used to when dealing with JavaScript collections, and at the same time you get some extra methods just like with jQuery.

## Static Methods

These are the static methods provided by Dominus. Consider these _the entry point_, just like the methods exposed by jQuery on `$`.

### `dominus()`

Returns an empty `Dominus` collection.

### `dominus(HTMLElement)`

Wraps the [`HTMLElement`][2] object in a `Dominus` collection.

### `dominus(Dominus)`

Returns the `Dominus` collection, as-is.

### `dominus(Array)`

Returns a `Dominus` collection with the [`HTMLElement`][2] objects found in the provided array.

### `dominus(selector, context?)`

See `dominus.find` below.

### `dominus.find(selector, context?)`

Queries the DOM for the provided selector, using [Sizzle][1]. Returns a `Dominus` collection with [`HTMLElement`][2] objects. If `context` is provided then the search is restricted to children of `context`.

### `dominus.findOne(selector, context?)`

Queries the DOM for the provided selector, using [Sizzle][1]. Returns the first matching [`HTMLElement`][2] object, if any. If `context` is provided then the search is restricted to children of `context`.

## Instance Methods

Once you've gotten yourself a `Dominus` collection, there's a few more methods you'll get access to. I'll denote array instances as `a`, where possible.

### `a.find(selector)`

Queries the DOM for children of the elements in the array, using the provided selector. Returns a single `Dominus` collection containing all of the results.

### `a.findOne(selector)`

Queries the DOM for children of the elements in the array, using the provided selector. Returns the first matching [`HTMLElement`][2] object, if any.

### `a.where(selector)`

Returns a subset of the elements in the array that match the provided selector.

### `a.is(selector)`

Returns whether at least one of the elements in the array match the provided selector.

### `a.html(value?)`

If a `value` is provided then every element in the `Dominus` collection gets assigned that HTML `value`, then `a` is returned for chaining. If you don't provide a `value`, you get the HTML contents of the first node in the `Dominus` collection back.

### `a.text(value?)`

If a `value` is provided then every element in the `Dominus` collection gets assigned that plain text `value`, then `a` is returned for chaining. If you don't provide a `value`, you get the plain text contents of the first node in the `Dominus` collection back. In the case of elements that can be `checked`, the native `value` property is used instead.

### `a.value(value?)`

If a `value` is provided then every element in the `Dominus` collection gets assigned that input `value`, then `a` is returned for chaining. If you don't provide a `value`, you get the input value of the first node in the `Dominus` collection back. In the case of elements that can be `checked`, the native `checked` property is used instead.

### `a.attr(name, value?)`

If a `value` is provided then every element in the `Dominus` collection gets assigned the attribute property `value`. If a `value` isn't provided then the current attribute value is returned. If the property can be accessed via programatic API that's preferred. For instance, using `a.attr('value', 'dog')` is the same as using `a.value('dog')` for text inputs.

### `a.on(type, fn)`

Attaches the event handler `fn` for events of type `type` on every element in the `Dominus` collection. You can also pass in a list of event types, such as `click dragstart`, and both events would get an event listener.

# License

MIT

[1]: http://sizzlejs.com/ "Sizzle.js Selector Engine"
[2]: https://developer.mozilla.org/en/docs/Web/API/HTMLElement
[3]: https://github.com/bevacqua/poser
