# js-module-exists

## Examples:

### ModuleExists() Method

```js
if (moduleExists("some-npm-package-name")) {
  //=> true
} else {
  //=> false
}
```

### ModuleExistsWithText() Method

**Expected output**: true

1. Sample use without if block

```js
moduleExistsWithText("some-npm-package-name");
//=> Terminal output: Installed!
```

2.  Sample use with if block

```js
if (moduleExistsWithText("some-npm-package-name")) {
  //=> true
  //=> Terminal output: Installed!
} else {
  //=> false
  //=> Terminal output: Not Installed!
}
```

3. Use with options provided

```js
moduleExistsWithText("some-npm-package-name", {
  success: {
    color: "#ffffff", // string of terminal emulators supported hex color || defaultColors.success
    text: "Module exists!", // string
    warn: {
      color: "#DEADED", // string of terminal emulators supported hex color || defaultColors.warn
      text: "Some exists warning text.", // string
    },
    info: {
      color: "#00cafc", // string of terminal emulators supported hex color || defaultColors.info
      text: "Some exists info text!", // string
    },
  },
  error: {
    color: "#ffffff", // string of terminal emulators supported hex color || defaultColors.error
    text: "Module not exist!", // string
    warn: {
      color: "#DEADED", // string of terminal emulators supported hex color || defaultColors.warn
      text: "Some exists warning text.", // string
    },
    info: {
      color: "#00cafc", // string of terminal emulators supported hex color || defaultColors.info
      text: "Some exists info text!", // string
    },
  },
});

//=> Terminal output:

    ✔ Module exists!
    ⚠ Some exists warning text.
    ℹ Some exists info text!

```

#### All options object properties

**IMPORTANT**
All of the object properties do not need to be provided only those which you want to modify!!!

```js
        options: {
            success: {
                color: string of terminal emulators supported hex color,
                text: string,
                warn: {
                    color: string of string of terminal emulators supported hex color,
                    text: string,
                },
                info: {
                    color: string of terminal emulators supported hex color,
                    text: string,
                },
            },
            error: {
                color: string of terminal emulators supported hex color,
                text: string,
                warn: {
                    color: string of terminal emulators supported hex color,
                    text: string,
                },
                info: {
                    color: string of terminal emulators supported hex color,
                    text: string,
                },
            }

```

###### EXAMPLE OF THE MOST POPULAR TERMINAL COLORS:

```code

    black - #000000
    red	- #cc0000
    green - #4e9a06
    yellow	- #c4a000
    blue* - #729fcf
    magenta - #75507b
    cyan - #06989a
    white - #d3d7cf
    bright black - #555753
    bright red - #ef2929
    bright green - #8ae234
    bright yellow - #fce94f
    bright blue* - #32afff
    bright magenta - #ad7fa8
    bright cyan	- #34e2e2
    bright white* - #ffffff
```

4.  Change only the text of the success message

**IMPORTANT**:
All of the examples for success messages are relevant to the use of error messages. Will use the default hex color for success, error, info, and warn.
If you want to change the color you need to add provided color property.

```js
moduleExistsWithText("some-npm-package-name", {
  success: {
    text: "Module exists!", // string
  },
});

//=> Terminal output:

    ✔ Module exists!

```

5. Change only the color of the success message

```js
moduleExistsWithText("some-npm-package-name", {
  success: {
    color: "#fff",
  },
});

//=> terminal success text color: #fff
//=> Terminal output:

    ✔ Module exists!
```

6. Add info message

**Important** To show info message the text property is mandatory! For the color will use the default one.

```js
moduleExistsWithText("some-npm-package-name", {
  success: {
    color: "#DEADED",
    info: {
      text: "Some info text!",
    },
  },
});


//=> Terminal success text color: #DEADED
//=> Terminal output:

    ✔ Installed!
    ℹ  Some info text!
```

7. Added info and warning messages

To show info and warn messages the text is mandatory! For the color will use default one.

```js
moduleExistsWithText("some-npm-package-name", {
  success: {
    color: "#000",
    text: "Module exists!",
    info: {
      color: "#ccc",
      text: "Some info text!",
    },
    warn: {
      text: "Some warning text!",
    },
  },
});

//=> terminal success text color: #000
//=> terminal info text color: #ccc
//=> Terminal output:

    ✔ Module exists!
    ⚠ Some warning text.
    ℹ  Some info text!
```

### setTextColors() Method

**Info**: Used only with moduleExistsWithText() method to change default colors.

**Expected result**: Set the default colors for success, error, info, and warn.

**Option**: Can change only for specific text output( example success) the rest will be by default colors.

1.Example of use

**Important** Use it before moduleExistsWithText();

```js
setTextColors({
  sucess: "#fff",
  error: "#000",
  info: "#00cafc",
  warn: "#DEADED",
});

// Expected result:

// Default colors was changed to:
// sucess: "#fff"
// error: "#000"
// info: "#00cafc"
// warn: "#DEADED"

moduleExistsWithText("some-npm-package-name");

//=> terminal success text color: #fff
//=> Terminal output:

    ✔ Installed!

```

2. Example of use with option color change in moduleExistsWithText() method.

```js
setTextColors({
  sucess: "#fff",

  // Expected result:
  // Default colors was changed to:
  // sucess: "#fff"
});

// Expected result:
// Default colors was changed to:
// sucess: "#fff"

moduleExistsWithText("some-npm-package-name", {
  success: {
    color: "#000",
  },
});

//=> terminal success text color: #000
//=> Terminal output:

      ✔ Installed!
```
