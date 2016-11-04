#jspm and system.js tutorial

1. install and init jspm

```bash
  npm install jspm -g
  mkdir my-app && cd my-app
  jspm init
```

2. install packages

```bash
  jspm install npm:lodash-node
  jspm install aweful=github:jon-schmidt/aweful
```

3. my application

lib/fuckingwhatever.js

```javascript
  import aweful from 'aweful';

  export function fuckingWhatever () {

  }

```

lib/main.js

```javascript
  import {fuckingWhatever} from './fuckingwhatever.js';

  fuckingWhatever();
```

build/index.html

```html
<!DOCTYPE html>
<html>
  <script src='jspm_packages/system.js'></script>
  <script src='config.js'></script>
  <script>
    System.import('lib/main.js');
  </script>
</html>
```
