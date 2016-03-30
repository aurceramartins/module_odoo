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
