# pkvue2desnpattbestprac
## State Management with Vuex
### State Management Pattern (SMP)
vue components->dispatchactions->commitmutations->mutatestate->renderviewcompoennt



### Creating a new store
src/store/index.js
```
import Vue from 'vue';
import Vuex from 'vuex';
Vue.use(Vuex);
export default new Vuex.Store({
  state:{
    count:0
  }
})
```
### Defing action types

src/store/mutation-types.js
```
export const INCREMENT = 'INCREMENT';
export const RESET = 'RESET';
```

### Actions
src/store/actions.js
```
import * as types from './mutation-types';
export default{
  [types.INCREMENT]({commit}){
    commit(types.INCREMENT);
  }
}
```
actually same as
```
import * as types from './mutation-types';
export default{
  [types.INCREMENT](store){
    store.commit(types.INCREMENT);
  }
}
```


### Mutations
/src/store/mutations.js
```
import * as types from './mutation-types';
export default {
  [types.INCREMENT](state){
    state.count++;
  }
}
```
### Getters
src/store/getters.js
```
export default {
  count(state){
    return state.count;
  }
}
```

### Combining elements
src/store/index.js
```
import Vue from 'vue';
import Vuex form 'vuex';
import actions from './actions';
import getters from './getters';
import mutations from './mutations';

Vue.use(Vuex);

export default new Vuex.Store({
  state: {
    count: 0,
  },
  actions,
  getters,
  mutations,
});
```
App.vue
```
<template>
  <div>
    <h1>{{count}}</h1>
    <button @click="increment">+</button>
    <button @click="decrement">-</button>
    <button @click="reset">R</button>
  </div>
</template>
```

```
import * as types from './store/mutation-types';

export default {
  methods: {
    increment() {
      this.$store.dispatch(types.INCREMENT);
    },
    decrement() {
      this.$store.dispatch(types.DECREMENT);
    },
    reset() {
      this.$store.dispatch(types.RESET);
    },
  },
  computed: {
    count() {
      return this.$store.getters.count;
    },
  },
}
```



## Server-Side Rendering with Nuxt
### Creating a Nuxt project
```
vue init nuxt-community/starter-template vue-next
```
### Nuxt configuration
```
head: {
  // Omitted
  link: [
    { rel: 'icon', type: 'image/x-icon', href: '/favicon.ico' },
    {
      rel: 'stylesheet',
      href:
    'https://cdnjs.cloudflare.com/ajax/libs/bulma/0.6.1/css/bulma.min.css',
    },
  ],
}
```

### Navigation
pages/index.vue
```
routes:[
  {
    name:'index',
    path:'/',
    component:'pages/index.vue'
  }
]
```
### Layouts
### The Mock REST API
```
npm install json-server -g
json-server --watch db.json --port 3001
```
