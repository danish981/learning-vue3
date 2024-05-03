# learning-vue3

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```


<!-- comments in the code make our code read better and understand better -->

### What I think should be added in the application
- when the todo is marked completed (strike through), don't show the pencil icon
- pinia (statement management and the store)
- the firebase db connection to hold the todo item details
- optimize the code  (like fixing the v-for with v-bind keys and not using the :index for the custom iterative elements)
- there should be a little toast message for adding, updating and deleting the todo item
- deleting the all todo items at once
- instead of clicking the button, we should make the enter button functional
- prevent adding duplicated todo element
- after adding a new todo item, we lost focus from the text field from to write todo 
- we can show the id of each todo item that is unique or count on hover too to uniquely identify
- show count at the top of the todo list
- rename the repo to the todo application and netlfiy target where the app is deployed
- update the versions and make pull requests and merge them




### What I'm doing ?
- when we have an invalid todo, we will have a dynamic class attached to the input element 
- learning and doing code for slots , what the slots are
- slots done, putting icons from iconify lib and customizing it 
- showing the todo items in stacked order and displaying the items todos into the textbox upon condition using v-if and v-else
- displaying the nice message if there is no todo item in the list
- getting the error inside the vscode (not in the project) that v-for needs the v-bind with the key (which is the right convention for looping through element )
- updating the todo item is completed
- started working on deleting a todo item ....


### Youtube Video at current time

https://youtu.be/KTFH4P8unUQ?t=5769