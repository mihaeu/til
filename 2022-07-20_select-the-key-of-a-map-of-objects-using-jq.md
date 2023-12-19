## Select the key of a map of objects using jq

Given an object like:

```json
{
    "key1": {
        "key": "value1"
    },
    "key2": {
      "key": "value2"
    }
}
```

you can use a combination of `map_values`, `select` and `contains` to find the right object and then `keys` to get the matching keys:

```
map_values(select(contains({"key": "value2"}))) | keys[]
```

* `contains(element)`: returns `true` if whatever is passed into it matches
* `select(boolean_expression)`: returns the input or nothing if the expression doesn't match
* `map_values(x)`: runs the filter function x on all inputs

the same function can also be written using the update-assignment operator `|=`:

```
.[] |= select(contains({"key": "value2"})) | keys[]
```

`.[]` creates an iterator and `|=` assigns a new value to each element. Similarly to the previous function empty values are filtered out using the combination of `select` and `contains`.


