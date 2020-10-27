# import/newline-after-import

Enforces having one or more empty lines after the last top-level import statement or require call.
+(fixable) The `--fix` option on the [command line] automatically fixes problems reported by this rule.

## Rule Details

This rule accepts two options,

1. `count` which sets the number of newlines that are enforced after the last top-level import statement or require call. The number of newlines should be greater than or equal to `count`. This option defaults to `1`.

2. `exactCount` which enforce the exact numbers of newlines that is mentioned in `count`. This option defaults to `false`.


Valid:

```js
import defaultExport from './foo';

const FOO = 'BAR';
```

```js
import defaultExport from './foo';
import { bar }  from 'bar-lib';

const FOO = 'BAR';
```

```js
const FOO = require('./foo');
const BAR = require('./bar');

const BAZ = 1;
```

Invalid:

```js
import * as foo from 'foo'
const FOO = 'BAR';
```

```js
import * as foo from 'foo';
const FOO = 'BAR';

import { bar }  from 'bar-lib';
```

```js
const FOO = require('./foo');
const BAZ = 1;
const BAR = require('./bar');
```

With `count` set to `2` this will be considered valid:

```js
import defaultExport from './foo';


const FOO = 'BAR';
```

```js
import defaultExport from './foo';



const FOO = 'BAR';
```

With `count` set to `2` these will be considered invalid:

```js
import defaultExport from './foo';
const FOO = 'BAR';
```

```js
import defaultExport from './foo';

const FOO = 'BAR';
```

With `count` set to `2` and `exactCount` set to `true` this will be considered valid:

```js
import defaultExport from './foo';


const FOO = 'BAR';
```

With `count` set to `2` and `exactCount` set to `true` these will be considered invalid:

```js
import defaultExport from './foo';
const FOO = 'BAR';
```

```js
import defaultExport from './foo';

const FOO = 'BAR';
```

```js
import defaultExport from './foo';



const FOO = 'BAR';
```

```js
import defaultExport from './foo';




const FOO = 'BAR';
```

## Example options usage
```json
{
  "rules": {
    "import/newline-after-import": ["error", { "count": 2 }]
  }
}
```


## When Not To Use It

If you like to visually group module imports with its usage, you don't want to use this rule.
