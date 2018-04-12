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
}
```
