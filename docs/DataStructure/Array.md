# λ°°μ΄ (Array)
*written by sohyeon, hyemin π‘*

<br>

## 1. λ°°μ΄μ΄λ?  

κ°μ μλ£νμ κ΅¬μ±μμκ° μ§μ λͺ¨μμΌλ‘ μ°μνμ¬ μ€μ§μ΄ μλ λ¨μν μλ£κ΅¬μ‘° μ΄λ€.  

### ex) μ¬μ© μμ

```Java
// λκ°μ§ μ μΈ λ°©λ²μ΄ μμ
int[] a;
int a[];

// λ°°μ΄ μμ±
a = new int[5];

a[1] = 37;
a[2] = 20;
a[3] = 11;
a[4] = 1;

for(int i=0; i<a.length; i++)
    System.out.println("a["+i+"]="+a[i]);
```

### μΆλ ₯ κ²°κ³Ό
```
a[0] = 0 
a[1] = 37
a[2] = 20
a[3] = 11
a[4] = 1
```
`new int[5]`λ‘ λ°°μ΄ λ³Έμ²΄λ₯Ό μμ±νκ³  λ³μ aκ° λ°°μ΄ λ³Έμ²΄λ₯Ό μ°Έμ‘°νλ€.

μΆλ ₯ κ²°κ³Όλ₯Ό λ³΄λ©΄ a[0]μ κ°μ λμνμ§ μμμ§λ§ μλμΌλ‘ 0 κ°μ΄ λμλμ΄ μλ κ²μ λ³Ό μμλ€.  
λ°°μ΄μ΄ μμ±λλ©΄ μλμΌλ‘ κ° μμλ€μ΄ 0μΌλ‘ μ΄κΈ°ν λλ€.  

λν λ°°μ΄ aμ μλ£νκ³Ό a[i] (iλ μμμ indexκ°)μ μλ£νμ λ€λ₯΄λ€λ κ²μ μμλμ.
λ°°μ΄ aλ int[5]ν μλ£ν, μ΄ 5κ°μ intν μ μ₯κ³΅κ°μ μ°¨μ§νλ κ²μ΄κ³ 
a[i]λ intν μλ£νμ κ°λλ€.

## 2. λ©μλ

* λ°°μ΄ λ³μ μ΄λ¦.length : κΈΈμ΄λ₯Ό κ΅¬νλ€.

* λ°°μ΄ μ΄λ¦.clone() : λ°°μ΄μ λ³΅μ νλ€.

* maxOf(λ°°μ΄ μ΄λ¦) : λ°°μ΄ κ΅¬μ±μμ μ€ μ΅λ κ°μ κ΅¬νλ€.


