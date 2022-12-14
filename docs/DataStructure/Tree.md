# νΈλ¦¬(Tree)
*written by sohyeon, hyemin π‘*

<br>

## 1. νΈλ¦¬λ?
`νΈλ¦¬(tree)`λ κ·Έλνμ ν μ’λ₯λ‘, λ°μ΄ν° μ¬μ΄μ κ³μΈ΅ κ΄κ³λ₯Ό λνλ΄λ μλ£κ΅¬μ‘°λ₯Ό λ§νλ€.  
  
  <br>
  
  ## 2. νΈλ¦¬μ νΉμ§
  * κ·Έλνμ ν μ’λ₯λ‘, `μ΅μ μ°κ²° νΈλ¦¬`λΌκ³  νλ€.
  
  * νΈλ¦¬λ `κ³μΈ΅ λͺ¨λΈ`μ΄λ€.
  
  * νΈλ¦¬λ `DAG(Directed Acyclic Graphs, λ°©ν₯μ±μ΄ μλ λΉμν κ·Έλν)`μ ν μ’λ₯λ‘, `μ¬μ΄ν΄μ΄ μλ€.`   
  
  * λΈλκ° Nκ°μΈ νΈλ¦¬λ ν­μ `N-1κ°μ κ°μ (κ°μ§, edge)`μ κ°μ§λ€.  
  
  * `ν κ°μ λ£¨νΈ λΈλ`λ§μ΄ μ‘΄μ¬νλ©°, λͺ¨λ  μμ λΈλλ ν κ°μ λΆλͺ¨ λΈλλ§μ κ°μ§λ€. 
  
  * `λΆλͺ¨ - μμ κ΄κ³`μ΄λ―λ‘ νλ¦μ top-bottom μ΄λ bottom-topμΌλ‘ μ΄λ£¨μ΄μ§λ€.
  
  * μνλ `Pre-order(μ μ), In-order(μ€μ) μλλ©΄ Post-order(νμ)`λ‘ μ΄λ£¨μ΄μ§λ€.  
  
  * νΈλ¦¬μ μ’λ₯μλ `μ΄μ§ νΈλ¦¬, μ΄μ§ νμ νΈλ¦¬, κ· ν νΈλ¦¬(AVL νΈλ¦¬, red-black νΈλ¦¬), μ΄μ§ ν(μ΅λν, μ΅μν)` λ±μ΄ μλ€.  
  
  <br>

## 3. νΈλ¦¬ κ΄λ ¨ μ©μ΄
νΈλ¦¬λ₯Ό κ΅¬μ±νλ μμλ `λΈλ(node)` μ `κ°μ (κ°μ§, edge)`μ΄λ€.  
  
<img src="./resources/tree.jpg" width="600px">  
  
* **λ£¨νΈ λΈλ(root node)**   
νΈλ¦¬μ κ°μ₯ μλΆλΆμ μμΉνλ λΈλλ‘, 0κ° μ΄μμ μμ λΈλλ₯Ό κ°μ§κ³  μλ€.    
  
* **λ¨λ§ λΈλ(leaf node)**  
νΈλ¦¬μ κ°μ₯ μλ«λΆλΆμ μμΉνλ λΈλλ‘, λ μ΄μ λ»μ΄λκ° μ μλ λ§μ§λ§μ μμΉν λΈλλ₯Ό λ§νλ€.  
  
* **λ΄λΆ(internal) λΈλ**  
λ£¨νΈλ₯Ό ν¬ν¨νμ¬ λ¦¬νλ₯Ό μ μΈν λΈλλ‘, λ€λ₯Έ μ©μ΄λ‘ λμ΄ μλ λΈλ(non-terminal node)λΌκ³  νλ€.  
  
* **μμ λΈλ(child node)**  
μ΄λ€ λΈλλ‘λΆν° κ°μ μΌλ‘ μ°κ²°λ μλμͺ½ λΈλλ‘, λΈλλ μμμ μ¬λ¬ κ° κ°μ§ μ μλ€. μλ₯Ό λ€μ΄ Xλ 1κ°, Yλ 2κ°μ μμμ κ°μ§κ³  μλ€.  
  
* **λΆλͺ¨ λΈλ(Parent Node)**  
μ΄λ€ λΈλμμ κ°μ μΌλ‘ μ°κ²°λ μμͺ½ λΈλλ‘, λΈλλ 1κ°μ λΆλͺ¨λ₯Ό κ°μ§λ€. μλ₯Ό λ€μ΄ Yμ λΆλͺ¨λ Xμ΄λ€.  
  
* **νμ  λΈλ(Sibling Node)**  
κ°μ λΆλͺ¨λ₯Ό κ°μ§λ λΈλλ₯Ό λ§νλ€.  
  
* **μ‘°μ**  
μ΄λ€ λΈλμμ κ°μ μΌλ‘ μ°κ²°λ μμͺ½ λΈλ λͺ¨λλ₯Ό λ§νλ€.  
  
* **μμ**  
μ΄λ€ λΈλμμ κ°μ μΌλ‘ μ°κ²°λ μλμͺ½ λΈλ λͺ¨λλ₯Ό λ§νλ€.  
  
* **λΈλμ λ λ²¨(level)**  
λ£¨νΈλ‘λΆν° μΌλ§λ λ¨μ΄μ Έ μλμ§μ λν κ°μ λ§νλ€. λ£¨νΈμ λ λ²¨μ 0μ΄κ³  λ£¨νΈλ‘λΆν° κ°μ μ΄ νλμ© μλλ‘ λ»μ΄λκ° λλ§λ€ λ λ²¨μ΄ 1μ© λμ΄λλ€.  
   
* **λΈλμ ν¬κΈ°(size)**  
μμ μ ν¬ν¨ν λͺ¨λ  μμ λΈλμ κ°μλ₯Ό λ§νλ€. μλ₯Ό λ€μ΄ Xμ ν¬κΈ°λ 4μ΄λ€. 
  
* **λΈλμ κΉμ΄(depth)**  
λ£¨νΈμμ μ΄λ€ λΈλμ λλ¬νκΈ° μν΄ κ±°μ³μΌ νλ κ°μ μ μλ₯Ό λ§νλ€. μλ₯Ό λ€μ΄ Yμ κΉμ΄λ 2μ΄λ€.  
  
 * **νΈλ¦¬μ μ°¨μ(degree of tree)**  
 λΈλκ° κ°λ μμμ μλ₯Ό λ§νλ€. λν, λͺ¨λ  λΈλμ μ°¨μκ° n μ΄νμΈ νΈλ¦¬λ₯Ό nμ§ νΈλ¦¬λΌκ³  νλ€. μλ₯Ό λ€μ΄ κ·Έλ¦Όμ λͺ¨λ  λΈλμ μμμ΄ 3κ° μ΄νμ΄λ―λ‘ 3μ§ νΈλ¦¬μ΄λ€.  
   
* **νΈλ¦¬μ λμ΄(height)**  
λ£¨νΈλ‘λΆν° κ°μ₯ λ©λ¦¬ λ¨μ΄μ§ λ¦¬νκΉμ§μ κ±°λ¦¬λ₯Ό λ§νλ€.  

* **μλΈ νΈλ¦¬**  
νΈλ¦¬ μμμ λ€μ μ΄λ€ λΈλλ₯Ό λ£¨νΈλ‘ μ νκ³  κ·Έ μμμΌλ‘ μ΄λ£¨μ΄μ§ νΈλ¦¬λ₯Ό λ§νλ€.    
    
* **λ νΈλ¦¬**  
λΈλ, κ°μ μ΄ μλ νΈλ¦¬λ₯Ό λ§νλ€.  
  
* **μμ νΈλ¦¬μ λ¬΄μμ νΈλ¦¬**  
νμ  λΈλμ μμλ₯Ό λ°μ§λ©΄ μμ νΈλ¦¬(ordered tree), λ°μ§μ§ μμΌλ©΄ λ¬΄μμ νΈλ¦¬(unordered tree)λΌκ³  νλ€.  

<br>


## Reference & Additional Resources
<https://gmlwjd9405.github.io/2018/08/12/data-structure-tree.html/>

