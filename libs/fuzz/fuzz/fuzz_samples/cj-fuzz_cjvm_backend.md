# cjvm 使用 cj-fuzz 功能

## 差异说明

cjvm 无法加载 `.a` 文件，只能加载 `.so` 文件。

cj-fuzz 运行时依赖 `libclang_rt.fuzzer_no_main.a` 和 `libcangjie-fuzz-fuzzFFI.a`，因此需要将它们链接为动态链接库的格式，命令如下：

```shell
clang++ -shared -Wl,--whole-archive libclang_rt.fuzzer_no_main.a ${CANGJIE_HOME}/lib/linux_x86_64_jet/libcangjie-fuzz-fuzzFFI.a -Wl,--no-whole-archive -o libcangjie-fuzz-fuzzFFI.so
```

## 运行 cj-fuzz

1. 通过上述命令，获得 `libcangjie-fuzz-fuzzFFI.so`
2. `cjc fuzz_main.cj --sanitizer-coverage-inline-8bit-counters ${CANGJIE_HOME}/modules/linux_x86_64_jet/fuzz/fuzz.bc -lcangjie-fuzz-fuzzFFI`：
   - `--sanitizer-coverage-inline-8bit-counters` 启用覆盖率插桩；
   - `${CANGJIE_HOME}/modules/linux_x86_64_jet/fuzz/fuzz.bc` 主动链接 fuzz 模块的 fuzz 包的字节码；
   - `-lcangjie-fuzz-fuzzFFI` 指定依赖库的名称，运行时会搜索 libcangjie-fuzz-fuzzFFI.so 进行动态加载。
3. `LD_LIBRARY_PATH=/path/to/lib:${LD_LIBRARY_PATH} cj main.cbc`：
   - 按需修改 LD_LIBRARY_PATH；
   - 执行 cbc 文件。

实际效果如下：

```text
cp /usr/lib/llvm-14/lib/clang/14.0.0/lib/linux/libclang_rt.fuzzer_no_main-x86_64.a .
clang++ -shared -Wl,--whole-archive libclang_rt.fuzzer_no_main-x86_64.a ${CANGJIE_HOME}/lib/linux_x86_64_jet/libcangjie-fuzz-fuzzFFI.a -Wl,--no-whole-archive -o libcangjie-fuzz-fuzzFFI.so
cjc --sanitizer-coverage-inline-8bit-counters fuzz_main.cj ${CANGJIE_HOME}/modules/linux_x86_64_jet/fuzz/fuzz.bc -lcangjie-fuzz-fuzzFFI
LD_LIBRARY_PATH=/path/to/lib:${LD_LIBRARY_PATH} cj main.cbc
>>>>
    INFO: Running with entropic power schedule (0xFF, 100).
    INFO: Seed: 3156944264
    INFO: Loaded 1 modules   (21 inline 8-bit counters): 21 [0x5627041690a0, 0x5627041690b5),
    INFO: -max_len is not provided; libFuzzer will not generate inputs larger than 4096 bytes
    INFO: A corpus is not provided, starting from an empty corpus
    #2      INITED ft: 4 corp: 1/1b exec/s: 0 rss: 52Mb
    #488    NEW    ft: 5 corp: 2/9b lim: 8 exec/s: 0 rss: 53Mb L: 8/8 MS: 1 InsertRepeatedBytes-
    #12303  NEW    ft: 6 corp: 3/17b lim: 122 exec/s: 0 rss: 54Mb L: 8/8 MS: 5 CrossOver-ChangeBit-ShuffleBytes-ShuffleBytes-ChangeByte-
    #20164  NEW    ft: 7 corp: 4/25b lim: 198 exec/s: 0 rss: 54Mb L: 8/8 MS: 1 ChangeByte-
    #180030 NEW    ft: 8 corp: 5/33b lim: 1780 exec/s: 180030 rss: 55Mb L: 8/8 MS: 1 ChangeByte-
    #524288 pulse  ft: 8 corp: 5/33b lim: 4096 exec/s: 174762 rss: 55Mb
    #671045 NEW    ft: 9 corp: 6/41b lim: 4096 exec/s: 167761 rss: 55Mb L: 8/8 MS: 5 InsertByte-ChangeByte-ChangeBit-ChangeByte-EraseBytes-
    #758816 NEW    ft: 10 corp: 7/49b lim: 4096 exec/s: 151763 rss: 55Mb L: 8/8 MS: 1 ChangeByte-
    #1048576        pulse  ft: 10 corp: 7/49b lim: 4096 exec/s: 149796 rss: 55Mb
    #1947938        NEW    ft: 11 corp: 8/57b lim: 4096 exec/s: 162328 rss: 55Mb L: 8/8 MS: 2 InsertByte-EraseBytes-
    #2097152        pulse  ft: 11 corp: 8/57b lim: 4096 exec/s: 161319 rss: 55Mb
    #3332055        NEW    ft: 12 corp: 9/65b lim: 4096 exec/s: 151457 rss: 55Mb L: 8/8 MS: 2 ChangeByte-ChangeBit-
    [WARNING]: Detect uncatched exception, maybe caused by bugs, exit now
    An exception has occurred:
    Exception: TRAP
             at default.api(/cjvm_demo/test.cj:20)
             at default.api(/cjvm_demo/test.cj:0)
             at fuzz/fuzz.libfuzzerCallback(/cangjie/lib/src/fuzz/fuzz/callback.cj:34)
             at fuzz/fuzz.Fuzzer.startFuzz(/cangjie/lib/src/fuzz/fuzz/fuzzer.cj:223)
             at default.<main>(/cjvm_demo/test.cj:5)
             at default.user.main(<unknown>:0)
    [INFO]: data is: [67, 97, 110, 103, 106, 105, 101, 33]
    [INFO]: crash file will stored with libfuzzer
    ==33946== ERROR: libFuzzer: fuzz target exited
    SUMMARY: libFuzzer: fuzz target exited
    MS: 1 ChangeByte-; base unit: 1719c2c0bbc676f5b436528c183e4743a455d66a
    0x43,0x61,0x6e,0x67,0x6a,0x69,0x65,0x21,
    Cangjie!
    artifact_prefix='./'; Test unit written to ./crash-555e7af32a2ceb585cdd9ce810c4804e65d41cea
    Base64: Q2FuZ2ppZSE=
```
