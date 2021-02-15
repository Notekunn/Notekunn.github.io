---
draft: false
template: "post"
title: Game oẳn tù tì sử dụng danh sách liên kết ?
slug: 2019/06/19/game-oan-tu-ti-su-dung-danh-sach-lien-ket
date: 2019-06-19T17:00:00.000Z
description: Sử dụng danh sách liên kết
socialImage: https://i.imgur.com/RNP2O57.png
tags:
  - C
  - Programming
  - Tutorial
---

# Game oẳn tù tì sử dụng danh sách liên kết ?

Chào các bạn, lại là mình đây.
Chắc các bạn cũng đã từng viết một game đơn giản như oẳn tù tì rồi đúng không nhỉ.
Mình đã tham khảo nhiểu bài viết trên mạng nhưng thuật toán kiểm tra khá là dài

## Thuật toán

Hôm nay mình sẽ hướng dẫn các bạn một thuật toán khác cũng dài không kém nhưng khá thú vị, đấy là sử dụng danh sách liên kết (vòng đơn):

![Mô tả thuật toán](https://i.imgur.com/qaqncbs.png)

Ý tưởng ở đây là:
 - Các node có giá trị lần lượt là 1, 2, 3 tương đương với BAO , BÚA , KÉO
 - Node phía trước sẽ trỏ tới node phía sau theo thứ tự BAO > BÚA > KÉO > BAO

## Các bước thực hiện

### Khởi tạo danh sách liên kết

Ở đây mình sử dụng danh sách liên kết vòng đơn nên khai báo như sau:

```c

#include <stdio.h>
#include <stdlib.h>
#include <conio.h>
#include <time.h>
// 1- bua : 2-keo: 3-bao
struct Node {
 //  struct Node *prev;
   int data;
   struct Node *next;
};
typedef struct Node Node;
Node *pHead, *pTail;

void init(){
    srand(time(NULL));//Khoi tao seed cho ham rand
    pHead = (Node *)malloc(sizeof(Node));//Bua
    pHead->data = 1;
    pHead->next = (Node *)malloc(sizeof(Node));//Keo
    pHead->next->data = 2;
    pTail = pHead->next->next = (Node *)malloc(sizeof(Node));//Bao
    pTail->data = 3;
    pTail->next = pHead;//tro ve Head
}

```

### Viết hàm chọn cho máy

Cái này rất đơn giản. Chỉ cần viết hàm random từ 1 đến 3.

```c
int computerChoose(){
    return rand() % 3 + 1; //random 1-3
}
```

### Viết hàm showMenu và showChoose

- hàm showMenu để hiển thị menu.
- hàm showChoose để chuyển 1-2-3 về BÚA, KÉO, BAO.

```c
void showMenu(){
    system("cls");//xóa màn hình
    printf("GAME OAN TU TI:\n");
    printf("1. Bua \n");
    printf("2. Keo \n");
    printf("3. Bao \n");
}
void showChoose(int value){
    switch(value){
        case 1: {
            printf("BUA");
            break;
        }
        case 2: {
            printf("KEO");
            break;
        }
        case 3: {
            printf("BAO");
            break;
        }
    }
}
```

### Viết hàm tìm kiếm node chứa lựa chọn

```c
Node *search(int value){
    Node *current = pHead;
    while(1){
        if(current->data == value) return current;
        if(current == pTail) return NULL;
        current = current->next;
    }
}
```

### Viết hàm xử lý kết quả

```c
int result(int player, int computer){
    if(computer == player) return 0;//Hòa
    else if(search(player)->next->data == computer) return 1;//Bạn thắng
    else return -1;//Máy thắng
}
```

## Full code

```c
int main()
{
    init();
    int player, computer, skip;
    do{
        showMenu();
        fflush(stdin);
        do{
            printf("\nLua chon cua ban: ");
            scanf("%d", &player);
        }while(player < 1 || player > 3);
        computer = computerChoose();

        printf("\nGAME OVER!\n");
        printf("Ban chon ");
        showChoose(player);
        printf(", may chon ");
        showChoose(computer);

        switch(result(player, computer)){
            case 1: {
                printf("\nBan thang.");
                break;
            }
            case 0: {
                printf("\nHoa.");
                break;
            }
            case -1: {
                printf("\nMay thang.");
                break;
            }
        }
        printf("\n\nBan co muon tiep tuc?\nChon 1 de tiep tuc, so khac de ket thuc: ");
        scanf("%d", &skip);
        if(skip != 1) break;
        else continue;
    }while(1);
    return 0;
}
```

