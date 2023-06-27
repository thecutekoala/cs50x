
### [回到學習討論區](https://hackmd.io/@thecutekoala/ryenf9u_n)

 ### 以下指令常用於Unix或Linux系統，要解決window報錯問題，需要裝上Make工具並且設定環境變數
 
1. 安裝 Make 工具：在 Windows 上，使用 [MinGW](https://sourceforge.net/projects/mingw/) 或 Cygwin 來安裝 Make 工具。這些工具提供了類似於 Unix 或 Linux 系統上的 Make 命令。從它們的官方網站下載並安裝。
2. 設定環境變數：安裝完 Make 工具後，需要將其安裝路徑添加到系統的環境變數中。請參考工具的安裝說明文件，找到相應的環境變數設定方法。
3. 重新啟動終端機：在設定完環境變數後，請關閉並重新打開你的終端機或命令提示字元視窗，以使變更生效。
 
 以上供參考，現階段課程在cs50.dev上面運作及可。
 
 ## 1. CLI指令
 
 1. Visual Studio Code
[code.cs50.io](https://cs50.dev/)
 
 2. `code hello.c`
 在名為terminal的CLI中輸入code hello.c，
 產生、打開或命名一個名為hello.c的檔案。
 
 3. `make hello`
 輸入make hello是使用Make工具來編譯和構建名為"hello.c"的程式文件，
 Make會查找名為"Makefile"的文件，
 來編譯"hello.c"文件並生成可執行文件"hello"。
 (注意，不需要打上副檔名)
 
 4. `./hello`
 輸入./hello，用來執行可執行文件"hello"。
 
 5.  `clear`
 清除terminal中的歷史資訊
 
 6. Manual Pages
 [manual.cs50.io](https://manual.cs50.io/)
 簡短的介紹各種C語言的標準輸入輸出頭文件（Standard Input/Output Header File）
 提供了許多用於進行輸入和輸出操作的函數和相關定義等資訊。
 
 ## 2. C 語法
 
 * <stdio.h>
### 1. `prinf(  );`
 印出()中的文字在螢幕上。
 例如：
```clike!
#include <stdio.h>

int main(void)
{
    printf("hello, world\n");
}
```
> hello, world
 
 * <cs50.h>
### 2. `get_string(  );`
 這個函數會需要使用者輸入一個字串，也包含一些程式碼(例如printf)，
 並且對應一個參數，而返回一個使用者輸入的字串。
 例如：
```clike!
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    string s = get_string("Input: ");
    printf("Output: %s\n", s);
}
```
> Input: 123
> Output: 123

###  3. if / else / get_int
  例如：
```clike!
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    int x = get_int("what's x ?\n");
    int y = get_int("what's y ?\n");

    if(x < y)
    {
        printf("x is less than y\n");
    }
    else if(x > y)
    {
        printf("x is greater than y\n");
    }
    else
    {
        printf("x is equal to y\n");
    }
}
```
> what's x ? 2
> what's y ? 3
> x is less than y

### 4. get_char
 例如：
```clike!
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    char c = get_char("Do you agree?\n");

    if (c == 'y' || c == 'Y')
    {
        printf("Agree.\n");
    }
    else if (c == 'n' || c == 'N')
    {
        printf("Not agree.\n");
    }
}
```
>Do you agree? Y
>Agree.

### 5. loop
* while loop
```clike!
#include <stdio.h>

int main(void)
{
    int i = 0;
    while (i < 3)
    {
        printf("meow\n");
        i++;
    }
}
```
>meow
>meow
>meow
* for loop
```clike!
#include <stdio.h>

int main(void)
{
    for (int i = 0; i < 3; i++)
    {
        printf("meow\n");
    }
}
```
>meow
>meow
>meow

### 6. nested loop
> 印出由#組成的3*3面積

```clike!
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    int n;
    do
    {
        n = get_int("Size: ");
    }
    while (n < 1);

    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            printf("#");
        }
        printf("\n");
    }
}
```
>`###`
>`###`
>`###`

> 印出n*n的面積，n可以自定義
> do{ } while( )用來確保n>1

```clike!
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    // 獲取這塊陣列的尺寸
    int n;
    do
    {
        n = get_int("Size: ");
    }
    while (n < 1);

    // 打印出這塊陣列
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            printf("#");
        }
        printf("\n");
    }
}
```
>Size: 5
>`#####`
>`#####`
>`#####`
>`#####`
>`#####`

### 7. Abstraction
將兩件事情單獨拆開來處理，
1.獲取這塊陣列的尺寸
2.打印出這塊陣列

```clike!
#include <cs50.h>
#include <stdio.h>

//  獲取size，不需要輸入參數，但會返回int   
int get_size(void);
//  需要輸入參數n，但不返回值。
void print_grid(int n);

// 實際執行的main簡化成兩行程式碼
int main(void)
{
    int n = get_size();
    print_grid(n);
}


int get_size(void)
{
    int n;
    do
    {
        n = get_int("Size: ");
    }
    while (n < 1);
    return n;
}

void print_grid(int n)
{
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            printf("#");
        }
        printf("\n");
    }
}
```
> 將兩件事情單獨包裹成get_size與print_grid

### 8. 運算子與型別

```clike!
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    int x = get_int("x: ");

    int y = get_int("y: ");

    printf("%i\n", x + y);
}
```
輸入x與y相加
x=1,y=x時
> 3

### 9. integer overflow (整數溢出)

x=2000000000
y=2000000000
> -294927696

稱為**整數溢出(integer overflow)**

> 因為一個int只能用32bits
> 32個0與1只能構成正負20幾億
> 因此要改為long將儲存容量擴增為64bits
> (容量約為正負4*10^19)

solve： 型別long
```clike!
#include <cs50.h>
#include <stdio.h>

int main(void)
{
   
    long x = get_int("x: ");

    long y = get_int("y: ");

    printf("%li\n", x + y);
}
```
> x = 2000000000
> y = 2000000000
>  4000000000


### 10. truncation (截斷誤差)

將計算改為 x / y

x=1
y=3
> 0

因為long為整數，小數點之後直接全部捨去

solve: 型別float

```clike!
{
  
    long x = get_int("x: ");

    long y = get_int("y: ");

    float z = (float) x / (float) y;
    printf("%f\n", z);
}
```
> x = 1
> y = 3
> 0.333333


### 11. floating-point imprecision (浮點數失準)
記憶體非無限制，所以小數點後面一定會出現誤差。

改成顯示小數點以下30位
```clike!
{
  
    long x = get_int("x: ");

    long y = get_int("y: ");

    float z = (float) x / (float) y;
    printf("%.30f\n", z);
}
```
> x = 1
> y = 3
> 0.333333343267440795898437500000

此時小數點底下第8位開始失準

solve: 型別double
```clike!
{
  
    long x = get_int("x: ");

    long y = get_int("y: ");

    double z = (double) x / (double) y;
    printf("%.30f\n", z);
}
```
> x = 1
> y = 0.333333333333333314829616256247

可以精確至小數點以下第16位

## 3. 其他型別

...待更新

## 4. 作業

[lab 1](https://cs50.harvard.edu/x/2023/labs/1/)
[problem set 1](https://cs50.harvard.edu/x/2023/psets/1/)
