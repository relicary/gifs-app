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
```


