# ν (Queue)
*written by sohyeon, hyemin π‘*

<br>

## 1. νλ?

`ν`λ λ°μ΄ν°λ₯Ό μΌμμ μΌλ‘ μμ λκΈ° μν μλ£κ΅¬μ‘°μ΄λ€.  
μμΆλ ₯ μμλ κ°μ₯ λ¨Όμ  λ£μ λ°μ΄ν°λ₯Ό κ°μ₯ λ¨Όμ  κΊΌλ΄λ `μ μμ μΆ`κ΅¬μ‘°λ₯Ό λ°λ₯Έλ€.  

<img src="./resources/queue.jpg" width="300px">

    μνμμ λ³Ό μ μλ νμ μμλ‘λ,
    μν μ°½κ΅¬μμμ μ°¨λ‘λ₯Ό κΈ°λ€λ¦¬λ λκΈ°, λ§νΈ κ³μ°μ μν΄ κΈ°λ€λ¦¬λ λκΈ°μ΄μ λ€ μ μλ€.

## 2. λ°°μ΄λ‘ ν λ§λ€κΈ°

νλ λ°°μ΄μ μ¬μ©νμ¬ κ΅¬νν  μ μλ€. λ°°μ΄μ μ¬μ©ν νμ λν μμμ΄λ€.  

### 2-1. ν΄λμ€μ μμ±μ

```Java
public class IntQueue{
	private int max; // νμ μ©λ
	private int front; // λ§¨ μ μ»€μ
	private int rear; // λ§¨ λ€ μ»€μ
	private int num; // νμ¬μ λ°μ΄ν° μ
	private int[] que; // νμ λ³Έμ²΄

	// μ€νν  λ μμΈοΌνκ° λΉμ΄ μμ
	public class EmptyIntQueueException extends RuntimeException {
		public EmptyIntQueueException() {
		}
	}

	// μ€νν  λ μμΈοΌνκ° κ°λ μ°Έ
	public class OverflowIntQueueException extends RuntimeException {
		public OverflowIntQueueException() {
		}
	}

	// μμ±μ
	public IntQueue(int capacity) {
		num = front = rear = 0;
		max = capacity;
		try {
			que = new int[max]; // ν λ³Έμ²΄μ© λ°°μ΄μ μμ±
		} catch (OutOfMemoryError e) { // μμ±ν  μ μμ΅λλ€.
			max = 0;
		}
    }
}
```

μμ± μ νλ λΉμ΄ μμΌλ―λ‘ μ€ν ν¬μΈν° num, front, rear λͺ¨λ 0μΌλ‘ νλ€.   
λ§€κ°λ³μ capacityλ‘ μ λ¬λ°μ κ°μ μ€ν μ©λμ λνλ΄λ maxμ λ³΅μ¬νκ³    
μμμκ° maxμΈ λ°°μ΄ queμ λ³Έμ²΄λ₯Ό μμ±νλ€.  

### 2-2. λ©μλ

### 1) λ°μ΄ν° μΆκ°, μ­μ 

<img src="./resources/queue_ex.jpg" width="600px">

### λ°μ΄ν° μΆκ° - enque

rearμ λ°μ΄ν°κ° μ μ₯λ μμ λ€μμ λ°μ΄ν°λ₯Ό μΆκ°νλ λ©μλμ΄λ€.  
νκ° κ°λμ°¨μ enque ν  μ μλ κ²½μ° μμΈ `OverflowIntQueueException`μ throwνλ€.  
μ λ¬λ°μ λ°μ΄ν°λ₯Ό λ£μ μ μμΌλ©΄ `que[rear++]`μ μ μ₯νκ³ , νμ¬ λ°μ΄ν° μ numμ μ¦κ° μν¨λ€.  
λ©μλμ λ°νκ°μ enqueν κ°μ΄λ€.  

```Java
public int enque(int x) throws OverflowIntQueueException {
	if (num >= max)
		throw new OverflowIntQueueException(); // νκ° κ°λ μ°Έ
	que[rear++] = x;
	num++;
	if (rear == max)
		rear = 0;
	return x;
}
```

### λ°μ΄ν° μ­μ  - deque

frontμ μμΉν λ§¨ μμ μμλ₯Ό κΊΌλΈ λ€μ κ·Έ μ΄νμ μμλ₯Ό μμΌλ‘ μ?κΈ°λ λ©μλμ΄λ€.  
νκ° λΉμ΄ μμ΄ deque ν  μμκ° μλ κ²½μ° μμΈ `EmptyIntQueueException`μ throwνλ€.  

```Java
public int deque() throws EmptyIntQueueException {
	if (num <= 0)
		throw new EmptyIntQueueException(); // νκ° λΉμ΄ μμ
	int x = que[front++];
	num--;
	if (front == max)
		front = 0;
	return x;
}
```

### 3) κ·Έ μΈ

* peek : frontμ μλ κ°μ λ³΄λ λ©μλμ΄λ€.

* indexOf : λ°°μ΄ queμ xμ κ°μ κ°μ λ°μ΄ν°κ° ν¬ν¨λμ΄ μλμ§,  
            ν¬ν¨λμ΄ μλ€λ©΄ λ°°μ΄μ μ΄λμ λ€μ΄ μλμ§λ₯Ό μ‘°μ¬νλ λ©μλμ΄λ€.  

* clear : νμ λͺ¨λ  λ°μ΄ν°λ₯Ό μ­μ νλ λ©μλ

* capacity : μ©λμ νμΈνλ λ©μλ

* size : νμ¬ νμ μμ¬μλ λ°μ΄ν° μλ₯Ό λ°ννλ λ©μλ

* isEmpty : νκ° λΉμ΄ μλμ§ κ²μ¬νλ λ©μλ

* isFull : νκ° κ°λ μ°Όλμ§ κ²μ¬νλ λ©μλ

```Java
// νμμ λ°μ΄ν°λ₯Ό νΌν¬(λ¨Έλ¦¬λ°μ΄ν°λ₯Ό μ΄ν΄λ΄)
public int peek() throws EmptyIntQueueException {
	if (num <= 0)
		throw new EmptyIntQueueException(); // νκ° λΉμ΄ μμ
	return que[front];
}

// νμμ xλ₯Ό κ²μνμ¬ index(μ°Ύμ§ λͺ»νλ©΄ -1)λ₯Ό λ°ν
public int indexOf(int x) {
    for (int i = 0; i < num; i++) {
        int idx = (i + front) % max;
        if (que[idx] == x) // κ²μμ±κ³΅
            return idx;
    }
    return -1; // κ²μμ€ν¨
}

// νλ₯Ό λΉμ
public void clear() {
    num = front = rear = 0;
}

// νμ μ©λμ λ°ν
public int capacity() {
    return max;
}

// νμ μμΈ λ°μ΄ν° μλ₯Ό λ°ν
public int size() {
    return num;
}

// νκ° λΉμ΄ μλκ°?
public boolean isEmpty() {
    return num <= 0;
}

// νκ° κ°λ μ°Όλκ°?
public boolean isFull() {
    return num >= max;
}

// ν μμ ν°(μ΄ν°λ₯Ό λ¨Έλ¦¬βκΌ¬λ¦¬μ μ°¨λ‘λ‘ λνλ
public void dump() {
    if (num <= 0)
        System.out.println("νκ° λΉμμ΅λλ€.");
    else {
        for (int i = 0; i < num; i++)
            System.out.print(que[(i + front) % max] + " ");
        System.out.println();
    }
}
```

## 3. λ§ λ²νΌλ‘ ν λ§λ€κΈ°

`λ§ λ²νΌ`λ λ°°μ΄μ μ²μμ΄ λκ³Ό μ°κ²°λμ΄μλ μλ£κ΅¬μ‘°μ΄λ€.  
`λ§ λ²νΌ`λ₯Ό νμ©νλ©΄ λ°°μ΄μμλ₯Ό μμͺ½μΌλ‘ μ?κΈ°λ μμμ΄ λΆνμνλ€.  
λΌλ¦¬μ μΌλ‘ μ²«λ²μ§Έ μμμ λ§μ§λ§ μμλ₯Ό μλ³νκΈ° μν΄ `front`μ `rear`λ³μκ° μ‘΄μ¬νλ€.  

<img src="./resources/ring_buffer.jpg" width="600px">

* front : λ§¨ μ²μ μμμ μΈλ±μ€
* rear : λ§¨ λ μμμ νλ λ€μ μΈλ±μ€ (λ€μ μμλ₯Ό μΈνν  μμΉλ₯Ό λ―Έλ¦¬ μ§μ )

### 3-1. ν΄λμ€μ μμ±μ

```Java
public class IntQueue{
	private int max;      // νμ μ©λ
	private int front;    // μ²«λ²μ§Έ μμ μ»€μ
	private int rear;     // λ§μ§λ§ μμ μ»€μ
	private int num;      // νμ¬ λ°μ΄ν° μ
	private int[] que;    // ν λ³Έμ²΄

	// μ€ν μ μμΈ: νκ° λΉμ΄ μμ
	public class EmptyIntQueueException extends RuntimeException{
		public OverflowIntQueueException(){}
	}

	// μ€ν μ μμΈ : νκ° κ°λ μ°¨ μμ
	public class OverflowIntQueueException extends RuntimeException{
		public OverflowIntQueueException(){}
	}

	// μμ±μ
	public IntQueue(int capacity){
		num = front = rear = 0;
		max = capacity;
		try{
			que = new int[max];
		} catch(OutOfMemoryError e){
			max = 0;
		}
	}
}
```

- `front`μ `rear`μ κ°μ΄ κ°μ λ νμ μνλ λΉμ΄μκ±°λ κ°λμ°¬ μνμ΄λ€.  
   μ΄ μ‘°κ±΄λ§μΌλ‘ κ΅¬λΆμ ν  μ μλ€. 
- `front`μ `rear`μ κ°μ΄ κ°μ κ²½μ°, νμ μνλ₯Ό κ΅¬λΆνκΈ° μν΄ `num`λ³μλ₯Ό νμ©  
   νκ° λΉμμ λ `num`μ 0μ΄κ³  νκ° κ°λ μ°Όμλ `num`μ maxμ κ°κ³Ό κ°λ€.    

### 3-2. λ©μλ

### 1) enque

νμ λ°μ΄ν°λ₯Ό μΈννκ³  μΈνλ κ°μ λ°ννλ λ©μλμ΄λ€.  
rearμ μμΉμ μμλ₯Ό μΆκ°νκ³  rearμ numκ°μ 1λ§νΌ μ¦κ°νλ€.  

μΈννκΈ° μ  rearμ κ°μ΄ max-1 κ°μ΄λΌλ©΄ enque μν ν rearκ°μ΄ maxμ κ°μμ§κ² λλ λ¬Έμ κ° λ°μνλ€.  
μ΄λ₯Ό λ°©μ§νκΈ° μν΄ rearκ°μ΄ 1λ§νΌ μ¦κ°νμ λ maxμ κ°μμ§λ κ²½μ° rearλ₯Ό λ°°μ΄μ μ²μμΈ 0μΌλ‘ λ³κ²½νλ€.  

```Java
public int enque(int x) throws OverflowIntQueueException {
	if(num>=max)
		throw new OverflowIntQueueException();
	que[rear++] = x;
	num++;
	if(rear == max)
		rear = 0;
	return x;
}
```

### 2) deque

νμμ λ°μ΄ν°λ₯Ό λννκ³  κ·Έ κ°μ λ°ννλ λ©μλμ΄λ€.  
frontμ μ μ₯λ κ°μ κΊΌλ΄κ³  frontκ°μ 1λ§νΌ μ¦κ°ν λ€μ numμ 1λ§νΌ κ°μμν¨λ€.  

λννκΈ° μ  frontκ°μ΄ λ°°μ΄μ λμ΄λΌλ©΄ λν μν μ΄νμ frontκ°μ΄ maxκ° λλ λ¬Έμ κ° λ°μνλ€.  
μ΄λ₯Ό λ°©μ§νκΈ° μν΄ frontκ°μ΄ 1λ§νΌ μ¦κ°νμ λ maxμ κ°μμ§λ©΄ frontκ°μ λ°°μ΄μ μ²μμΈ 0μΌλ‘ λ³κ²½νλ€.  

```Java
public int deque() throws EmptyIntQueueException{
	if(num<=0)
		throw new EmptyIntQueueException();
	int x = que[front++];
	num--;
	if(front == max)
		front = 0;
	return x;
}
```

### 3) κ·Έ μΈ

```Java
// νμμ λ°μ΄ν°λ₯Ό νΌν¬ (νλ°νΈ λ°μ΄ν°λ₯Ό λ€μ¬λ€λ΄)
public int peek() throws EmptyIntQueueException {
	if (num <= 0)
		throw new EmptyIntQueueException();				// νκ° λΉμ΄ μμ
	return que[front];
}

// νμμ xλ₯Ό κ²μνμ¬ μΈλ±μ€(μ°Ύμ§ λͺ»νλ©΄ β1)λ₯Ό λ°ν
public int indexOf(int x) {
	for (int i = 0; i < num; i++) {
		int idx = (i + front) % max;
		if (que[idx] == x)								// κ²μ μ±κ³΅
			return idx;
	}
	return -1;											// κ²μ μ€ν¨
}

// νλ₯Ό λΉμ
public void clear() {
	num = front = rear = 0;
}

// νμ μ©λμ λ°ν
public int capacity() {
	return max;
}

// νμ μμ¬ μλ λ°μ΄ν° μλ₯Ό λ°ν
public int size() {
	return num;
}

// νκ° λΉμ΄ μλμ?
public boolean isEmpty() {
	return num <= 0;
}

// νκ° κ°λ μ°Όλμ?
public boolean isFull() {
	return num >= max;
}

// ν μμ λͺ¨λ  λ°μ΄ν°λ₯Ό νλ°νΈ β λ¦¬μ΄ μμΌλ‘ μΆλ ₯
public void dump() {
	if (num <= 0)
		System.out.println("νκ° λΉμ΄ μμ΅λλ€.");
	else {
		for (int i = 0; i < num; i++)
			System.out.print(que[(i + front) % max] + " ");
		System.out.println();
	}
}
```

## 4. λ±(μλ°©ν₯ λκΈ°μ΄, deque/double ended queue)

μμκ³Ό λ μ§μ , μμͺ½μμ λ°μ΄ν°λ₯Ό μΈννκ±°λ λννλ μλ£κ΅¬μ‘°μ΄λ€.  

<img src="./resources/deque.jpg" width="300px">

### λ± λ§λ€κΈ°

```Java
public class IntDeque {
	private int max; // λ±(deck)μ μ©λ
	private int num; // νμ¬μ λ°μ΄ν° μ
	private int front; // λ§¨ μ μ»€μ
	private int rear; // λ§¨ λ€ μ»€μ
	private int[] que; // λ±(deck)μ λ³Έμ²΄

	// μ€νν  λ μμΈοΌνκ° λΉμ΄ μμ
	public class EmptyIntDequeException extends RuntimeException {
		public EmptyIntDequeException() {
		}
	}

	// μ€νν  λ μμΈοΌνκ° κ°λ μ°Έ
	public class OverflowIntDequeException extends RuntimeException {
		public OverflowIntDequeException() {
		}
	}

	// μμ±μ
	public IntDeque(int capacity) {
		num = front = rear = 0;
		max = capacity;
		try {
			que = new int[max]; // λ±(deck)λ³Έμ²΄μ© λ°°μ΄μ μμ±
		} catch (OutOfMemoryError e) { // μμ±ν  μ μμ΅λλ€
			max = 0;
		}
	}

	// λ±(deck)μ λ°μ΄ν°λ₯Ό λ¨Έλ¦¬μͺ½λΆν° μΈν
	public int enqueFront(int x) throws OverflowIntDequeException {
		if (num >= max)
			throw new OverflowIntDequeException(); // λ±(deck)μ΄ κ°λ μ°Έ
		num++;
		if (--front < 0)
			front = max - 1;
		que[front] = x;
		return x;
	}

	// λ±(deck)μ λ°μ΄ν°λ₯Ό κΌ¬λ¦¬μͺ½λΆν° μΈν
	public int enqueRear(int x) throws OverflowIntDequeException {
		if (num >= max)
			throw new OverflowIntDequeException(); // λ±(deck)μ κ°λ μ°Έ
		que[rear++] = x;
		num++;
		if (rear == max)
			rear = 0;
		return x;
	}

	// λ±(deck)μ λ¨Έλ¦¬λΆν° λ°μ΄ν°λ₯Ό λν
	public int dequeFront() throws EmptyIntDequeException {
		if (num <= 0)
			throw new EmptyIntDequeException(); // λ±(deck)μ΄ λΉμ΄ μμ
		int x = que[front++];
		num--;
		if (front == max)
			front = 0;
		return x;
	}

	// λ±(deck)μ κΌ¬λ¦¬λΆν° λ°μ΄ν°λ₯Ό λν
	public int dequeRear() throws EmptyIntDequeException {
		if (num <= 0)
			throw new EmptyIntDequeException(); // λ±(deck)μ΄ λΉμ΄ μμ
		num--;
		if (--rear < 0)
			rear = max - 1;
		return que[rear];
	}

	// λ±(deck)μ λ¨Έλ¦¬λΆν° λ°μ΄ν°λ₯Ό νΌν¬(λ¨Έλ¦¬λ°μ΄ν°λ₯Ό μ΄ν΄λ΄)
	public int peekFront() throws EmptyIntDequeException {
		if (num <= 0)
			throw new EmptyIntDequeException(); // λ±(deck)μ΄ λΉμ΄ μμ
		return que[front];
	}

	// λ±(deck)μ κΌ¬λ¦¬λΆν° λ°μ΄ν°λ₯Ό νΌν¬(κΌ¬λ¦¬λ°μ΄ν°λ₯Ό μ΄ν΄λ΄)
	public int peekRear() throws EmptyIntDequeException {
		if (num <= 0)
			throw new EmptyIntDequeException(); // λ±(deck)μ΄ λΉμ΄ μμ
		return que[rear == 0 ? max - 1 : rear - 1];
	}

	// λ±(deck)μμ xλ₯Ό κ²μνμ¬ index(μ°Ύμ§ λͺ»νλ©΄ -1)λ₯Ό λ°ν
	public int indexOf(int x) {
		for (int i = 0; i < num; i++)
			if (que[(i + front) % max] == x) // κ²μμ±κ³΅
				return i + front;
		return -1; // κ²μμ€ν¨
	}

	// λ±(deck)μμ xλ₯Ό κ²μνμ¬ λ¨Έλ¦¬λΆν° λͺ λ² μ§ΈμΈκ°(μ°Ύμ§ λͺ»νλ©΄ 0)λ₯Ό λ°ν
	public int search(int x) {
		for (int i = 0; i < num; i++)
			if (que[(i + front) % max] == x) // κ²μμ±κ³΅
				return i + 1;
		return 0; // κ²μμ€ν¨
	}

	// λ±(deck)μ λΉμ
	public void clear() {
		num = front = rear = 0;
	}

	// λ±(deck)μ μ©λμ λ°ν
	public int capacity() {
		return max;
	}

	// λ±(deck)μ μμΈ λ°μ΄ν° μλ₯Ό λ°ν
	public int size() {
		return num;
	}

	// λ±(deck)μ΄ λΉμ΄ μλκ°?
	public boolean isEmpty() {
		return num <= 0;
	}

	// λ±(deck)μ΄ κ°λ μ°Όλκ°?
	public boolean isFull() {
		return num >= max;
	}

	// λ±(deck)λ΄μ λ°μ΄ν°λ₯Ό λ¨Έλ¦¬βκΌ¬λ¦¬μ μ°¨λ‘λ‘ λνλ
	public void dump() {
		if (num <= 0)
			System.out.println("λ±(deck)μ΄ λΉμμ΅λλ€.");
		else {
			for (int i = 0; i < num; i++)
				System.out.print(que[(i + front) % max] + " ");
			System.out.println();
		}
	}
}
```
