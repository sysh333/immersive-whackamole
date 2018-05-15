# Checkpoint 3

In this checkpoint, we will be figuring out how a parent and child component communicate by reading through existing code as well as using documentation.

The problem: The parent (_App_) holds the application data about which moles or active and inactive. But a nested child, _Mole_, knows when it is clicked. That means the _App_ and _Mole_ needs to be able to communicate with each other.

We can see how a parent and child communicate by altering main.js to render the _Hello_ component instead of the _App_ component. Give it a try and read the code:

* [ ] Inside of `main.js`, replace all reference of `App` with `Hello` to render the `src/Hello.vue`.
* [ ] View the `Hello.vue` file and look at the line that says: `v-on:sendGreeting="handleGreeting"`. The `v-on:CUSTOM_EVENT` syntax allows you to register functions to custom events.
* [ ] View the `GreetingButton.vue` and observe the `this.$emit()` function being called. This is how you "emit" an event. Emitting an event will notify the parent that the custom event has occurred!

Take a few more minutes to read through the code and observe how a parent-child components talk to each other.

## Now it's your turn:

* [ ] Create a method on the App component that just console logs. I suggest naming it something like `handleWhack` to signify that it’s a function that runs when a Mole is “whacked” (clicked). 
* [ ] Using `v-on:CUSTOM_EVENT` (change the event name to be appropriate) and `this.$emit` inside of a child, have a mole click invoke the App method that console logs.
  * [ ] **[Hint]** You will need to emit the event in the Mole to let the Moles component know, then the Moles component will need to emit the event to let the App know.
* [ ] Pass another prop from Moles to Mole, to ensure that a Mole knows what its own ID is
* [ ] Provide the mole ID as an argument into the custom event handler function
* [ ] Consult the VueJS documentation for this.$emit for further details. [this.$emit JP docs](https://jp.vuejs.org/v2/api/index.html#vm-emit)
