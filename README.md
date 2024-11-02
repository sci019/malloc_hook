# mallocをLD_PRELOADでフックするコード
必要最低限のサンプルコードです。

## 実行手順
### ①フックAPIをコンパイル
```
gcc -fPIC -shared -o alloc_api.so alloc_api.c 
```

### ②テストコードをビルドし、実行  
```
gcc test.c -o test
LD_PRELOAD=./alloc_api.so ./test 
```

## 実行結果
* `API名、API呼び出し時刻、アドレス、確保サイズ` がログとして出力される
```
malloc,1730529137,0x555f5c03b2a0,1024 
```
