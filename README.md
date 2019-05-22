
# KUBERNETES
Instalación e Información.
INFORMACIÓN

QUE ES KUBERNETES?

 Kubernetes más conocido como k8s, es un Orquestador de Docker, lo cual quiere decir que desde Kubernetes podremos gestionar la vida de nuestros contenedores y realizar diferentes tareas con respecto a estos contenedores. Es un proyecto OpenSource y creado por Google.
 
Lo que intenta solucionar Kubernetes, sobre todo, son los problemas ocasionados de los procesos manuales, que están involucrados en la implementación y escalabilidad de las aplicaciones que corremos en estos contenedores.

Normalmente, en producción estas aplicaciones constan de varios contenedores, que pueden estar alojados en distintos hosts de servidores y no tenemos por qué tener visibilidad directa con ellos. Con Kubernetes se pueden crear servicios de aplicaciones que abarcan varios contenedores, se pueden programar en un cluster, escalar y administrar el estado de dichos contenedores.

Entonces, con Kubernetes lo que se trata de solucionar es el problema de proliferación de contenedores, porque podemos mantener el número de contenedores que queremos, podemos escalarlo en caso de necesidad o podemos reducirlo en caso de que ya no hagan falta.

NOMENCLATURA

Cluster: Conjunto de máquinas físicas o virtuales que son utilizados por Kubernetes

Pod: es la unidad mínima de Kubernetes, realmente es un contenedor en jerga de Docker

Labels y selectors: son pares de claves y valores, las cuales se pueden aplicar a pods, services, replication controllers, etc…. y con ellos podremos identificarlos para poderlos gestionar.

Node: es el servidor ya sea virtual o físico que aloja el sistema de Kubernetes y donde vamos a desplegar nuestros pods (contenedores). Si buscáis información por internet, antiguamente se llamaban Minions.

Replication Controller: es el responsable de gestionar la vida de los pods y el encargado de mantener arrancados los pods que se le hayan indicado en la configuración. Permite escalar de forma muy sencilla los sistemas y maneja la recreación de un pod cuando ocurre algún tipo de fallo.

Replica Sets: Es la nueva generación del Replication Controller, con nuevas funcionalidades. Una de las funcionalidades destacadas es que nos permite desplegar pods en función de los labels y selectors

Deployments: Es donde e especifican la cantidad de réplicas de pods que tendremos en el sistema. Es una funcionalidad más avanzada que los Replication Controller y muy parecida a los Replciation Sets, pero con otras características.

Namespaces: son agrupaciones, en ellos podremos diferenciar espacios de trabajo para diferentes situaciones. Por ejemplo podríamos realizar un Namespace para producción y otro para desarrollo y cada Namespace tendría sus propios pods, replication controllers, etc….

Volumes: Es el acceso a un sistema de almacenamiento

Secrets: Es donde se guarda la información confidencial como usuarios y passwords, para poder acceder a los recursos.

Service: Es la política de acceso a los pods. Lo podríamos definir como la abstracción que define un conjunto de pods y la lógica para poder acceder a ellos.

SOLUCIONES QUE OFRECE KUBERNETES

Entre las soluciones que ofrece Kubernetes destacamos las siguientes:

- Orquestar contenedores en varios hosts.

- Optimizar el consumo de los recursos de hardware.

- Controlar y automatizar las implementaciones y actualizaciones de las aplicaciones implementadas.

- Añadir almacenamiento para ejecutar aplicaciones con estado.

- Escalar aplicaciones de contenedores o aumentar sobre la marcha los recursos que están consumiendo los mismos.

- Administrar servicios de forma declarativa, garantizando así que las aplicaciones implementadas siempre se ejecuten en el mismo nodo en el que se implementaron.

- Realizar comprobaciones de estado y de auto regeneración de las aplicaciones con ubicación, reinicio, replicación y escalamiento automático.

OTRAS HERRAMIENTAS  SIMILARES A KUBERNETES

Kubernetes no es la única herramienta de este tipo en el mercado, aunque si es la más utilizada. Existen otras alternativas como pueden ser:

- Docker Swarm: Es la solución nativa de Docker. Históricamente Kubernetes salió antes que Docker Swarm y al principio Docker no daba soporte para Kubernetes. Pasados unos años se vieron obligados a dar soporte nativo porque el mercado que acaparaba Kubernetes era mucho mayor que el de Docker Swarm.

- Marathon: Es un orquestador de Mesos, y es la segunda alternativa más famosa.

ARQUITECTURA

ETCD

es un almacén de datos persistente, liviano, distribuido de clave-valor desarrollado por CoreOS que almacena de manera confiable los datos de configuración del clúster, representando el estado general del cluster en un punto del tiempo dado.

Servidor de API

El servidor API es un componente central y sirve a la API de Kubernetes utilizando JSON sobre HTTP, que proveen la interfaz interna y externa de Kubernetes13​21​. El servidor API procesa y valida las peticiones REST y actualiza el estado de los objetos API en etcd, así permitiendo a los clientes configurar flujos de trabajos y contenedores a través de los nodos esclavos.

PLANIFICADOR

El planificador es el componente enchufable que selecciona sobre qué nodo deberá correr un pod sin planificar (la unidad básica de manejo del planificador) basado en la disponibilidad de recursos. El planificador lleva la cuenta de la utilización de recursos en cada nodo para asegurar que un flujo de trabajo no es planificado en exceso de la disponibilidad de los recursos.

ADMINISTRADOR DE CONTROLADOR

El administrador de controlador es el proceso sobre el cual el núcleo de los controladores Kubernetes como DaemonSet y Replication se ejecuta. Los controladores se comunican con el servidor API para crear, actualizar y eliminar recursos que ellos manejan (pods, servicios, etc.)

NODO KUBERNETES

El nodo, también conocido como esclavo o worker, es la máquina física (o virtual) donde los contenedores (flujos de trabajos) son desplegados. Cada nodo en el clúster debe ejecutar la rutina de tiempo de ejecución (como Docker), así como también los componentes mencionados más abajo, para comunicarse con el maestro para la configuración en red de estos contenedores.

KUBELET

Kubelet es responsable por el estado de ejecución de cada nodo (es decir, asegurarse que todos los contenedores en el nodo se encuentran saludables). Se encarga del inicio, la detención y el mantenimiento de los contenedores de aplicaciones (organizados como pods) como es indicado por el panel de control.

KUBE-PROXY

.Kube-Proxy es la implementación de un proxy de red y balanceador de carga soportando la abstracción del servicio junto con otras operaciones de red

Es responsable del enrutamiento del tráfico hacia el contenedor correcto basado en la dirección IP y el número de puerto indicados en el pedido.

cADVISOR

cAdvisor es un agente que monitorea y recoge métricas de utilización de recursos y rendimiento como CPU, memoria, uso de archivos y red de los contenedores en cada nodo.

