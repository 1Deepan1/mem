## Design Patterns [in progress]

---

### Strategy Pattern

> Behavioural Pattern:
Define a family of algorithims, encapsulate each one and make them interchangeable.
Strategy lets the algorithim vary independently from clients that use it.

---

### Class Diagaram

<img src="https://yuml.me/diagram/scruffy/class/[Context]<>->[<<Strategy>>],[<<Strategy>>]^-[ConcreteStrategyA], [<<Strategy>>]^-[ConcreteStrategyB]" />


```
Example in Java library:-

Collections.sort(list,comparator);
```

---

### State Pattern

> Behavioural Pattern
Allow an object to alter ints behavior when its internal state changes.
The object will appear to change its class.

---

### Class Diagram

<img src="https://yuml.me/diagram/scruffy/class/[Context|-state|+Context(state:State)|+changeState(state:State)|+Request()]<>->[<<State>>],[<<State>>]^-[ConcreteStateA|+Handle()], [<<State>>]^-[ConcreteStateB|+Handle()]]" />

- State can be changed by the client  or by the concrete state themselves.

---