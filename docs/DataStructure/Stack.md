# μ€ν (Stack)
*written by sohyeon, hyemin π‘*

<br>

## 1. μ€νμ΄λ?

`μ€ν`μ λ°μ΄ν°λ₯Ό μΌμμ μΌλ‘ μ μ₯νκΈ° μν μλ£κ΅¬μ‘°μ΄λ€.  
μμΆλ ₯ μμλ κ°μ₯ λμ€μ λ£μ λ°μ΄ν°λ₯Ό κ°μ₯ λ¨Όμ  κΊΌλ΄λ `νμμ μΆ`μ μμλ₯Ό λ°λ₯Έλ€.  

<img src="./resources/stack.jpg" width="400px">

    μλ° νλ‘κ·Έλ¨μμ λ©μλλ₯Ό νΈμΆνκ³  μ€νν  λ νλ‘κ·Έλ¨ λ΄λΆμμ μ€νμ μ¬μ©νλ€.  

## 2. μ€ν λ§λ€κΈ°

intν μλ£λ₯Ό μ μ₯νλ μ€νμ λ§λλ μμμ΄λ€.  

### 2-1. μ€ν λ³Έμ²΄

μ€ν λ³Έμ²΄μ λ°°μ΄μ΄λ€.
μΈλ±μ€κ° 0μΈ μμκ° μ€νμ `bottom`μ΄λ€.  
κ°μ₯ λ¨Όμ  `push`λ λ°μ΄ν°λ₯Ό μ μ₯νλ κ³³μ `stk[0]`μ΄λ€.  

```Java
class IntStack{
    int max;    // μ€ν μ©λ
    int ptr;    // μ€ν ν¬μΈν°
    int[] stk;  // μ€νμ λ³Έμ²΄
}
```

<img src="./resources/stack_ex.jpg" width="500px">

* max : μ€νμ μ©λ, μ€νμ μμ μ μλ μ΅λ λ°μ΄ν° μλ₯Ό λνλ΄λ νλ

* ptr : μ€νμ μμ¬ μλ λ°μ΄ν° μλ₯Ό λνλ΄λ νλ, μ€ν ν¬μΈν°

### 2-2. μμ±μ

```Java
public class IntStack{
    private int max;
    private int ptr;
    private int[] stk;

    // μ€ν μ μμΈ: μ€νμ΄ λΉμ΄ μμ
    public class EmptyIntStackException extends RuntimeException{
        public EmptyIntStackException(){}
    }
    // μ€ν μ μμΈ: μ€νμ΄ κ°λ μ°Έ
    public class OverflowIntStackException extends RuntimeException{
        public OverflowIntStackException(){}
    }

    // μμ±μ
    public IntStack(int capacity){
        ptr = 0;
        max = capacity;
        try{
            stk = new int[max];
        }catch(OutOfMemoryError e){
            max = 0;
        }
    }
}
```

μμ± μ μ€νμ λΉμ΄ μμΌλ―λ‘ μ€ν ν¬μΈν° ptrκ°μ 0μΌλ‘ νλ€.  
λ§€κ°λ³μ capacityλ‘ μ λ¬λ°μ κ°μ μ€ν μ©λμ λνλ΄λ maxμ λ³΅μ¬νκ³   
μμμκ° maxμΈ λ°°μ΄ stkμ λ³Έμ²΄λ₯Ό μμ±νλ€.  

### 2-3. λ©μλ

### 1) push

μ€νμ΄ κ°λμ°¨μ νΈμν  μ μλ κ²½μ° μμΈ `OverflowIntStackException`μ throwνλ€.  
μ λ¬λ°μ λ°μ΄ν°λ₯Ό λ£μ μ μμΌλ©΄ `stk[ptr]`μ μ μ₯νκ³ , μ€ν ν¬μΈν°λ₯Ό μ¦κ° μμΌμ€λ€.  
λ©μλμ λ°νκ°μ pushν κ°μ΄λ€.  

```Java
public int push(int x) throws OverflowIntStackException{
    if(ptr>=max)
        throw enw OverflowIntStackException();
    return stk[ptr++] = x;
}
```

### 2) pop

μ€νμ κΌ­λκΈ° κ°μ μ κ±°νκ³  κ·Έ κ°μ λ°ννλ€.  
μ€νμ΄ λΉμ΄ μμ κ²½μ° μμΈ `EmptyIntStackException`μ throwνλ€.  

```Java
public int pop() throws EmptyIntStackException{
    if(ptr<=0)
        throw new EmptyIntStackException();
    return stk[--ptr];
}
```

### 3) peek

μ€νμ κΌ­λκΈ°μ μλ κ°μ λ³΄λ λ©μλμ΄λ€.  
μ€νμ΄ λΉμ΄ μμ κ²½μ° μμΈ `EmptyIntStackException`μ throwνλ€.  
λ°μ΄ν°μ μλ ₯κ³Ό μΆμμ΄ μμΌλ―λ‘ μ€ν ν¬μΈν°λ λ³ννμ§ μλλ€.  

```Java
public int peek() throws EmptyIntStackException{
    if(ptr<=0)
        throw enw EmptyIntStackException();
    return stk[ptr - 1];
}
```

### 4) indexOf

μ€ν λ³Έμ²΄μ λ°°μ΄ stkμ xμ κ°μ κ°μ λ°μ΄ν°κ° ν¬ν¨λμ΄ μλμ§,  
ν¬ν¨λμ΄ μλ€λ©΄ λ°°μ΄μ μ΄λμ λ€μ΄ μλμ§λ₯Ό μ‘°μ¬νλ λ©μλμ΄λ€.  

κΌ­λκΈ° μͺ½μμ λ°λ₯ μͺ½μΌλ‘ μ ν κ²μμ μννλ€.  
κ²μμ μ±κ³΅νλ©΄ μ°ΎμλΈ μμμ μΈλ±μ€λ₯Ό λ°ν, μ€ν¨νλ©΄ -1μ λ°ννλ€.  

```Java
public int indexOf(int x){
    for(int i=ptr-1; i>=0; i--){
        if(stk[i] == x)
            return i
    }
    return -1
}
```

### 5) dump

μ€νμ μμ¬ μλ λͺ¨λ  λ°μ΄ν°λ₯Ό λ°λ₯μμ κΌ­λκΈ° μμΌλ‘ νμνλ λ©μλ

```Java
public void dump(){
    if(ptr<=0)
        System.out.println("μ€νμ΄ λΉμ΄ μμ΅λλ€.");
    else{
        for(int i=0; i<ptr; i++)
            System.out.println(skt[i]+" ");
        System.out.println();
    }
}
```

### 6) κ·Έ μΈ

* clear : μ€νμ λͺ¨λ  λ°μ΄ν°λ₯Ό μ­μ νλ λ©μλ

* capacity : μ©λμ νμΈνλ λ©μλ

* size : νμ¬ μ€νμ μμ¬μλ λ°μ΄ν° μλ₯Ό λ°ννλ λ©μλ

* isEmpty : μ€νμ΄ λΉμ΄ μλμ§ κ²μ¬νλ λ©μλ

* isFull : μ€νμ΄ κ°λ μ°Όλμ§ κ²μ¬νλ λ©μλ

```Java
public void clear(){
    ptr=0;
}

public int capacity(){
    return max;
}

public int size(){
    return ptr;
}

public boolean isEmpty(){
    return ptr<=0;
}

public boolean isFull(){
    return ptr >= max;
}
```

