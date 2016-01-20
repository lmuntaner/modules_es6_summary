# Understanding modules in ES6

Summary to understand different ways to export and import in ES6. Almost no explanation just a small summary.

### Summary Table

| Export Modules | Import Modules | Result |
| --- | --- | --- |
| `export const some = 1;` `export const some = 1;` | `import * as h from 'file.js';` | `// h = { some: 1, other: 2 }` |
| `export const some = 1;` `export const some = 1;` | `import { some, other } from 'file.js';` | `// some = 1;` `// other = 2;` |
| `export const some = 1;` `export const some = 1;` | `import some from 'file.js';` | `// some is undefined` |
| `export const some = 1;` `export const some = 1;` `export default some;` | `import * as h from 'file.js';` | `// h = { some: 1, other: 2, default: 1 }` |
| `export const some = 1;` `export const some = 1;` `export default some;` | `import { some, other } from 'file.js';` | `// some = 1;` `// other = 2;` |
| `export const some = 1;` `export const some = 1;` `export default some;` | `import any from 'file.js';` | `// some = 1;` |

---
### Without using default

**Export**

This represents the export command in a `file.js`

- Named Exports:

```
export const some = 1;
export const other = 2;
```
- All at once:

```
const some = 1;
const other = 2;
export { some, other };
```
*This two ways of exporting give the same results*

**Import**

- Using `*` when importing:

```
import * as h from 'file.js';
//=> h = { some: 1, other: 2 }
```

- Using object deconstruction:

```
import { some, other } from 'file.js';
// some = 1
// other = 2
```

- Assuming default:

```
import some from 'file.js';
// some is 'undefined'
```

---
### Using default

**Export**

- Adding `export default`

```
export const some = 1;
export const other = 2;
export default some;
```

**Import**

- Using ```*``` when importing:

```
import * as h from 'file.js';
//=> h = { some: 1, other: 2, default: 1 }
```
*Adds a ```default``` key to the object with the value of the defaulted value*

- Using object deconstruction:

```
import { some, other } from 'file.js';
// some = 1
// other = 2
```
*Nothing changes here*

- Assuming default:

```
import any from 'file.js';
// any = 1
```
*Even though the name of the variable is different - some vs any - that doesn't matter since it's the value that gets imported and attached to the variable*