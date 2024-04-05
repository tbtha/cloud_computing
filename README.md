# cloud_computing

#### CLIENTE-SERVIDOR
~~~
Un CLIENTE puede ser un navegador web o una app de escritorio, con la que interactua una persona para realizar
	solicitudes a los servidores de computo un cliente solicita un articulo de noticias, puntuacion de un juego,etc
Un SERVIDOR puede ser un servicio como Amazon Elastic Compute Cloud (Amazon EC2), un tipo de servidor virtual.
	el servidor evalua los detalles de la solicitud y la cumple al devolver la informacion del cliente
		*Es un aparato informático que almacena, distribuye y suministra información
~~~

#### CLOUD 
~~~
***Recursos TI : software y hadware utilizados para : almacenamiento, cómputo, redes,
bases de datos, analítica, machine learning, Internet de las cosas, seguridad,
desarrollo, entre otras
	
*Como usuario podemos acceder a AWS x :
	-AWS Management Console (protected by password + MFA)
	-AWS Command Line Intefaces (CLI): protected by access keys (herramienta que permite interactuar con los servicios de AWs mediante comandos en una shell de linea de comandos )
	-AWS Software Developer Kit (SDK): for code : protected by acces keys (para llamar a las API de AWS desde el cod de su app)
	Estos estan protegidos por la misma clave de acceso, generamos las claves de acceso en la consola de administracion recordar mantener secreta su 
		-Access Key ID
		-Secret Access Key 
		
Para utilizar la CLI b: "install AWS CLI in windows" descargar de la pag, aceptar los terminos y verificar si se instalo correctamente revisando la version con aws --version 
*Para actualizar es necesario volver a descargar el AWS CLI MSI y volver a ejecutar 
	-indicaciones de configuracion y de uso en el modulo 6 IAM
	

IMPLEMENTACION CLOUD

>Basada en la nube / All-in cloud
	Todas sus aplicaciones se implementan completamente en la nube.
	Puede crear esas aplicaciones en una infraestructura de bajo nivel que requiere que el personal de TI las administre.
	De forma alternativa, puede crearlas mediante servicios de nivel superior que reducen los requisitos de administración,
		 arquitectura y escalado de la infraestructura principal.
	*Por ejemplo, una empresa podría crear una aplicación compuesta por servidores virtuales, bases de datos
		 y componentes de red totalmente basados en la nube.
>En las instalaciones / nube privada / on premises 
	Los recursos se implementan en las instalaciones locales mediante herramientas de virtualización y administración de recursos.
	*Por ejemplo, es posible que tenga aplicaciones que se ejecutan con tecnología que se almacena por completo 
		en su centro de datos local.
>Hibrida 
	Algunas de sus aplicaciones se implementan en la nube, pero otras permanecen en las instalaciones. Las aplicaciones aún pueden conectarse entre sí.
	Conecte los recursos basados en la nube a la infraestructura en las instalaciones locales.
	*Por ejemplo con una implementación híbrida, la empresa podría mantener las aplicaciones heredadas en las 
		instalaciones y beneficiarse de los servicios de datos y análisis que se ejecutan en la nube.

BENEFICIOS / VENTAJAS 
>Cambiar gastos iniciales por gastos variables 
	gastos iniciales = centro de datos, servidores fisicos y otros recursos en los que tendria que invertir antes de utilizarlos 
	gatos variables = solo paga por los recurso de computo que consume 

>Gaste estratégicamente / Deja de gastar dinero en la ejecucion y el mantenimiento de centro de datos
	Los centro de datos requieren mas gasto y tiempo en administrar la infraestructura y los servidores
		la idea es centrarse mas en las aplicaciones y los clientes 

>Planificación de la capacidad /Deja de adivinar la capacidad 
	No tiene que predecir cuánta capacidad de infraestructura necesitará antes de implementar una aplicación, 
		puede aumentar o disminuir la capacidad de computo en minutos de acuerdo a la demanda 

>Economias de escala 
	El uso agregado de la nube por parte de un gran número de clientes se traduce en menores precios de pago por uso.
	 AWS le transfiere ahorros a medida que los clientes aumentan.

>Aumentar la velocidad y la agilidad
	Aprovisione recursos de forma rápida y bajo demanda.
	El cómputo en la nube le permite acceder a nuevos recursos y disponibilidad en cuestión de minutos
		 en un centro de datos fisico esto seria en cuestion de semanas 
	La flexibilidad facilita el desarrolo y la implementacion de app

> Globalizarse en minutos 
	Le permite implementar rápidamente aplicaciones a clientes de todo el mundo, a la vez que les proporciona una
		 latencia baja utilizando la infraestructura global 
~~~
