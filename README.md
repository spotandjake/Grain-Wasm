# Grain-Wasm

Grain wasm is a simple and fast wasm parser and builder written in grain-lang.

*Note*: This is a work in progress most of the work having been done in a single day, so there are likely bugs as no tests have been written for different features and I am still learning the wasm spec. If you find any bugs please open an issue.

A note on speed, the parser may seem slow at the moment this should not be the case forever, I have a few optimizations planned that should make it much faster.

Example on how to use the parsing module:
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

An odd thing you may notice about the parser is that it is implemented in two stages one stage to parse the file into section and one stage to parse the data out of each respective section this design decision was made to allow for more speed and flexibility, there are a lot of jobs such as parsing the import section that are not needed for every program the layout of the parser allows the user to skip these sections if they are not needed. While this makes the worst case slightly slower it makes the best case much faster.

## Parsing Support
Currently we support most of the wasm spec, along with the tail call spec, As we do not have tests not of this has been fully tested yet thought.
# Supported Proposals
+ [x] MVP
+ [x] Tail Call
+ [x] Bulk Memory
+ [ ] Other Proposals

## Builder Support
Building support is a work in progress but is a pretty large undertaking the builder will not handle optimizations it will just consume the ir and compile it into a wasm module.

## Other TODO's

* Look into breaking the instructions up into separate spaces 
* Generate a parser from and builder from the spec
* Add tests for all features.
* Name Section Parsing
* Build Verifier Module
* Build Optimizer Module
* Build A Searchable API, so we can support type mapping and provide a more workable interface rather than just a simple ir.

## Optimizer Planning
This section is for planning out a future optimizer module, none of this is implemented or fully researched and is just preliminary ideas.
### Ideas
#### Memory Optimizer
Would allow you to state regions in memory that are not externally visible and possibly handle some sort of constant propagation thorough them.

### Easier
* Direct Call Non Table Function Culling
* Unused Memory
* Unused Data Section *Note*: Look into if this is actually easy
* Side Effect Analysis
* 100% Dead Code Analysis
  * Stuff After Unreachable
* Unused Import Removal
* Unused Local Removal
* Unused Global Removal

### Harder
* Data Section Merging
* Unused Function With Tables
* Constant Propagation

