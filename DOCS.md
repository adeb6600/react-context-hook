<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### Table of Contents

-   [useStore][1]
    -   [Parameters][2]
    -   [Examples][3]
-   [useStoreState][4]
    -   [Examples][5]
-   [useSetStoreValue][6]
    -   [Parameters][7]
    -   [Examples][8]
-   [useDeleteStoreValue][9]
    -   [Parameters][10]
    -   [Examples][11]
-   [useGetAndSet][12]
    -   [Parameters][13]
    -   [Examples][14]
-   [useGetAndDelete][15]
    -   [Parameters][16]
    -   [Examples][17]
-   [useSetAndDelete][18]
    -   [Parameters][19]
    -   [Examples][20]
-   [useStoreValue][21]
    -   [Parameters][22]
-   [withStore][23]
    -   [Parameters][24]
    -   [Examples][25]

## useStore

`useStore` is a React Hook that access a value stored in the application global store. It returns the value, a function to update it (like React.useState) and a function to delete it.

### Parameters

-   `key` **[string][26]** The lookup key to find the saved value in the store
-   `defaultValue` **any** The value if the value in the store is missing
-   `createIfMissing` **[boolean][27]** if true and the data is missing it will be created in the store

### Examples

```javascript
import {useStore} from 'react-context-hook'
const [username, setUsername, deleteUsername] = useStore('username')
<div>hello {username}</div>
<button onClick={()=> setUsername('my_username')}>set username</button>
```

Returns **[array][28]** an array with length 3:<br>
position 0 - the value of the data in the store.<br>
position 1 - a function _setValue_ to modify the data in the store. When used, this function return a promise that resolve nothing, thus you can use `setValue('a value').then(() => {doSomething() //when the store did update})`<br>
position 2 - a function _deleteValue_ to delete the value from the store. When used, this function return a promise that resolve nothing, thus you can use `deleteValue('a value').then(() => {doSomething() //when the store did update})`

## useStoreState

Returns the whole store value, with all the variables stored in it. Changes to this object will not change the store

### Examples

```javascript
import {useStoreState} from 'react-context-hook'
const store = useStoreState()
console.log('the store is', JSON.stringify(store))
```

Returns **[object][29]** An object representing the whole store value in read only mode.

## useSetStoreValue

Returns a function to set or update a variable in the store. You want to use this hook when you just need to modify the store, not read or delete a value from it.

### Parameters

-   `key` **[string][26]** the name of the variable to set in the store

### Examples

```javascript
import {useSetStoreValue} from 'react-context-hook'
const setUsername = useSetStoreValue('username')
<button onClick={()=> setUsername('my_username')}>set username</button>
```

Returns **[Function][30]** a function to set a variable in the store with the given name When used, this function return a promise that resolve nothing, thus you can use `setValue('a value').then(() => {doSomething() //when the store did update})`

## useDeleteStoreValue

Returns a function to delete a variable in the store. You want to use this hook when you just need to delete a value in the store, not read or set a value from it.

### Parameters

-   `key` **[string][26]** the name of the variable to set in the store

### Examples

```javascript
import {useDeleteStoreValue} from 'react-context-hook'
const deleteUsername = useDeleteStoreValue('username')
<button onClick={()=> deleteUsername('my_username')}>set username</button>
```

Returns **[Function][30]** a function to delete a variable in the store with the given name. When used, this function return a promise that resolve nothing, thus you can use `deleteValue('a value').then(() => {doSomething() //when the store did update})`

## useGetAndSet

This React hook returns an array to read and modify a value in the store:
`const [value, setValue] = useGetAndSet('a_lookup_key_in_the_store')`. The name of the variable in the arry is arbitrary and you can choose any string you like.

### Parameters

-   `key` **[string][26]** The lookup key to find the saved value in the store
-   `defaultValue` **any** The default value if missing

### Examples

```javascript
import {useGetAndSet} from 'react-context-hook'
const [username, setUsername] = useGetAndSet('username')
<div>hello {username}</div>
<button onClick={()=> setUsername('my_username')}>set username</button>

 const [value, setValue] = useGetAndSet('a_lookup_key_in_the_store')
```

Returns **[array][28]** an array with length 2:<br>
position 0 - the value of the data in the store.<br>
position 1 - a function _setValue_ to modify the data in the store. When used, this function return a promise that resolve nothing, thus you can use `setValue('a value').then(() => {doSomething() //when the store did update})`<br>

## useGetAndDelete

This React hook returns an array to read and delete a value in the store:
`const [value, deleteValue] = useGetAndDelete('a_lookup_key_in_the_store')`. The name of the variable in the arry is arbitrary and you can choose any string you like.

### Parameters

-   `key` **[string][26]** The lookup key to find the saved value in the store

### Examples

```javascript
import {useGetAndDelete} from 'react-context-hook'
const [username, deleteUsername] = useGetAndDelete('username')
<div>hello {username}</div>
<button onClick={()=> deleteUsername('my_username')}>set username</button>
```

Returns **[array][28]** an array with length 2:<br>
position 0 - the value of the data in the store.<br>
position 1 - a function _deleteValue_ to delete the data in the store. When used, this function return a promise that resolve nothing, thus you can use `deleteValue('a value').then(() => {doSomething() //when the store did update})`<br>

## useSetAndDelete

This React hook returns an array to set and delete a value in the store:
`const [setValue, deleteValue] = useGetAndDelete('a_lookup_key_in_the_store')`. The name of the variable in the arry is arbitrary and you can choose any string you like.

### Parameters

-   `key` **[string][26]** The lookup key to find the saved value in the store

### Examples

```javascript
import {useGetAndDelete} from 'react-context-hook'
const [username, deleteUsername] = useGetAndDelete('username')
<div>hello {username}</div>
<button onClick={()=> deleteUsername('my_username')}>set username</button>
```

Returns **[array][28]** an array with length 2:<br>
position 0 - a function _setValue_ to modify the data in the store. When used, this function return a promise that resolve nothing, thus you can use `setValue('a value').then(() => {doSomething() //when the store did update})`<br>
position 1 - a function _deleteValue_ to delete the data in the store. When used, this function return a promise that resolve nothing, thus you can use `deleteValue('a value').then(() => {doSomething() //when the store did update})`<br>

## useStoreValue

### Parameters

-   `key` **[string][26]** the name of the variable / value to be retrieved in the global store.
-   `defaultValue` **any?** an optional default value, if the value in the global store is not present.

Returns **any** the value on the global store, or the default value if passed, or `undefined`

## withStore

### Parameters

-   `WrappedComponent` **ReactElement** the component to connect with the store
-   `initialValue` **[Object][29]** the initial store value or nothing
-   `config` **[Object][29]** the custom configuration. If nothing is passed will use the default config
    -   `config.listener` **[Function][30]** a function that is triggered each time the store is modified.
    -   `config.proxyStore` **[boolean][27]** default `true` - if true the store will be protected by a Proxy. Set to false if your environment does not support Proxy. If you use `react-context-hook` in the browser set it to true

### Examples

```javascript
const initialState = { count: 10 }

const storeConfig = {
 listener: state => {
   console.log('state changed', state)
 },
 logging: true //process.env.NODE_ENV !== 'production'
}

export default withStore(App, initialState, storeConfig)
```

[1]: #usestore

[2]: #parameters

[3]: #examples

[4]: #usestorestate

[5]: #examples-1

[6]: #usesetstorevalue

[7]: #parameters-1

[8]: #examples-2

[9]: #usedeletestorevalue

[10]: #parameters-2

[11]: #examples-3

[12]: #useGetAndSet

[13]: #parameters-3

[14]: #examples-4

[15]: #usegetanddelete

[16]: #parameters-4

[17]: #examples-5

[18]: #usesetanddelete

[19]: #parameters-5

[20]: #examples-6

[21]: #usestorevalue

[22]: #parameters-6

[23]: #withstore

[24]: #parameters-7

[25]: #examples-7

[26]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String

[27]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean

[28]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array

[29]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object

[30]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/function