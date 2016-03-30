# Modulo de Odoo
---
##Comenzamos el tutorial del modulo de odoo para la versión 9.0 

 Lo primero que debemos hacer es abrir la terminal turkey postgres y ahí obtener la dirección IP Después abrimos un putty con esta dirección y nos logueamos.
Ahora lo que debemos hacer es ir a la carpeta addons :
cd opt/odoo/addons
ahí pondremos :
./odoo.py scaffold openacademy addons ,
esto nos creara en addons una carpeta llamada openacademy podremos verlo con ls.

Ahora vamos al proyecto
Creamos el proyecto de netbeans 

1. Php aplication from remote server  next
2. Cambiamos el nombre del proyecto y next
3. En Project URLEscribimos la dirección IP y editamos manage:
4. Creamos una conexión SFTP si no la tenemos y rellenamos el formulario
5. Ahora comprobamos la conexión y ok
6. En upload directory pondremos la dirección de addons y le damos a next
7. Nos saldrán unas carpetas y elegimos solo la de openacademy

y listo ya tenemos el proyecto creado.

##Definimos un Modelo
Vamos a definir el modelo llamado Course. El curso tiene un titulo (obligatorio) y una descripción.
Para ello editamos el archivo models.py

##Definimos los datos de demostración.
Creamos unos datos como ejemplo cumpliendo el modelo Courses con unos pocos cursos de demostración
Para ello editamos el archivo demo.xml 

##Definimos nuevas entradas de menú
Definimos estas entradas para acceder Courses y Sessions desde el menú de Open Academy.El usuario podrá ver todos los cursos y crear/editar cursos.

Crear el archivo openacademy.xml  y modificar el código data de  __openerp__.py 

##Editar form view usando XML
Views define la forma en que se muestran los registros de un modelo. LA vista es declarada como un registro del modelo ir.ui.view. El campo arch indica que tipo de vista va a tener el modelo (el campoarch debe ser declarado como type=”xml”) . Podremos elegir varios tipos form,tree,graph etc


Tree views muestra los registros de la tabla y Forms se usa para crear y editar esos registros

Creamos nuestra vista de course que mostrara los nombres y las descripciones.

##Notebooks
En el form view del curso pondremos la descripción de campo en otra etiqueta, después sera fácil añadir otras tablas que añadan información.
Modificamos el openacademy.xml


##Buscar los cursos
Los podremos encontrar por su titulo o descripción
Modificaremos de nuevo opneacademy.xml


#Relaciones entre modelos

##Creamos un modelo Session
Este modelo permitirá apuntarse a personas en los cursos y podrán elegir el día la duración y el numero de asientos. Para ello tendrá que escribir su nombre

* Creamos la clase Session en models.py
* Añadimos el acceso a la session en openacademy.xml

##Relaciones Many2one
Usando many2one ,modificamos los modelos curso y sesión para reflejar la relación con otros modelos
* Cada curso tiene un usuario responsable; el valor del campo es un registro del modelo incorporado res.users. 
* Cada sesión tiene un instructor; el valor del campo es un registro del modelo incorporado res.partner. 
* Cada sesión se relaciona con un curso; el valor del campo es un registro del modelo openacademy.course y es necesario. 
*Adaptamos la vista

1. Modificamos el models.py y le añadimos los many2one relevantes
2. Los añadimos en openacademy.xml en las vistas

##Relaciones One2many
Es la inversa de many2one , modifica los modelos para reflejar la relacione entre cursos y sesiones

1. modificamos la clase course
2.Añadimos el campo en la vista

##Relación múltiple many2many
Cada registro de un modelo puede relacionarse con cualquier numero de registros del otro modelo.

Usamos many2many, para modificar el modelo Session  y así relacionar cada sesión con unos asistentes. Los asistentes serán representados por un registro.

* Modificamos la clase Session
*añadimos a la vista

##Editar el contenido existente
* Ahora usaremos el modelo herencia para modificar el modelo del socio y añadiremos un instructor de tipo booleano, y usaremos many2many para relacionar la sesión con el socio
* Usaremos la vista de herencia, para que se vean las casillas

Para ello:
1. Crearemos un fichero partner.py y lo añadiremos al __inti__.py
2.Crearemos un fichero partner.xml y lo añadiremos al  __openerp__.py 

##Dominios en los campos relacionales
Cuando seleccionamos el instructor en la session, solo los instructores(instructor=True) deben ser visibles

##Dominios mas complejos
Creamos un nuevo socio con categorías Teacher / Level 1 y Teacher / Level 2. 
El instructor puede ser instructor o profesor dependiendo de la session

1. Modificamos el dominio en la sesión en models.py
2.Modificamos partner xml para obtener el acceso a las categorías del asociado

## Campos computados
* Añadimos el porcentaje de coger sitios en la session
* Lo mostramos en las vistas
* Creamos la barra de porcentaje
 
1. Añadimos un campo computado a la session en models.py
2. Mostramos el campo en la vista en openacademy.xml

##Valores por defecto
 Marcaremos por defecto la fecha de hoy a crear la session
* Para ello definimos start_date como today 
* Añadiremos el campo active en la clase session,y pondremos la session active por defecto ##Relaciones Many2one
Usando many2one ,modificamos los modelos curso y sesión para reflejar la relación con otros modelos
* Cada curso tiene un usuario responsable; el valor del campo es un registro del modelo incorporado res.users. 
* Cada sesión tiene un instructor; el valor del campo es un registro del modelo incorporado res.partner. 
* Cada sesión se relaciona con un curso; el valor del campo es un registro del modelo openacademy.course y es necesario. 
*Adaptamos la vista

1. Modificamos el models.py y le añadimos los many2one relevantes
2. Los añadimos en openacademy.xml en las vistas
