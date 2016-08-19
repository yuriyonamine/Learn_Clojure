Learn_Clojure
=============
Repository to learn and test Clojure functional language.

Summary
=============

* **Functions must to be between parentheses**

* **Calling a sum function. First is the operator or the function name followed by parameters (in this case, 2)**
    ```clojure
    (+ n1 n2) 
    ```
 
* **Defining a new var called 'age' with 65 as a value**
    ```clojure
    (def age 65)
    ```
 
* **Defining a new function called 'xxxx' that receive 2 parameters ('var1', 'var2') and between parentheses it is the processing function.**
    ```clojure
    (defn xxxx [var1 var2] (+ var1 var2))
    ```
* **Defining a function without parameters**
    ```clojure
    (defn xxxx [] (println "test"))  
    ```
    
* **Calling previous declared function**
    ```clojure
    (xxxx)  
    ```
    
* **IF statement**
    ```clojure
    (if (= age 200)
        (println "Congrats. You are the oldest people in the world"))  
    ```
    
* **Multiple 'IFs' can be replaced by 'COND' statement**
    ```clojure
    (cond                   ;Equals 'case' statement of java
		(= up 0) (lose)      ;Case up = 0, call 'lose' function
		(is-the-boss-dead?) (win) ;Case function is-the-boss-dead return true, call 'win' function
		:else (keep-trying) ;Other case, call 'keep-trying' function
    ```
    
    
    
* **Best practices**
    
    **Close parentheses at the end of the last block line**
    ```clojure
    (defn jogo [vidas palavra acertos] 
	
	(cond 
		(= vidas 0)(perdeu)
		(acertou-a-palavra-toda? palavra acertos)(ganhou)
		:else
		(let [chute (le-letra!)]
			(if(acertou? chute palavra)
				(do
					(println "Acertou a letra!") 
					(recur vidas palavra (conj acertos chute))) ;HERE
				(do
					(println "Errou a letra e perdeu 1 vida!")
					(recur (dec vidas) palavra acertos)))))) ;HERE

    ```
    
