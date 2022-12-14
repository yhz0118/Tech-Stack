# OSI 7 κ³μΈ΅

*written by sohyeon, hyemin π‘*

<br>

## 1. OSI 7κ³μΈ΅ μ΄λ?

OSIλ, κ°λ°©ν μμ€ν μνΈμ°κ²° λͺ¨λΈλ‘μ, μμ€ν μνΈ μ°κ²°μ μμ΄ κ°λ°© λͺ¨λΈμ λ»νλ€.  
μνΈ μ΄μ§μ μΈ λ€νΈμν¬κ°μ μ°κ²°μ μ΄λ €μμ΄ λ§μλ° μ΄λ¬ν νΈνμ±μ κ²°μ¬λ₯Ό λ§κΈ°μν΄ ISOμμ μ μν λͺ¨λΈμ΄λ€.  

μ½κ² λ§ν΄ λ€νΈμν¬ ν΅μ  κ³Όμ μ 7λ¨κ³λ‘ λλ κ²μ΄λ€.  

![OSI 7 κ³μΈ΅](./resources/OSI7layer.jpg)

## 7κ³μΈ΅ - μμ© κ³μΈ΅ (Application Layer)

μ¬μ©μκ° λ€νΈμν¬μ μ κ·Όν  μ μλλ‘ ν΄μ£Όλ κ³μΈ΅μ΄λ€.  
μ¬μ©μ μΈν°νμ΄μ€, μ μμ°νΈ, λ°μ΄ν°λ² μ΄μ€ κ΄λ¦¬ λ± **μλΉμ€**λ₯Ό μ κ³΅νλ€.  

* ### νλ‘ν μ½ μ’λ₯

* SMTP
* DNS
* FTP
* HTTP  ...  

## 6κ³μΈ΅ - νν κ³μΈ΅ (Presentation Layer)

μ΄μμ²΄κ³μ ν λΆλΆμΌλ‘ μλ ₯ λλ μΆλ ₯λλ λ°μ΄ν°λ₯Ό νλμ νν ννλ‘ λ³ννλ€.  
νμν λ²μ­μ μννμ¬ λ μ₯μΉκ° μΌκ΄λκ² μ μ‘ λ°μ΄ν°λ₯Ό μλ‘ μ΄ν΄ν  μ μλλ‘ νλ€.  
μ μ΄μ½λλ λ¬Έμ λ° κ·Έλν½ λ±μ νμ₯μλ₯Ό μκ°νλ©΄ μ½λ€.  

* ### νλ‘ν μ½ μ’λ₯

* JPEG
* MPEG
* SMB
* AFP ...  

## 5κ³μΈ΅ - μΈμ κ³μΈ΅ (Session Layer)

ν΅μ μ₯μΉ κ°μ μνΈμμ©μ μ€μ νκ³  μ μ§νλ©° λκΈ°ννλ€.  
μ¬μ©μκ°μ ν¬νΈμ°κ²°(μΈμ)μ΄ μ ν¨νμ§ νμΈνκ³  μ€μ νλ€.
ν΅μ μ μν λΌλ¦¬μ μΈ μ°κ²° λ¨κ³λ‘ TCP/IP μΈμμ λ§λ€κ³  μμ λ μ±μμ μ§

* ### νλ‘ν μ½ μ’λ₯

* SSH
* TLS ...  
 
## 4κ³μΈ΅ - μ μ‘ κ³μΈ΅ (Transport Layer)

μ μ²΄ λ©μμ§λ₯Ό λ°μ μ§ λ λͺ©μ μ§(μ’λ¨ λ μ’λ¨)κ° μ μ΄μ μλ¬λ₯Ό κ΄λ¦¬νλ€.  
ν¨ν·λ€μ μ μ‘μ΄ μ ν¨νμ§ νμΈνκ³  μ€ν¨ν ν¨ν·μ λ€μ λ³΄λ΄λ λ± μ λ’°μ±μλ ν΅μ μ λ³΄μ₯νλ©°,
ν€λ λΆλΆμ **μΈκ·Έλ¨ΌνΈ**λ₯Ό ν¬ν¨νλ€.
λ³΄λ΄κ±°λ/λ°λ νλ‘μΈμ€λ₯Ό μλ³νκΈ° μν΄ λΆκ° λ°μ΄ν°(Port)λ₯Ό μΆκ°νλ€.

* ### νλ‘ν μ½ μ’λ₯

* TCP
* UDP ...  

## 3κ³μΈ΅ - λ€νΈμν¬ κ³μΈ΅ (Network Layer)

λ€μ€ λ€νΈμν¬ λ§ν¬μμ **ν¨ν·**μ λ°μ μ§λ‘λΆν° λͺ©μ μ§λ‘ μ λ¬ν  μ±μμ κ°λλ€.  
λ°μ΄ν°λ₯Ό λͺ©μ μ§κΉμ§ κ°μ₯ μμ νκ³  λΉ λ₯΄κ² μ λ¬νκΈ° μν λΌμ°ν κΈ°λ₯.  
IP μ£Όμλ₯Ό μ νκ³  κ²½λ‘μ λ°λΌ ν¨ν·μ μ λ¬ν΄μ€λ€.  

    - HTTP packet
    
    HTTP νλ‘ν μ½μ μ΄μ©ν κ²½μ° λ³΄λ΄λ λ°μ΄ν°λ₯Ό HTTP packet μ΄λΌκ³  νλ€.  
    HTTP packetμ κ΅¬μ‘°λ ν¬κ² Header μ Body λ‘ λλμ΄μ§λ€.  
    Headerμλ λ©μΈμ§λ₯Ό λ³΄λ΄κΈ° μν΄ 7κ°μ§ HTTP Method μ€ λ¬΄μμ μ¬μ©νλμ§,  
    ν΄λΌμ΄μΈνΈ μ λ³΄, λΈλΌμ°μ  μ λ³΄, μ μν  URL λ±κ³Ό κ°μ ν΄λΌμ΄μΈνΈ μ λ³΄λ₯Ό λ΄λλ€.   
    Bodyλ λ³΄ν΅ λΉμ΄ μμ§λ§ νΉμ  λ°μ΄ν°λ₯Ό λ΄μμ μλ²μ μμ²­μ λ³΄λΌ μ μλ€.  
    μκΈ°μ κ°λ μλ, λ³΄ν΅ μΉμμλ HTTPμ MethodμΈ GETκ³Ό POSTλ₯Ό ν΅ν΄ μμ²­νλ€.  

* ### νλ‘ν μ½ μ’λ₯

* IP
* ICMP
* IGMP ...  

## 2κ³μΈ΅ - λ°μ΄ν°λ§ν¬ κ³μΈ΅ (Datalink Layer)

μ€λ₯μμ΄ ν μ₯μΉμμ λ€λ₯Έ μ₯μΉλ‘ νλ μμ μ λ¬νλ μ­ν μ νλ€.  
μ€μμΉκ°μ μ₯λΉμ κ²½μ° MACμ£Όμλ₯Ό μ΄μ©νμ¬ μ νν μ₯μΉλ‘ μ λ³΄λ₯Ό μ λ¬νλ€.
3κ³μΈ΅μμ μ λ³΄λ₯Ό λ°μ μ£Όμμ μ μ΄μ λ³΄λ₯Ό μμκ³Ό λμ μΆκ°νλ€.
   
    IP μ£Όμλ νλμ νΈμ€νΈλ₯Ό λνλ΄λ μ£Όμμ§λ§, MAC μ£Όμλ νΈμ€νΈμ μ°κ²°λ λ¬Όλ¦¬μ  ν΅μ  μ₯μΉ νλλ₯Ό λνλ΄λ μ£Όμμ΄λ€.   
    λ°λΌμ MAC μ£Όμλ IP μ£Όμμ λ¬λ¦¬ μ μΌν λΆλ³κ°μ΄λ€.  

* ### νλ‘ν μ½ μ’λ₯

* Ethernet ...  

## 1κ³μΈ΅ - λ¬Όλ¦¬ κ³μΈ΅ (Physical Layer)

λ¬Όλ¦¬μ  λ§€μ²΄λ₯Ό ν΅ν΄ λΉνΈ νλ¦μ μ μ‘νκΈ° μν΄ μκ΅¬λλ κΈ°λ₯λ€μ μ‘°μ νλ€.  
λ¨μν ν΅μ  μΌμ΄λΈλ‘ λ°μ΄ν°λ₯Ό μ£Όκ³ λ°λ μ­ν μ νλ€.  

* ### νλ‘ν μ½ μ’λ₯

* μ μ , μ ν  
* κ΄μ¬μ , λμΆ μΌμ΄λΈ ...