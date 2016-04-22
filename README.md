# JigSass Objects Button

  > Unopinionated and configurable button objects

The JigSass Button object is built for maximal flexibility, providing only very basic styles
as default. JigSass Button objects are transparent by default, and are meant to be extended by
type-size, color and background-color utils, and by configurable button object modifiers.


## Installation

Using npm:

```sh
npm i -S jigsass-objects-button
```


## Usage
First, you need to import JigSass Objects Button:
```scss
@import 'path/to/jigsass-objects-button/scss/index';
```
And optionally [reconfigure](https://txhawks.github.io/jigsass-objects-button/#configuration) the defaults to your liking.


Like all other JigSass modules, JigSass Button does not automatically generate any CSS when imported.
In order to use its classes, you would have to first explicitly indicate your intention to use
them by enabling their generation in the associated 
[configurations map](https://txhawks.github.io/jigsass-objects-button#css-output), Leaving
us only with CSS we need:

All JigSass Button classes are responsive-enabled, using
[JigSass MQ](https://txhawks.github.io/jigsass-tools-mq/) and the breakpoints defined in the
[$jigsass-breakpoints](https://txhawks.github.io/jigsass-tools-mq/#variable-jigsass-breakpoints)
variable.

Based enabled selectors in the [configuration map](https://txhawks.github.io/jigsass-objects-button#css-output), responsive modifiers are
generated according to the following logic:

```scss
.o-btn[--modifier][-[-from-{breakpoint-name}][-until-{breakpoint-name}][-misc-{breakpoint-name}]]
```

So, assuming the `medium`, `large` and `landscape` breakpoints are defined in `$jigsass-breakpoints`
as `600px`, `1024px` and `(orientation: landscape)` respectively,

```scss
$jigsass-btn-conf: (
  no-breakpoint: (
    outline: true,
  ),
  until-medium: (
    outline: true,
  ),
  from-large-when-landscape: (
    facebook: true,
  ),
)
```

will generate the following classes:
  - `.o-btn--outline`, which is not limited to any media-query.
  - `.o-btn--outline--until-medium`, which will be in effect at
    `(max-width: 37.49em)` and will override styles in the default class
    until that point.
  - `.o-btn--facebook--from-large-when-landscape`, which will go into effect at
    `(min-width: 64em) and (orientation: landscape)` and will override styles
    in the default class under these  conditions.


See the [full documentation](https://txhawks.github.io/jigsass-objects-button/) for more details.


## CSS Output

As mentioned above, By default, JigSass Button does not generate any CSS output when imported into
a stylesheet. CSS output must be enabled on a per-selector basis, inside the
dedicated configuration maps:

#### Buttons and modifier classes
```scss
$jigsass-btn-config
```


**Type:** `Map`

Configuration map for enabling generation of
button  button modifier classes.


**Default:** `()`


**Example:**
```scss
$jigsass-btn-conf: (
  no-breakpoint: (
    no-modifier: true,  // Enables generation of the `.o-btn`
                        // class outside of any media query.
    foo: true,          // Enables generation of the `.o-btn--foo`
                        // modifier class outside of any media query.
  ),
  from-<bp-name>: (
    no-modifier: true,  // Enables generation of the `.o-btn--from-<bp-name>`
                        // class inside a min-width media query
                        // defined ins `$jigsass-breakpoints.length`.
    foo: true,          // Enables generation of the `.o-btn--foo--from-<bp-name>`
                        // class inside a min-width media query
                        // defined ins `$jigsass-breakpoints.length`.
  ),
  until-<bp-name>: (
    no-modifier: true,  // Enables generation of the `.o-btn--until-<bp-name>`
                        // class inside a max-width media query
                        // defined ins `$jigsass-breakpoints.length`.
  foo: true,          // Enables generation of the `.o-btn--foo--until-<bp-name>`
                        // class inside a max-width media query
                        // defined ins `$jigsass-breakpoints.length`.
  ),
  when-<bp-name>: (
    no-modifier: true,  // Enables generation of the `.o-btn--when-<bp-name>`
                        // class inside a misc media query
                        // defined ins `$jigsass-breakpoints.features`.
    foo: true,          // Enables generation of the `.o-btn--foo--when-<bp-name>`
                        // class inside a misc media query
                        // defined ins `$jigsass-breakpoints.features`.
  ),
  from-<bp-name>-until-<bp-name>: (...);
  from-<bp-name>-when-<bp-name>: (...);
  until-<bp-name>-when-<bp-name>: (...);
  from-<bp-name>-until-<bp-name>-when-<bp-name>: (...);
);
```

#### Disabled buttons
```scss
$jigsass-btn-disabled-conf
```


**Type:** `Map`

Configuration map for enabling generation of
disabled button classes.


**Default:** `()`


**Example:**
```scss
$jigsass-btn-disabled-conf: (
  no-breakpoint: (
    no-modifier: true,  // Enables generation of the `.o-btn-is-disabled`
                        // class outside of any media query.
    foo: true,          // Enables generation of the `.o-btn-is-disabled--foo`
                        // modifier class outside of any media query.
  ),
  from-<bp-name>: (
    no-modifier: true,  // Enables generation of the `.o-btn-is-disabled--from-<bp-name>`
                        // class inside a min-width media query
                        // defined ins `$jigsass-breakpoints.length`.
    foo: true,          // Enables generation of the `.o-btn-is-disabled--foo--from-<bp-name>`
                        // class inside a min-width media query
                        // defined ins `$jigsass-breakpoints.length`.
  ),
  until-<bp-name>: (
    no-modifier: true,  // Enables generation of the `.o-btn-is-disabled--until-<bp-name>`
                        // class inside a max-width media query
                        // defined ins `$jigsass-breakpoints.length`.
  foo: true,          // Enables generation of the `.o-btn-is-disabled--foo--until-<bp-name>`
                        // class inside a max-width media query
                        // defined ins `$jigsass-breakpoints.length`.
  ),
  when-<bp-name>: (
    no-modifier: true,  // Enables generation of the `.o-btn-is-disabled--when-<bp-name>`
                        // class inside a misc media query
                        // defined ins `$jigsass-breakpoints.features`.
    foo: true,          // Enables generation of the `.o-btn-is-disabled--foo--when-<bp-name>`
                        // class inside a misc media query
                        // defined ins `$jigsass-breakpoints.features`.
  ),
  from-<bp-name>-until-<bp-name>: (...);
  from-<bp-name>-when-<bp-name>: (...);
  until-<bp-name>-when-<bp-name>: (...);
  from-<bp-name>-until-<bp-name>-when-<bp-name>: (...);
);
```

## Configuration

JigSass Button allows for some modification through configuration variables. 
Redefine them to your liking _before_ importing JigSass Buttons.


#### Button Padding
```scss
$jigsass-btn-padding
```

**Type:** `Map`

A map of button padding modifiers, each key should contain a list of two
unitless numbers, representing the number of rhythm units used as padding
on the horizontal and vertical axes, respectively.

**Default:** `(default: 2 1)`

**Properties:**

Name | Description | Type | Default Value
--- | --- | --- | ---
default | Sets the padding of default button object | List | 2 1

<p></p>

**Example:**
```scss
$jigsass-btn-padding: (
  default: 2 1,
  small: 1 0.5,
  large: 3 3,
);
```


#### Button Outline
```scss
$jigsass-btn-outline
```

**Type:** `List`

The border width and style (and optionally color) of outlined buttons (`.o-btn--outline`)

**Default:** `1px solid`


#### Button Style
```scss
$jigsass-btn-style
```

**Type:** `Map`

Style declarations to add to the `.o-btn` class.

**Default:** `()`

**Example:**
```scss
$jigsass-btn-style: (
  transition: all 0.25s ease-out,
);
```


#### Button Modifiers
```scss
$jigsass-btn-modifiers
```

**Type:** `Map`

CSS declarations for button modifiers, with each modifier being a nested
map at the first level.

**Default:** `()`

**Example:**
```scss
$jigsass-btn-modifiers: (
  primary: (
    background-color: #09a5d9,
    color: #fff,

    '&:hover, &:focus, &:active': (
      background-color: darken(#09a5d9, 5%),
    )
  ),
  facebook: (
    background-color: #3b5998,
    color: #fff,

    '&:hover, &:focus, &:active': (
      background-color: darken(#3b5998, 5%),
    )
  ),
  twitter: (
    background-color: #55acee,
    color: #fff,

    '&:hover, &:focus, &:active': (
      background-color: darken(#55acee, 5%),
    )
  ),
  gplus: (
    background-color: #dc4e41,
    color: #fff,

    '&:hover, &:focus, &:active': (
      background-color: darken(#dc4e41, 5%),
    )
  ),
);
```


#### Disabled Buttons
```scss
$jigsass-btn-disabled
```

**Type:** `Map`

Style declarations for the `.o-btn-is-disabled` class.

**Default:** `
```scss
(
  opacity: 0.4,
  cursor: default,
)
```


## Documentation

The full documentation was generated using mdcss, and is available at 
[https://txhawks.github.io/jigsass-objects-button/](https://txhawks.github.io/jigsass-objects-button/)

## Contributing

It is a best practice for JigSass modules to *not* automatically generate css on `@import`, but 
rather have the user explicitly enable the generation of specific styles from the module.

Contributions in the form of pull-requests, issues, bug reports, etc. are welcome.
Please feel free to fork, hack or modify JigSass Button in any way you see fit.

#### Writing documentation

Good documentation is crucial for usability, scalability and maintainability. When 
contributing, please do make sure that both its Sass functionality (functions, mixins, 
variables and placeholder selectors), as well as the CSS it generates (selectors, 
concepts, usage exmples, etc.) are well documented.

Jigsass Button uses Jonathan Neal's [mdcss](//github.com/jonathantneal/mdcss).

When styles and documentation comments are not automatically generated by your module on `@import`,
please use the `sgSrc/sg.scss` file to enable their generation.

In addition, any file in `sgSrc/assets` will be available for use in the style guide.


## File structure
```bash
┬ ./
│
├─┬ scss/ 
│ └─ index.scss # The module's importable file.
│
├─┬ sgSrc/      # Style guide sources
│ │
│ ├── sg.sccs   # It is a best practice for JigSass 
│ │             # modules to not automatically generate 
│ │             # css and documentation on `@import.` 
│ │             # Please use this file to enable css
│ │             # and documentation comments) generation.
│ │
│ └── assets/   # Files in `sgSrc/assets` will be 
│               # available for use in the style guide
│
└─┬ docs/      # Documention
  │
  └── styleguide/ # Generated documentation 
                  # of the module's CSS
```

**License:** MIT

