#Learn_Clojure
Repository to learn and test Clojure functional language.

---

##Summary
* **It is immutable (Once the variable is defined, you can't change the state)**
* nil -> same as null(Java)
* **Methods always has a return. If there is no return defined in your method, when invoking it, it will return nil**
* **Everytime you edit .clj files, you will need to reload it in order to changes to be seen. You can simply stop and start the application again or use the following command: (require '[yourFile.core] :reload)
* **Functions must to be between parentheses**

* **Calling a sum function. First is the operator or the function name followed by parameters (in this case, 2)**
    ```clojure
    (+ n1 n2) 
    ```
 
* **Defining a new var called 'age' with 65 as a value**
    ```clojure
    (def age 65)
    ```
* **In general, the functions that return a boolean has a '?' at the end of declaration**
    ```clojure
    (defn is-old? [age] (age > 150))	;Declaring the boolean function
    (if (is-old?)	;Calling the boolean function
    	(print "You are very old"))
    ```
 
 * **Functions that changes state, there are any collateral effects (Depends on some resource like input of a keyboard) that affect the return of a function, has a '!' at the end of declaration**
    ```clojure
    (defn read-char! [] (read-line))	;Declaring the read-char function (read-line is a function that waits some keyboard input)
    (le-letra!) 	;Calling the function
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
    (cond	;Equals 'case' statement of java
	(= up 0) (lose)      ;Case up = 0, call 'lose' function
	(is-the-boss-dead?) (win) ;Case function is-the-boss-dead return true, call 'win' function
	:else (keep-trying) ;Other case, call 'keep-trying' function
    ```
    
* **Set of items is declared as #{"first element" "second element" "and so on"}. The set doesn't allow duplicated items**
    ```clojure
    (def set #{"L" "M" "A"})	;Define the set
    (conj set "X")		;Create a new set with "L", "M", "A", "X" (Remember that variables are immutable)
    (def set-with-x (conj set "X"))	;You can do that and use the new Set named set-with-x
    
    (disj set-with-x "L")	;Create a new set without "L" element 
    ```

* **Vector of items is declared as ["first element" "second element" "and so on"]. The vector allow duplicated items**
    ```clojure
    (def numbers [1 2 3 4])	;Define the vector
    ```

* **We can send a function as a parameter**
    ```clojure
    (def nums [1, 2, 3, 4])
    (defn function-as-parameter [n] (+ n 10)) 	;Sum 10
    (map function-as-parameter nums)	;The map function iterates over each number in nums vector, execute the function-as-parameter to each and return a new vector.
    ; The map function will return (11, 12, 13, 14)
    ```

---

##**Best practices**
  
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


---

##**Creating JAR File and Running on JVM**

1. **In the project folder, execute the command: lein uberjar **
2. **Go to target/uberjar and execute the jar File: java -jar name.jar**
