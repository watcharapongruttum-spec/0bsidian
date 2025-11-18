Angular considers almost all are components

![[Pasted image 20231118055820.png]]
# Create new component
Create Header component using CLI

```shell
ng generate component <directory name>/<component name>  --skip-tests

ng generate component components/header --skip-tests
ng g c components/header --skip-tests
```

**--skip-tests** = do not generate unit testing file

![[Pasted image 20231118060335.png]]

![[Pasted image 20231118060733.png]]

# Using components

import the component
**app.component.ts**
```ts
import { HeaderComponent } from './components/header/header.component';

... 

imports: [CommonModule, RouterOutlet, HeaderComponent],
```

call imported component using tag directive
**app.component.html**
```html
<app-header></app-header>
<h1>Hello World!!!</h1>
```

![[Pasted image 20231118060645.png]]


