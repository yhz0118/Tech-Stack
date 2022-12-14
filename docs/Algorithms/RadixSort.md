# ๊ธฐ์ ์ ๋ ฌ (Radix Sort)
*written by sohyeon, hyemin ๐ก*

<br>

## 1. ๊ธฐ์ ์ ๋ ฌ์ด๋?

`๊ธฐ์ ์ ๋ ฌ`์ ๋ฎ์ ์๋ฆฌ์๋ถํฐ ๋น๊ตํ์ฌ ์ ๋ ฌํด ๊ฐ๋ค๋ ๊ฒ์ ๊ธฐ๋ณธ ๊ฐ๋์ผ๋ก ํ๋ ์ ๋ ฌ ์๊ณ ๋ฆฌ์ฆ์ด๋ค.  
๊ธฐ์ ์ ๋ ฌ์ ์๋ ฅ ๋ฐ์ดํฐ์ ๋ํด์ ์ด๋ค ๋น๊ต ์ฐ์ฐ๋ ์คํํ์ง ์๊ณ  ๋ฐ์ดํฐ๋ฅผ ์ ๋ ฌํ  ์ ์๋ ์๋ค๋ฅธ ์ ๋ ฌ ๊ธฐ๋ฒ์ด๋ค.  

<br>

## 2. ๋์ ๋ฐฉ์

<img src="./resources/RadixSort.jpeg" height="400px">

`10๊ฐ์ ๋ฒ์ผ(bucket)`์ ๋ง๋ค์ด์ ์๋ ฅ ๋ฐ์ดํฐ๋ฅผ ์ผ์ ์๋ฆฟ์๋ถํฐ ๊ฐ ์๋ฆฟ์์ ๊ฐ์ ๋ฐ๋ผ ๋ฒ์ผ์ ๋ฃ๋๋ค.  
๊ทธ๋ฆฌ๊ณ  ์์์๋ถํฐ ์๋๋ก ์์ฐจ์ ์ผ๋ก ๋ฒ์ผ ์์ ๋ค์ด ์๋ ์ซ์๋ค์ ์ฝ์์ผ๋ก์จ ์ ๋ ฌ๋ ์ซ์ ๋ฆฌ์คํธ๋ฅผ ์ป์ ์ ์๋ค.  

<br>

## 3. ํน์ง

### 1) ์ฅ์ 
- ์๋ฆฟ์๊ฐ ๊ณ ์ ๋์ด ์์ด ์์ ์ ์ด๋ค.  
- ๋ฐ์ดํฐ ๊ฐ์ ์๋์  ์์๊ฐ ๋ณด์กด๋๋ stable ์ ๋ ฌ์ด๋ค.  
- ๋น๊ต์ฐ์ฐ์ ํ์ง ์๋๋ค. 

### 2) ๋จ์ 
- ์๋ฆฟ์๊ฐ ์๋ ๋ฐ์ดํฐ๋ ์ ๋ ฌํ์ง ๋ชปํ๋ค.  
- ์ถ๊ฐ์ ์ธ ์ ์ฅ ๊ณต๊ฐ์ด ํ์ํ๋ค.  

<br>

## 4. ์๊ฐ๋ณต์ก๋

- ๊ฐ์ฅ ํฐ ๋ฐ์ดํฐ์ ์๋ฆฌ ์ ๋งํผ ์์ ํ ์ ๋ ฌ ๊ณผ์ ์ด ๋ฐ๋ณต๋๋ค.  
```
RadixSort(A,d)
    for i=1 to d
        StableSort(A) on digit i
        
๋ฐ๋ผ์, T(n) = O(dn)
```

<br>

## 5. ๊ธฐ์ ์ ๋ ฌ Java ์ฝ๋
#### ex) ์์ 
```
// ๊ธฐ์ ์ ๋ ฌ 
import java.io.*; 
import java.util.*; 

class Radix { 
    // ๋ฐฐ์ด arr์์ ์ต๋๊ฐ์ ์ป๊ธฐ ์ํ ๋ฉ์๋
    static int getMax(int arr[], int n) { 
        int mx = arr[0]; 
        for (int i = 1; i < n; i++) 
        if (arr[i] > mx) 
            mx = arr[i]; 
        return mx; 
    } 

    // ๊ฐ ์๋ฆฟ์์ ๊ฐ์ ๋ฐ๋ผ ์ ๋ ฌํ๋ ๋ฉ์๋ 
    static void countSort(int arr[], int n, int exp) { 
        int output[] = new int[n]; // ๊ฒฐ๊ณผ ๋ฐฐ์ด 
        int i; 
        int count[] = new int[10]; 
        Arrays.fill(count,0); 

        // Store count of occurrences in count[] 
        for (i = 0; i < n; i++) 
            count[ (arr[i]/exp)%10 ]++; 

        for (i = 1; i < 10; i++) 
            count[i] += count[i - 1]; 

        for (i = n - 1; i >= 0; i--) { 
            output[count[ (arr[i]/exp)%10 ] - 1] = arr[i]; 
            count[ (arr[i]/exp)%10 ]--; 
        } 

        for (i = 0; i < n; i++) 
            arr[i] = output[i]; 
    } 

    // ๊ธฐ์ ์ ๋ ฌ 
    static void radixsort(int arr[], int n) { 
        // ์ต๋๊ฐ์ ์๋ฆฟ์๋ฅผ ์ฐพ๋๋ค.
        int m = getMax(arr, n);     
        for (int exp = 1; m/exp > 0; exp *= 10) 
            countSort(arr, n, exp); 
    } 

    // ๋ฐฐ์ด์ ์ถ๋ ฅํ๊ธฐ ์ํ ๋ฉ์๋ 
    static void print(int arr[], int n) { 
        for (int i=0; i<n; i++) 
            System.out.print(arr[i]+" "); 
    } 

    // ๊ธฐ์ ์ ๋ ฌ์ ์คํํ๋ ๋ฉ์ธ
    public static void main (String[] args) { 
        int arr[] = {170, 45, 75, 90, 802, 24, 2, 66}; 
        int n = arr.length; 
        radixsort(arr, n);  
        print(arr, n); 
    } 
} 

```

<br>

## Reference & Additional Resources
* C์ธ์ด๋ก ์ฝ๊ฒ ํ์ด์ด ์๋ฃ ๊ตฌ์กฐ  

* [Radix Sort](https://www.geeksforgeeks.org/radix-sort/)

