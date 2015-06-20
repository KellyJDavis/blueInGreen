# blueInGreen

A [Bower](http://bower.io/) packaged, Prolog-like logic programming language implemented in [ES6 JavaScript](https://people.mozilla.org/~jorendorff/es6-draft.html).

## Quick Start

```html
<script src="bower_components/blueInGreen/src/parser.js"></script>
<script src="bower_components/blueInGreen/src/interpreter.js"></script>
<script>
// Create prolog code indicating mother child relations
var rulesText = 'mother_child(stephanie, thorne).' +
                'mother_child(stephanie, kristen).' +
                'mother_child(stephanie, felicia).';

// Lex and parse the prolog code into rules
var rules = parser(lexer(rulesText)).parseRules();

// Create a database holding the rules
var db = new Database(rules);

// Create a prolog query asking who is kristen's mother
var goalText = 'mother_child(X, kristen)';

// Lex and parse the prolog query
var goal = parser(lexer(goalText)).parseTerm();

// Obtain the X variable of the goal
var x = goal.args[0]; // variable X

// Run the query against the database of rules and print the results
for (var item of db.query(goal)) {
    print(item);
    print('value of X = ' + goal.match(item).get(x));
}
</script>
```

## Inspiration and Implementation

The repository's name [blueInGreen](https://github.com/kdavis-mozilla/blueInGreen) is inspired by the tune "[Blue In Green](https://soundcloud.com/clintashlock/blue-in-green)" by Bill Evans and Miles Davis. The implementation is based off of the [curiosity-driven](https://github.com/curiosity-driven) [prolog-interpreter](https://github.com/curiosity-driven/prolog-interpreter).
