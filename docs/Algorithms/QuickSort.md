# ํต ์ ๋ ฌ (Quick Sort)
*written by sohyeon, hyemin ๐ก*

<br>

## 1. ํต ์ ๋ ฌ์ด๋?

์ผ๋ฐ์ ์ผ๋ก ์ฌ์ฉ๋๊ณ  ์๋ ์์ฃผ ๋น ๋ฅธ ์ ๋ ฌ ์๊ณ ๋ฆฌ์ฆ์ด๋ค.  
์ ๋ ฌ ์๋๊ฐ ๋น ๋ฅธ ๋ฐ์ ์ฐฉ์ํด `ํต` ์ ๋ ฌ ์ด๋ผ๋ ์ด๋ฆ์ด ๋ถ์ฌ์ก๋ค.  
๋ค๋ฅธ ์์์์ ๋น๊ต๋ง์ผ๋ก ์ ๋ ฌ์ ์ํํ๋ ์๊ณ ๋ฆฌ์ฆ์ด๋ค.  

## 2. ๋์ ๋ฐฉ์

๋์์ ์ํํ  ๋ ๊ฐ ๊ทธ๋ฃน์ ๋ํด `pivot`์ค์ ๊ณผ ๊ทธ๋ฃน ๋๋์ ๋ฐ๋ณตํ๊ฒ ๋๋ฉฐ  
๋ชจ๋  ๊ทธ๋ฃน์ด 1๋ช์ด ๋๋ฉด ์ ๋ ฌ์ ๋ง์น๊ฒ ๋๋ค.  

์ด ๊ณผ์ ์ ๋ถํ ์ ๋ณต (Divide and Conquer)์ด๋ผ๊ณ  ํ๋ค.  

### 1) Divide and Conquer

-	Divide (PARTITION๊ณผ์ )   
    
    ์ ๋ ฌ ํด์ผ ํ  ๋ฆฌ์คํธ ์์ ์๋ ํ ์์๋ฅผ ์ ํํด pivot์ผ๋ก ์ง์ ,  
    pivot์ ๊ธฐ์ค์ผ๋ก ์์ ์์๋ค์ ์ผ์ชฝ, ํฐ ์์๋ค์ ์ค๋ฅธ์ชฝ์ผ๋ก ์ด๋  

-	Conquer  
    
    pivot์ ์ ์ธํ ์ผ์ชฝ, ์ค๋ฅธ์ชฝ ๋ฆฌ์คํธ๋ฅผ ๋ค์ ์ ๋ ฌ  
    ๋ถํ ๋ ๋ถ๋ถ ๋ฆฌ์คํธ์ ๋ํด ๋ค์ pivot์ ์ง์ ํ๊ณ   
    2๊ฐ์ ๋ถ๋ถ๋ฆฌ์คํธ๋ก ๋๋๋ ๊ณผ์  ๋ฐ๋ณต  

- Pivot ์ค์ 

<img src="./resources/pivot.jpg" width="500px" style="margin-left: 40px">

### 2) ๋์ ๊ณผ์ 

<img src="./resources/QuickSort.jpg" width="600px">

-	์์์ ํ ์์๋ฅผ pivot์ผ๋ก ์ ํ
-	Pivot์ ๊ธฐ์ค์ผ๋ก ์์ ๊ฐ์ ์ผ์ชฝ, ํฐ ๊ฐ์ ์ค๋ฅธ์ชฝ์ผ๋ก ์ด๋
-	Pivot์ ์ ์ธํ ์ผ์ชฝ, ์ค๋ฅธ์ชฝ ๋ฆฌ์คํธ์ partition๊ณผ์  ๋ฐ๋ณต
-	์์ ๊ณผ์ ์ ๋ฐ๋ณตํด ๊ฐ๊ฐ ๋ถํ ๋ ๋ฆฌ์คํธ์ ํฌ๊ธฐ๊ฐ 0์ด๋ 1์ด ๋๋ฉด ์ ๋ ฌ์ด ๋๋จ

## 3. ํน์ง

### 1) ์ฅ์ 

- ํ๊ท ์ ์ผ๋ก ๋น ๋ฅธ ์ํ ์๋๋ฅผ ๊ฐ์ง

### 2) ๋จ์ 

- Unstableํ ์ ๋ ฌ์

## 4. ์๊ฐ ๋ณต์ก๋

์๋ ฅ๋๋ ์๋ฃ์ ๋ฐ๋ผ ์๊ฐ๋ณต์ก๋๊ฐ ๋ฌ๋ผ์ง ์ ์๋ค.

### 1) Worst Case

์์ ํ๊ฒ ํ์ชฝ์ผ๋ก ๋ชฐ๋ ค ๊ทธ๋ฃน์ด ๋๋๋ ๊ฒฝ์ฐ,  
left๊ฐ n-1๊ฐ์ ์์๋ฅผ ๊ฐ๊ณ  right๊ฐ 0๊ฐ์ ์์๋ฅผ ๊ฐ์ง ๋  

<img src="./resources/Quick_worst.jpg" width="400px">

```
T(n)=1+2+โฏ+n-1+n=n(n-1)/2
โดT(n)=O(n^2)
```

### 2) Best Case

pivot๊ฐ์ด ๊ณ์ ์ค์์ ์์ฑํด left, right๊ฐ ๊ท ๋ฑํ๊ฒ ๋๋  ๋  

<img src="./resources/quick_best_pivot.jpg" width="300px">

```
T(n) = 2T(n/2)+O(n) ( O(n)์ Divide๊ณผ์  )
```

<img src="./resources/quick_best.jpg" width="700px">

```
โดT(n)=O(nlog_2โกn)
```

### 3) Average Case

best case์ ๋ณดํต ๊ฐ๊น์  

- ์ผ์ ํ ๋น์จ๋ก ๋ถํ  ๋๋ค๋ฉด O(nlog_2โกn )์ ์๊ฐ ๋ณต์ก๋๋ฅผ ๊ฐ์ง  

- ๊ทน๋จ์ ์ด๊ฒ ๋ถํ ๋๋ ๋น์จ์ด ์น์ฐ์น ๊ฒฝ์ฐ์๋ ๋์ผํจ  

<img src="./resources/quick_average.jpg" width="700px">

<img src="./resources/quick_average_bigo1.jpg" width="200px">

์๋ ์ฆ๋ช์ ์ํด log_2n์ผ๋ก ํํ์ด ๊ฐ๋ฅํ๋ค.

<img src="./resources/quick_average_bigo2.jpg" width="200px">

๋ฐ๋ผ์ T(n)์ ์๋์ ๊ฐ์ด ๊ตฌํ  ์ ์๋ค.

<img src="./resources/quick_average_bigo3.jpg" width="200px">

## 4. ์์  ์ฝ๋

```Java
import java.util.Scanner;
// ํต ์ ๋ ฌ

class QuickSort {
	// ๋ฐฐ์ด ์์ a[idx1]๊ณผ a[idx2]์ ๊ฐ์ ๋ฐ๊ฟ๋๋ค.
	static void swap(int[] a, int idx1, int idx2) {
		int t = a[idx1];  a[idx1] = a[idx2];  a[idx2] = t;
	}

	// ํต ์ ๋ ฌ
	static void quickSort(int[] a, int left, int right) {
		int pl = left;					// ์ผ์ชฝ ์ปค์
		int pr = right;					// ์ค๋ฅธ์ชฝ ์ปค์
		int x = a[(pl + pr) / 2];		// ํผ๋ฒ

		do {
			while (a[pl] < x) pl++;
			while (a[pr] > x) pr--;
			if (pl <= pr)
				swap(a, pl++, pr--);
		} while (pl <= pr);

		if (left < pr)  quickSort(a, left, pr);
		if (pl < right) quickSort(a, pl, right);
	}

	public static void main(String[] args) {
		Scanner stdIn = new Scanner(System.in);

		System.out.println("ํต ์ ๋ ฌ");
		System.out.print("์์์๏ผ");
		int nx = stdIn.nextInt();
		int[] x = new int[nx];

		for (int i = 0; i < nx; i++) {
			System.out.print("x[" + i + "]๏ผ");
			x[i] = stdIn.nextInt();
		}

		quickSort(x, 0, nx - 1);			// ๋ฐฐ์ด x๋ฅผ ํต ์ ๋ ฌ

		System.out.println("์ค๋ฆ์ฐจ์์ผ๋ก ์ ๋ ฌํ์ต๋๋ค.");
		for (int i = 0; i < nx; i++)
			System.out.println("x[" + i + "]๏ผ" + x[i]);
	}
}
```
