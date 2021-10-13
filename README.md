# Conditional-property-assignment


## Motivation
There are two viable ways to assign a property on an object only if a given condition is true.

### 1. The multi-step approach
```js
let objectWithProperties = {
  propA: 'propAValue',
  propB: true
}

let someCondition = true;
if(someCondition) {
  objectWithProperties.propC = 'propCValue'
}
```

### 2. The spread shorthand assignment
```js
let someCondition = true;
let objectWithProperties = {
  propA: 'propAValue',
  propB: true,
  ...(someCondition && { propC: 'propCValue' })
};
```
In the case where `someCondition` is `true`, the key `propC` is added to `objectWithProperties` with a value `propCValue`. 
In the case where `someCondition` is `false`, the `&&` short-circutes and the expression is evaluated as `...(false)` - which means nothing is assigned.


## Definition
This proposal introduces a new conditional assignment operator `?():` which evaluates a condition in parenthesis to determine whether to assign a property to the object.

```js
let objectWithPropertyAssigned = {
  propA ?(true): 'propAValue'
};

console.log(objectWithPropertyAssigned); // { propA: 'propAValue' }

let emptyObject = {
  propA ?(false): 'propAValue'
}

console.log(emptyObject); // {}
```

## Examples
