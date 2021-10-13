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

In the case where `someCondition` is `false`, the `&&` short-circuits and the expression is evaluated as `...(false)` - which means nothing is assigned.


## Definition
This proposal introduces a new conditional assignment operator. There are currently multiple possible syntaxes under consideration:


### 1. Syntax `key ?<expression>: value`

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

### 2. Syntax `expression && key: value`

### 3. Syntax `expression ?? key: value`
## Examples
