# vuex-class-state2way

TypeScript decorator to create getters/setters for a Vuex state.

The main purpose is to use `v-model` directive without the overhead of manually creating simple getters and setters.

Check [vuex-class](https://github.com/ktsn/vuex-class) repository for a lot more Vuex decorators!

## Dependencies

- [Vue](https://github.com/vuejs/vue)
- [Vuex](https://github.com/vuejs/vuex)
- [vue-class-component](https://github.com/vuejs/vue-class-component)

## Installation

```bash
$ npm install --save vuex-class-state2way
# or
$ yarn add vuex-class-state2way
```

## Usage

* Get `variable_name` from the state, and commit `"mutation name"` to update this variable in the state
```ts
@State2Way("mutation name") variable_name
```

* Get `variable_name` from the state and set its value to the variable `other_name`, and commit `"mutation name"` to update this variable in the state
```ts
@State2Way("mutation name", "variable_name") other_name
```

* To get a deep value, you can do both:
```ts
@State2Way("mutation name", state => state.foo.bar) fooBar // you get type checking
@State2Way("mutation name", "foo.bar") fooBar
```

## Example

```ts
import Vue from 'vue'
import Component from 'vue-class-component'
import { State2Way } from 'vuex-class-state2way'

@Component
export class Comp extends Vue {
    @State2Way('updateFoo', 'foo') stateFoo
    @State2Way('updateBar') bar
    @State2Way('updateFooBar', 'foobar.example') stateFooBarExample
    @State2Way('updateFooBar', state => state.foobar.example) stateFooBarExemple2
}
```