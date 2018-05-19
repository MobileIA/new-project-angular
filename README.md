# Nuevo proyecto en Angular
Pasos para la creación de un proyecto en Angular.

1. Instalar AngularCLI, si todavia no lo tienes instalado:
```bash
npm install -g @angular/cli
```
2. Crear nueva aplicación:
```bash
ng new name-of-project
```
3. Ejecutar proyecto para poder verlo en el navegador y realizar las pruebas:
```bash
cd name-of-project
ng serve --open
```

# Como crear un nuevo componente:
1. Ejecutar siguiente comando:
```bash
ng generate component name-of-component
```

# Como usar Routing:
1. Abrir archivo: app.module.ts
```js
// Agregar import arriba de todo
import { RouterModule, Routes } from '@angular/router';
```
2. Crear constante para almacenar las rutas:
```js
const routes:Routes = [
  { 
    path: 'create', 
    component: CreateComponent 
  },
  {
    path: 'edit/:id',
    component: EditComponent
  },
  { 
    path: 'index',
    component: IndexComponent
  }
];
```
3. Importar modulo de Router con los valores generados:
```js
imports: [
    BrowserModule,
    RouterModule.forRoot(routes)
],
```
4. Agregar en el archivo: "app.component.html", que va a representar donde se cargaran los componentes:
```html
<div>
  <router-outlet></router-outlet>
</div>
```
5. Como obtener parametro desde la URL:
```js
export class EditComponent implements OnInit {

    game: any = {};

    constructor(private route: ActivatedRoute, 
            private router: Router) { 
    }

    ngOnInit() {
        this.route.params.subscribe(params => {
        
                var idGame = params['id'];

    });
  }
}
```

# Como agregar Bootstrap:
1. Descargamos los archivos desde la web: https://getbootstrap.com/docs/4.1/getting-started/download/
2. Copiamos los archivos descargados dentro de la carpeta "assets".
3. Agregamos enlace al CSS en el archivo "index.html"
```html
<link rel="stylesheet" href="assets/css/bootstrap.min.css">
```

# Activar modulo para realizar peticiones HTTP:
1. Importar modulo (HttpClientModules) en el archivo "app.module.ts":
```js
import { HttpClientModule } from '@angular/common/http';

imports: [
    BrowserModule, RouterModule.forRoot(appRoutes), HttpClientModule
],
```


# Como crear un nuevo servicio:
1. Ejecutar siguiente comando:
```bash
ng generate service name-of-service
```
2. Agregar servicio al modulo: app.modules.ts:
```ts
providers: [
    YourServiceService,
    /* . . . */
  ],
```
3. Agregar la libreria para realizar una petición en el Servicio o Componente:
```js
import { HttpClient } from '@angular/common/http';
```
4. Recibir modulo desde el constructor del servicio, para poder utilizarlo:
```js
constructor(private http: HttpClient) { }
```
5. Ejemplo de como se realiza una petición:
```js
addGame(name, price) {
    const uri = 'http://localhost:4000/games/add';
    const obj = {
      name: name,
      price: price
    };
    this.http.post(uri, obj)
        .subscribe(res => console.log('Done'));
  }
```


# Como usar formularios:
1. Importar libreria:
```js
import { ReactiveFormsModule } from '@angular/forms';

imports: [
    ReactiveFormsModule
  ],
```
2. Importar libreria en el componente:
```js
import { FormGroup,  FormBuilder,  Validators } from '@angular/forms';
```


# Compilar proyecto:
1. Ejecutar siguiente comando:
```bash
ng build --prod
```

# Recursos disponibles:
1. Plataforma para generar documentación de un proyecto Angular facilmente: https://compodoc.github.io/compodoc/