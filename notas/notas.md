# 1. Importar archivos

> library.less Para archivos less, se compilara en el archivo final donde se lo importe.

```less
@import "library.less";
```

> Para que **_no se compile_** un archivo importado, poner guion bajo( \_ ) en el inico del nombre del archivo.

```less
@import "./ruta/_library.less";
//Este archivo no se compilara.
```

> importar archivos css.

```less
@import "typo.css";
// este archivo se compila en el archivo final less.
```

### 1.2 Opciones de importación

```less
@import (opcion1, opcion2) "filename.less";
```

> Pueden ir sin refencias (_Sin parentesis_) o usarse hasta dos opciones, depende de la opcion para que se compile o no en el archivo.

```less
@import (reference) "archivo.less";
// use un archivo Less pero no lo compila no lo incluye en el archivo less y css.

@import (inline) "archivo.less";
//incluya el archivo fuente en la salida css, pero no lo compila

@import (less) "archivo.less";
//trata el archivo como un archivo Less, sin importar la extensión del archivo

@import (css) "archivo.less";
//trata el archivo como un archivo css, sin importar la extensión del archivo

@import (once) "archivo.less";
//solo incluye el archivo una vez (este es el predeterminado)

@import (multiple) "archivo.less";
//incluye el archivo varias veces

@import (optional) "archivo.less";
//continuar compilando cuando no se encuentra el archivo
```

# 2. Variables

> una variables es un contenedor de un valor para reutilizarlo.
> Los colores deben ir en variables

```less
@var1: 10px;
@var2: @var1 + 10px;

//Usar asi:
#header {
  width: @var1;
  height: @var2;
}

// Compilara el css asi:
#header {
  width: 10px;
  height: 20px;
}
```

### 2.1 Constantes

> Se declaran igual que las variables pero se las usa para: **padding, margins, separaciones**

### 2.2 Anidaciones

> Referenciar al padre del elemento sin escribir otro elemento.  
> Para que no ponga espacios en las pseuduclases poner &

```less
ul {
  propiedad: valor1;
  propiedad: valor2;
  li {
    propiedad: valor1;
    propiedad: valor2;
    //Para que no ponga espacios en las pseuduclases poner &
    &:hover {
      propiedad: valor1;
      propiedad: valor2;
      //Pone hover en el elemento li
    }
  }
}

//imprime
ul {
  propiedad: valor1;
  propiedad: valor2;
}
ul li {
  propiedad: valor1;
  propiedad: valor2;
}
ul li:hover {
  // si no pongo el & dejaria un espacio entre li y :
  propiedad: valor1;
  propiedad: valor2;
}
```

> O tambien.

```less
.btn {
  propiedad: valor1;
  &:hover {
    // no es necesario poner (btn:hover)
    propiedad: valor1;
  }
  &--alert {
    // no es necesario poner (btn--hover)
    propiedad: valor1;
  }
}
//imprime
.btn {
  propiedad: valor1;
}
.btn:hover {
  propiedad: valor1;
}
.btn--alert {
  propiedad: valor1;
}
```
