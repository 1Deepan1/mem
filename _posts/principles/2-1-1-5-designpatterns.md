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

> Behavioural Pattern, 
> Allow an object to alter ints behavior when its internal state changes.
The object will appear to change its class.

---

### Motivation

- The State pattern is useful when you want to have an object represent the state of an application, and you want to change the state by changing that object.
- The State pattern is intended to provide a mechanism to allow an object to alter its behavior in response to internal state changes. To the client, it appears as though the object has changed its class.
- The benefit of the State pattern is that state-specific logic is localized in classes that represent that state.

---

### Class Diagram

<img src="https://yuml.me/diagram/scruffy/class/[Context|-state|+Context(state:State)|+changeState(state:State)|+Request()]<>->[<<State>>],[<<State>>]^-[ConcreteStateA|+Handle()], [<<State>>]^-[ConcreteStateB|+Handle()]]" />

---

### Participants
> Context: defines the interface of interest to clients,
maintains an instance of a ConcreteState subclass that defines the current state.

> State: defines an interface for encapsulating the behavior associated with a particular state of the Context.

> Concrete State: each subclass implements a behavior associated with a state of Context.

---

### Structural Code 

Client :

		public class Test {
			public static void main( String arg[] ) {
			State state = new ConcreteStateA(); 
			Context context = new Context(); 
			context.setState( state ); 
			context.request();
			}
		}	

---

Context:

		/**
		* Defines the interface of interest to clients. 
		* Maintains an instance of a ConcreteState 
		* subclass that defines the current state.
		*/
		public class Context {
			private State state;
			public void setState( State state ){
			 this.state = state; 
			}
			public State getState() { 
			return state; 
			}
			public void request(){
			 state.handle();
			}
		}

---

State: 

		/**
		* Defines an interface for encapsulating the behavior 
		* associated with a particular state of the Context.
		*/
		public interface State{
		void handle();
		}

---

Concrete State:

		/**
		* Each subclass implements a 
		* behavior associated with a state of the Context. 
		*/
		public class ConcreteStateA implements State { 
			public void handle() {}
		}
		public class ConcreteStateB implements State { 
			public void handle() {}
		}

---

### Real Time Example : Coffee Vending machine

VendingMachineContext:

		public class VendingMacineContext {

			private State state;

			public VendingMachine(){
				state = new InitialState();
			}

			public void setState(State state){

				this.state = state;
			}

			public void insertCoin(Context context){
				state.insertCoin();
			}

			public void selectCoffeeType(Context context){
				...
			}

			public void dispense(Context context){
				...
			}

			public void abort(Context context){
				...
			}

		}

---

State :

		public interface VendingState {
			
			public void insertCoin(Context context);

			public void selectCoffeeType(Context context);

			public void dispense(Context context);

			public void abort(Context context);
		}

---

InitialState :

		public InitialState implements VendingState {
			public void insertCoin(Context context){
				sysout("Received coins..");
				context.set(new SelectionState());
				sysout("Select type..")
			}

			public void selectCoffeeType(Context Context){
				sysout("Please insert coin..");
			} 

			public void dispense(Context context){
				sysout("please insert coin...");
	 		}

	 		public void abort(){
	 			context.setState(new InitialState()); //not required..
	 		}
		}

---

SelectionState:

		public SelectionState implement VendingState {
			public void insertCoin(){
				sysout("cannot insert coin , try abort.. or select type..")
			}

			public void selectCoffeeType(Context Context){

				sysout("Selected latte..");
				context.set(new BrewingState());

				Thread.sleep(2000); //simulate brewing time..
				context.set(new DispenseState());

			}

			public void dispense(Context context){
				sysout("Please select coffee type first..");
	 		}

			public void abort(){
	 			context.setState(new InitialState()); 
	 		}
		}

---

BrewingState:

		public SelectionState implement VendingState {
			
			public void insertCoin(){
				sysout("Please wait , brewing coffee..");
			}

			public void selectCoffeeType(Context Context){
				sysout("Please wait , brewing coffee..");
			}

			public void dispense(Context context){
				sysout("Please wait , brewing coffee..");
	 		}

			public void abort(){
	 			context.setState(new InitialState()); 
	 		}
		}

---

DispenseState:

	 	public DispenseState implement VendingState {
	 		public void insertCoin(){
	 			sysout("Please wait , dispensing coffee..");
	 		}

	 		public void selectCoffeeType(Context Context){
				sysout("Please wait , dispensing coffee..");
	 		}

	 		public void dispense(Context context){
				sysout("Cofee Dispensed...");
				context.setState(new InitialState());
	 		}

	 		public void abort(){
	 			sysout("Stop  dispensing..")
	 			context.setState(new InitialState());
	 		}
	
	 	}

----

































