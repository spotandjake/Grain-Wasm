# Grain-Wasm

Grain wasm is a simple and fast wasm parser and builder written in grain-lang.

*Note*: This is a work in progress most of the work having been done in a single day, so there are likely bugs as no tests have been written for different features and I am still learning the wasm spec. If you find any bugs please open an issue.

A note on speed, the parser may seem slow at the moment this should not be the case forever, I have a few optimizations planned that should make it much faster.

Example on how to use:
```
let fileContents = readFile("./test.wasm") // Read the file as bytes up to you
let parsedFile = match (Wasm.Parser.parseModule(fileContents)) {
  Ok(parsed) => parsed,
  Err(err) => fail toString(err),
}
// Parse Sections
let sections = List.map(section =>
  Wasm.Parser.parseSection(section), parsedFile)
print(sections)
```

## Design Notes

An odd thing you may notice about the parser is that it is implemented in two stages one stage to parse the file into section and one stage to parse the data out of each respective section this design decision was made to allow for more speed and flexibility, there are a lot of jobs such as parsing the import section that are not needed for every program the layout of the parser allows the user to skip these sections if they are not needed.

## Parsing Support
Currently we support most of the wasm spec, along with the tail call spec, Things left to add include but are not limited to:
- [ ] Vector Instructions

## Builder Support
Building wasm has not yet been implemented but is a planned feature.

## Other TODO's

* Document with graindoc.
* Add tests for all features.
* Name Section Parsing

