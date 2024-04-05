# cloud_computing

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
#### AWS Identify and Access Management AWS IAM (Politicas de IAM)/ AWS Organizations ( Politicas de control de servicios (SCPs) )
#### AWS SHIELD / AWS WAF / AWS Key Management Services (AWS KMS)  
~~~
>>>Modelo de responsabilidad compartida 

CLIENTE, responsable de la seguridad EN la nube 
	Son responsable de todo lo que crean y almacenan en la nube 
		controla cómo se conceden, administran y revocan los derechos de acceso.
	Capas a cargo : SISTEMA OPERATIVO / APLICACIONES / DATOS

AWS, responsable de la seguridad DE la nube
	Aws opera, administra y controla los componentes en todos los niveles de la infraestructura.
	Capas a cargo : FISICO / RED / HIPERVISOR 
	

Al crear una cuenta en AWs, se recibe el usuario ROOT/RAIZ de la cuenta, quien es el propietario y tiene acceso 
	y control de cualquier recurso de la cuenta 
*Se recomienda activar la autenticacion multi-factor (MFA) para que al iniciar sesion deba ingresar
	correo, contraseña y un token aleatorio
*No utilice el usuario raíz para las tareas cotidianas. 
Tareas que requieren el uso de credenciales de usuario ROOT 
	Cambiar el plan de soporte de AWS
	Eliminar cuentas de AWs 

		Para controlar el acceso a la cuenta:
>>>>>>>>>> AWS Identify and Access Management AWS IAM <<<<<<<<<<< SERVICIO GLOBAL
IAM -> Autenticacion y autorizacion como servicio, permite administrar el acceso a los servicios y recursos de AWS de forma segura.

*Root , se crea por defecto, debe ocupar root solo para fines especificos 
*Users, son personas parte de la organizacion , estas se pueden organizar en grupos
*Gruops, conjunto de usuarios, solo contiene users , no otros grupos(sirve para facilitar la administracion)
POR QUE CREAMOS USUARIOS/GRUPOS? 
A los usuarios o grupos podemos asignarles documentos JSON que son "politicas", estas politicas definen los permisosque tendran esos users, de forma predeterminada se deniegan todos los permiso, explicitamente hay que
	darle permisos para que puedan acceder a los recursos (PRINCIPIO DE MENOR PRIVILEGIO: un usuario solo tiene acceso a lo que realmente necesita)

>>> Politicas de IAM -> es un documento JSON que describe que llamadas a la API un usuario puede o no hacer 
			documento que permite o deniega permisos para los servicios y recursos de AWS 
	ej1:
	"Version": "2012-10-17", (version de la politica)
	"Id": "S3-Account-Permissions", (identificador de la politica)
	"Statement":[  (declaraciones)
		"Sid": "1" (id),
		"Effect" :"Allow" / "Deny"  (le da acceso o deniega el permiso)
	]	"Principal":{
			"AWS": ["arn:aws:iam::123456789012:root/*"] (  a que cuenta, usuario o rol se aplicara esta politica )
			}
		"Action":[   (lista de llamadas a la APi que se permitiran segun el efecto )
			"s3:GetObject",
			"s3:PutObject"
		],
		"Resource":  (lista de recursos a los que se aplicaran las acciones )
			["arn:aws:s3:::mybucket/*"]
		
	

	ej2:
	Effect : "Allow"
	Action : "s3:ListObject"
	Resource : "arn:aws:s3:::coffee_shop_reports" 
	*En este ejemplo de política de IAM se concede permiso para acceder a los objetos del bucket

*Podemos asociar una politica a un grupo y asi todos los usuarios de ese grupo tienen los mismo permisos 
*Roles : Podemos crear ROLES que tienen permisos asociados que permiten o deniegan acciones especificas, estos
 	los asumen durante un periodo te tiempo limitado, no tienen nombre de usuario ni contraseña

**
>>>>> Ataques de denegacion de servicios distribuido DDoS / Disttributed denial-of-service
Es un intento deliberado de hacer que un sitio web o una aplicación no estén disponibles para los usuarios.
El objetivo del ataque es anular la capacidad de funcionar de su aplicacion por medio de saturar el sistema
	al punto que no pueda operar mas 
El atacante intenta saturar la capacidad de sua app para denegar sus serviciosa cualquier person, el ataque
 desde una maquina no es suficiente, el atacante aprovecha otras maquinas en internet para tocar a su infraestructura
 La idea principal es que el comandante del ataque haga el menor trabajo posible, y que la victima sea
 objeto de una carga de trabajo insoportable de procesar 

Ataques especificos
>>> Inundacion UDP
EJ:	Cualquiera que pueda enviar una solicitud al sistema meteorologico recibira como respuesta una cantidad
	grande de datos, aqui el ataque es simple el atacante envia una solicitud como el pronostico del tiempo
	pero da una direccion de retorno falsa como una nuestra, entonces todas la respuestas/info/datos inunda
	nuestro servidor y paraliza el sistema al tratar de recibir una info que nunca solicito 
	*Ataque de bajo nivel diseñado para agotar la red
**Solucion: Los grupos de seguridad solo permiten el trafico entrarte de solicitudes autorizadas, el protocolo
	meteorologico es distinto al habitual, entonces si no esta en la lista de entrada no se puede comunicar con el servidor 

>>> Ataques a nivel HTTP
	Parecen cliente normales con solicitudes normales, todas proenientes de un ejercito de quipos, demandan tanta
	atencion que los clientes habituales no pueden entrar, intentan trucos como el siguiente ataque:
>>> Ataque Slowloris
	El atacante finge tener una conexion lenta y la  solicitud al servidor se hace larguisima y la fila no puede avanzar 
	Pueden agotar la capacidad de todo un frontend sin esfuerzo
**Solucion: Elastic Load Balancer espera recibir la solicitud completa antes de hacerla llegar al servidor, puede interntar
	saturarlo pero es escalable 

***Para ataques mas audaces/sofisticado:
Aws tiene herramientas de defensa 

>>>>>>>>>>> AWS WAF <<<<<<<<<< ????????????????????????????????????????
es un firewall de aplicaciones web que le permite monitorear las solicitudes de red que llegan a las aplicaciones web. 
AWS WAF funciona de forma similar para bloquear o permitir el tráfico. Sin embargo, lo hace mediante una lista de control de acceso (ACL)
	web para proteger sus recursos de AWS. 

>>>>>>>>>>> AWS SHIELD <<<<<<<<<< : ESCUDO
Servicio que PROTEGE las aplicaciones DDoS
Proporciona una mitigación en línea automática y una detección siempre activa que minimizan el tiempo de inactividad y la latencia de la
	 aplicación, por lo que no es necesario disponer de AWS Support para beneficiarse de la protección contra DDoS.
Dos niveles : Standard / Advanced 

>>AWS Shield Standard 
	SIN COSTO Protege automaticamente a todos los clientes de aws de ataques Ddos
	AWS Shield Standard utiliza diversas técnicas de análisis para detectar el tráfico malicioso en tiempo real y mitigarlo automáticamente.

>> AWS Shield Advanced 
	DE PAGO servicio que proporciona DIAGNOSTICO DETALLADO de ataques y la capacidad de detectar y mitigar ataques DDoS


** puede integrar AWS Shield con AWS WAF escribiendo reglas personalizadas para mitigar los ataques DDoS complejos
https://aws.amazon.com/es/shield/?whats-new-cards.sort-by=item.additionalFields.postDateTime&whats-new-cards.sort-order=desc

>>>>>> AWS SHIELD / AWS WAF <<<<< ???????????????????????????????????????????
aws waf usa un firewall para app web para filtrar el trafico entrante, cuenta con capacidades de aprendizaje automatico y puede
reconocer nuevas amenazas a medida que evoluciona y ayuda a defender a su sistema de forma proactiva 



~~~

~~~
¿Qué es la computación en la nube? 
La computación en la nube es la entrega  bajo demanda de recursos de TI en línea, con precios de pago por uso

Tres modelos de computación en la nube
	Infraestructura como servicio (IaaS) : el proveedor de la nube ejecuta el  hardware  y el software de virtualización . Usted aprovisiona y administra sus servidores virtuales y todo el software que está instalado en ellos.

	Plataforma como servicio (PaaS) : el proveedor de la nube ejecuta y administra el hardware , el software de virtualización y los servidores virtuales . Solo necesita implementar su aplicación y sus datos.

	Software como servicio (SaaS ): el proveedor de la nube  ejecuta y administra todo , desde el hardware hasta la aplicación. Solo necesita suscribirse a la aplicación para usarla 

~~~
### Costos
~~~
>>>>>>>>>> Panel de facturacion/ Billing dashboard <<<<<<<<<< FACTURACION 
Como va la facturacion de la cuenta ?
>>> Bills :
	Acceso a los servicios que estamos pagando (Facturacion)
Gasto mensual hasta la fecha y los servicios utilizados 
Grafico con montos de mes anterior, actuales y previstos del mes sig 
Tabla con uso actual de la capa gratuita 
*Para pagar la factura de AWS, monitorear el uso y analizar y controlar los costos.
https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/billing-what-is.html

>>>Billing Consolidado:  AWS Organization 
	Beneficios de usar AWS Organization es la facturacion consolidada, al final del mes puede unir 
		la facturacion al propietario de la organizacion 
	Simplifica el proceso de facturacion 
	Compartir ahorros entre cuentas (descuentos por volumen)
	Funcion billing gratuita 
>>>>>>>>>> AWS Budgets <<<<<<<<<<<	PRESUPUESTOS PERSONALIZADOS PARA ESCENARIOS COSTO/USO 
Presupuesto personalizados para escenarios de costos y uso
Recibe notificacion de forma anticipada si va exceder el monto presupuestado de ese recurso 
Puede crear presupuestos para planificar el uso del servicio, los costos de los servicios y las reservas de instancias.
*Para personalizar un budgets debe establacer un monto y especificar un umbral por ej cuando se llegue a ocupa
	el 80% y añadimos un email para que llegue la notificacion

>>>>>>>>>> Cost Explorer <<<<<<<<<<<< OBSERVAR Y ANALIZAR COSTOS A LO LARGO DEL TIEMPO 
Permite observar y analizar como gasta su dinero en aws a lo largo del tiempo
*12 meses de gastos historicos para analizar y hacer seguimiento de los gastos (puedo agrupar por
	 atributos, las etiquetas son utiles para filtrar )
AWS Cost Explorer incluye un informe predeterminado de los costos y el uso de los cinco servicios de AWS de mayor costo acumulados. 
*Puede crear  informes personalizados de costos y guardarlos para volver a revisarlos 
https://aws.amazon.com/es/aws-cost-management/aws-cost-explorer/

~~~
### Servicios
~~~
Amazon S3 (Simple Storage Service)
Amazon EBS (Elastic Block Store)
Amazon Glacier
Amazon EFS (Elastic File System)
~~~

### Conformidad 
~~~
>>>>> Conformidad
Cada industria tiene estandares que deben cumplirse, se realizan auditorias para validar que se cumplieron los estandes 
EJEMPLO:
	Si utilizamos sofwate que trata con datos  de consumidores de la union europea debemos asegurarnos de que cumplimos con el
		Reglamento General de Proteccion de Datos (GDPR)
	Si utilizamos app del sector de sanidad de eeuu, hay que diseñar la arquitetcura para que cumpla con los requisitos de HIPAA
		Health Insurance Portability and Accountability Act

AWS ya creo la infraestructura de centros de datos y de redes con las practicas recomendadas de seguridad de la industria
Como cliente heredamos todas las practicas recomendadas de aws 

La region puede ayudarnos a cumplir con normas de conformidad 
Ej:si solo puede almacenar datos en su pais, puede elegir una region apropiada y aws no replicara automaticamente en otras regiones 
*El cliente es propietario de los datos y es SU reponsabilidad proteger los datos , hay varios mecanismos de seguridad 
Para habilitar la proteccion de datos en muchos servicios es parte de la configuracion que tiene que gestionar en el recurso

AWS puede proporcionales documentacion que demuestre que sigue las practicas recomendadas de seguridad y conformidad
	podemos acceder a estos documentos en el servicio AWS Artifact, aqui puede tener acceso a informes de conformidad
	realizados por terceros que han validado una amplia gama de estandares de conformidad "Centro de Conformidad de AWS" para info 
~~~
