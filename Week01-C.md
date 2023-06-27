### [回到學習討論區](https://hackmd.io/@thecutekoala/ryenf9u_n)

* [Visual Studio Code ](https://cs50.dev/)


## 1. CLI指令補充

1. `clang -o hello hello.c`
將hello.c經過編譯器clang生成的可執行文件hello。
(-o是`clang`編譯器的一個選項，output)
> 與`make hello`不同的地方在於
> `make hello`會根據Makefile中的定義來調用相應的編譯器(例如`clang`)編譯hello.c，
> 而`clang -o hello hello.c`則是直接使用編譯器`clang`。

2. `clang -o hello hello.c -lcs50`
將hello.c經過編譯器clang生成的可執行文件hello，並指定使用cs50這個lib函式庫文件。
(-l是`clang`編譯器的一個選項，library)

3. `debug50 ./hello`
開啟debug模式

## 2. 編譯過程

1. **preprocessing**
預處理，這裡指編譯的第一個階段，
在正式編譯之前，預處理器(preprocessor)會處理#字符開頭的特殊指令，
(例如`#define` `#include` 等等)
是整個編譯過程最早的完成的階段。

2. **compiling**
編譯，將整個程式編譯成組合語言([assembly code](https://zh.wikipedia.org/zh-tw/%E6%B1%87%E7%BC%96%E8%AF%AD%E8%A8%80))

3. **assembling**
組譯，進一步將組合語言組譯成機械語言([machine code](https://zh.wikipedia.org/zh-tw/%E6%9C%BA%E5%99%A8%E8%AF%AD%E8%A8%80))

4. **linking**
連結，將檔案連結各種函示庫之後，形成一個可執行檔案。

5. **decompiling**
反編譯，將已經編譯過的二進位代碼轉換成高級程式碼的過程。