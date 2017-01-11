### What is ```use strict``` and what does it do ?

Strict mode allows you to place a program or a function in what's called ```strict operating context```. In another words it makes debugging easier. Code errors that would be otherwise ignored or failed silently will generate errors or throw exceptions thanks to ```use strict```.


### How to enable strict mode in javascript file?

There are two ways to apply strict mode:
- place it at the top of the file:  ```"use strict"```
- or place it inside the function:

```js
// not a strict mode
function someCode() {
  "use strict";
  //strict mode
}

```

**Wondering why ```use strict``` is a string?**

When this feature was released as a two keywords: ```use strict```, it was failing in the browser which hasn't yet supported it. This is why its been changed to be wrapped as a string.

### What does it do and why to use it?

- **avoid accidentally creating global variable**

  Not strict mode:
  ```js
  num = 1 // I just created a global variable
  console.log(window.num);

  ```

  In strict mode - above code throws an error: ```ReferenceError: num is not defined```

  ```js
  "use strict";
  num = 1 // ReferenceError

  ```

- **makes you stop using the reserved keywords even in a future released of javascript**

  Not strict mode:

  ```js
  var let = 1; // this is be ok without strict mode

  ```

  With strict mode - above code throws an error: ```Unexpected strict mode reserved word```

  ```js
  "use strict";

  var let = 1; // Error

  ```

- **doesn't allow you to delete function, variable or function argument**

  Not strict mode:
  ```js
  var foo = 1;
  delete foo; // this is ok with no strict mode

  function moo() {};
  delete moo; // this is ok as well
  ```

  With strict mode  - above code throws an error: ```SyntaxError: Delete of an unqualified identifier in strict mode.```

  Not strict mode:
  ```js
  "use strict";

  var foo = 1;
  delete foo; // Error

  function moo() {};
  delete moo; // Error

  function moo(arg) {
    delete arg; // Error
  }
  ```

- **makes ```eval```a bit safer to use (still dangerous but powerful feature)**

  Not strict mode
  ```js
  eval("var a = 1");
  console.log(a) // 1  - leaking a variable from eval scope
  ```

  With strict mode  - above code throws an error: ```ReferenceError: a is not defined```
  ```js
  "use strict";
  eval("var a = 1");
  console.log(a); //ReferenceError: a is not defined
  ```
