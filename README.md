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

_Author: Ical Balino_

###