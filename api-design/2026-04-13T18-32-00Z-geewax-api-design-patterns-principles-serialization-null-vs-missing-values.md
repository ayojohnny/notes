# API Design Patterns | Design Principles - Serialization - Missing vs. Null Values

```js
fruit1 = { name: "apple", color: "red"  };
fruit2 = { name: "apple", color: ""     };
fruit3 = { name: "apple", color: null   };
fruit4 = { name: "apple" };
```

When considering serialization of data, it's important to consider cases when values
are `null`, missing completely (i.e. omitted JSON key), or their default value.

`fruit1`'s color is obviously `"red"`, but what about the others? Is an empty color
`""` the same as an explicit `null` color (is fruit2.color the same as fruit3.color?).
Is fruit4.color any different than fruit2 or fruit3's color since it's `color` key is
omitted?

It is important to consider these edge cases when defining public API interfaces. 
Client code serialization libraries will be wildly different for various factors such
as differnet programming ecosystems, differnet libraries w/in a given ecosystem, etc.

Never rely on the serialization library to do the **correct** thing.

