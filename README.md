# gifs-app

# Creación del proyecto

Aunque este ejemplo está creado con `Angular 17`, se va a usar una arquitectura modular por el momento.

```bash
$> ng new gifs-app --no-standalone
```

La innovación de no usar módulos la dejo para ejemplos futuros.

# Estructura del proyecto

Como se ha indicado en el punto anterior, se van a definir módulos funcionales (que pueden ejecutarse de forma independiente)

* `gifs`: Módulo que contendrá todo lo relacionado con los GIFs
* `shared`: Elementos comunes a más de un módulo


¿Cómo crear un módulo? Desde la raíz del proyecto

```bash
$> ng g m gifs
CREATE src/app/gifs/gifs.module.ts (202 bytes)
$> ng generate module shared
CREATE src/app/shared/shared.module.ts (204 bytes)
```

¿Cómo crear componentes? Desde el directorio `app`

```bash
$> ng g component shared/components/sidebar
CREATE src/app/shared/components/sidebar/sidebar.component.html (23 bytes)
CREATE src/app/shared/components/sidebar/sidebar.component.spec.ts (631 bytes)
CREATE src/app/shared/components/sidebar/sidebar.component.ts (213 bytes)
CREATE src/app/shared/components/sidebar/sidebar.component.css (0 bytes)
UPDATE src/app/shared/shared.module.ts (304 bytes)
```

De este modo se genera el componente Sidebar dentro del módulo `shared`

Otro ejemplo es: 

```bash
$> ng g component gifs/pages/home-page
CREATE src/app/gifs/pages/home-page/home-page.component.html (25 bytes)
CREATE src/app/gifs/pages/home-page/home-page.component.spec.ts (639 bytes)
CREATE src/app/gifs/pages/home-page/home-page.component.ts (220 bytes)
CREATE src/app/gifs/pages/home-page/home-page.component.css (0 bytes)
UPDATE src/app/gifs/gifs.module.ts (384 bytes)
```

# Decorador View Child

Este decorador permite recoger elementos HTML del componente.

Por ejemplo: dado un `input` identificado como `txtTagInput`, se desea recoger su `value` e imprimirlo por consola cuando se pulse `Enter`. El decorador `@ViewChild` permite recuperar en el `TS` el elemento `HTML`

```typescript
export class SearchBoxComponent {

  @ViewChild('txtTagInput')
  public tagInput!: ElementRef<HTMLInputElement>;

  searchTag () {
    const newTag = this.tagInput.nativeElement.value;
    console.log({ newTag });
  }

}
```

```html
<input type="text"
  class="form-control"
  placeholder="Buscar gifs..."
  (keyup.enter)="searchTag()"
  #txtTagInput
>	
```

Es importante ver cómo el `TS` y el `HTML` son interdependientes.

# Services

Como se explicó en el curso anterior, los **services** permiten la gestión de datos. En este caso, se crean a nivel de módulo y su estructura básica es sencilla:

```typescript
@Injectable({providedIn: 'root'})
export class GifsService {
  constructor() { }
}
```
