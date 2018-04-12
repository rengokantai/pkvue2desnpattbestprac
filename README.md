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
