#### Debugging
1. `object` : important to keep the format right. Missing "," or ";" can cause an error. (e.g. we ran into an error because we forgot to put "," after the key-value pairs within the curly brackets)
    ```js
    var letter1 = {
        letter: 'a'
        position: 0,
        color: 'g',
    };
    ```
    ❌: we missed a `,` after `letter: 'a'` !

2. `.filter()`: [.filter()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter) takes a `function` as a parameter and the function passed in has to return a `boolean value` (otherwise javascript will convert the return value to a boolean value for us, which might cause unexpected error)
    ```js
    var words = ['apple', 'banana', 'citrus'];
    var output = words.filter(input => input.charAt(0));
    ```
    ❌: Array output will not produce proper filtered result as expected, because the function we passed into `.filter()` here will return a char and a char will always be deemed as true in javascript. 
    - for example, if the return value of the unnamed function is 'a', then the code will be come `words.filter('a')`, and `.filter()` will take `'a'` as `true` (the same goes for `'b'` and `'c'`). Thus all the element in the original array will be kept in the shadow array. 

    ✅: to fix the issue, we have to add a `===`
    ```js
    var words = ['apple', 'banana', 'citrus'];
    var output = words.filter(input => input.charAt(0) === 'a');
    ```
    - here, `input.charAt(0) === 'a'` will produce a proper boolean value and Array output will become`['apple']`
3. using `!` in `.filter()` to negate the boolean value. 
```js
var names = ['Mark', 'Daisy', 'Mickey'];
var filteredNames = names.filter(word => !word.includes('i'));
```
`word => !word.includes('i')`: this function will return true if the word does not contain character 'i', return false if the word contains 'i'. 
`names.filter(word => !word.includes('i'));`: keep the words that do not contain character `i`, eliminate the words that contain character `i`. (`filteredNames` will be `['Mark']`)

`names.filtered(word => word.includes('i'))`: keep the words that contain character 'i', eliminate the words that do not contain character 'i'. (`filteredNames` will be `['Daisy', 'Mickey']`)

3. lowercase and uppercase matters, especially when we use strictly equal `===` 
4. `.toLowerCase()` and `toUpperCase()` do not modify the original array, it returns a new string formatted to lower/upper case. 




---
#### New knowledge!
- `=>` is a syntax for unnamed functions. `input => input.charAt(0)` is the same as 
    ```js
    function getChar(input) {
        return input.charAt(0);
    }
    ```
    but without a name. 

- grep 
    - a program uses regular expression to search stuff
    - Regular expression: like a powerful search engine

    - Linux and Mac are both originated from Unix, which has a box of tools such as regular expression, ls, cd, and a bunch of other commands

- git
    - after `create a local repo -> add and commit -> create an online repo -> connect the two repos -> git push`, if we delete the `.git` in the local directory and then create a local repo again and connect to the same online repo, you will not be able to push file to the repo anymore(will run into an access error)
---
#### Review
- `cmd` + `d` in VS code: select and substitute
- `cmd` + `shift` + `z`: undo cmd + z
- git
    - Have to do `git init` first before connect to a github online repo (you have to have a local repo first)
    - `git add` and `git commit` first before you push, otherwise you’ll have nothing to push and that will throw you an error 
    - `git clone` + SSH address
- `.charAt(index)` -> `char`
- `.indexOf(char)` -> `index`
- `.includes(char)` -> `boolean`
- string interpolation 
    - ```
       `${variableName}` 
       ```




    