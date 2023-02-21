
# Project Title

A brief description of what this project does and who it's for

# Modelo MVC 

MVC significa modelo (model) vista (view) controlador (controller). Esto es lo que significan cada uno de esos componentes. Modelo: El backend que contiene toda la lógica de datos Vista: El frontend o interfaz gráfica de usuario (GUI) Controlador: El cerebro de la aplicación que controla como se muestran los datos.

## Modelo de representación de los datos.

Las solicitudes del usuario en turno se enrutan a un controlador, el cual es el encargado directo de trabajar con el modelo para producir las acciones del usuario o recuperar los resultados de las consultas.

- El controlador elige la vista para mostrar al usuario y proporciona cualquier dato de modelo que sea necesario.

## Funcionalidades de la aplicación.

1.- El usuario interactúa con la interfaz de usuario de alguna forma (por ejemplo, el usuario pulsa un botón, enlace, etc.)

2.- El controlador recibe (por parte de los objetos de la interfaz-vista) la notificación de la acción solicitada por el usuario. El controlador gestiona el evento que llega, frecuentemente a través de un gestor de eventos (handler) o callback.

3.-El controlador accede al modelo, actualizándolo, posiblemente modificándolo de forma adecuada a la acción solicitada por el usuario (por ejemplo, el controlador actualiza el carro de la compra del usuario). Los controladores complejos están a menudo estructurados usando un patrón de comando que encapsula las acciones y simplifica su extensión.

4.- El controlador delega a los objetos de la vista la tarea de desplegar la interfaz de usuario. La vista obtiene sus datos del modelo para generar la interfaz apropiada para el usuario donde se refleja los cambios en el modelo (por ejemplo, produce un listado del contenido del carro de la compra). El modelo no debe tener conocimiento directo sobre la vista. Sin embargo, se podría utilizar el patrón Observador para proveer cierta indirección entre el modelo y la vista, permitiendo al modelo notificar a los interesados de cualquier cambio. Un objeto vista puede registrarse con el modelo y esperar a los cambios, pero aun así el modelo en sí mismo sigue sin saber nada de la vista. 
El controlador no pasa objetos de dominio (el modelo) a la vista aunque puede dar la orden a la vista para que se actualice. Nota: En algunas implementaciones la vista no tiene acceso directo al modelo, dejando que el controlador envíe los datos del modelo a la vista.

5.-La interfaz de usuario espera nuevas interacciones del usuario, comenzando el ciclo nuevamente.

## Infraestructura y recuperación de datos

Consiste en un patrón de diseño de software que se utiliza para separar en tres componentes los datos, la metodología y la interfaz gráfica de una aplicación. La gran ventaja que posee esta técnica de programación es que permite modificar cada uno de ellos sin necesidad de modificar los demás, lo que permite desarrollar aplicaciones modulares y escalables que se puedan actualizar fácilmente y añadir o eliminar nuevos módulos.

## Ejemplos:

### **VISTA**
~~~
<html>
   <head>
      <title>ABARROTES JUAN</title>
   </head>
   <body>
     <h1>productos dados de alta en nuestra tienda</h1>
     <table border="1">
        <tr>
           <th>NOMBRE</th>
           <th>PRECIO</th>
        </tr>
~~~

### **MODELO**
~~~
<?php
   $db = new PDO('mysql:host=localhost;dbname=juan', 'comprador', 'proweb2013');
   $result = $db->query('SELECT nombre, precio FROM productos');
   while ($producto = $result->fetch()) { }
function getproducto($id)
{
   $db = getConnection();
   $query = 'SELECT * FROM productos WHERE id = ?';
   $stmt = $db->prepare($query);
   $stmt->execute(array($id));
   $producto = $stmt->fetch();
   return $producto;
}
?>
~~~
### **CONTROLADOR**
~~~
<?php
   // modelo
   require 'model.php';
   // un array con todos los productos del modelo
   //La vista recibe un array para mostrarlo por pantalla
   include 'view.php';
?>
function ver ()
{
   if ( !isset ( $_GET [ 'id' ] ) )
      die("No has especificado un identificador de producto.");
   $id = $_GET [ 'id' ];
   //Incluimos el modelo
   require 'models/productos_model.php';
   //Le pide al modelo el producto con id = $id
   $producto = getproducto($id);
   if ($producto === null)
      die("Identificador de producto incorrecto");
   //Pasamos a la vista toda la información que se desea representar
   include('views/productos_ver.php');
}
~~~


# Vista

Vista: La vista es la presentación al usuario de la información contenida en el modelo. Esto generalmente consiste en pantallas que contienen información del modelo. Los datos pueden mostrarse en campos, en ventanas de editor, en tablas, etc. Además, los datos pueden ser de solo lectura o pueden ser editables.

### Ejemplo 
~~~
<html>
   <head>
      <title>ABARROTES JUAN</title>
   </head>
   <body>
     <h1>productos dados de alta en nuestra tienda</h1>
     <table border="1">
        <tr>
           <th>NOMBRE</th>
           <th>PRECIO</th>
        </tr>
~~~

![ Imagen ](https://th.bing.com/th/id/R.da1acec1594bcae30786fae5fcb9e49a?rik=85Hv9Uw7xALbEQ&riu=http%3a%2f%2fwww.microsiervos.com%2fimages%2fAmazonES-home.jpg&ehk=jAsgTgsSYBezIYZ%2b860Ssd%2fzBPo7P91hsWwEPsoAxy4%3d&risl=&pid=ImgRaw&r=0)

## Controlador

#### Lógica de negocio / Lógica de la aplicación

Es un conjunto de reglas que se siguen en el software para reaccionar ante distintas situaciones. En una aplicación el usuario se comunica con el sistema por medio de una interfaz, pero cuando acciona esa interfaz para realizar acciones con el programa, se ejecutan una serie de procesos que se conocen como la lógica del negocio. Este es un concepto de desarrollo de software en general.

La lógica del negocio, aparte de marcar un comportamiento cuando ocurren cosas dentro de un software, también tiene normas sobre lo que se puede hacer y lo que no se puede hacer. Eso también se conoce como reglas del negocio. Bien, pues en el MVC la lógica del negocio queda del lado de los modelos. Ellos son los que deben saber cómo operar en diversas situaciones y las cosas que pueden permitir que ocurran en el proceso de ejecución de una aplicación.

![imagen](https://desarrolloweb.com/archivoimg/general/2758.jpg)
