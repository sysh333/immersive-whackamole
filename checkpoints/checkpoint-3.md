# Checkpoint 3

## Watch a tech mentor:

* [ ] Create a method on the App component that just console logs. I suggest naming it something like `handleWhack` to signify that it’s a function that runs when a Mole is “whacked” (clicked). 
* [ ] Using `v-on:CUSTOM_EVENT` (change the event name to be appropriate) and `this.$emit` inside of a child, have a mole click invoke the App method that console logs.
  * [ ] **[Hint]** You will need to emit the event in the Mole to let the Moles component know, then the Moles component will need to emit the event to let the App know.
* [ ] Pass another prop from Moles to Mole, to ensure that a Mole knows what its own ID is
* [ ] Provide the mole ID as an argument into the custom event handler function
* [ ] Consult the VueJS documentation for this.$emit for further details. [this.$emit JP docs](https://jp.vuejs.org/v2/api/index.html#vm-emit)
