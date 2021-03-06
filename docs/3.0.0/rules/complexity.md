---
title: complexity - Rules
layout: doc
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# Limit Cyclomatic Complexity (complexity)

Cyclomatic complexity measures the number of linearly independent paths through a program's source code. This rule allows setting a cyclomatic complexity threshold.

```js
function a(x) {
    if (true) {
        return x; // 1st path
    } else if (false) {
        return x+1; // 2nd path
    } else {
        return 4; // 3rd path
    }
}
```

## Rule Details

This rule is aimed at reducing code complexity by capping the amount of cyclomatic complexity allowed in a program. As such, it will warn when the cyclomatic complexity crosses the configured threshold (default is `20`).

Examples of **incorrect** code for a maximum of 2:

```js
/*eslint complexity: ["error", 2]*/

function a(x) {
    if (true) {
        return x;
    } else if (false) {
        return x+1;
    } else {
        return 4; // 3rd path
    }
}
```

Examples of **correct** code for a maximum of 2:

```js
/*eslint complexity: ["error", 2]*/

function a(x) {
    if (true) {
        return x;
    } else {
        return 4;
    }
}
```

## Options

Optionally, you may specify a `max` object property:

```json
"complexity": ["error", 2]
```

is equivalent to

```json
"complexity": ["error", { "max": 2 }]
```

**Deprecated:** the object property `maximum` is deprecated. Please use the property `max` instead.

## When Not To Use It

If you can't determine an appropriate complexity limit for your code, then it's best to disable this rule.

## Further Reading

* [Complexity Analysis of JavaScript Code](http://ariya.ofilabs.com/2012/12/complexity-analysis-of-javascript-code.html)

## Related Rules

* [max-depth](max-depth)
* [max-len](max-len)
* [max-nested-callbacks](max-nested-callbacks)
* [max-params](max-params)
* [max-statements](max-statements)

## Version

This rule was introduced in ESLint 0.0.9.

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/complexity.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/complexity.md)
