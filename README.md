# gimgim-web-apps-with-vueandnuxt
```
npm install
```

## keynote project game-a
- `npm install -g @vue/cli`
- `vue create game-a`
- grab all of the `main.css` and dump it right into top level app component 
- google font setup - [ubuntu](https://fonts.googleapis.com/css2?family=Ubuntu:wght@300;400&display=swap)
- add background.svg
- add components
- add state
###
**Open project game-a**
###
- add basesvg.svg to `App.vue`
- add ui State
- using vmapState
- add `GamestateStart.vue` (showing a modal)
- add a `slot`
- `v-if/v-else` for ui state (start)
- add state (character, characterChoices)
- `v-for` (loop the characterChoices)
###
- adding button and method
- add mutations and call mutations (committing)
- add some folks and different component for character
- and make it loading in different characters conditionally
###
- creating a question index (questionIndex and score) in `store`
- add class `friendtalk` and class `zombietalk`
- mention `questionIndex`
- grab that question array (output) in `friendtalk`
- `questions[questionIndex].question`
- add `buttons` to answer the question
- in `zombietalk` loop the `characterChoices`
- the output is the character
###
- updating the `score` based you got the character on not
- select something and go to the next question
- make the `pickQuestion` mutation and `method`
- check if the `state.character` is the `character`
- update the `score` and question index
###
- install gsap library `npm install gsap`
- give needle some visual indication
- check the needle if going off or the right way (use `watcher`)
- open `Score.vue` import `gsap` and add `watcher` 
- adding score to the end of game state (array of question)
- get to the end of the question index 
- tell UI state (won or lost) pass that as a string
- add `shuffle` method
###
- add `GamestateFinish.vue`
- import `mapState` and add method `restart`
- add mutation `restartGame` and `updateScore` in `store`
- import and add component `GamestateFinish.vue` into `App.vue`
- add `score` in `mapState`
- add `watch` use `gsap` to control the animation with a watcher
- we have uistate is `start` if the character is chosen
- and uistate has `finish` and uistate `won or lost`
- we create a result modal
###
###

## keynote project foodfoodnuxt
```
npm init nuxt-app foodfoodnuxt
```
```
cd foodfoodnuxt
npm run dev
```
The application is now running on http://localhost:3000 . Well done!
###
**Open project foodfoodnuxt**
###
- manually add dir assets, layouts, middleware, and plugins  
- google font setup - [Mulish and Poppins](https://fonts.googleapis.com/css2?family=Mulish:wght@300&family=Poppins:wght@600&display=swap)
- config and add `assets` `components` `layouts` `pages` `static` `store` `nuxt.config.js`
- adding manually stuff like image, css(scss), and readme file
- create pages
- create import `AppMenu.vue` and explain what Nuxt Layouts do
- SFC (single file component)
- we'll use `default.vue`
- create a masthead `AppHeader.vue` using [Hero Generator](https://hero-generator.netlify.app/)
- create a `footer` and `restaurant.vue`
- create `nuxt-link` to restaurant
###
- bring things via `API`, via `Vuex Store`, and a `Plugin`
- our [API](https://dva9vm8f1h.execute-api.us-east-2.amazonaws.com/production/restaurants)
- empty the `fooddata` in `store` to empty array
- adding `actions` and `mutations`
- in `actions` we `fetch` the API
- using a API key `process.env.AWS_API_KEY` and `.env` file (that file is get ignore)
- using an `actions` to call `mutations` (asynchronous logic) and `mutations` changes the state
- we're gonna build and concatenate all those files and create dynamic routes from all of these pages
- creating on the server, call it once while the pages are building instead calling on the client
- adding `getfood.server.js` in `plugins`, is tell nuxt do this on the server don't on the client
- in `getfood.server.js` pass in the `store` remember we dispatch `actions`, we commit `mutations`
- go into nuxt config and let it know that this plugins exists `'~/plugins/getfood.server.js'`
- now data it's not coming in from that static piece of information, it's coming in from API
###
- create components `AppSelect.vue`, add `<select>`, and `props`
- import into `restaurant.vue` in pages
- we wanna emit from the child to the parent, what the value is
- `vemit-child` in select tag 
- collecting data to `data()` and return `selectedRestaurant` in `restaurant.vue`
- `vemit-parent` on that `<AppSelect />`
- make a `computed` properties
- add import `mapstate` `filteredRestaurants()`
- in `AppRestaurantInfo.vue` delete `mapstate`, `computed` with `fooddata`
- we need bring `props` with `datasource`
- on that `<AppRestaurantInfo />` in `restaurant` passing in the `props`
- in the home page `index.vue` passing in the `fooddata`, call `vmapsate` in `computed`
###
- create `_id.vue` inside `item` directori in `pages`
- go in `AppRestaurantInfo.vue` `add nuxt-link`
- in `_id.vue` add `vmapsate` and bring `fooddata`, add `currentItem`
- add `main` with class `container`
- add `section` it's working with image, add section with class `details`
- we have `fieldset` for `option` and `addon`
- add `section` with class `option`
- make a `combinedPrice`
- collecting data to `data()`
###
- creating toast component `AppToast.vue` with `slot`, go to `_id.vue` and import
- on `data()` make `cartSubmitted: false`
- add click handler on button add to cart
- make `addToCart` method, on that make `formOutput` to add things to a cart
###
- using vuex store mutations and [UUID](https://www.npmjs.com/package/uuid)
- add store commit on `_id.vue`
- go in store `index.js` add `cart` with empty array 
- on that mutations add `addToCart`
- create cart page and make use of uuid
- install uuid package `npm install uuid`
- import and use `uuid` in store `index.js`
- go to pages create `cart.vue`, and also add cart into the `AppMenu.vue`
- make sure we're actually doing that, go to _localhost->devtools->vue->vuex_
###
- create an `SVG` icon with conditional layout
- make a component `AppLogo.vue`
- get the svg `foodlogo.svg` in resource and drop into `AppLogo.vue`
- make it semantic and good for screen readers with `aria-labelledby`
- add to the App `AppMenu.vue`
###
- take whatevers on the cart we're going to show
- also going to use `getters` to show combined price for everything
- put static table on `cart.vue`, use `mapstate` to go gather the cart
- loop through all of the table rows to put what on the cart to the table
- create `getters` in store `index.js`, `totalPrice` getter
- we're returning the reduction of all the combined price in that cart
- now we can use into `cart.vue`, bringing in that `getters` from the store with `mapGetters`
###
- show the count of the cart in the menu use class `'smallnum'`
- if the cart is empty, show the empty cart SVG, make it accessible
- using getters make `cartCount` in store `index.js`
- we're using it, is gonna be inside the components into `AppMenu.vue` 
- bring that in from `vuex` with `mapgetters` 
- inside the `cart.vue`, make section `v-if` **if the cart have some length** show this cart
- make components `AppEmptyCart.vue`, otherwise we wanna show this **if the cart had no length**
- in `AppEmptyCart.vue` we make section and we've got this SVG
- add `AppEmptyCart.vue` on that `cart.vue`
###
- we wanna make sure of that we can't add to the cart unless some addon was added
- make sure that the user does that with [vuelidate](https://css-tricks.com/form-validation-in-under-an-hour-with-vuelidate/)
- install vuelidate `npm install vuelidate --save`
- make `vuelidate.js` in plugins, register on `nuxt.config`
- go into `_id.vue` add `v-model="$v.itemOptions.$model"` and `v-model="$v.itemAddons.$model"`
- connecting to `itemOptions` with `$` sign
- go down import the `required` from vuelidate and make `validations` object
- on `data()` we wanna have this things called `errors: false`
- we're going to check if `addOnError` `optionError` invalid or errors
- if there's errors than `this.errors = true` but if not `this.errors = false`
- `this.cartSubmitted = true` and go ahead
- store commit `addToCart` to add to the cart until that's done, until we have validate that exists



###

_Author: Ical Balino_

###