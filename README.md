# Slicer Kata

This is the skeleton for a `slicer` utility that lets you slice up JSON
documents on the command line. The guts have been intentionally left
un-implemented as an exercise for the reader.

Given the following JSON document:

```json
{
  "oregon": {
    "cities": ["portland", "salem", "eugene"],
    "capitol": "salem"
  },
  "california": {
    "cities": ["san francisco", "los angeles", "san jose", "sacramento"],
    "capitol": "sacramento"
  },
  "washington": {
    "cities": ["tacoma", "seattle", "olympia"],
    "capitol": "olympia"
  }
}
```

... `slicer` lets you do things like:

```
$ slicer oregon cities.json
{ "cities": ["portland", "salem", "eugene"], "capitol": "salem" }

$ slicer oregon.cities cities.json
["portland", "salem", "eugene"]

$ slicer oregon.capitol cities.json
salem

$ slicer florida.capitol
null

$ slicer 'oregon.cities[1]' cities.json
salem

$ slicer '*.cities[0]' cities.json
["portland", "san francisco", "tacoma"]
```

The executable is already built, and can be run with `bundle exec ./bin/slicer`.
The example JSON file above exists in `text/fixtures/cities.json`.

It relies on the following method on the `Slicer` module, left for you to
implement:

```ruby
def self.slice(query, tree)
  ...
end
```

`query` should be a query string as seen in the examples above, and `tree`
should be an already-parsed JSON object graph. Your task is to implement `slice`
in any way you see fit.
