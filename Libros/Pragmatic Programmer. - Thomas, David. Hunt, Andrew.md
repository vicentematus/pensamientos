Lo encontre por el blog de https://martinfowler.com/ y algunas tier list de libros de software engineering.


(missing)

## Chapter 3
- Entender el scope del problema en profundo.
- "*You can't be a great programmer until you become highly skill at debugging*".
- Keep knowledge in plain text (ver Engineering Daybook)
- Si haces todo atraves de una GUI, pierdes todo el potencial que te ofrece hacer cosas con el CLI.
- Debugging es un tema emocional y sensitivo para algunos programadores. Puedes buscar quien fue el culpable del código, pero olvídalo. Mejor enfocate en resolver el problema. Al final del día, tienes que hacerlo. 
- Primera regla de debuggear: don't panic.
- Don't fold under pressure of stakeholders/users, take a step back before  finding a solution. 
- La solucion puede estar unos pasos más allá de lo que piensas.
- Trata de reproducir el bug con los mismos datos. Aisla el caso, prueba los casos bordes y como realmente el usuario usa la aplicación. No como si la estuvieras usando desde una perspectiva de dev.
- Si miras un error stack, usa binary search a partir de un frame que puede ser.
- Lee el error antes de saltar el codigo.

## Chapter 4
- Design by contract: establece quien hace que cosa, responsabilidades de cada equipo. https://en.wikipedia.org/wiki/Design_by_contract
- Design by contract es un approach para diseñar software en el cual se definen precondiciones (guard clause, debe cumplicar ciertas condiciones), postcondiciones (esta funcion deberia devolverme un output).
- Bastante deprecado ya que muchos problemas no simplemente se solucionan con un contrato. Los  requerimientos son caoticos.
- Se rescatan ideas como defensive programming, tipo agregar guard clauses donde corresponde antes que llegue a otras partes.



_MISSING_


# Chapter 5

QUOTES: Tip 49: Sometimes the easiest way to find the transformations is to start with the requirements and determine its inputs and outputs. Now you've defined the function representing the overall program. You can then find steps that lead you from input  to poutp. This is a top-down approach.

Q: What facilitates coupling?
A: Making things easier to change

Q: What are train wrecks?
A:  When a piece of code traverse a lot of levels of abstractions.

public void applyDiscount(customer, order_id, discount): {
totals = customer.orders.find(order_id).get_totals()
}

Q: What are some problems of train wrecks?
A: if one of the methods changes it will break the code.

Q: What is the principle "Tell, Don't Ask"?
A: don't make decisions based on the internal state of an object. 

A2: Rather than asking an object for data and acting on in, we should instead tell the object what to do. ([see Martin Fowler](https://martinfowler.com/bliki/TellDontAsk.html))
![](Libros/Pasted%20image%2020251018151643.png) 



Q: Based on this example how can we improve with using Tell, Don't Ask principle? 

public void applyDiscount(customer, order_id, discount): {
totals = customer.orders.find(order_id).get_totals().apply_discount(discount)
}

A: Remove the train wreck and just tell the object what to to do.
totals = customer.findOrder(order_id).applyDiscount(discount)



Q: What is an Event by the definition of the book?
A:  An event represents some action that has taken in the system. For example, click a button, a search finishes.


Q: What is a Finite State Machine?
A: Una especificacion de como manejar eventos. Consiste en una serie de estados, de las cuales existen eventos asociados a ella


Q:  What is the Observer Pattern?
A: When we have a source of events called "Observable" and a list of clients "Observers" who are interested in those events.


Q: What is Pub Sub?
A: We have publishers and subscribers, which are connected via channels.

Q: How does publishers and subscribers communicate?
A: Via Channels.


Q: In what sense Pub Sub helps with decoupling?
A: for decoupling the handling of asynchronious events.

Q: What is a real benefit of code changes using Pub Sub? 
A: You can realize change to codes while the application is running. (?)


Q: What correspond to a shared interface in Publish/Subscribe?
A: The channel.


Q: All programs transforms xxx
A: Data


Q: How we should think about programs?
A: Like a series of data transformations.

Q:  If programs is all about transforming data, how we should pass down data?
A: Like pipelines.

Q: How should data flow between functions?
A: Pasandole de una funcion a otra. Por ejemplo const user = getUser(id); const profile = getProfile(user)

Q: Cual es un mal ejemplo de data flow?
A: Cuando un metodo de una clase depende de sus atriubtos. Por ejemplo  varios metodos que estan fuertemente acoplado a  un atributo de la clase


Q: What problems causes inheritance?
A: Inheritance is coupling.

Q: Visually what inheritance causes?
A: A tree shaped diagram.

Q: What are better alternatives to inheritances?
A: Interfaces.


Q: What is better to express polymorphism?
A: Interfaces


Q: Where should you keep configuration?
A: Always outside of the app. 

Q: Why you should keep your configuration outside of the app?
A: To change easily enviroments.


## Chapter 6 

Q: What is concurrency?
A: is when the exectuion of two or more pieces of code act as if they run at the same time.


Q: What is the objective of Concurrency?
A: About efficiently managing multiple task at once.

Q: What is a real example of Concurrency?
A: Web applications such as Facebook handle database queries concurrently. 


Q: What is parallelism?
A:   Parallelism is when tasks actually run simultaneously on multiple processors or cores.

Q: What is the objective of Parallelism?
A:  focuses on boosting performance by handling computation-heavy task simultaneously

Q: What is an example of Parallelism?
A: Machine learning uses paralelism to distribute training for LLM. Video rendering proccess multiple frames between multiple cores.






--- 

## Preguntas

###### Que emoción deberías tener cuidado cuando estas haciendo debugging?
A: La necesidad de echarle la culpa a alguién del error.

 Q: In design by contract  we recommend be ---- ___in what you will accept before you begin and promise ---- as possible.___ 
strict, as little
 
###### 
