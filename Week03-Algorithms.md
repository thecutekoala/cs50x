### [回到學習資源區](https://hackmd.io/@thecutekoala/ryenf9u_n)

* [Visual Studio Code ](https://cs50.dev/)

## 一. Time Complexity (時間複雜度)

### O($n$)
線性階
Linear Search
線性搜尋法

### O($logn$)
對數階
Binary Search
二分搜尋法

### others
時間由快到慢
O($1$) > O($logn$) > O($n$) > O($nlogn$) > O($n^2$)

## 二. Asymptotic Notation 漸進符號

### Big-O( Ο )
演算法時間函式的上限(Upper bound)，或最糟情況下的執行次數。

### Omega( Ω )
演算法時間函式的下限(Lower bound)。

### Theta( θ )
演算法時間函式的上限與下限。

## 三. code

### 1. 線性搜尋 in C
```clike!
int numbers[] = {20, 500, 10, 5, 100, 1, 50};

    int n = get_int("Number: ");
    for (int i = 0; i < 7; i++)
    {
        if (numbers[i] == n)
        {
            printf("Found\n");
            return 0;
        }
    }
    printf("Not found\n");
    return 1;
}
```

### 2. 搜尋字串 in C
```clike!
#include <string.h>
    
//......

string  strings[] = {"battle", "Knife", "ship", "cannon", "iron", "boot", "tank"};

    string  s = get_string("String: ");
    for (int i = 0; i < 7; i++)
    {
        if (strcmp(string[i], s) == 0)
        {
            printf("Found\n");
            return 0;
        }
    }
    printf("Not found\n");
    return 1;
}
```
> 如果strings length < for loop 次數，會產生錯誤：  
> Segmantation fault (core dump)

### 3. typedef 自定義結構
```clike!
typedef struct
{
    string name;
    string number;
}
person;
```
>　有object內味兒了

### 4. 搜尋電話 in C
```clike!
int main(void)
{
    person people[2];

    people[0].name = "Carter";
    people[0].number = "+886-983-887-555";

    people[1].name = "David";
    people[1].number = "+886-925-000-777";

    string name = get_string("Name: ");
    for (int i = 0; i < 2; i++)
    {
        if(strcmp(people[i].name, name) == 0)
        {
            printf("Found %s\n", people[i].number);
            return 0;
        }
    }
    printf("Not Found");
    return 1;
}
```

## 四. Sorting

### 1. Selection Sort
選擇排序法

1從未排序的數列中找到最小值
2將最小值跟未排序數列最左邊的數字交換
3重複1直到序列全部排序完成
時間複雜度為
O($n^2$) / Ω($n^2$)

### 2. Bubble Sort
氣泡排序法(又稱交換排序法)

1第一筆資料與隔壁相比較，如果順序有誤就交換
2進行過一輪之後可以確定最後一筆資料位置正確，重複1直到所有排序正確
O($n^2$) / Ω($n$)

### 3. Merge Sort
合併排序法
![](https://hackmd.io/_uploads/ByqiHX3F3.png =50%x)

1將資料分割$logn$次
2每次合併時互相比較
3每層總共比較n次
O($nlogn$) Ω($nlogn$)

## IDE 補充

`time ./sort random.txt`
用來顯示sort檔案執行的時間