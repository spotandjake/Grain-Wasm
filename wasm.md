---
title: Wasm
---

## Types

Type declarations included in the Wasm module.

### Wasm.**WasmParseError**

```grain
enum WasmParseError {
  UnexpectedWasmToken(String),
  InvalidWasmType(Int16),
  InvalidImportDescType(Int16),
  InvalidWasmLimitType(Int16),
  InvalidWasmGlobal,
  InvalidExportDescription(Int16),
  InvalidWasmInstr(Int16),
  UnexpectedEndOfInput,
}
```

### Wasm.**RawSections**

```grain
enum RawSections {
  RawCustomSection(Bytes),
  RawTypeSection(Bytes),
  RawImportSection(Bytes),
  RawFunctionSection(Bytes),
  RawTableSection(Bytes),
  RawMemorySection(Bytes),
  RawGlobalSection(Bytes),
  RawExportSection(Bytes),
  RawStartSection(Bytes),
  RawElementSection(Bytes),
  RawDataCountSection(Bytes),
  RawCodeSection(Bytes),
  RawDataSection(Bytes),
}
```

### Wasm.**WasmExportDesc**

```grain
enum WasmExportDesc {
  FuncExport(Number),
  TableExport(Number),
  MemoryExport(Number),
  GlobalExport(Number),
}
```

### Wasm.**WasmType**

```grain
enum WasmType {
  WasmFuncType(List<WasmType>, List<WasmType>),
  WasmI32,
  WasmI64,
  WasmF32,
  WasmF64,
  WasmV128,
  WasmFuncRef,
  WasmExternRef,
  EmptyType,
  TypeIdx(Number),
}
```

### Wasm.**WasmInstr**

```grain
enum WasmInstr {
  WasmInstrUnreachable,
  WasmInstrNop,
  WasmInstrBlock(WasmType, List<WasmInstr>),
  WasmInstrLoop(WasmType, List<WasmInstr>),
  WasmInstrIf(WasmType, List<WasmInstr>),
  WasmInstrIfElse(WasmType, List<WasmInstr>, List<WasmInstr>),
  WasmInstrBr(Number),
  WasmInstrBrIf(Number),
  WasmInstrBrTable(List<Number>, Number),
  WasmInstrReturn,
  WasmInstrCall(Number),
  WasmInstrCallIndirect(Number, Number),
  WasmInstrReturnCall(Number),
  WasmInstrReturnCallIndirect(Number, Number),
  WasmInstrRefNull(WasmType),
  WasmInstrRefIsNUll,
  WasmInstrRefFunc(Number),
  WasmInstrDrop,
  WasmInstrSelect(Option<List<WasmType>>),
  WasmInstrLocalGet(Number),
  WasmInstrLocalSet(Number),
  WasmInstrLocalTee(Number),
  WasmInstrGlobalGet(Number),
  WasmInstrGlobalSet(Number),
  WasmInstrTableGet(Number),
  WasmInstrTableSet(Number),
  WasmInstrTableInit(Number, Number),
  WasmInstrElemDrop(Number),
  WasmInstrTableCopy(Number, Number),
  WasmInstrTableGrow(Number),
  WasmInstrTableSize(Number),
  WasmInstrTableFill(Number),
  WasmInstrI32Load{
    align: Number,
    offset: Number,
  },
  WasmInstrI64Load{
    align: Number,
    offset: Number,
  },
  WasmInstrF32Load{
    align: Number,
    offset: Number,
  },
  WasmInstrF64Load{
    align: Number,
    offset: Number,
  },
  WasmInstrI32Load8S{
    align: Number,
    offset: Number,
  },
  WasmInstrI32Load8U{
    align: Number,
    offset: Number,
  },
  WasmInstrI32Load16S{
    align: Number,
    offset: Number,
  },
  WasmInstrI32Load16U{
    align: Number,
    offset: Number,
  },
  WasmInstrI64Load8S{
    align: Number,
    offset: Number,
  },
  WasmInstrI64Load8U{
    align: Number,
    offset: Number,
  },
  WasmInstrI64Load16S{
    align: Number,
    offset: Number,
  },
  WasmInstrI64Load16U{
    align: Number,
    offset: Number,
  },
  WasmInstrI64Load32S{
    align: Number,
    offset: Number,
  },
  WasmInstrI64Load32U{
    align: Number,
    offset: Number,
  },
  WasmInstrI32Store{
    align: Number,
    offset: Number,
  },
  WasmInstrI64Store{
    align: Number,
    offset: Number,
  },
  WasmInstrF32Store{
    align: Number,
    offset: Number,
  },
  WasmInstrF64Store{
    align: Number,
    offset: Number,
  },
  WasmInstrI32Store8{
    align: Number,
    offset: Number,
  },
  WasmInstrI32Store16{
    align: Number,
    offset: Number,
  },
  WasmInstrI64Store8{
    align: Number,
    offset: Number,
  },
  WasmInstrI64Store16{
    align: Number,
    offset: Number,
  },
  WasmInstrI64Store32{
    align: Number,
    offset: Number,
  },
  WasmInstrMemorySize,
  WasmInstrMemoryGrow,
  WasmInstrMemoryInit(Number),
  WasmInstrDataDrop(Number),
  WasmInstrMemoryCopy,
  WasmInstrMemoryFill,
  WasmInstrI32Const(Number),
  WasmInstrI64Const(Number),
  WasmInstrF32Const(Number),
  WasmInstrF64Const(Number),
  WasmInstrI32Eqz,
  WasmInstrI32Eq,
  WasmInstrI32Ne,
  WasmInstrI32LtS,
  WasmInstrI32LtU,
  WasmInstrI32GtS,
  WasmInstrI32GtU,
  WasmInstrI32LeS,
  WasmInstrI32LeU,
  WasmInstrI32GeS,
  WasmInstrI32GeU,
  WasmInstrI64Eqz,
  WasmInstrI64Eq,
  WasmInstrI64Ne,
  WasmInstrI64LtS,
  WasmInstrI64LtU,
  WasmInstrI64GtS,
  WasmInstrI64GtU,
  WasmInstrI64LeS,
  WasmInstrI64LeU,
  WasmInstrI64GeS,
  WasmInstrI64GeU,
  WasmInstrF32Eq,
  WasmInstrF32Ne,
  WasmInstrF32Lt,
  WasmInstrF32Gt,
  WasmInstrF32Le,
  WasmInstrF32Ge,
  WasmInstrF64Eq,
  WasmInstrF64Ne,
  WasmInstrF64Lt,
  WasmInstrF64Gt,
  WasmInstrF64Le,
  WasmInstrF64Ge,
  WasmInstrI32Clz,
  WasmInstrI32Ctz,
  WasmInstrI32Popcnt,
  WasmInstrI32Add,
  WasmInstrI32Sub,
  WasmInstrI32Mul,
  WasmInstrI32DivS,
  WasmInstrI32DivU,
  WasmInstrI32RemS,
  WasmInstrI32RemU,
  WasmInstrI32And,
  WasmInstrI32Or,
  WasmInstrI32Xor,
  WasmInstrI32Shl,
  WasmInstrI32ShrS,
  WasmInstrI32ShrU,
  WasmInstrI32Rotl,
  WasmInstrI32Rotr,
  WasmInstrI64Clz,
  WasmInstrI64Ctz,
  WasmInstrI64Popcnt,
  WasmInstrI64Add,
  WasmInstrI64Sub,
  WasmInstrI64Mul,
  WasmInstrI64DivS,
  WasmInstrI64DivU,
  WasmInstrI64RemS,
  WasmInstrI64RemU,
  WasmInstrI64And,
  WasmInstrI64Or,
  WasmInstrI64Xor,
  WasmInstrI64Shl,
  WasmInstrI64ShrS,
  WasmInstrI64ShrU,
  WasmInstrI64Rotl,
  WasmInstrI64Rotr,
  WasmInstrF32Abs,
  WasmInstrF32Neg,
  WasmInstrF32Ceil,
  WasmInstrF32Floor,
  WasmInstrF32Trunc,
  WasmInstrF32Nearest,
  WasmInstrF32Sqrt,
  WasmInstrF32Add,
  WasmInstrF32Sub,
  WasmInstrF32Mul,
  WasmInstrF32Div,
  WasmInstrF32Min,
  WasmInstrF32Max,
  WasmInstrF32CopySign,
  WasmInstrF64Abs,
  WasmInstrF64Neg,
  WasmInstrF64Ceil,
  WasmInstrF64Floor,
  WasmInstrF64Trunc,
  WasmInstrF64Nearest,
  WasmInstrF64Sqrt,
  WasmInstrF64Add,
  WasmInstrF64Sub,
  WasmInstrF64Mul,
  WasmInstrF64Div,
  WasmInstrF64Min,
  WasmInstrF64Max,
  WasmInstrF64CopySign,
  WasmInstrI32WrapI64,
  WasmInstrI32TruncF32S,
  WasmInstrI32TruncF32U,
  WasmInstrI32TruncF64S,
  WasmInstrI32TruncF64U,
  WasmInstrI64ExtendI32S,
  WasmInstrI64ExtendI32U,
  WasmInstrI64TruncF32S,
  WasmInstrI64TruncF32U,
  WasmInstrI64TruncF64S,
  WasmInstrI64TruncF64U,
  WasmInstrF32ConvertI32S,
  WasmInstrF32ConvertI32U,
  WasmInstrF32ConvertI64S,
  WasmInstrF32ConvertI64U,
  WasmInstrF32DemoteF64,
  WasmInstrF64ConvertI32S,
  WasmInstrF64ConvertI32U,
  WasmInstrF64ConvertI64S,
  WasmInstrF64ConvertI64U,
  WasmInstrF64PromoteF32,
  WasmInstrI32ReinterpretF32,
  WasmInstrI64ReinterpretF64,
  WasmInstrF32ReinterpretI32,
  WasmInstrF64ReinterpretI64,
  WasmInstrI32Extend8S,
  WasmInstrI32Extend16S,
  WasmInstrI64Extend8S,
  WasmInstrI64Extend16S,
  WasmInstrI64Extend32S,
  WasmInstrI32TruncSatF32S,
  WasmInstrI32TruncSatF32U,
  WasmInstrI32TruncSatF64S,
  WasmInstrI32TruncSatF64U,
  WasmInstrI64TruncSatF32S,
  WasmInstrI64TruncSatF32U,
  WasmInstrI64TruncSatF64S,
  WasmInstrI64TruncSatF64U,
  WasmInstrElse,
  WasmInstrEnd,
}
```

### Wasm.**WasmTableType**

```grain
record WasmTableType {
  wasmType: WasmType,
  minLimit: Number,
  maxLimit: Option<Number>,
}
```

### Wasm.**WasmGlobalType**

```grain
record WasmGlobalType {
  wasmType: WasmType,
  isMutable: Bool,
}
```

### Wasm.**WasmExportType**

```grain
record WasmExportType {
  name: String,
  exportDesc: WasmExportDesc,
}
```

### Wasm.**WasmLocalType**

```grain
record WasmLocalType {
  wasmType: WasmType,
  count: Number,
}
```

### Wasm.**WasmFunctionType**

```grain
record WasmFunctionType {
  locals: List<WasmLocalType>,
  body: List<WasmInstr>,
}
```

### Wasm.**WasmImportDesc**

```grain
enum WasmImportDesc {
  WasmFuncImportDesc(Number),
  WasmTableImportDesc(WasmTableType),
  WasmMemoryImportDesc(Number, Option<Number>),
  WasmGlobalImportDesc(WasmGlobalType),
}
```

### Wasm.**WasmImport**

```grain
record WasmImport {
  importModName: String,
  importName: String,
  importDesc: WasmImportDesc,
}
```

### Wasm.**Sections**

```grain
enum Sections {
  CustomSection(Bytes),
  TypeSection(List<WasmType>),
  ImportSection(List<WasmImport>),
  FunctionSection(List<Number>),
  TableSection(List<WasmTableType>),
  MemorySection(List<(Number, Option<Number>)>),
  GlobalSection(List<(WasmGlobalType, List<WasmInstr>)>),
  ExportSection(List<WasmExportType>),
  StartSection(Number),
  ElementSection(Void),
  DataCountSection(Number),
  CodeSection(List<WasmFunctionType>),
  DataSection(Void),
}
```

## Wasm.Parser

### Values

Functions and constants included in the Wasm.Parser module.

#### Wasm.Parser.**parseModule**

```grain
parseModule : (rawBytes: Bytes) -> Result<List<RawSections>, WasmParseError>
```

#### Wasm.Parser.**parseSection**

```grain
parseSection : (section: RawSections) -> Result<Sections, WasmParseError>
```

