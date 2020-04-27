#  Variables en JavaScript.

## Concepto de ámbito de variables.

Se le llama ámbito de las variables al lugar donde estas están disponibles. Por lo general, cuando declaramos una variable hacemos que esté disponible en el lugar donde se ha declarado, esto ocurre en todos los lenguajes de programación y como Javascript se define dentro de una página web, las variables que declaremos en la página estarán accesibles dentro de ella.

En Javascript no podremos acceder a variables que hayan sido definidas en otra página. Por tanto, la propia página donde se define es el ámbito más habitual de una variable y le llamaremos a este tipo de variables globales a la página. Veremos también se pueden hacer variables con ámbitos distintos del global, es decir, variables que declararemos y tendrán validez en lugares más acotados.

### Variables Globales.
Las variables globales son las que están declaradas en el ámbito más amplio posible, que en Javascript es una página web. Para declarar una variable global a la página simplemente lo haremos en un script, con la palabra var.

```javascript
 <SCRIPT> 
var variableGlobal 
</SCRIPT> 
```
Las variables globales son accesibles desde cualquier lugar de la página, es decir, desde el script donde se han declarado y todos los demás scripts de la página, incluidos los manejadores de eventos, como el onclick, que ya vimos que se podía incluir dentro de determinadas etiquetas HTML.

### Variables Locales.

 A estas variables les llamaremos locales. Cuando se declaren variables locales sólo podremos acceder a ellas dentro del lugar donde se ha declarado, es decir, si la habíamos declarado en una función solo podremos acceder a ella cuando estemos en esa función.

Las variables pueden ser locales a una función, pero también pueden ser locales a otros ámbitos, como por ejemplo un bucle. En general, son ámbitos locales cualquier lugar acotado por llaves.

```javascript
 <SCRIPT> 
function miFuncion (){ 
    var variableLocal 
} 
</SCRIPT>
```
No hay problema en declarar una variable local con el mismo nombre que una global, en este caso la variable global será visible desde toda la página, excepto en el ámbito donde está declarada la variable local ya que en este sitio ese nombre de variable está ocupado por la local y es ella quien tiene validez. 
```javascript
<SCRIPT> 
var numero = 2 
function miFuncion (){ 
    var numero = 19 
    document.write(numero) //imprime 19 
} 
document.write(numero) //imprime 2 
</SCRIPT>
```
### Diferencias entre declarar variables con var, o no declararlas.
En concreto, cuando utilizamos var estamos haciendo que la varible que estamos declarando sea local al ámbito donde se declara. Por otro lado, si no utilizamos la palabra var para declarar una variable, ésta será global a toda la página, sea cual sea el ámbito en el que haya sido declarada.

# Ambito de la variable (Scope)
El ámbito de una variable (llamado "scope" en inglés) es la zona del programa en la que se define la variable. JavaScript define dos ámbitos para las variables: global y local.

 Ejemplo ilustra el comportamiento de los ámbitos:

 ~~~JavaScript
 function creaMensaje() {
  var mensaje = “Mensaje de prueba”;
}
creaMensaje();
alert(mensaje);
 ~~~


# ¿Qué es Hoisting?

En JavaScript existen variables globales, las cuales tienen sus ventajas en un lenguaje como este, pero también están llenas de peligros, y variables locales, cuyo ámbito se circunscribe exclusivamente a las funciones en las que se declaran.

Podemos utilizar una variable global desde dentro de una función cualquiera, ya que están accesibles desde cualquier lugar de la página, por ejemplo:

~~~JavaScript
//Variable global
var name = "Jose";

function HelloWorld(){
  alert(name);
}

HelloWorld();
~~~
 Al hacer esto  nos saldra el mensaje con el nombre que hay en la variable, pero que pasa si hacemos esto.  


 ~~~JavaScript
 //Variable global
var name = "Jose";

function HelloWorld(){
  //Variable local
  var name = "Pepe";
  alert(name);
}

HelloWorld();
 ~~~

 Las reglas de precedencia de variables en JavaScript dicen que las variables locales preceden a las globales, por lo que en este caso veríamos aparecer por pantalla la palabra “Pepe” que es el valor de la variable local.

### El efecto de Elevacion.

Aunque JavaScript es un lenguaje interpretado y procesa las líneas de código una a una según se las va encontrando, en realidad no es del todo así. En el caso de las variables que hay dentro de una función lo que hace el intérprete es declararlas todas a la vez al principio de la función, independientemente de donde estén realmente declaradas dentro de ésta.