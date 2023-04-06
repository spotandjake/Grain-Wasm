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

Represents errors for Wasm parsing.

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

Represents raw unparsed wasm sections.

### Wasm.**WasmExportDesc**

```grain
enum WasmExportDesc {
  FuncExport(Number),
  TableExport(Number),
  MemoryExport(Number),
  GlobalExport(Number),
}
```

Represents wasm export descriptions

### Wasm.**WasmMemoryArg**

```grain
record WasmMemoryArg {
  align: Number,
  offset: Number,
}
```

Represents wasm memory argument

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

Represents wasm primitive types.

### Wasm.**WasmInstr**

```grain
enum WasmInstr {
  WasmInstr_Unreachable,
  WasmInstr_Nop,
  WasmInstr_Block(WasmType, Expression),
  WasmInstr_Loop(WasmType, Expression),
  WasmInstr_If(WasmType, Expression),
  WasmInstr_If_Else(WasmType, Expression, Expression),
  WasmInstr_Br(Number),
  WasmInstr_Br_If(Number),
  WasmInstr_Br_Table(List<Number>, Number),
  WasmInstr_Return,
  WasmInstr_Call(Number),
  WasmInstr_Call_Indirect(Number, Number),
  WasmInstr_Return_Call(Number),
  WasmInstr_Return_Call_Indirect(Number, Number),
  WasmInstr_Ref_Null(WasmType),
  WasmInstr_Ref_Is_Null,
  WasmInstr_Ref_Func(Number),
  WasmInstr_Drop,
  WasmInstr_Select(Option<List<WasmType>>),
  WasmInstr_Local_Get(Number),
  WasmInstr_Local_Set(Number),
  WasmInstr_Local_Tee(Number),
  WasmInstr_Global_Get(Number),
  WasmInstr_Global_Set(Number),
  WasmInstr_Table_Get(Number),
  WasmInstr_Table_Set(Number),
  WasmInstr_Table_Init(Number, Number),
  WasmInstr_Elem_Drop(Number),
  WasmInstr_Table_Copy(Number, Number),
  WasmInstr_Table_Grow(Number),
  WasmInstr_Table_Size(Number),
  WasmInstr_Table_Fill(Number),
  WasmInstr_I32_Load(WasmMemoryArg),
  WasmInstr_I64_Load(WasmMemoryArg),
  WasmInstr_F32_Load(WasmMemoryArg),
  WasmInstr_F64_Load(WasmMemoryArg),
  WasmInstr_I32_Load8_S(WasmMemoryArg),
  WasmInstr_I32_Load8_U(WasmMemoryArg),
  WasmInstr_I32_Load16_S(WasmMemoryArg),
  WasmInstr_I32_Load16_U(WasmMemoryArg),
  WasmInstr_I64_Load8_S(WasmMemoryArg),
  WasmInstr_I64_Load8_U(WasmMemoryArg),
  WasmInstr_I64_Load16_S(WasmMemoryArg),
  WasmInstr_I64_Load16_U(WasmMemoryArg),
  WasmInstr_I64_Load32_S(WasmMemoryArg),
  WasmInstr_I64_Load32_U(WasmMemoryArg),
  WasmInstr_I32_Store(WasmMemoryArg),
  WasmInstr_I64_Store(WasmMemoryArg),
  WasmInstr_F32_Store(WasmMemoryArg),
  WasmInstr_F64_Store(WasmMemoryArg),
  WasmInstr_I32_Store8(WasmMemoryArg),
  WasmInstr_I32_Store16(WasmMemoryArg),
  WasmInstr_I64_Store8(WasmMemoryArg),
  WasmInstr_I64_Store16(WasmMemoryArg),
  WasmInstr_I64_Store32(WasmMemoryArg),
  WasmInstr_Memory_Size,
  WasmInstr_Memory_Grow,
  WasmInstr_Memory_Init(Number),
  WasmInstr_Data_Drop(Number),
  WasmInstr_Memory_Copy,
  WasmInstr_Memory_Fill,
  WasmInstr_I32_Const(Number),
  WasmInstr_I64_Const(Number),
  WasmInstr_F32_Const(Number),
  WasmInstr_F64_Const(Number),
  WasmInstr_I32_Eqz,
  WasmInstr_I32_Eq,
  WasmInstr_I32_Ne,
  WasmInstr_I32_Lt_S,
  WasmInstr_I32_Lt_U,
  WasmInstr_I32_Gt_S,
  WasmInstr_I32_Gt_U,
  WasmInstr_I32_Le_S,
  WasmInstr_I32_Le_U,
  WasmInstr_I32_Ge_S,
  WasmInstr_I32_Ge_U,
  WasmInstr_I64_Eqz,
  WasmInstr_I64_Eq,
  WasmInstr_I64_Ne,
  WasmInstr_I64_Lt_S,
  WasmInstr_I64_Lt_U,
  WasmInstr_I64_Gt_S,
  WasmInstr_I64_Gt_U,
  WasmInstr_I64_Le_S,
  WasmInstr_I64_Le_U,
  WasmInstr_I64_Ge_S,
  WasmInstr_I64_Ge_U,
  WasmInstr_F32_Eq,
  WasmInstr_F32_Ne,
  WasmInstr_F32_Lt,
  WasmInstr_F32_Gt,
  WasmInstr_F32_Le,
  WasmInstr_F32_Ge,
  WasmInstr_F64_Eq,
  WasmInstr_F64_Ne,
  WasmInstr_F64_Lt,
  WasmInstr_F64_Gt,
  WasmInstr_F64_Le,
  WasmInstr_F64_Ge,
  WasmInstr_I32_Clz,
  WasmInstr_I32_Ctz,
  WasmInstr_I32_Popcnt,
  WasmInstr_I32_Add,
  WasmInstr_I32_Sub,
  WasmInstr_I32_Mul,
  WasmInstr_I32_Div_S,
  WasmInstr_I32_Div_U,
  WasmInstr_I32_Rem_S,
  WasmInstr_I32_Rem_U,
  WasmInstr_I32_And,
  WasmInstr_I32_Or,
  WasmInstr_I32_Xor,
  WasmInstr_I32_Shl,
  WasmInstr_I32_Shr_S,
  WasmInstr_I32_Shr_U,
  WasmInstr_I32_Rotl,
  WasmInstr_I32_Rotr,
  WasmInstr_I64_Clz,
  WasmInstr_I64_Ctz,
  WasmInstr_I64_Popcnt,
  WasmInstr_I64_Add,
  WasmInstr_I64_Sub,
  WasmInstr_I64_Mul,
  WasmInstr_I64_Div_S,
  WasmInstr_I64_Div_U,
  WasmInstr_I64_Rem_S,
  WasmInstr_I64_Rem_U,
  WasmInstr_I64_And,
  WasmInstr_I64_Or,
  WasmInstr_I64_Xor,
  WasmInstr_I64_Shl,
  WasmInstr_I64_Shr_S,
  WasmInstr_I64_Shr_U,
  WasmInstr_I64_Rotl,
  WasmInstr_I64_Rotr,
  WasmInstr_F32_Abs,
  WasmInstr_F32_Neg,
  WasmInstr_F32_Ceil,
  WasmInstr_F32_Floor,
  WasmInstr_F32_Trunc,
  WasmInstr_F32_Nearest,
  WasmInstr_F32_Sqrt,
  WasmInstr_F32_Add,
  WasmInstr_F32_Sub,
  WasmInstr_F32_Mul,
  WasmInstr_F32_Div,
  WasmInstr_F32_Min,
  WasmInstr_F32_Max,
  WasmInstr_F32_CopySign,
  WasmInstr_F64_Abs,
  WasmInstr_F64_Neg,
  WasmInstr_F64_Ceil,
  WasmInstr_F64_Floor,
  WasmInstr_F64_Trunc,
  WasmInstr_F64_Nearest,
  WasmInstr_F64_Sqrt,
  WasmInstr_F64_Add,
  WasmInstr_F64_Sub,
  WasmInstr_F64_Mul,
  WasmInstr_F64_Div,
  WasmInstr_F64_Min,
  WasmInstr_F64_Max,
  WasmInstr_F64_CopySign,
  WasmInstr_I32_Wrap_I64,
  WasmInstr_I32_Trunc_F32_S,
  WasmInstr_I32_Trunc_F32_U,
  WasmInstr_I32_Trunc_F64_S,
  WasmInstr_I32_Trunc_F64_U,
  WasmInstr_I64_Extend_I32_S,
  WasmInstr_I64_Extend_I32_U,
  WasmInstr_I64_Trunc_F32_S,
  WasmInstr_I64_Trunc_F32_U,
  WasmInstr_I64_Trunc_F64_S,
  WasmInstr_I64_Trunc_F64_U,
  WasmInstr_F32_Convert_I32_S,
  WasmInstr_F32_Convert_I32_U,
  WasmInstr_F32_Convert_I64_S,
  WasmInstr_F32_Convert_I64_U,
  WasmInstr_F32_Demote_F64,
  WasmInstr_F64_Convert_I32_S,
  WasmInstr_F64_Convert_I32_U,
  WasmInstr_F64_Convert_I64_S,
  WasmInstr_F64_Convert_I64_U,
  WasmInstr_F64_Promote_F32,
  WasmInstr_I32_Reinterpret_F32,
  WasmInstr_I64_Reinterpret_F64,
  WasmInstr_F32_Reinterpret_I32,
  WasmInstr_F64_Reinterpret_I64,
  WasmInstr_I32_Extend8_S,
  WasmInstr_I32_Extend16_S,
  WasmInstr_I64_Extend8_S,
  WasmInstr_I64_Extend16_S,
  WasmInstr_I64_Extend32_S,
  WasmInstr_I32_TruncSat_F32_S,
  WasmInstr_I32_TruncSat_F32_U,
  WasmInstr_I32_TruncSat_F64_S,
  WasmInstr_I32_TruncSat_F64_U,
  WasmInstr_I64_TruncSat_F32_S,
  WasmInstr_I64_TruncSat_F32_U,
  WasmInstr_I64_TruncSat_F64_S,
  WasmInstr_I64_TruncSat_F64_U,
  WasmInstr_V128_Load(WasmMemoryArg),
  WasmInstr_V128_8x8_Load_S(WasmMemoryArg),
  WasmInstr_V128_8x8_Load_U(WasmMemoryArg),
  WasmInstr_V128_16x4_Load_S(WasmMemoryArg),
  WasmInstr_V128_16x4_Load_U(WasmMemoryArg),
  WasmInstr_V128_32x2_Load_S(WasmMemoryArg),
  WasmInstr_V128_32x2_Load_U(WasmMemoryArg),
  WasmInstr_V128_Load_8_Splat(WasmMemoryArg),
  WasmInstr_V128_Load_16_Splat(WasmMemoryArg),
  WasmInstr_V128_Load_32_Splat(WasmMemoryArg),
  WasmInstr_V128_Load_64_Splat(WasmMemoryArg),
  WasmInstr_Load_32_Zero(WasmMemoryArg),
  WasmInstr_Load_64_Zero(WasmMemoryArg),
  WasmInstr_V128_Store(WasmMemoryArg),
  WasmInstr_V128_Load8_Lane(WasmMemoryArg, Number),
  WasmInstr_V128_Load16_Lane(WasmMemoryArg, Number),
  WasmInstr_V128_Load32_Lane(WasmMemoryArg, Number),
  WasmInstr_V128_Load64_Lane(WasmMemoryArg, Number),
  WasmInstr_V128_Store8_Lane(WasmMemoryArg, Number),
  WasmInstr_V128_Store16_Lane(WasmMemoryArg, Number),
  WasmInstr_V128_Store32_Lane(WasmMemoryArg, Number),
  WasmInstr_V128_Store64_Lane(WasmMemoryArg, Number),
  WasmInstr_V128_Const(Number),
  WasmInstr_I8x16_Shuffle(Number),
  WasmInstr_I8x16_Extract_Lane_S(Number),
  WasmInstr_I8x16_Extract_Lane_U(Number),
  WasmInstr_I8x16_Replace_Lane(Number),
  WasmInstr_I16x8_Extract_Lane_S(Number),
  WasmInstr_I16x8_Extract_Lane_U(Number),
  WasmInstr_I16x8_Replace_Lane(Number),
  WasmInstr_I32x4_Extract_Lane(Number),
  WasmInstr_I32x4_Replace_Lane(Number),
  WasmInstr_I64x2_Extract_Lane(Number),
  WasmInstr_I64x2_Replace_Lane(Number),
  WasmInstr_F32x4_Extract_Lane(Number),
  WasmInstr_F32x4_Replace_Lane(Number),
  WasmInstr_F64x2_Extract_Lane(Number),
  WasmInstr_F64x2_Replace_Lane(Number),
  WasmInstr_I8x16_Swizzle,
  WasmInstr_I8x16_Splat,
  WasmInstr_I16x8_Splat,
  WasmInstr_I32x4_Splat,
  WasmInstr_I64x2_Splat,
  WasmInstr_F32x4_Splat,
  WasmInstr_F64x2_Splat,
  WasmInstr_I8x16_Eq,
  WasmInstr_I8x16_Ne,
  WasmInstr_I8x16_Lt_S,
  WasmInstr_I8x16_Lt_U,
  WasmInstr_I8x16_Gt_S,
  WasmInstr_I8x16_Gt_U,
  WasmInstr_I8x16_Le_S,
  WasmInstr_I8x16_Le_U,
  WasmInstr_I8x16_Ge_S,
  WasmInstr_I8x16_Ge_U,
  WasmInstr_I16x8_Eq,
  WasmInstr_I16x8_Ne,
  WasmInstr_I16x8_Lt_S,
  WasmInstr_I16x8_Lt_U,
  WasmInstr_I16x8_Gt_S,
  WasmInstr_I16x8_Gt_U,
  WasmInstr_I16x8_Le_S,
  WasmInstr_I16x8_Le_U,
  WasmInstr_I16x8_Ge_S,
  WasmInstr_I16x8_Ge_U,
  WasmInstr_I32x4_Eq,
  WasmInstr_I32x4_Ne,
  WasmInstr_I32x4_Lt_S,
  WasmInstr_I32x4_Lt_U,
  WasmInstr_I32x4_Gt_S,
  WasmInstr_I32x4_Gt_U,
  WasmInstr_I32x4_Le_S,
  WasmInstr_I32x4_Le_U,
  WasmInstr_I32x4_Ge_S,
  WasmInstr_I32x4_Ge_U,
  WasmInstr_I64x2_Eq,
  WasmInstr_I64x2_Ne,
  WasmInstr_I64x2_Lt_S,
  WasmInstr_I64x2_Gt_S,
  WasmInstr_I64x2_Le_S,
  WasmInstr_I64x2_Ge_S,
  WasmInstr_F32x4_Eq,
  WasmInstr_F32x4_Ne,
  WasmInstr_F32x4_Lt,
  WasmInstr_F32x4_Gt,
  WasmInstr_F32x4_Le,
  WasmInstr_F32x4_Ge,
  WasmInstr_F64x2_Eq,
  WasmInstr_F64x2_Ne,
  WasmInstr_F64x2_Lt,
  WasmInstr_F64x2_Gt,
  WasmInstr_F64x2_Le,
  WasmInstr_F64x2_Ge,
  WasmInstr_V128_Not,
  WasmInstr_V128_And,
  WasmInstr_V128_And_Not,
  WasmInstr_V128_Or,
  WasmInstr_V128_Xor,
  WasmInstr_V128_Bitselect,
  WasmInstr_V128_Any_True,
  WasmInstr_I8x16_Abs,
  WasmInstr_I8x16_Neg,
  WasmInstr_I8x16_Popcnt,
  WasmInstr_I8x16_All_True,
  WasmInstr_I8x16_Bitmask,
  WasmInstr_I8x16_Narrow_I16x8_S,
  WasmInstr_I8x16_Narrow_I16x8_U,
  WasmInstr_I8x16_Shl,
  WasmInstr_I8x16_Shr_S,
  WasmInstr_I8x16_Shr_U,
  WasmInstr_I8x16_Add,
  WasmInstr_I8x16_Add_Sat_S,
  WasmInstr_I8x16_Add_Sat_U,
  WasmInstr_I8x16_Sub,
  WasmInstr_I8x16_Sub_Sat_S,
  WasmInstr_I8x16_Sub_Sat_U,
  WasmInstr_I8x16_Min_S,
  WasmInstr_I8x16_Min_U,
  WasmInstr_I8x16_Max_S,
  WasmInstr_I8x16_Max_U,
  WasmInstr_I8x16_Avgr_U,
  WasmInstr_I16x8_ExtAdd_Pairwise_I8x16_S,
  WasmInstr_I16x8_ExtAdd_Pairwise_I8x16_U,
  WasmInstr_I16x8_Abs,
  WasmInstr_I16x8_Neg,
  WasmInstr_I16x8_q15mulr_sat_s,
  WasmInstr_I16x8_All_True,
  WasmInstr_I16x8_Bitmask,
  WasmInstr_I16x8_Narrow_I32x4_S,
  WasmInstr_I16x8_Narrow_I32x4_U,
  WasmInstr_I16x8_Extend_Low_I8x16_S,
  WasmInstr_I16x8_Extend_High_I8x16_S,
  WasmInstr_I16x8_Extend_Low_I8x16_U,
  WasmInstr_I16x8_Extend_High_I8x16_U,
  WasmInstr_I16x8_Shl,
  WasmInstr_I16x8_Shr_S,
  WasmInstr_I16x8_Shr_U,
  WasmInstr_I16x8_Add,
  WasmInstr_I16x8_Add_Sat_S,
  WasmInstr_I16x8_Add_Sat_U,
  WasmInstr_I16x8_Sub,
  WasmInstr_I16x8_Sub_Sat_S,
  WasmInstr_I16x8_Sub_Sat_U,
  WasmInstr_I16x8_Mul,
  WasmInstr_I16x8_Min_S,
  WasmInstr_I16x8_Min_U,
  WasmInstr_I16x8_Max_S,
  WasmInstr_I16x8_Max_U,
  WasmInstr_I16x8_Avgr_U,
  WasmInstr_I16x8_ExtMulLow_I8x16_S,
  WasmInstr_I16x8_ExtMulHigh_I8x16_S,
  WasmInstr_I16x8_ExtMulLow_I8x16_U,
  WasmInstr_I16x8_ExtMulHigh_I8x16_U,
  WasmInstr_I32x4_ExtAdd_Pairwise_I16x8_S,
  WasmInstr_I32x4_ExtAdd_Pairwise_I16x8_U,
  WasmInstr_I32x4_Abs,
  WasmInstr_I32x4_Neg,
  WasmInstr_I32x4_All_True,
  WasmInstr_I32x4_Bitmask,
  WasmInstr_I32x4_Extend_Low_I16x8_S,
  WasmInstr_I32x4_Extend_High_I16x8_S,
  WasmInstr_I32x4_Extend_Low_I16x8_U,
  WasmInstr_I32x4_Extend_High_I16x8_U,
  WasmInstr_I32x4_Shl,
  WasmInstr_I32x4_Shr_S,
  WasmInstr_I32x4_Shr_U,
  WasmInstr_I32x4_Add,
  WasmInstr_I32x4_Sub,
  WasmInstr_I32x4_Mul,
  WasmInstr_I32x4_Min_S,
  WasmInstr_I32x4_Min_U,
  WasmInstr_I32x4_Max_S,
  WasmInstr_I32x4_Max_U,
  WasmInstr_I32x4_Dot_I16x8_S,
  WasmInstr_I32x4_ExtMulLow_I16x8_S,
  WasmInstr_I32x4_ExtMulHigh_I16x8_S,
  WasmInstr_I32x4_ExtMulLow_I16x8_U,
  WasmInstr_I32x4_ExtMulHigh_I16x8_U,
  WasmInstr_I64x2_Abs,
  WasmInstr_I64x2_Neg,
  WasmInstr_I64x2_All_True,
  WasmInstr_I64x2_Bitmask,
  WasmInstr_I64x2_Extend_Low_I32x4_S,
  WasmInstr_I64x2_Extend_High_I32x4_S,
  WasmInstr_I64x2_Extend_Low_I32x4_U,
  WasmInstr_I64x2_Extend_High_I32x4_U,
  WasmInstr_I64x2_Shl,
  WasmInstr_I64x2_Shr_S,
  WasmInstr_I64x2_Shr_U,
  WasmInstr_I64x2_Add,
  WasmInstr_I64x2_Sub,
  WasmInstr_I64x2_Mul,
  WasmInstr_I64x2_ExtMulLow_I32x4_S,
  WasmInstr_I64x2_ExtMulHigh_I32x4_S,
  WasmInstr_I64x2_ExtMulLow_I32x4_U,
  WasmInstr_I64x2_ExtMulHigh_I32x4_U,
  WasmInstr_F32x4_Ceil,
  WasmInstr_F32x4_Floor,
  WasmInstr_F32x4_Trunc,
  WasmInstr_F32x4_Nearest,
  WasmInstr_F32x4_Abs,
  WasmInstr_F32x4_Neg,
  WasmInstr_F32x4_Sqrt,
  WasmInstr_F32x4_Add,
  WasmInstr_F32x4_Sub,
  WasmInstr_F32x4_Mul,
  WasmInstr_F32x4_Div,
  WasmInstr_F32x4_Min,
  WasmInstr_F32x4_Max,
  WasmInstr_F32x4_Pmin,
  WasmInstr_F32x4_Pmax,
  WasmInstr_F64x2_Ceil,
  WasmInstr_F64x2_Floor,
  WasmInstr_F64x2_Trunc,
  WasmInstr_F64x2_Nearest,
  WasmInstr_F64x2_Abs,
  WasmInstr_F64x2_Neg,
  WasmInstr_F64x2_Sqrt,
  WasmInstr_F64x2_Add,
  WasmInstr_F64x2_Sub,
  WasmInstr_F64x2_Mul,
  WasmInstr_F64x2_Div,
  WasmInstr_F64x2_Min,
  WasmInstr_F64x2_Max,
  WasmInstr_F64x2_Pmin,
  WasmInstr_F64x2_Pmax,
  WasmInstr_I32x4_Trunc_Sat_F32x4_S,
  WasmInstr_I32x4_Trunc_Sat_F32x4_U,
  WasmInstr_F32x4_Convert_I32x4_S,
  WasmInstr_F32x4_Convert_I32x4_U,
  WasmInstr_I32x4_Trunc_Sat_F64x2_S_Zero,
  WasmInstr_I32x4_Trunc_Sat_F64x2_U_Zero,
  WasmInstr_F64x2_ConvertLow_I32x4_S,
  WasmInstr_F64x2_ConvertLow_I32x4_U,
  WasmInstr_F32x4_Demote_F64x2_Zero,
  WasmInstr_F64x2_PromoteLow_F32x4,
  Wasm_Instr_Else,
  Wasm_Instr_End,
}
```

Represents wasm instructions and corresponding data.

### Wasm.**Expression**

```grain
type Expression = List<WasmInstr>
```

Represents a wasm expression

### Wasm.**WasmTableType**

```grain
record WasmTableType {
  wasmType: WasmType,
  minLimit: Number,
  maxLimit: Option<Number>,
}
```

Represents a wasm table.

### Wasm.**WasmGlobalType**

```grain
record WasmGlobalType {
  wasmType: WasmType,
  isMutable: Bool,
}
```

Represents a wasm global.

### Wasm.**WasmExportType**

```grain
record WasmExportType {
  name: String,
  exportDesc: WasmExportDesc,
}
```

Represents a wasm export.

### Wasm.**WasmLocalType**

```grain
record WasmLocalType {
  wasmType: WasmType,
  count: Number,
}
```

Represents a wasm local.

### Wasm.**WasmFunctionType**

```grain
record WasmFunctionType {
  locals: List<WasmLocalType>,
  body: Expression,
}
```

Represents a wasm function.

### Wasm.**WasmElemMode**

```grain
enum WasmElemMode {
  ElemPassive,
  ElemActive{
    tableIdx: Number,
    offset: Expression,
  },
  ElemDeclarative,
}
```

Represents a wasm elements mode.

### Wasm.**WasmElementSegment**

```grain
record WasmElementSegment {
  wasmType: WasmType,
  contents: List<Expression>,
  elemMode: WasmElemMode,
}
```

Represents a wasm element segment.

### Wasm.**WasmDataSegment**

```grain
enum WasmDataSegment {
  DataActive{
    memIdx: Number,
    offset: Expression,
    content: Bytes,
  },
  DataPassive{
    content: Bytes,
  },
}
```

Represents a wasm data segment.

### Wasm.**WasmImportDesc**

```grain
enum WasmImportDesc {
  WasmFuncImportDesc(Number),
  WasmTableImportDesc(WasmTableType),
  WasmMemoryImportDesc(Number, Option<Number>),
  WasmGlobalImportDesc(WasmGlobalType),
}
```

Represents a wasm import description.

### Wasm.**WasmImport**

```grain
record WasmImport {
  importModName: String,
  importName: String,
  importDesc: WasmImportDesc,
}
```

Represents a wasm import.

### Wasm.**Sections**

```grain
enum Sections {
  CustomSection(Bytes),
  TypeSection(List<WasmType>),
  ImportSection(List<WasmImport>),
  FunctionSection(List<Number>),
  TableSection(List<WasmTableType>),
  MemorySection(List<(Number, Option<Number>)>),
  GlobalSection(List<(WasmGlobalType, Expression)>),
  ExportSection(List<WasmExportType>),
  StartSection(Number),
  ElementSection(List<WasmElementSegment>),
  DataCountSection(Number),
  CodeSection(List<WasmFunctionType>),
  DataSection(List<WasmDataSegment>),
}
```

Represents parsed wasm sections.

## Wasm.Parser

Wasm Parsing Utils.

### Values

Functions and constants included in the Wasm.Parser module.

#### Wasm.Parser.**parseModule**

```grain
parseModule : (rawBytes: Bytes) -> Result<List<RawSections>, WasmParseError>
```

Parse a wasm binary into unparsed sections.

Parameters:

|param|type|description|
|-----|----|-----------|
|`rawBytes`|`Bytes`|The wasm binary to parse|

Returns:

|type|description|
|----|-----------|
|`Result<List<RawSections>, WasmParseError>`|The unparsed sections|

#### Wasm.Parser.**parseSection**

```grain
parseSection : (section: RawSections) -> Result<Sections, WasmParseError>
```

Parse a section into a parsed wasm section.

Parameters:

|param|type|description|
|-----|----|-----------|
|`section`|`RawSections`|The unparsed section to parse|

Returns:

|type|description|
|----|-----------|
|`Result<Sections, WasmParseError>`|The parsed section|

