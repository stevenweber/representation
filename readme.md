# Render

Render improves the way you work with APIs.

* [Generate type-specific, dynamic API response data for testing](spec/integration/render/schema_spec.rb) with just a schema (JSON or Ruby)
* [Make API requests](spec/integration/render/graph_spec.rb) with a URL and a schema
* Build Graphs that [interpret data from one endpoint to call others](spec/integration/render/nested_graph_spec.rb)

## Setup

Update your Gemfile:

      gem "render"

## Usage

Check out examples as part of the [integration tests](spec/integration/render).

## Caveats/Notes/Assumptions

- Currently under initial development
- Assumes additionalProperties is always false

Render is not meant to be a validator. As such, it does not care about:

  - dependencies (attributes depending on others being present)
  - minProperties/maxProperties
  - Divergent responses, e.g. no errors will be raised if "abc" is returned for String with { "minLength": 4 }

It will however,

  - Defensively type response values based on definition

## Roadmap

- Leveraging $schema for nested schemas
- Enhance Graph to Graph relationships
- Defensive type casting
- Variable types, i.e. { type: [String, Float] }
- The following keywords:
  - anyOf/allOf/oneOf/not
  - minimum/exclusiveMinimum/maximum/exclusiveMaximum
  - multipleOf
  - pattern/patternProperties
  - uniqueItems
- Tuples of varying types, e.g. [3, { name: "bob" }]
- Relating to requests
  - Custom options, e.g. headers, timeouts
  - Drop-in custom requesting

## Contributing

* Bugs and questions welcomed. If you know (or kind of know) what's going on:
  * Write a failing test, kudos for solving it
  * Put up a [pull request](https://help.github.com/articles/using-pull-requests)
