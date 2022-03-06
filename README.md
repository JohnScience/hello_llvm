# How to emit LLVM IR from Cargo

According to [the answer from Stack Overflow](https://stackoverflow.com/questions/39004513/how-to-emit-llvm-ir-from-cargo), one can do this via the following command:

```text
cargo rustc -- --emit=llvm-ir
```

and then the output of the `debug` build will be in `hello_llvm/target/debug/deps/hello_llvm.ll`.

Alternatively, one can obtain the release version of the LLVM Bitcode via this command:

```text
cargo rustc --release -- --emit=llvm-ir
```

and then the output of the `release` build will be in `hello_llvm/target/release/deps/hello_llvm.ll`.

# Actual output

<details>
    <summary>`debug` build</summary>

```llvm
; ModuleID = '1uelxnk0ai0reuli'
source_filename = "1uelxnk0ai0reuli"
target datalayout = "e-m:w-p270:32:32-p271:32:32-p272:64:64-i64:64-f80:128-n8:16:32:64-S128"
target triple = "x86_64-pc-windows-msvc"

%"core::fmt::Arguments" = type { { [0 x { [0 x i8]*, i64 }]*, i64 }, { i64*, i64 }, { [0 x { i8*, i64* }]*, i64 } }
%"core::panic::location::Location" = type { { [0 x i8]*, i64 }, i32, i32 }

@alloc2 = private unnamed_addr constant <{ [13 x i8] }> <{ [13 x i8] c"Hello, llvm!\0A" }>, align 1
@alloc3 = private unnamed_addr constant <{ i8*, [8 x i8] }> <{ i8* getelementptr inbounds (<{ [13 x i8] }>, <{ [13 x i8] }>* @alloc2, i32 0, i32 0, i32 0), [8 x i8] c"\0D\00\00\00\00\00\00\00" }>, align 8
@alloc10 = private unnamed_addr constant <{ [0 x i8] }> zeroinitializer, align 8
@vtable.0 = private unnamed_addr constant <{ i8*, [16 x i8], i8*, i8*, i8*, [0 x i8] }> <{ i8* bitcast (void (i64**)* @"_ZN4core3ptr85drop_in_place$LT$std..rt..lang_start$LT$$LP$$RP$$GT$..$u7b$$u7b$closure$u7d$$u7d$$GT$17he50d0bdd422f951eE" to i8*), [16 x i8] c"\08\00\00\00\00\00\00\00\08\00\00\00\00\00\00\00", i8* bitcast (i32 (i64**)* @"_ZN4core3ops8function6FnOnce40call_once$u7b$$u7b$vtable.shim$u7d$$u7d$17he22012a6de0c00a0E" to i8*), i8* bitcast (i32 (i64**)* @"_ZN3std2rt10lang_start28_$u7b$$u7b$closure$u7d$$u7d$17h0b6d08a626f3ce1aE" to i8*), i8* bitcast (i32 (i64**)* @"_ZN3std2rt10lang_start28_$u7b$$u7b$closure$u7d$$u7d$17h0b6d08a626f3ce1aE" to i8*), [0 x i8] zeroinitializer }>, align 8, !dbg !0
@alloc7 = private unnamed_addr constant <{ [12 x i8] }> <{ [12 x i8] c"invalid args" }>, align 1
@alloc8 = private unnamed_addr constant <{ i8*, [8 x i8] }> <{ i8* getelementptr inbounds (<{ [12 x i8] }>, <{ [12 x i8] }>* @alloc7, i32 0, i32 0, i32 0), [8 x i8] c"\0C\00\00\00\00\00\00\00" }>, align 8
@alloc21 = private unnamed_addr constant <{ [75 x i8] }> <{ [75 x i8] c"/rustc/e789f3a3a3d96ebf99b7bbd95011527e5be32a11\\library\\core\\src\\fmt\\mod.rs" }>, align 1
@alloc22 = private unnamed_addr constant <{ i8*, [16 x i8] }> <{ i8* getelementptr inbounds (<{ [75 x i8] }>, <{ [75 x i8] }>* @alloc21, i32 0, i32 0, i32 0), [16 x i8] c"K\00\00\00\00\00\00\00\81\01\00\00\0D\00\00\00" }>, align 8

; core::ops::function::FnOnce::call_once{{vtable.shim}}
; Function Attrs: inlinehint uwtable
define internal i32 @"_ZN4core3ops8function6FnOnce40call_once$u7b$$u7b$vtable.shim$u7d$$u7d$17he22012a6de0c00a0E"(i64** %_1) unnamed_addr #0 !dbg !108 {
start:
  %_1.dbg.spill = alloca i64**, align 8
  %_2 = alloca {}, align 1
  store i64** %_1, i64*** %_1.dbg.spill, align 8
  call void @llvm.dbg.declare(metadata i64*** %_1.dbg.spill, metadata !119, metadata !DIExpression()), !dbg !124
  call void @llvm.dbg.declare(metadata {}* %_2, metadata !120, metadata !DIExpression()), !dbg !124
  %0 = load i64*, i64** %_1, align 8, !dbg !124, !nonnull !24
; call core::ops::function::FnOnce::call_once
  %1 = call i32 @_ZN4core3ops8function6FnOnce9call_once17h15a20a67bd6b436bE(i64* nonnull %0), !dbg !124
  br label %bb1, !dbg !124

bb1:                                              ; preds = %start
  ret i32 %1, !dbg !124
}

; core::ops::function::FnOnce::call_once
; Function Attrs: inlinehint uwtable
define internal i32 @_ZN4core3ops8function6FnOnce9call_once17h15a20a67bd6b436bE(i64* nonnull %0) unnamed_addr #0 personality i32 (...)* @__CxxFrameHandler3 !dbg !125 {
start:
  %_2 = alloca {}, align 1
  %_1 = alloca i64*, align 8
  store i64* %0, i64** %_1, align 8
  call void @llvm.dbg.declare(metadata i64** %_1, metadata !129, metadata !DIExpression()), !dbg !131
  call void @llvm.dbg.declare(metadata {}* %_2, metadata !130, metadata !DIExpression()), !dbg !131
; invoke std::rt::lang_start::{{closure}}
  %1 = invoke i32 @"_ZN3std2rt10lang_start28_$u7b$$u7b$closure$u7d$$u7d$17h0b6d08a626f3ce1aE"(i64** align 8 dereferenceable(8) %_1)
          to label %bb1 unwind label %funclet_bb3, !dbg !131

bb1:                                              ; preds = %start
  br label %bb2, !dbg !131

bb3:                                              ; preds = %funclet_bb3
  br label %bb4, !dbg !131

funclet_bb3:                                      ; preds = %start
  %cleanuppad = cleanuppad within none []
  br label %bb3

bb4:                                              ; preds = %bb3
  cleanupret from %cleanuppad unwind to caller, !dbg !131

bb2:                                              ; preds = %bb1
  ret i32 %1, !dbg !131
}

; core::ops::function::FnOnce::call_once
; Function Attrs: inlinehint uwtable
define internal void @_ZN4core3ops8function6FnOnce9call_once17hae31d20c66f0faf5E(void ()* nonnull %_1) unnamed_addr #0 !dbg !132 {
start:
  %_1.dbg.spill = alloca void ()*, align 8
  %_2 = alloca {}, align 1
  store void ()* %_1, void ()** %_1.dbg.spill, align 8
  call void @llvm.dbg.declare(metadata void ()** %_1.dbg.spill, metadata !136, metadata !DIExpression()), !dbg !140
  call void @llvm.dbg.declare(metadata {}* %_2, metadata !137, metadata !DIExpression()), !dbg !140
  call void %_1(), !dbg !140
  br label %bb1, !dbg !140

bb1:                                              ; preds = %start
  ret void, !dbg !140
}

; core::ptr::drop_in_place<std::rt::lang_start<()>::{{closure}}>
; Function Attrs: inlinehint uwtable
define internal void @"_ZN4core3ptr85drop_in_place$LT$std..rt..lang_start$LT$$LP$$RP$$GT$..$u7b$$u7b$closure$u7d$$u7d$$GT$17he50d0bdd422f951eE"(i64** %_1) unnamed_addr #0 !dbg !141 {
start:
  %_1.dbg.spill = alloca i64**, align 8
  store i64** %_1, i64*** %_1.dbg.spill, align 8
  call void @llvm.dbg.declare(metadata i64*** %_1.dbg.spill, metadata !147, metadata !DIExpression()), !dbg !150
  ret void, !dbg !150
}

; hello_llvm::main
; Function Attrs: uwtable
define internal void @_ZN10hello_llvm4main17h3557140cb13f3a5eE() unnamed_addr #1 !dbg !151 {
start:
  %_2 = alloca %"core::fmt::Arguments", align 8
; call core::fmt::Arguments::new_v1
  call void @_ZN4core3fmt9Arguments6new_v117hd1998ab66b662a4bE(%"core::fmt::Arguments"* noalias nocapture sret(%"core::fmt::Arguments") dereferenceable(48) %_2, [0 x { [0 x i8]*, i64 }]* nonnull align 8 bitcast (<{ i8*, [8 x i8] }>* @alloc3 to [0 x { [0 x i8]*, i64 }]*), i64 1, [0 x { i8*, i64* }]* nonnull align 8 bitcast (<{ [0 x i8] }>* @alloc10 to [0 x { i8*, i64* }]*), i64 0), !dbg !154
  br label %bb1, !dbg !154

bb1:                                              ; preds = %start
; call std::io::stdio::_print
  call void @_ZN3std2io5stdio6_print17hdd22d39cb98498cbE(%"core::fmt::Arguments"* noalias nocapture dereferenceable(48) %_2), !dbg !154
  br label %bb2, !dbg !154

bb2:                                              ; preds = %bb1
  ret void, !dbg !155
}

; core::hint::black_box
; Function Attrs: inlinehint uwtable
define internal void @_ZN4core4hint9black_box17h37dbf4e992589e2cE() unnamed_addr #0 !dbg !156 {
start:
  %dummy.dbg.spill = alloca {}, align 1
  call void @llvm.dbg.declare(metadata {}* %dummy.dbg.spill, metadata !162, metadata !DIExpression()), !dbg !165
  call void asm sideeffect "", "r,~{memory}"({}* undef), !dbg !166, !srcloc !167
  br label %bb1, !dbg !166

bb1:                                              ; preds = %start
  ret void, !dbg !168
}

; std::process::ExitCode::to_i32
; Function Attrs: inlinehint uwtable
define internal i32 @_ZN3std7process8ExitCode6to_i3217h20917dea0f8c3aadE(i32 %0) unnamed_addr #0 !dbg !169 {
start:
  %self = alloca i32, align 4
  store i32 %0, i32* %self, align 4
  call void @llvm.dbg.declare(metadata i32* %self, metadata !184, metadata !DIExpression()), !dbg !185
; call std::sys::windows::process::ExitCode::as_i32
  %1 = call i32 @_ZN3std3sys7windows7process8ExitCode6as_i3217h9ebba9861c121561E(i32* align 4 dereferenceable(4) %self), !dbg !186
  br label %bb1, !dbg !186

bb1:                                              ; preds = %start
  ret i32 %1, !dbg !187
}

; <() as std::process::Termination>::report
; Function Attrs: inlinehint uwtable
define internal i32 @"_ZN54_$LT$$LP$$RP$$u20$as$u20$std..process..Termination$GT$6report17he18684357fdb4889E"() unnamed_addr #0 !dbg !188 {
start:
  %self.dbg.spill = alloca {}, align 1
  call void @llvm.dbg.declare(metadata {}* %self.dbg.spill, metadata !193, metadata !DIExpression()), !dbg !194
; call <std::process::ExitCode as std::process::Termination>::report
  %0 = call i32 @"_ZN68_$LT$std..process..ExitCode$u20$as$u20$std..process..Termination$GT$6report17h93050ea666c8781aE"(i32 0), !dbg !195
  br label %bb1, !dbg !195

bb1:                                              ; preds = %start
  ret i32 %0, !dbg !196
}

; <std::process::ExitCode as std::process::Termination>::report
; Function Attrs: inlinehint uwtable
define internal i32 @"_ZN68_$LT$std..process..ExitCode$u20$as$u20$std..process..Termination$GT$6report17h93050ea666c8781aE"(i32 %self) unnamed_addr #0 !dbg !197 {
start:
  %self.dbg.spill = alloca i32, align 4
  store i32 %self, i32* %self.dbg.spill, align 4
  call void @llvm.dbg.declare(metadata i32* %self.dbg.spill, metadata !202, metadata !DIExpression()), !dbg !203
  ret i32 %self, !dbg !204
}

; std::rt::lang_start
; Function Attrs: uwtable
define hidden i64 @_ZN3std2rt10lang_start17hbcb4da67ff9ef2dbE(void ()* nonnull %main, i64 %argc, i8** %argv) unnamed_addr #1 !dbg !205 {
start:
  %v.dbg.spill = alloca i64, align 8
  %argv.dbg.spill = alloca i8**, align 8
  %argc.dbg.spill = alloca i64, align 8
  %main.dbg.spill = alloca void ()*, align 8
  %_8 = alloca i64*, align 8
  %_4 = alloca i64, align 8
  store void ()* %main, void ()** %main.dbg.spill, align 8
  call void @llvm.dbg.declare(metadata void ()** %main.dbg.spill, metadata !214, metadata !DIExpression()), !dbg !219
  store i64 %argc, i64* %argc.dbg.spill, align 8
  call void @llvm.dbg.declare(metadata i64* %argc.dbg.spill, metadata !215, metadata !DIExpression()), !dbg !220
  store i8** %argv, i8*** %argv.dbg.spill, align 8
  call void @llvm.dbg.declare(metadata i8*** %argv.dbg.spill, metadata !216, metadata !DIExpression()), !dbg !221
  %0 = bitcast i64** %_8 to void ()**, !dbg !222
  store void ()* %main, void ()** %0, align 8, !dbg !222
  %_5.0 = bitcast i64** %_8 to {}*, !dbg !222
; call std::rt::lang_start_internal
  %1 = call i64 @_ZN3std2rt19lang_start_internal17h83bc6c99d74b7515E({}* nonnull align 1 %_5.0, [3 x i64]* align 8 dereferenceable(24) bitcast (<{ i8*, [16 x i8], i8*, i8*, i8*, [0 x i8] }>* @vtable.0 to [3 x i64]*), i64 %argc, i8** %argv), !dbg !223
  store i64 %1, i64* %_4, align 8, !dbg !223
  br label %bb1, !dbg !223

bb1:                                              ; preds = %start
  %v = load i64, i64* %_4, align 8, !dbg !223
  store i64 %v, i64* %v.dbg.spill, align 8, !dbg !223
  call void @llvm.dbg.declare(metadata i64* %v.dbg.spill, metadata !217, metadata !DIExpression()), !dbg !224
  ret i64 %v, !dbg !225
}

; std::rt::lang_start::{{closure}}
; Function Attrs: inlinehint uwtable
define internal i32 @"_ZN3std2rt10lang_start28_$u7b$$u7b$closure$u7d$$u7d$17h0b6d08a626f3ce1aE"(i64** align 8 dereferenceable(8) %_1) unnamed_addr #0 !dbg !226 {
start:
  %_1.dbg.spill = alloca i64**, align 8
  store i64** %_1, i64*** %_1.dbg.spill, align 8
  %0 = load i64**, i64*** %_1.dbg.spill, align 8, !nonnull !24
  %1 = bitcast i64** %0 to void ()**
  call void @llvm.dbg.declare(metadata i64*** %_1.dbg.spill, metadata !231, metadata !DIExpression(DW_OP_deref)), !dbg !232
  %2 = bitcast i64** %_1 to void ()**, !dbg !233
  %_4 = load void ()*, void ()** %2, align 8, !dbg !233, !nonnull !24
; call std::sys_common::backtrace::__rust_begin_short_backtrace
  call void @_ZN3std10sys_common9backtrace28__rust_begin_short_backtrace17h9a4642dc608ef17aE(void ()* nonnull %_4), !dbg !233
  br label %bb1, !dbg !233

bb1:                                              ; preds = %start
; call <() as std::process::Termination>::report
  %_2 = call i32 @"_ZN54_$LT$$LP$$RP$$u20$as$u20$std..process..Termination$GT$6report17he18684357fdb4889E"(), !dbg !233
  br label %bb2, !dbg !233

bb2:                                              ; preds = %bb1
; call std::process::ExitCode::to_i32
  %3 = call i32 @_ZN3std7process8ExitCode6to_i3217h20917dea0f8c3aadE(i32 %_2), !dbg !233
  br label %bb3, !dbg !233

bb3:                                              ; preds = %bb2
  ret i32 %3, !dbg !233
}

; std::sys_common::backtrace::__rust_begin_short_backtrace
; Function Attrs: noinline uwtable
define internal void @_ZN3std10sys_common9backtrace28__rust_begin_short_backtrace17h9a4642dc608ef17aE(void ()* nonnull %f) unnamed_addr #2 personality i32 (...)* @__CxxFrameHandler3 !dbg !234 {
start:
  %f.dbg.spill = alloca void ()*, align 8
  %result.dbg.spill = alloca {}, align 1
  call void @llvm.dbg.declare(metadata {}* %result.dbg.spill, metadata !240, metadata !DIExpression()), !dbg !244
  store void ()* %f, void ()** %f.dbg.spill, align 8
  call void @llvm.dbg.declare(metadata void ()** %f.dbg.spill, metadata !239, metadata !DIExpression()), !dbg !245
; call core::ops::function::FnOnce::call_once
  call void @_ZN4core3ops8function6FnOnce9call_once17hae31d20c66f0faf5E(void ()* nonnull %f), !dbg !246
  br label %bb1, !dbg !246

bb1:                                              ; preds = %start
; invoke core::hint::black_box
  invoke void @_ZN4core4hint9black_box17h37dbf4e992589e2cE()
          to label %bb2 unwind label %funclet_bb3, !dbg !247

bb2:                                              ; preds = %bb1
  ret void, !dbg !248

bb3:                                              ; preds = %funclet_bb3
  br label %bb4, !dbg !248

funclet_bb3:                                      ; preds = %bb1
  %cleanuppad = cleanuppad within none []
  br label %bb3

bb4:                                              ; preds = %bb3
  cleanupret from %cleanuppad unwind to caller, !dbg !245
}

; core::fmt::Arguments::new_v1
; Function Attrs: inlinehint uwtable
define internal void @_ZN4core3fmt9Arguments6new_v117hd1998ab66b662a4bE(%"core::fmt::Arguments"* noalias nocapture sret(%"core::fmt::Arguments") dereferenceable(48) %0, [0 x { [0 x i8]*, i64 }]* nonnull align 8 %pieces.0, i64 %pieces.1, [0 x { i8*, i64* }]* nonnull align 8 %args.0, i64 %args.1) unnamed_addr #0 !dbg !249 {
start:
  %args.dbg.spill = alloca { [0 x { i8*, i64* }]*, i64 }, align 8
  %pieces.dbg.spill = alloca { [0 x { [0 x i8]*, i64 }]*, i64 }, align 8
  %_23 = alloca { i64*, i64 }, align 8
  %_15 = alloca %"core::fmt::Arguments", align 8
  %_3 = alloca i8, align 1
  %1 = getelementptr inbounds { [0 x { [0 x i8]*, i64 }]*, i64 }, { [0 x { [0 x i8]*, i64 }]*, i64 }* %pieces.dbg.spill, i32 0, i32 0
  store [0 x { [0 x i8]*, i64 }]* %pieces.0, [0 x { [0 x i8]*, i64 }]** %1, align 8
  %2 = getelementptr inbounds { [0 x { [0 x i8]*, i64 }]*, i64 }, { [0 x { [0 x i8]*, i64 }]*, i64 }* %pieces.dbg.spill, i32 0, i32 1
  store i64 %pieces.1, i64* %2, align 8
  call void @llvm.dbg.declare(metadata { [0 x { [0 x i8]*, i64 }]*, i64 }* %pieces.dbg.spill, metadata !313, metadata !DIExpression()), !dbg !315
  %3 = getelementptr inbounds { [0 x { i8*, i64* }]*, i64 }, { [0 x { i8*, i64* }]*, i64 }* %args.dbg.spill, i32 0, i32 0
  store [0 x { i8*, i64* }]* %args.0, [0 x { i8*, i64* }]** %3, align 8
  %4 = getelementptr inbounds { [0 x { i8*, i64* }]*, i64 }, { [0 x { i8*, i64* }]*, i64 }* %args.dbg.spill, i32 0, i32 1
  store i64 %args.1, i64* %4, align 8
  call void @llvm.dbg.declare(metadata { [0 x { i8*, i64* }]*, i64 }* %args.dbg.spill, metadata !314, metadata !DIExpression()), !dbg !315
  %_4 = icmp ult i64 %pieces.1, %args.1, !dbg !316
  br i1 %_4, label %bb1, label %bb2, !dbg !316

bb2:                                              ; preds = %start
  %_12 = add i64 %args.1, 1, !dbg !316
  %_9 = icmp ugt i64 %pieces.1, %_12, !dbg !316
  %5 = zext i1 %_9 to i8, !dbg !316
  store i8 %5, i8* %_3, align 1, !dbg !316
  br label %bb3, !dbg !316

bb1:                                              ; preds = %start
  store i8 1, i8* %_3, align 1, !dbg !316
  br label %bb3, !dbg !316

bb3:                                              ; preds = %bb2, %bb1
  %6 = load i8, i8* %_3, align 1, !dbg !316, !range !317
  %7 = trunc i8 %6 to i1, !dbg !316
  br i1 %7, label %bb4, label %bb6, !dbg !316

bb6:                                              ; preds = %bb3
  %8 = bitcast { i64*, i64 }* %_23 to {}**, !dbg !318
  store {}* null, {}** %8, align 8, !dbg !318
  %9 = bitcast %"core::fmt::Arguments"* %0 to { [0 x { [0 x i8]*, i64 }]*, i64 }*, !dbg !318
  %10 = getelementptr inbounds { [0 x { [0 x i8]*, i64 }]*, i64 }, { [0 x { [0 x i8]*, i64 }]*, i64 }* %9, i32 0, i32 0, !dbg !318
  store [0 x { [0 x i8]*, i64 }]* %pieces.0, [0 x { [0 x i8]*, i64 }]** %10, align 8, !dbg !318
  %11 = getelementptr inbounds { [0 x { [0 x i8]*, i64 }]*, i64 }, { [0 x { [0 x i8]*, i64 }]*, i64 }* %9, i32 0, i32 1, !dbg !318
  store i64 %pieces.1, i64* %11, align 8, !dbg !318
  %12 = getelementptr inbounds %"core::fmt::Arguments", %"core::fmt::Arguments"* %0, i32 0, i32 1, !dbg !318
  %13 = getelementptr inbounds { i64*, i64 }, { i64*, i64 }* %_23, i32 0, i32 0, !dbg !318
  %14 = load i64*, i64** %13, align 8, !dbg !318
  %15 = getelementptr inbounds { i64*, i64 }, { i64*, i64 }* %_23, i32 0, i32 1, !dbg !318
  %16 = load i64, i64* %15, align 8, !dbg !318
  %17 = getelementptr inbounds { i64*, i64 }, { i64*, i64 }* %12, i32 0, i32 0, !dbg !318
  store i64* %14, i64** %17, align 8, !dbg !318
  %18 = getelementptr inbounds { i64*, i64 }, { i64*, i64 }* %12, i32 0, i32 1, !dbg !318
  store i64 %16, i64* %18, align 8, !dbg !318
  %19 = getelementptr inbounds %"core::fmt::Arguments", %"core::fmt::Arguments"* %0, i32 0, i32 2, !dbg !318
  %20 = getelementptr inbounds { [0 x { i8*, i64* }]*, i64 }, { [0 x { i8*, i64* }]*, i64 }* %19, i32 0, i32 0, !dbg !318
  store [0 x { i8*, i64* }]* %args.0, [0 x { i8*, i64* }]** %20, align 8, !dbg !318
  %21 = getelementptr inbounds { [0 x { i8*, i64* }]*, i64 }, { [0 x { i8*, i64* }]*, i64 }* %19, i32 0, i32 1, !dbg !318
  store i64 %args.1, i64* %21, align 8, !dbg !318
  ret void, !dbg !319

bb4:                                              ; preds = %bb3
; call core::fmt::Arguments::new_v1
  call void @_ZN4core3fmt9Arguments6new_v117hd1998ab66b662a4bE(%"core::fmt::Arguments"* noalias nocapture sret(%"core::fmt::Arguments") dereferenceable(48) %_15, [0 x { [0 x i8]*, i64 }]* nonnull align 8 bitcast (<{ i8*, [8 x i8] }>* @alloc8 to [0 x { [0 x i8]*, i64 }]*), i64 1, [0 x { i8*, i64* }]* nonnull align 8 bitcast (<{ [0 x i8] }>* @alloc10 to [0 x { i8*, i64* }]*), i64 0), !dbg !320
  br label %bb5, !dbg !320

bb5:                                              ; preds = %bb4
; call core::panicking::panic_fmt
  call void @_ZN4core9panicking9panic_fmt17hf1365c0b3f412305E(%"core::fmt::Arguments"* noalias nocapture dereferenceable(48) %_15, %"core::panic::location::Location"* align 8 dereferenceable(24) bitcast (<{ i8*, [16 x i8] }>* @alloc22 to %"core::panic::location::Location"*)) #6, !dbg !320
  unreachable, !dbg !320
}

; std::sys::windows::process::ExitCode::as_i32
; Function Attrs: inlinehint uwtable
define internal i32 @_ZN3std3sys7windows7process8ExitCode6as_i3217h9ebba9861c121561E(i32* align 4 dereferenceable(4) %self) unnamed_addr #0 !dbg !321 {
start:
  %self.dbg.spill = alloca i32*, align 8
  store i32* %self, i32** %self.dbg.spill, align 8
  call void @llvm.dbg.declare(metadata i32** %self.dbg.spill, metadata !327, metadata !DIExpression()), !dbg !328
  %_2 = load i32, i32* %self, align 4, !dbg !329
  ret i32 %_2, !dbg !330
}

; Function Attrs: nofree nosync nounwind readnone speculatable willreturn
declare void @llvm.dbg.declare(metadata, metadata, metadata) #3

declare i32 @__CxxFrameHandler3(...) unnamed_addr #4

; std::io::stdio::_print
; Function Attrs: uwtable
declare void @_ZN3std2io5stdio6_print17hdd22d39cb98498cbE(%"core::fmt::Arguments"* noalias nocapture dereferenceable(48)) unnamed_addr #1

; std::rt::lang_start_internal
; Function Attrs: uwtable
declare i64 @_ZN3std2rt19lang_start_internal17h83bc6c99d74b7515E({}* nonnull align 1, [3 x i64]* align 8 dereferenceable(24), i64, i8**) unnamed_addr #1

; core::panicking::panic_fmt
; Function Attrs: cold noinline noreturn uwtable
declare void @_ZN4core9panicking9panic_fmt17hf1365c0b3f412305E(%"core::fmt::Arguments"* noalias nocapture dereferenceable(48), %"core::panic::location::Location"* align 8 dereferenceable(24)) unnamed_addr #5

define i32 @main(i32 %0, i8** %1) unnamed_addr #4 {
top:
  %2 = sext i32 %0 to i64
; call std::rt::lang_start
  %3 = call i64 @_ZN3std2rt10lang_start17hbcb4da67ff9ef2dbE(void ()* @_ZN10hello_llvm4main17h3557140cb13f3a5eE, i64 %2, i8** %1)
  %4 = trunc i64 %3 to i32
  ret i32 %4
}

attributes #0 = { inlinehint uwtable "target-cpu"="x86-64" }
attributes #1 = { uwtable "target-cpu"="x86-64" }
attributes #2 = { noinline uwtable "target-cpu"="x86-64" }
attributes #3 = { nofree nosync nounwind readnone speculatable willreturn }
attributes #4 = { "target-cpu"="x86-64" }
attributes #5 = { cold noinline noreturn uwtable "target-cpu"="x86-64" }
attributes #6 = { noreturn }

!llvm.module.flags = !{!25, !26, !27, !28}
!llvm.dbg.cu = !{!29}

!0 = !DIGlobalVariableExpression(var: !1, expr: !DIExpression())
!1 = distinct !DIGlobalVariable(name: "impl$<std::rt::lang_start::closure_env$0<tuple$<> >, core::ops::function::Fn<tuple$<> > >::vtable$", scope: null, file: !2, type: !3, isLocal: true, isDefinition: true)
!2 = !DIFile(filename: "<unknown>", directory: "")
!3 = !DICompositeType(tag: DW_TAG_structure_type, name: "impl$<std::rt::lang_start::closure_env$0<tuple$<> >, core::ops::function::Fn<tuple$<> > >::vtable_type$", file: !2, size: 384, align: 64, flags: DIFlagArtificial, elements: !4, vtableHolder: !15, templateParams: !24, identifier: "impl$<std::rt::lang_start::closure_env$0<tuple$<> >, core::ops::function::Fn<tuple$<> > >::vtable_type$")
!4 = !{!5, !8, !11, !12, !13, !14}
!5 = !DIDerivedType(tag: DW_TAG_member, name: "drop_in_place", scope: !3, file: !2, baseType: !6, size: 64, align: 64)
!6 = !DIDerivedType(tag: DW_TAG_pointer_type, name: "ptr_const$<tuple$<> >", baseType: !7, size: 64, align: 64, dwarfAddressSpace: 0)
!7 = !DIBasicType(name: "()", encoding: DW_ATE_unsigned)
!8 = !DIDerivedType(tag: DW_TAG_member, name: "size", scope: !3, file: !2, baseType: !9, size: 64, align: 64, offset: 64)
!9 = !DIDerivedType(tag: DW_TAG_typedef, name: "usize", file: !2, baseType: !10)
!10 = !DIBasicType(name: "size_t", size: 64, encoding: DW_ATE_unsigned)
!11 = !DIDerivedType(tag: DW_TAG_member, name: "align", scope: !3, file: !2, baseType: !9, size: 64, align: 64, offset: 128)
!12 = !DIDerivedType(tag: DW_TAG_member, name: "__method3", scope: !3, file: !2, baseType: !6, size: 64, align: 64, offset: 192)
!13 = !DIDerivedType(tag: DW_TAG_member, name: "__method4", scope: !3, file: !2, baseType: !6, size: 64, align: 64, offset: 256)
!14 = !DIDerivedType(tag: DW_TAG_member, name: "__method5", scope: !3, file: !2, baseType: !6, size: 64, align: 64, offset: 320)
!15 = !DICompositeType(tag: DW_TAG_structure_type, name: "closure_env$0<tuple$<> >", scope: !16, file: !2, size: 64, align: 64, elements: !19, templateParams: !24, identifier: "4c1f16f696c175f8c8e11d0edf114074")
!16 = !DINamespace(name: "lang_start", scope: !17)
!17 = !DINamespace(name: "rt", scope: !18)
!18 = !DINamespace(name: "std", scope: null)
!19 = !{!20}
!20 = !DIDerivedType(tag: DW_TAG_member, name: "main", scope: !15, file: !2, baseType: !21, size: 64, align: 64)
!21 = !DIDerivedType(tag: DW_TAG_pointer_type, name: "void (*)()", baseType: !22, size: 64, align: 64, dwarfAddressSpace: 0)
!22 = !DISubroutineType(types: !23)
!23 = !{null}
!24 = !{}
!25 = !{i32 7, !"PIC Level", i32 2}
!26 = !{i32 7, !"PIE Level", i32 2}
!27 = !{i32 2, !"CodeView", i32 1}
!28 = !{i32 2, !"Debug Info Version", i32 3}
!29 = distinct !DICompileUnit(language: DW_LANG_Rust, file: !30, producer: "clang LLVM (rustc version 1.60.0-nightly (e789f3a3a 2022-02-11))", isOptimized: false, runtimeVersion: 0, emissionKind: FullDebug, enums: !31, globals: !107)
!30 = !DIFile(filename: "src\\main.rs\\@\\1uelxnk0ai0reuli", directory: "C:\\Users\\demen\\Documents\\GitHub\\hello_llvm")
!31 = !{!32, !39, !62, !87, !101, !106}
!32 = !DICompositeType(tag: DW_TAG_enumeration_type, name: "Option", scope: !33, file: !2, baseType: !35, size: 64, align: 64, flags: DIFlagEnumClass, elements: !36)
!33 = !DINamespace(name: "option", scope: !34)
!34 = !DINamespace(name: "core", scope: null)
!35 = !DIDerivedType(tag: DW_TAG_pointer_type, name: "ptr_mut$<tuple$<> >", baseType: !7, size: 64, align: 64, dwarfAddressSpace: 0)
!36 = !{!37, !38}
!37 = !DIEnumerator(name: "None", value: 0)
!38 = !DIEnumerator(name: "Some", value: 1)
!39 = !DICompositeType(tag: DW_TAG_enumeration_type, name: "Discriminant$", scope: !40, file: !2, baseType: !9, size: 64, align: 64, flags: DIFlagEnumClass, elements: !99)
!40 = !DICompositeType(tag: DW_TAG_union_type, name: "enum$<core::option::Option<slice$<core::fmt::rt::v1::Argument> >, 1, 18446744073709551615, Some>", file: !2, size: 128, align: 64, elements: !41, templateParams: !96, identifier: "fccb351037f3dc8c5a2b357f3707b797")
!41 = !{!42, !98}
!42 = !DIDerivedType(tag: DW_TAG_member, name: "dataful_variant", scope: !40, file: !2, baseType: !43, size: 128, align: 64)
!43 = !DICompositeType(tag: DW_TAG_structure_type, name: "Some", scope: !40, file: !2, size: 128, align: 64, elements: !44, templateParams: !96, identifier: "fccb351037f3dc8c5a2b357f3707b797::Some")
!44 = !{!45}
!45 = !DIDerivedType(tag: DW_TAG_member, name: "__0", scope: !43, file: !2, baseType: !46, size: 128, align: 64)
!46 = !DICompositeType(tag: DW_TAG_structure_type, name: "slice$<core::fmt::rt::v1::Argument>", file: !2, size: 128, align: 64, elements: !47, templateParams: !24, identifier: "178f6f11496f0052cd5988605aa7a71d")
!47 = !{!48, !95}
!48 = !DIDerivedType(tag: DW_TAG_member, name: "data_ptr", scope: !46, file: !2, baseType: !49, size: 64, align: 64)
!49 = !DIDerivedType(tag: DW_TAG_pointer_type, baseType: !50, size: 64, align: 64, dwarfAddressSpace: 0)
!50 = !DICompositeType(tag: DW_TAG_structure_type, name: "Argument", scope: !51, file: !2, size: 448, align: 64, elements: !54, templateParams: !24, identifier: "9c3556e2d74b98554950875367eb3de6")
!51 = !DINamespace(name: "v1", scope: !52)
!52 = !DINamespace(name: "rt", scope: !53)
!53 = !DINamespace(name: "fmt", scope: !34)
!54 = !{!55, !56}
!55 = !DIDerivedType(tag: DW_TAG_member, name: "position", scope: !50, file: !2, baseType: !9, size: 64, align: 64)
!56 = !DIDerivedType(tag: DW_TAG_member, name: "format", scope: !50, file: !2, baseType: !57, size: 384, align: 64, offset: 64)
!57 = !DICompositeType(tag: DW_TAG_structure_type, name: "FormatSpec", scope: !51, file: !2, size: 384, align: 64, elements: !58, templateParams: !24, identifier: "1df244a439ca978a14dd345431a17d55")
!58 = !{!59, !61, !70, !73, !94}
!59 = !DIDerivedType(tag: DW_TAG_member, name: "fill", scope: !57, file: !2, baseType: !60, size: 32, align: 32, offset: 256)
!60 = !DIBasicType(name: "char", size: 32, encoding: DW_ATE_unsigned_char)
!61 = !DIDerivedType(tag: DW_TAG_member, name: "align", scope: !57, file: !2, baseType: !62, size: 8, align: 8, offset: 320)
!62 = !DICompositeType(tag: DW_TAG_enumeration_type, name: "Alignment", scope: !51, file: !2, baseType: !63, size: 8, align: 8, flags: DIFlagEnumClass, elements: !65)
!63 = !DIDerivedType(tag: DW_TAG_typedef, name: "u8", file: !2, baseType: !64)
!64 = !DIBasicType(name: "unsigned __int8", size: 8, encoding: DW_ATE_unsigned)
!65 = !{!66, !67, !68, !69}
!66 = !DIEnumerator(name: "Left", value: 0)
!67 = !DIEnumerator(name: "Right", value: 1)
!68 = !DIEnumerator(name: "Center", value: 2)
!69 = !DIEnumerator(name: "Unknown", value: 3)
!70 = !DIDerivedType(tag: DW_TAG_member, name: "flags", scope: !57, file: !2, baseType: !71, size: 32, align: 32, offset: 288)
!71 = !DIDerivedType(tag: DW_TAG_typedef, name: "u32", file: !2, baseType: !72)
!72 = !DIBasicType(name: "unsigned __int32", size: 32, encoding: DW_ATE_unsigned)
!73 = !DIDerivedType(tag: DW_TAG_member, name: "precision", scope: !57, file: !2, baseType: !74, size: 128, align: 64)
!74 = !DICompositeType(tag: DW_TAG_union_type, name: "enum$<core::fmt::rt::v1::Count>", file: !2, size: 128, align: 64, elements: !75, templateParams: !24, identifier: "36c63ad902995c4ff9f507c49e5c07ff")
!75 = !{!76, !80, !84, !86}
!76 = !DIDerivedType(tag: DW_TAG_member, name: "variant0", scope: !74, file: !2, baseType: !77, size: 128, align: 64, extraData: i64 0)
!77 = !DICompositeType(tag: DW_TAG_structure_type, name: "Is", scope: !74, file: !2, size: 128, align: 64, elements: !78, templateParams: !24, identifier: "36c63ad902995c4ff9f507c49e5c07ff::Is")
!78 = !{!79}
!79 = !DIDerivedType(tag: DW_TAG_member, name: "__0", scope: !77, file: !2, baseType: !9, size: 64, align: 64, offset: 64)
!80 = !DIDerivedType(tag: DW_TAG_member, name: "variant1", scope: !74, file: !2, baseType: !81, size: 128, align: 64, extraData: i64 1)
!81 = !DICompositeType(tag: DW_TAG_structure_type, name: "Param", scope: !74, file: !2, size: 128, align: 64, elements: !82, templateParams: !24, identifier: "36c63ad902995c4ff9f507c49e5c07ff::Param")
!82 = !{!83}
!83 = !DIDerivedType(tag: DW_TAG_member, name: "__0", scope: !81, file: !2, baseType: !9, size: 64, align: 64, offset: 64)
!84 = !DIDerivedType(tag: DW_TAG_member, name: "variant2", scope: !74, file: !2, baseType: !85, size: 128, align: 64, extraData: i64 2)
!85 = !DICompositeType(tag: DW_TAG_structure_type, name: "Implied", scope: !74, file: !2, size: 128, align: 64, elements: !24, templateParams: !24, identifier: "36c63ad902995c4ff9f507c49e5c07ff::Implied")
!86 = !DIDerivedType(tag: DW_TAG_member, name: "discriminant", scope: !74, file: !2, baseType: !87, size: 64, align: 64)
!87 = !DICompositeType(tag: DW_TAG_enumeration_type, name: "Count", scope: !51, file: !2, baseType: !88, size: 64, align: 64, flags: DIFlagEnumClass, elements: !90)
!88 = !DIDerivedType(tag: DW_TAG_typedef, name: "u64", file: !2, baseType: !89)
!89 = !DIBasicType(name: "unsigned __int64", size: 64, encoding: DW_ATE_unsigned)
!90 = !{!91, !92, !93}
!91 = !DIEnumerator(name: "Is", value: 0)
!92 = !DIEnumerator(name: "Param", value: 1)
!93 = !DIEnumerator(name: "Implied", value: 2)
!94 = !DIDerivedType(tag: DW_TAG_member, name: "width", scope: !57, file: !2, baseType: !74, size: 128, align: 64, offset: 128)
!95 = !DIDerivedType(tag: DW_TAG_member, name: "length", scope: !46, file: !2, baseType: !9, size: 64, align: 64, offset: 64)
!96 = !{!97}
!97 = !DITemplateTypeParameter(name: "T", type: !46)
!98 = !DIDerivedType(tag: DW_TAG_member, name: "discriminant", scope: !40, file: !2, baseType: !39, size: 128, align: 64)
!99 = !{!100}
!100 = !DIEnumerator(name: "None", value: 0, isUnsigned: true)
!101 = !DICompositeType(tag: DW_TAG_enumeration_type, name: "Result", scope: !102, file: !2, baseType: !63, size: 8, align: 8, flags: DIFlagEnumClass, elements: !103)
!102 = !DINamespace(name: "result", scope: !34)
!103 = !{!104, !105}
!104 = !DIEnumerator(name: "Ok", value: 0)
!105 = !DIEnumerator(name: "Err", value: 1)
!106 = !DICompositeType(tag: DW_TAG_enumeration_type, name: "Option", scope: !33, file: !2, baseType: !88, size: 64, align: 64, flags: DIFlagEnumClass, elements: !36)
!107 = !{!0}
!108 = distinct !DISubprogram(name: "call_once<std::rt::lang_start::closure_env$0<tuple$<> >,tuple$<> >", linkageName: "_ZN4core3ops8function6FnOnce40call_once$u7b$$u7b$vtable.shim$u7d$$u7d$17he22012a6de0c00a0E", scope: !110, file: !109, line: 227, type: !113, scopeLine: 227, flags: DIFlagPrototyped, spFlags: DISPFlagLocalToUnit | DISPFlagDefinition, unit: !29, templateParams: !121, retainedNodes: !118)
!109 = !DIFile(filename: "/rustc/e789f3a3a3d96ebf99b7bbd95011527e5be32a11\\library\\core\\src\\ops\\function.rs", directory: "", checksumkind: CSK_SHA1, checksum: "9bea7362fff50bbe301170918847d3ca3912a24a")
!110 = !DINamespace(name: "FnOnce", scope: !111)
!111 = !DINamespace(name: "function", scope: !112)
!112 = !DINamespace(name: "ops", scope: !34)
!113 = !DISubroutineType(types: !114)
!114 = !{!115, !117}
!115 = !DIDerivedType(tag: DW_TAG_typedef, name: "i32", file: !2, baseType: !116)
!116 = !DIBasicType(name: "__int32", size: 32, encoding: DW_ATE_signed)
!117 = !DIDerivedType(tag: DW_TAG_pointer_type, name: "ptr_mut$<std::rt::lang_start::closure_env$0<tuple$<> > >", baseType: !15, size: 64, align: 64, dwarfAddressSpace: 0)
!118 = !{!119, !120}
!119 = !DILocalVariable(arg: 1, scope: !108, file: !109, line: 227, type: !117)
!120 = !DILocalVariable(arg: 2, scope: !108, file: !109, line: 227, type: !7)
!121 = !{!122, !123}
!122 = !DITemplateTypeParameter(name: "Self", type: !15)
!123 = !DITemplateTypeParameter(name: "Args", type: !7)
!124 = !DILocation(line: 227, scope: !108)
!125 = distinct !DISubprogram(name: "call_once<std::rt::lang_start::closure_env$0<tuple$<> >,tuple$<> >", linkageName: "_ZN4core3ops8function6FnOnce9call_once17h15a20a67bd6b436bE", scope: !110, file: !109, line: 227, type: !126, scopeLine: 227, flags: DIFlagPrototyped, spFlags: DISPFlagLocalToUnit | DISPFlagDefinition, unit: !29, templateParams: !121, retainedNodes: !128)
!126 = !DISubroutineType(types: !127)
!127 = !{!115, !15}
!128 = !{!129, !130}
!129 = !DILocalVariable(arg: 1, scope: !125, file: !109, line: 227, type: !15)
!130 = !DILocalVariable(arg: 2, scope: !125, file: !109, line: 227, type: !7)
!131 = !DILocation(line: 227, scope: !125)
!132 = distinct !DISubprogram(name: "call_once<void (*)(),tuple$<> >", linkageName: "_ZN4core3ops8function6FnOnce9call_once17hae31d20c66f0faf5E", scope: !110, file: !109, line: 227, type: !133, scopeLine: 227, flags: DIFlagPrototyped, spFlags: DISPFlagLocalToUnit | DISPFlagDefinition, unit: !29, templateParams: !138, retainedNodes: !135)
!133 = !DISubroutineType(types: !134)
!134 = !{null, !21}
!135 = !{!136, !137}
!136 = !DILocalVariable(arg: 1, scope: !132, file: !109, line: 227, type: !21)
!137 = !DILocalVariable(arg: 2, scope: !132, file: !109, line: 227, type: !7)
!138 = !{!139, !123}
!139 = !DITemplateTypeParameter(name: "Self", type: !21)
!140 = !DILocation(line: 227, scope: !132)
!141 = distinct !DISubprogram(name: "drop_in_place<std::rt::lang_start::closure_env$0<tuple$<> > >", linkageName: "_ZN4core3ptr85drop_in_place$LT$std..rt..lang_start$LT$$LP$$RP$$GT$..$u7b$$u7b$closure$u7d$$u7d$$GT$17he50d0bdd422f951eE", scope: !143, file: !142, line: 188, type: !144, scopeLine: 188, flags: DIFlagPrototyped, spFlags: DISPFlagLocalToUnit | DISPFlagDefinition, unit: !29, templateParams: !148, retainedNodes: !146)
!142 = !DIFile(filename: "/rustc/e789f3a3a3d96ebf99b7bbd95011527e5be32a11\\library\\core\\src\\ptr\\mod.rs", directory: "", checksumkind: CSK_SHA1, checksum: "f72f4549b954f891aa6c07064a899d3b597de310")
!143 = !DINamespace(name: "ptr", scope: !34)
!144 = !DISubroutineType(types: !145)
!145 = !{null, !117}
!146 = !{!147}
!147 = !DILocalVariable(arg: 1, scope: !141, file: !142, line: 188, type: !117)
!148 = !{!149}
!149 = !DITemplateTypeParameter(name: "T", type: !15)
!150 = !DILocation(line: 188, scope: !141)
!151 = distinct !DISubprogram(name: "main", linkageName: "_ZN10hello_llvm4main17h3557140cb13f3a5eE", scope: !153, file: !152, line: 1, type: !22, scopeLine: 1, flags: DIFlagPrototyped, spFlags: DISPFlagLocalToUnit | DISPFlagDefinition | DISPFlagMainSubprogram, unit: !29, templateParams: !24, retainedNodes: !24)
!152 = !DIFile(filename: "src\\main.rs", directory: "C:\\Users\\demen\\Documents\\GitHub\\hello_llvm", checksumkind: CSK_SHA1, checksum: "0b5c041f827eb1a434f8a580985724f832b21138")
!153 = !DINamespace(name: "hello_llvm", scope: null)
!154 = !DILocation(line: 2, scope: !151)
!155 = !DILocation(line: 3, scope: !151)
!156 = distinct !DISubprogram(name: "black_box<tuple$<> >", linkageName: "_ZN4core4hint9black_box17h37dbf4e992589e2cE", scope: !158, file: !157, line: 173, type: !159, scopeLine: 173, flags: DIFlagPrototyped, spFlags: DISPFlagLocalToUnit | DISPFlagDefinition, unit: !29, templateParams: !163, retainedNodes: !161)
!157 = !DIFile(filename: "/rustc/e789f3a3a3d96ebf99b7bbd95011527e5be32a11\\library\\core\\src\\hint.rs", directory: "", checksumkind: CSK_SHA1, checksum: "91019e21840ac32d7c5abefbffa63d35358616e9")
!158 = !DINamespace(name: "hint", scope: !34)
!159 = !DISubroutineType(types: !160)
!160 = !{null, !7}
!161 = !{!162}
!162 = !DILocalVariable(name: "dummy", arg: 1, scope: !156, file: !157, line: 173, type: !7)
!163 = !{!164}
!164 = !DITemplateTypeParameter(name: "T", type: !7)
!165 = !DILocation(line: 173, scope: !156)
!166 = !DILocation(line: 174, scope: !156)
!167 = !{i32 3171427}
!168 = !DILocation(line: 175, scope: !156)
!169 = distinct !DISubprogram(name: "to_i32", linkageName: "_ZN3std7process8ExitCode6to_i3217h20917dea0f8c3aadE", scope: !171, file: !170, line: 1689, type: !181, scopeLine: 1689, flags: DIFlagPrototyped, spFlags: DISPFlagLocalToUnit | DISPFlagDefinition, unit: !29, templateParams: !24, retainedNodes: !183)
!170 = !DIFile(filename: "/rustc/e789f3a3a3d96ebf99b7bbd95011527e5be32a11\\library\\std\\src\\process.rs", directory: "", checksumkind: CSK_SHA1, checksum: "9a227b9bcc92ab17e8684a77aa37859fb404358d")
!171 = !DICompositeType(tag: DW_TAG_structure_type, name: "ExitCode", scope: !172, file: !2, size: 32, align: 32, elements: !173, templateParams: !24, identifier: "67666fc5f6d620e31e32d4920da134c6")
!172 = !DINamespace(name: "process", scope: !18)
!173 = !{!174}
!174 = !DIDerivedType(tag: DW_TAG_member, name: "__0", scope: !171, file: !2, baseType: !175, size: 32, align: 32)
!175 = !DICompositeType(tag: DW_TAG_structure_type, name: "ExitCode", scope: !176, file: !2, size: 32, align: 32, elements: !179, templateParams: !24, identifier: "d49fe94ada2131c8c01c482308c845b2")
!176 = !DINamespace(name: "process", scope: !177)
!177 = !DINamespace(name: "windows", scope: !178)
!178 = !DINamespace(name: "sys", scope: !18)
!179 = !{!180}
!180 = !DIDerivedType(tag: DW_TAG_member, name: "__0", scope: !175, file: !2, baseType: !71, size: 32, align: 32)
!181 = !DISubroutineType(types: !182)
!182 = !{!115, !171}
!183 = !{!184}
!184 = !DILocalVariable(name: "self", arg: 1, scope: !169, file: !170, line: 1689, type: !171)
!185 = !DILocation(line: 1689, scope: !169)
!186 = !DILocation(line: 1690, scope: !169)
!187 = !DILocation(line: 1691, scope: !169)
!188 = distinct !DISubprogram(name: "report", linkageName: "_ZN54_$LT$$LP$$RP$$u20$as$u20$std..process..Termination$GT$6report17he18684357fdb4889E", scope: !189, file: !170, line: 2048, type: !190, scopeLine: 2048, flags: DIFlagPrototyped, spFlags: DISPFlagLocalToUnit | DISPFlagDefinition, unit: !29, templateParams: !24, retainedNodes: !192)
!189 = !DINamespace(name: "impl$50", scope: !172)
!190 = !DISubroutineType(types: !191)
!191 = !{!171, !7}
!192 = !{!193}
!193 = !DILocalVariable(name: "self", arg: 1, scope: !188, file: !170, line: 2048, type: !7)
!194 = !DILocation(line: 2048, scope: !188)
!195 = !DILocation(line: 2049, scope: !188)
!196 = !DILocation(line: 2050, scope: !188)
!197 = distinct !DISubprogram(name: "report", linkageName: "_ZN68_$LT$std..process..ExitCode$u20$as$u20$std..process..Termination$GT$6report17h93050ea666c8781aE", scope: !198, file: !170, line: 2090, type: !199, scopeLine: 2090, flags: DIFlagPrototyped, spFlags: DISPFlagLocalToUnit | DISPFlagDefinition, unit: !29, templateParams: !24, retainedNodes: !201)
!198 = !DINamespace(name: "impl$55", scope: !172)
!199 = !DISubroutineType(types: !200)
!200 = !{!171, !171}
!201 = !{!202}
!202 = !DILocalVariable(name: "self", arg: 1, scope: !197, file: !170, line: 2090, type: !171)
!203 = !DILocation(line: 2090, scope: !197)
!204 = !DILocation(line: 2092, scope: !197)
!205 = distinct !DISubprogram(name: "lang_start<tuple$<> >", linkageName: "_ZN3std2rt10lang_start17hbcb4da67ff9ef2dbE", scope: !17, file: !206, line: 139, type: !207, scopeLine: 139, flags: DIFlagPrototyped, spFlags: DISPFlagLocalToUnit | DISPFlagDefinition, unit: !29, templateParams: !163, retainedNodes: !213)
!206 = !DIFile(filename: "/rustc/e789f3a3a3d96ebf99b7bbd95011527e5be32a11\\library\\std\\src\\rt.rs", directory: "", checksumkind: CSK_SHA1, checksum: "fda45b079f39e54b791ab9d76adb74b19bd1112f")
!207 = !DISubroutineType(types: !208)
!208 = !{!209, !21, !209, !211}
!209 = !DIDerivedType(tag: DW_TAG_typedef, name: "isize", file: !2, baseType: !210)
!210 = !DIBasicType(name: "ptrdiff_t", size: 64, encoding: DW_ATE_signed)
!211 = !DIDerivedType(tag: DW_TAG_pointer_type, name: "ptr_const$<ptr_const$<u8> >", baseType: !212, size: 64, align: 64, dwarfAddressSpace: 0)
!212 = !DIDerivedType(tag: DW_TAG_pointer_type, name: "ptr_const$<u8>", baseType: !63, size: 64, align: 64, dwarfAddressSpace: 0)
!213 = !{!214, !215, !216, !217}
!214 = !DILocalVariable(name: "main", arg: 1, scope: !205, file: !206, line: 140, type: !21)
!215 = !DILocalVariable(name: "argc", arg: 2, scope: !205, file: !206, line: 141, type: !209)
!216 = !DILocalVariable(name: "argv", arg: 3, scope: !205, file: !206, line: 142, type: !211)
!217 = !DILocalVariable(name: "v", scope: !218, file: !206, line: 144, type: !209, align: 8)
!218 = distinct !DILexicalBlock(scope: !205, file: !206, line: 144)
!219 = !DILocation(line: 140, scope: !205)
!220 = !DILocation(line: 141, scope: !205)
!221 = !DILocation(line: 142, scope: !205)
!222 = !DILocation(line: 145, scope: !205)
!223 = !DILocation(line: 144, scope: !205)
!224 = !DILocation(line: 144, scope: !218)
!225 = !DILocation(line: 150, scope: !205)
!226 = distinct !DISubprogram(name: "closure$0<tuple$<> >", linkageName: "_ZN3std2rt10lang_start28_$u7b$$u7b$closure$u7d$$u7d$17h0b6d08a626f3ce1aE", scope: !16, file: !206, line: 145, type: !227, scopeLine: 145, flags: DIFlagPrototyped, spFlags: DISPFlagLocalToUnit | DISPFlagDefinition, unit: !29, templateParams: !163, retainedNodes: !230)
!227 = !DISubroutineType(types: !228)
!228 = !{!115, !229}
!229 = !DIDerivedType(tag: DW_TAG_pointer_type, name: "ref$<std::rt::lang_start::closure_env$0<tuple$<> > >", baseType: !15, size: 64, align: 64, dwarfAddressSpace: 0)
!230 = !{!231}
!231 = !DILocalVariable(name: "main", scope: !226, file: !206, line: 140, type: !21, align: 8)
!232 = !DILocation(line: 140, scope: !226)
!233 = !DILocation(line: 145, scope: !226)
!234 = distinct !DISubprogram(name: "__rust_begin_short_backtrace<void (*)(),tuple$<> >", linkageName: "_ZN3std10sys_common9backtrace28__rust_begin_short_backtrace17h9a4642dc608ef17aE", scope: !236, file: !235, line: 118, type: !133, scopeLine: 118, flags: DIFlagPrototyped, spFlags: DISPFlagLocalToUnit | DISPFlagDefinition, unit: !29, templateParams: !242, retainedNodes: !238)
!235 = !DIFile(filename: "/rustc/e789f3a3a3d96ebf99b7bbd95011527e5be32a11\\library\\std\\src\\sys_common\\backtrace.rs", directory: "", checksumkind: CSK_SHA1, checksum: "8773b096a79345e40815a51ccfb666eb0e8da511")
!236 = !DINamespace(name: "backtrace", scope: !237)
!237 = !DINamespace(name: "sys_common", scope: !18)
!238 = !{!239, !240}
!239 = !DILocalVariable(name: "f", arg: 1, scope: !234, file: !235, line: 118, type: !21)
!240 = !DILocalVariable(name: "result", scope: !241, file: !235, line: 122, type: !7, align: 1)
!241 = distinct !DILexicalBlock(scope: !234, file: !235, line: 122)
!242 = !{!243, !164}
!243 = !DITemplateTypeParameter(name: "F", type: !21)
!244 = !DILocation(line: 122, scope: !241)
!245 = !DILocation(line: 118, scope: !234)
!246 = !DILocation(line: 122, scope: !234)
!247 = !DILocation(line: 125, scope: !241)
!248 = !DILocation(line: 128, scope: !234)
!249 = distinct !DISubprogram(name: "new_v1", linkageName: "_ZN4core3fmt9Arguments6new_v117hd1998ab66b662a4bE", scope: !251, file: !250, line: 383, type: !310, scopeLine: 383, flags: DIFlagPrototyped, spFlags: DISPFlagLocalToUnit | DISPFlagDefinition, unit: !29, templateParams: !24, retainedNodes: !312)
!250 = !DIFile(filename: "/rustc/e789f3a3a3d96ebf99b7bbd95011527e5be32a11\\library\\core\\src\\fmt\\mod.rs", directory: "", checksumkind: CSK_SHA1, checksum: "553b4f9f06121e4fc335738106767224fe914a71")
!251 = !DICompositeType(tag: DW_TAG_structure_type, name: "Arguments", scope: !53, file: !2, size: 384, align: 64, elements: !252, templateParams: !24, identifier: "e3ac515aef4d99f23d310261ec67d9d0")
!252 = !{!253, !264, !265}
!253 = !DIDerivedType(tag: DW_TAG_member, name: "pieces", scope: !251, file: !2, baseType: !254, size: 128, align: 64)
!254 = !DICompositeType(tag: DW_TAG_structure_type, name: "slice$<str>", file: !2, size: 128, align: 64, elements: !255, templateParams: !24, identifier: "a673d89da0bdcf4d8c9ca87ae2c56d84")
!255 = !{!256, !263}
!256 = !DIDerivedType(tag: DW_TAG_member, name: "data_ptr", scope: !254, file: !2, baseType: !257, size: 64, align: 64)
!257 = !DIDerivedType(tag: DW_TAG_pointer_type, baseType: !258, size: 64, align: 64, dwarfAddressSpace: 0)
!258 = !DICompositeType(tag: DW_TAG_structure_type, name: "str", file: !2, size: 128, align: 64, elements: !259, templateParams: !24, identifier: "84eec819988617519061e0b609a72fe3")
!259 = !{!260, !262}
!260 = !DIDerivedType(tag: DW_TAG_member, name: "data_ptr", scope: !258, file: !2, baseType: !261, size: 64, align: 64)
!261 = !DIDerivedType(tag: DW_TAG_pointer_type, baseType: !63, size: 64, align: 64, dwarfAddressSpace: 0)
!262 = !DIDerivedType(tag: DW_TAG_member, name: "length", scope: !258, file: !2, baseType: !9, size: 64, align: 64, offset: 64)
!263 = !DIDerivedType(tag: DW_TAG_member, name: "length", scope: !254, file: !2, baseType: !9, size: 64, align: 64, offset: 64)
!264 = !DIDerivedType(tag: DW_TAG_member, name: "fmt", scope: !251, file: !2, baseType: !40, size: 128, align: 64, offset: 128)
!265 = !DIDerivedType(tag: DW_TAG_member, name: "args", scope: !251, file: !2, baseType: !266, size: 128, align: 64, offset: 256)
!266 = !DICompositeType(tag: DW_TAG_structure_type, name: "slice$<core::fmt::ArgumentV1>", file: !2, size: 128, align: 64, elements: !267, templateParams: !24, identifier: "a8df28905cd62817b651cc3ac99fdb3a")
!267 = !{!268, !309}
!268 = !DIDerivedType(tag: DW_TAG_member, name: "data_ptr", scope: !266, file: !2, baseType: !269, size: 64, align: 64)
!269 = !DIDerivedType(tag: DW_TAG_pointer_type, baseType: !270, size: 64, align: 64, dwarfAddressSpace: 0)
!270 = !DICompositeType(tag: DW_TAG_structure_type, name: "ArgumentV1", scope: !53, file: !2, size: 128, align: 64, elements: !271, templateParams: !24, identifier: "d4548110aaa961f0226634fddf82cb01")
!271 = !{!272, !275}
!272 = !DIDerivedType(tag: DW_TAG_member, name: "value", scope: !270, file: !2, baseType: !273, size: 64, align: 64)
!273 = !DIDerivedType(tag: DW_TAG_pointer_type, name: "ref$<core::fmt::extern$0::Opaque>", baseType: !274, size: 64, align: 64, dwarfAddressSpace: 0)
!274 = !DICompositeType(tag: DW_TAG_structure_type, name: "Opaque", file: !2, align: 8, elements: !24, identifier: "308878d95badc3d828ca1945f1b6cd8e")
!275 = !DIDerivedType(tag: DW_TAG_member, name: "formatter", scope: !270, file: !2, baseType: !276, size: 64, align: 64, offset: 64)
!276 = !DIDerivedType(tag: DW_TAG_pointer_type, name: "enum$<core::result::Result<tuple$<>,core::fmt::Error> > (*)(ref$<core::fmt::extern$0::Opaque>,ref_mut$<core::fmt::Formatter>)", baseType: !277, size: 64, align: 64, dwarfAddressSpace: 0)
!277 = !DISubroutineType(types: !278)
!278 = !{!101, !273, !279}
!279 = !DIDerivedType(tag: DW_TAG_pointer_type, name: "ref_mut$<core::fmt::Formatter>", baseType: !280, size: 64, align: 64, dwarfAddressSpace: 0)
!280 = !DICompositeType(tag: DW_TAG_structure_type, name: "Formatter", scope: !53, file: !2, size: 512, align: 64, elements: !281, templateParams: !24, identifier: "61786309314a1e242c044f7c77be063")
!281 = !{!282, !283, !284, !285, !297, !298}
!282 = !DIDerivedType(tag: DW_TAG_member, name: "flags", scope: !280, file: !2, baseType: !71, size: 32, align: 32, offset: 384)
!283 = !DIDerivedType(tag: DW_TAG_member, name: "fill", scope: !280, file: !2, baseType: !60, size: 32, align: 32, offset: 416)
!284 = !DIDerivedType(tag: DW_TAG_member, name: "align", scope: !280, file: !2, baseType: !62, size: 8, align: 8, offset: 448)
!285 = !DIDerivedType(tag: DW_TAG_member, name: "width", scope: !280, file: !2, baseType: !286, size: 128, align: 64)
!286 = !DICompositeType(tag: DW_TAG_union_type, name: "enum$<core::option::Option<usize> >", file: !2, size: 128, align: 64, elements: !287, templateParams: !290, identifier: "bcfb946962c432cf3fb1fe925d062ab7")
!287 = !{!288, !292, !296}
!288 = !DIDerivedType(tag: DW_TAG_member, name: "variant0", scope: !286, file: !2, baseType: !289, size: 128, align: 64, extraData: i64 0)
!289 = !DICompositeType(tag: DW_TAG_structure_type, name: "None", scope: !286, file: !2, size: 128, align: 64, elements: !24, templateParams: !290, identifier: "bcfb946962c432cf3fb1fe925d062ab7::None")
!290 = !{!291}
!291 = !DITemplateTypeParameter(name: "T", type: !9)
!292 = !DIDerivedType(tag: DW_TAG_member, name: "variant1", scope: !286, file: !2, baseType: !293, size: 128, align: 64, extraData: i64 1)
!293 = !DICompositeType(tag: DW_TAG_structure_type, name: "Some", scope: !286, file: !2, size: 128, align: 64, elements: !294, templateParams: !290, identifier: "bcfb946962c432cf3fb1fe925d062ab7::Some")
!294 = !{!295}
!295 = !DIDerivedType(tag: DW_TAG_member, name: "__0", scope: !293, file: !2, baseType: !9, size: 64, align: 64, offset: 64)
!296 = !DIDerivedType(tag: DW_TAG_member, name: "discriminant", scope: !286, file: !2, baseType: !106, size: 64, align: 64)
!297 = !DIDerivedType(tag: DW_TAG_member, name: "precision", scope: !280, file: !2, baseType: !286, size: 128, align: 64, offset: 128)
!298 = !DIDerivedType(tag: DW_TAG_member, name: "buf", scope: !280, file: !2, baseType: !299, size: 128, align: 64, offset: 256)
!299 = !DICompositeType(tag: DW_TAG_structure_type, name: "ref_mut$<dyn$<core::fmt::Write> >", file: !2, size: 128, align: 64, elements: !300, templateParams: !24, identifier: "c702772094c7a177b7e8ada1551f6109")
!300 = !{!301, !304}
!301 = !DIDerivedType(tag: DW_TAG_member, name: "pointer", scope: !299, file: !2, baseType: !302, size: 64, align: 64)
!302 = !DIDerivedType(tag: DW_TAG_pointer_type, baseType: !303, size: 64, align: 64, dwarfAddressSpace: 0)
!303 = !DICompositeType(tag: DW_TAG_structure_type, name: "dyn$<core::fmt::Write>", file: !2, align: 8, elements: !24, templateParams: !24, identifier: "29811859ad68e6fbef540db814f8f92b")
!304 = !DIDerivedType(tag: DW_TAG_member, name: "vtable", scope: !299, file: !2, baseType: !305, size: 64, align: 64, offset: 64)
!305 = !DIDerivedType(tag: DW_TAG_pointer_type, name: "ref$<array$<usize,3> >", baseType: !306, size: 64, align: 64, dwarfAddressSpace: 0)
!306 = !DICompositeType(tag: DW_TAG_array_type, baseType: !9, size: 192, align: 64, elements: !307)
!307 = !{!308}
!308 = !DISubrange(count: 3, lowerBound: 0)
!309 = !DIDerivedType(tag: DW_TAG_member, name: "length", scope: !266, file: !2, baseType: !9, size: 64, align: 64, offset: 64)
!310 = !DISubroutineType(types: !311)
!311 = !{!251, !254, !266}
!312 = !{!313, !314}
!313 = !DILocalVariable(name: "pieces", scope: !249, file: !250, line: 383, type: !254, align: 8)
!314 = !DILocalVariable(name: "args", scope: !249, file: !250, line: 383, type: !266, align: 8)
!315 = !DILocation(line: 383, scope: !249)
!316 = !DILocation(line: 384, scope: !249)
!317 = !{i8 0, i8 2}
!318 = !DILocation(line: 387, scope: !249)
!319 = !DILocation(line: 388, scope: !249)
!320 = !DILocation(line: 385, scope: !249)
!321 = distinct !DISubprogram(name: "as_i32", linkageName: "_ZN3std3sys7windows7process8ExitCode6as_i3217h9ebba9861c121561E", scope: !175, file: !322, line: 664, type: !323, scopeLine: 664, flags: DIFlagPrototyped, spFlags: DISPFlagLocalToUnit | DISPFlagDefinition, unit: !29, templateParams: !24, retainedNodes: !326)
!322 = !DIFile(filename: "/rustc/e789f3a3a3d96ebf99b7bbd95011527e5be32a11\\library\\std\\src\\sys\\windows\\process.rs", directory: "", checksumkind: CSK_SHA1, checksum: "1b9c9c943ced65809cfa66b658f59c11a3bf8cff")
!323 = !DISubroutineType(types: !324)
!324 = !{!115, !325}
!325 = !DIDerivedType(tag: DW_TAG_pointer_type, name: "ref$<std::sys::windows::process::ExitCode>", baseType: !175, size: 64, align: 64, dwarfAddressSpace: 0)
!326 = !{!327}
!327 = !DILocalVariable(name: "self", arg: 1, scope: !321, file: !322, line: 664, type: !325)
!328 = !DILocation(line: 664, scope: !321)
!329 = !DILocation(line: 665, scope: !321)
!330 = !DILocation(line: 666, scope: !321)
```

</details>

<details>
    <summary>`release` build</summary>
  
```llvm
; ModuleID = 'hello_llvm.41829c61-cgu.0'
source_filename = "hello_llvm.41829c61-cgu.0"
target datalayout = "e-m:w-p270:32:32-p271:32:32-p272:64:64-i64:64-f80:128-n8:16:32:64-S128"
target triple = "x86_64-pc-windows-msvc"

%"core::fmt::Arguments" = type { { [0 x { [0 x i8]*, i64 }]*, i64 }, { i64*, i64 }, { [0 x { i8*, i64* }]*, i64 } }

@alloc2 = private unnamed_addr constant <{ [13 x i8] }> <{ [13 x i8] c"Hello, llvm!\0A" }>, align 1
@alloc3 = private unnamed_addr constant <{ i8*, [8 x i8] }> <{ i8* getelementptr inbounds (<{ [13 x i8] }>, <{ [13 x i8] }>* @alloc2, i32 0, i32 0, i32 0), [8 x i8] c"\0D\00\00\00\00\00\00\00" }>, align 8
@alloc10 = private unnamed_addr constant <{ [0 x i8] }> zeroinitializer, align 8
@vtable.0 = private unnamed_addr constant <{ i8*, [16 x i8], i8*, i8*, i8*, [0 x i8] }> <{ i8* bitcast (void (i64**)* @"_ZN4core3ptr85drop_in_place$LT$std..rt..lang_start$LT$$LP$$RP$$GT$..$u7b$$u7b$closure$u7d$$u7d$$GT$17hac93bd7ac519a7d7E" to i8*), [16 x i8] c"\08\00\00\00\00\00\00\00\08\00\00\00\00\00\00\00", i8* bitcast (i32 (i64**)* @"_ZN4core3ops8function6FnOnce40call_once$u7b$$u7b$vtable.shim$u7d$$u7d$17hec5617c0a7fabb11E" to i8*), i8* bitcast (i32 (i64**)* @"_ZN3std2rt10lang_start28_$u7b$$u7b$closure$u7d$$u7d$17h785d46129563f416E" to i8*), i8* bitcast (i32 (i64**)* @"_ZN3std2rt10lang_start28_$u7b$$u7b$closure$u7d$$u7d$17h785d46129563f416E" to i8*), [0 x i8] zeroinitializer }>, align 8

; core::ops::function::FnOnce::call_once{{vtable.shim}}
; Function Attrs: inlinehint uwtable
define internal i32 @"_ZN4core3ops8function6FnOnce40call_once$u7b$$u7b$vtable.shim$u7d$$u7d$17hec5617c0a7fabb11E"(i64** nocapture readonly %_1) unnamed_addr #0 personality i32 (...)* @__CxxFrameHandler3 {
start:
  %0 = bitcast i64** %_1 to void ()**
  %1 = load void ()*, void ()** %0, align 8, !nonnull !2
; call std::sys_common::backtrace::__rust_begin_short_backtrace
  tail call fastcc void @_ZN3std10sys_common9backtrace28__rust_begin_short_backtrace17h8e630f4fb7f0d948E(void ()* nonnull %1), !noalias !3
  ret i32 0
}

; core::ptr::drop_in_place<std::rt::lang_start<()>::{{closure}}>
; Function Attrs: inlinehint mustprogress nofree norecurse nosync nounwind readnone uwtable willreturn
define internal void @"_ZN4core3ptr85drop_in_place$LT$std..rt..lang_start$LT$$LP$$RP$$GT$..$u7b$$u7b$closure$u7d$$u7d$$GT$17hac93bd7ac519a7d7E"(i64** nocapture readnone %_1) unnamed_addr #1 {
start:
  ret void
}

; hello_llvm::main
; Function Attrs: uwtable
define internal void @_ZN10hello_llvm4main17h2287ed6f2a24428bE() unnamed_addr #2 {
start:
  %_2 = alloca %"core::fmt::Arguments", align 8
  %0 = bitcast %"core::fmt::Arguments"* %_2 to i8*
  call void @llvm.lifetime.start.p0i8(i64 48, i8* nonnull %0)
  %1 = getelementptr inbounds %"core::fmt::Arguments", %"core::fmt::Arguments"* %_2, i64 0, i32 0, i32 0
  store [0 x { [0 x i8]*, i64 }]* bitcast (<{ i8*, [8 x i8] }>* @alloc3 to [0 x { [0 x i8]*, i64 }]*), [0 x { [0 x i8]*, i64 }]** %1, align 8, !alias.scope !6
  %2 = getelementptr inbounds %"core::fmt::Arguments", %"core::fmt::Arguments"* %_2, i64 0, i32 0, i32 1
  store i64 1, i64* %2, align 8, !alias.scope !6
  %3 = getelementptr inbounds %"core::fmt::Arguments", %"core::fmt::Arguments"* %_2, i64 0, i32 1, i32 0
  store i64* null, i64** %3, align 8, !alias.scope !6
  %4 = getelementptr inbounds %"core::fmt::Arguments", %"core::fmt::Arguments"* %_2, i64 0, i32 2, i32 0
  store [0 x { i8*, i64* }]* bitcast (<{ [0 x i8] }>* @alloc10 to [0 x { i8*, i64* }]*), [0 x { i8*, i64* }]** %4, align 8, !alias.scope !6
  %5 = getelementptr inbounds %"core::fmt::Arguments", %"core::fmt::Arguments"* %_2, i64 0, i32 2, i32 1
  store i64 0, i64* %5, align 8, !alias.scope !6
; call std::io::stdio::_print
  call void @_ZN3std2io5stdio6_print17hdd22d39cb98498cbE(%"core::fmt::Arguments"* noalias nocapture nonnull dereferenceable(48) %_2)
  call void @llvm.lifetime.end.p0i8(i64 48, i8* nonnull %0)
  ret void
}

; std::rt::lang_start
; Function Attrs: uwtable
define hidden i64 @_ZN3std2rt10lang_start17h63beaef9518fe175E(void ()* nonnull %main, i64 %argc, i8** %argv) unnamed_addr #2 {
start:
  %_8 = alloca i64*, align 8
  %0 = bitcast i64** %_8 to i8*
  call void @llvm.lifetime.start.p0i8(i64 8, i8* nonnull %0)
  %1 = bitcast i64** %_8 to void ()**
  store void ()* %main, void ()** %1, align 8
  %_5.0 = bitcast i64** %_8 to {}*
; call std::rt::lang_start_internal
  %2 = call i64 @_ZN3std2rt19lang_start_internal17h83bc6c99d74b7515E({}* nonnull align 1 %_5.0, [3 x i64]* noalias readonly align 8 dereferenceable(24) bitcast (<{ i8*, [16 x i8], i8*, i8*, i8*, [0 x i8] }>* @vtable.0 to [3 x i64]*), i64 %argc, i8** %argv)
  call void @llvm.lifetime.end.p0i8(i64 8, i8* nonnull %0)
  ret i64 %2
}

; std::rt::lang_start::{{closure}}
; Function Attrs: inlinehint uwtable
define internal i32 @"_ZN3std2rt10lang_start28_$u7b$$u7b$closure$u7d$$u7d$17h785d46129563f416E"(i64** noalias nocapture readonly align 8 dereferenceable(8) %_1) unnamed_addr #0 {
start:
  %0 = bitcast i64** %_1 to void ()**
  %_4 = load void ()*, void ()** %0, align 8, !nonnull !2
; call std::sys_common::backtrace::__rust_begin_short_backtrace
  tail call fastcc void @_ZN3std10sys_common9backtrace28__rust_begin_short_backtrace17h8e630f4fb7f0d948E(void ()* nonnull %_4)
  ret i32 0
}

; std::sys_common::backtrace::__rust_begin_short_backtrace
; Function Attrs: noinline uwtable
define internal fastcc void @_ZN3std10sys_common9backtrace28__rust_begin_short_backtrace17h8e630f4fb7f0d948E(void ()* nocapture nonnull %f) unnamed_addr #3 personality i32 (...)* @__CxxFrameHandler3 {
start:
  tail call void %f()
  tail call void asm sideeffect "", "r,~{memory}"({}* undef) #6, !srcloc !9
  ret void
}

declare i32 @__CxxFrameHandler3(...) unnamed_addr #4

; Function Attrs: argmemonly mustprogress nofree nosync nounwind willreturn
declare void @llvm.lifetime.start.p0i8(i64 immarg, i8* nocapture) #5

; std::io::stdio::_print
; Function Attrs: uwtable
declare void @_ZN3std2io5stdio6_print17hdd22d39cb98498cbE(%"core::fmt::Arguments"* noalias nocapture dereferenceable(48)) unnamed_addr #2

; Function Attrs: argmemonly mustprogress nofree nosync nounwind willreturn
declare void @llvm.lifetime.end.p0i8(i64 immarg, i8* nocapture) #5

; std::rt::lang_start_internal
; Function Attrs: uwtable
declare i64 @_ZN3std2rt19lang_start_internal17h83bc6c99d74b7515E({}* nonnull align 1, [3 x i64]* noalias readonly align 8 dereferenceable(24), i64, i8**) unnamed_addr #2

define i32 @main(i32 %0, i8** %1) unnamed_addr #4 {
top:
  %_8.i = alloca i64*, align 8
  %2 = sext i32 %0 to i64
  %3 = bitcast i64** %_8.i to i8*
  call void @llvm.lifetime.start.p0i8(i64 8, i8* nonnull %3)
  %4 = bitcast i64** %_8.i to void ()**
  store void ()* @_ZN10hello_llvm4main17h2287ed6f2a24428bE, void ()** %4, align 8
  %_5.0.i = bitcast i64** %_8.i to {}*
; call std::rt::lang_start_internal
  %5 = call i64 @_ZN3std2rt19lang_start_internal17h83bc6c99d74b7515E({}* nonnull align 1 %_5.0.i, [3 x i64]* noalias readonly align 8 dereferenceable(24) bitcast (<{ i8*, [16 x i8], i8*, i8*, i8*, [0 x i8] }>* @vtable.0 to [3 x i64]*), i64 %2, i8** %1)
  call void @llvm.lifetime.end.p0i8(i64 8, i8* nonnull %3)
  %6 = trunc i64 %5 to i32
  ret i32 %6
}

attributes #0 = { inlinehint uwtable "target-cpu"="x86-64" }
attributes #1 = { inlinehint mustprogress nofree norecurse nosync nounwind readnone uwtable willreturn "target-cpu"="x86-64" }
attributes #2 = { uwtable "target-cpu"="x86-64" }
attributes #3 = { noinline uwtable "target-cpu"="x86-64" }
attributes #4 = { "target-cpu"="x86-64" }
attributes #5 = { argmemonly mustprogress nofree nosync nounwind willreturn }
attributes #6 = { nounwind }

!llvm.module.flags = !{!0, !1}

!0 = !{i32 7, !"PIC Level", i32 2}
!1 = !{i32 7, !"PIE Level", i32 2}
!2 = !{}
!3 = !{!4}
!4 = distinct !{!4, !5, !"_ZN3std2rt10lang_start28_$u7b$$u7b$closure$u7d$$u7d$17h785d46129563f416E: %_1"}
!5 = distinct !{!5, !"_ZN3std2rt10lang_start28_$u7b$$u7b$closure$u7d$$u7d$17h785d46129563f416E"}
!6 = !{!7}
!7 = distinct !{!7, !8, !"_ZN4core3fmt9Arguments6new_v117h9e029beeeeaac882E: argument 0"}
!8 = distinct !{!8, !"_ZN4core3fmt9Arguments6new_v117h9e029beeeeaac882E"}
!9 = !{i32 3171427}
```
</details>