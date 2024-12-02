---
id: 1732909399-associate-cloud-engineer-notes
aliases:
  - Associate Cloud Engineer Notes
tags: []
---

# Associate Cloud Engineer Exam Practicee

## Section 1: Setting up a cloud solution environment (~20% of the exam)

Establecer las bases para la implementación de un entorno en la nube, comenzando por la configuración de los proyectos y las cuentas asociadas, manejo de la facturación y configuración del CLI.
> Podemos llamar a esta etapa como: 'Landing Zone'

### Entender las jerarquías de los recursos

1. **Organización**: 
  - Nivel superior de jerarquía, representa a la empresa. 
  - Está asociado a un dominio de Workspace o Cloud Identity (nombredeempresa.com)
  - Todas las carpetas, proyectos y recursos pertenecen a una organización
  - Tiene control centralizado para políticas, roles y permisos mediante IAM

2. **Carpetas**: 
  - Es opcional, pero ayuda a estructurar y agrupar departamentos de una emppresa, como por ejemplo Logística, Marketing, etc.
  - Permite aplicar políticas y roles específicos al departamento de manera más granular
  - Es posible anidar carpetas, permitiendo estructurar de mejor manera un departamento y sus áreas

3. **Proyectos**: 
  - Es la unidad principal de organización, desde aquí se administran y gestionan los recursos.
  - Cada recurso utilizado en GCP está asociado a un único proyecto.
  - Sirve para definir entornos de desarrollo, pruebas y producción.
  - Los límites de cuotas y facturación se definen a este nivel, permitiendo monitorear y controlar el uso de recursos.
  - Son identificados de manera única por una id, un número y un nombre
  - Por ejemplo un proyecto dentro de la carpeta de marketing (departamento) podría ser un entorno para una campaña de marketing (proyecto) que requiere el uso de bases de datos (recurso).
  > Cada proyecto contiene tres atributos específicos: id, número y nombre, el id puede ser asignado al crear un proyecto pero no es modificable luego, el número es asignado por la plataforma y es un número random, y el nombre es el único atributo que puede ser modificado luego de creado.

4. **Recursos**: 
  - Elementos específicos utilizados en un proyecto
  - Los permisos para interactuar con estos recursos se configuran en los niveles superiores de acuerdo a la jerarquía.

> Las políticas y roles se heredan de las jerarquías superiores a las inferiores

### IAM

Sistema centralizado para gestionar accesos y permisos a los recursos.

Responde a las siguientes preguntas:

1. **Quién**: Identidades (usuarios, grupos, cuentas de servicio)   
2. **Qué puede hacer**: Roles que definen permisos. 
3. **En qué recurso**: Recursos específicos al que se aplican los permisos.

#### Componentes de IAM
- **Principales (Principals)**: Las entidades que pueden acceder a los recursos (Quién)
  - Usuarios: Personas con cuenta de Google
  - Grupos: Conjunto de usuarios administrados en Google Workspace o Google Identity
  - Cuentas de servicio: Identidades usadas por servicios o aplicaciones de Google para interactuar con nuestros recursos
  - Dominios: Nombres de dominio de Google Workspace o Google Identity
- **Roles**: Conjunto de permisos predefinidos o custom
  - Básicos, contiene grupos de roles predefinidos: 
    - Owner: Control total
    - Editor: Modificación
    - Viewer: Lectura
  - Predefinidos:
    - Para tareas específicas, por ejemplo: `roles/storage.objectViewer`
  - Custom: 
    - Son creados manualmente para necesidades específicas. Es una buena opción para crear roles que sigan los principios de seguridad del mínimo privilegio.
- **Permisos**: 
  - Operaciones que un rol permite realizar sobre un recurso, ejemplo: `storage.buckets.create`
- **Políticas**: 
  - Definen relación entre entidades, roles y recursos, es un "documento" que establece establece las relaciones.

> Nota: Las políticas y roles se heredan de las jerarquías superiores a las inferiores, pero en niveles finales (proyectos o recurso) asignar explícitamente una política o un rol sin incluír a un grupo que sí tiene acceso a ese recurso por haberse asignado a nivel de organización, provoca que pierda el acceso. A niveles intermedios (carpetas) Esto no sucede, las políticas o roles se heredan y combinan.

##### Métodos para asignar roles y políticas desde CLI
`gcloud <jerarquía> <tipo> <nombre> --<atributo>=<valor>`
- `add-iam-policy-binding`: Agrega un rol a un usuario, grupo o cuenta de servicio
- `--member=<usuario|grupo|cuenta>`: El usuario, grupo o cuenta al que se le asigna el rol
- `--role=<rol>`: El rol que se le asigna al usuario, grupo o cuenta

Ejemplos:

- Proyecto: `gcloud projects add-iam-policy-binding <proyecto> --member=user:<usuario> --role=roles/owner`
- Carpeta: `gcloud resource-manager folders add-iam-policy-binding <carpeta> --member=user:<usuario> --role=roles/owner`
- Organización: `gcloud organizations add-iam-policy-binding <organización> --member=user:<usuario> --role=roles/owner`

##### Método para crear políticas desde JSON y YAML
```json
{
  "bindings": [
  {
      "role": "roles/owner",
      "members": [
        "user:user@example.com"
      ]
    }
  ]
}
```

- Se aplican usando `set-iam-policy` haciendo referencia a la ruta del archivo JSON o YAML
  - `gcloud <jeraruquía> set-iam-policy <type-id> <url-al-archivo>`


#### Facturación

- Finanzas y operaciones son administradas de manera separada.
- Una cuenta de facturación puede ser asignada a múltiples proyectos y recursos específicos
   - Pero un proyecto o recurso sólo puede estar fijo a una sola cuenta de facturación
- Una cuenta de facturación pertenece a la organización y no a alguno de los sub-recursos
- A nivel de organización podemos tener múltiples cuentas de facturación, separadas como mejor lo necesite la empresa o entidad

##### Budget Alert

Podemos asignar alertas relacionadas a las finanzas utilizando la herramienta de Google Monitoring


### Configurando CLI, Shell, SDK and console

Tanto Shell como SDK vienen preinstalados y son las únicas maneras de interactuar con GCP desde la línea de comandos
Console es es el apartado visual
Existen plataformas como Mobile y la API-Rest que no viene instalado por defecto en Shell

## Sección 2:

> [!IMPORTANT] Egress Charges se refiere a los gastos asociados a recursos que van desde nuestros buckets hacia afuera, mientras que Ingress Charges se refiere a los gastos asociados a recursos que entran a nuestros buckets

### Eligiendo y configurando infraestructura y servicios de despliegue 

#### Infraestructura como servicio (IaaS)
  - Google Compute Engine (GCE)
    - Control total
    - Permite controlar el sistema operativo
    - Casos de uso:
      - Cualquier flujo que requiera un sistema operativo específico
      - 
  - Google Kubernetes Engine (GKE)
    - No depende de un sistema operativo
    - Incrementa la velocidad y operativilidad dado que automatiza la escalabilidad
    - Manejar contenedores en producción
    - Casos de Uso:
      - Flujos de contenedores
      - Sistemas distribuidos basados en la nube
      - Aplicaciones híbridas

#### Plataforma como servicio (PaaS)
  - Google App Engine
    - Plataforma para construir aplicaciones basadas en el código
    - Velocidad de desarrollo
    - Minimiza los gastos operacionales
    - Casos de Uso:
      - Sitios web
      - Aplicaciones
      - Backend para videojuegos (u otros)
      - IoT apps
  - Google Cloud Run 
    - Despliega código o contenedores que escuchan request o eventos
    - Escala en conjunto a la demanda
    - Se paga por el uso ( puede llegar a ser más barato para proyectos pequeños )
    - Soporta API endpoints para comunicarse con la app
    - Casos de Uso:
      - Web Frameworks
      - Microservicios
  - Google Run Functions
    - funciones que corren sobre Google Run
    - Entorno serverless para ejecutar o conectar servicios cloud
    - flujos basados en eventos
    - Escala con la demanda
    - Mínima configuración
    - Casos de Uso:
      - Análisis estadístico
      - Generación de imágenes pequeñas
      - Automatizaciones específicas

### Eligiendo y configurando opciones de almacenamiento de datos

  - Relacionales:
    - Cloud SQL:
      - Web frameworks as CMS, eCommerce
    - Spanner:
      - RDBMS+scale, HA, HTAP (revisar)
      - Metadatos de usuarios
  - No relacionales
    - Firestore
      - Jerárquico, web, apps
      - Perfiles de usuario, Estados de juegos
    - Bigtable
      - Lecturas pesadas y escrituras, eventos
      - FinTech, IoT
  - Objetos:
    - Cloud Storage
      - Guardar binarios o objetos
      - Imágenes, backups, etc
  - Almacén de datos
    - BigQuery
      - almacén de datos a nivel empresarial
      - Analíticas, dashboards.


##### Clases de Cloud Storage

Standard -> Nearline -> Coldline -> Archive
Para mayor cantidad de lectura permitida, menor es el costo de lectura pero mayor el costo de GB almacenado, esto significa que en archive el costo por lectura es muy alto, pero por GB de almacenamiento es muy bajo a diferencia de standard que es al revés.

## Planificación y Configuración de recursos de red

> [!IMPORTANT]
> Estudiar Redes a profundidad, entender diferentes protocolos, TCP/UDP, load balancers, proxies, etc

##### Resultados del estudio:
- TCP y UDP son protocolos de comunicación que corresponden a la capa 4 del modelo OSI, correspondiente a la capa de transporte
  - TCP corresponde al protocolo de transferencia estable y se asgura de que los datos se envíen y lleguen al destinatario de la manera correcta
  - UDP es un protocolo que no presta atención a la integridad de los datos, si no que comprende una comunicación más directa y veloz, es útil para servicios de stream o videojuegos en tiempo real

- Load Balancers
  - Sistemas que permiten distribuir tráfico de redes a diferentes servidores
  - Existen LB para distintas capas
    - Capa 4, balanceo basado en puertos y direcciones IP
      - No procesa la información, sólo distribuye los tráficos que llegan de acuerdo al protocolo establecido
      - Existen balanceadores de carga basados en tcp/udp, ssl proxys (cifrados y mediante https), tcp proxys (no cifrados y solo de capa 4)
    - Capa 7, basado en URL (por ejemplo)
      - Redirige tráfico basado en un endpoint por ejemplo, dado que el LB en esta capa se basa en los headers, cookies o url

- Proxy
  - Intermediario entre un usuario final y un servidor
  - Actúa como receptor de las solicitudes del cliente y las distribuye al backend (servidor)
  - Un proxy puede procesar los datos de varias maneras, cacher información, distribuir carga, etc

Google utiliza el modelo OSI para definir sus capas de redes

##### Balanceadores de carga basados en las capas 4 y 7 del modelo OSI
Capa 4, Firewalls, ports, ips, etc
Capa 7 HTTP(S), SMTP, DHCP (principalmente), también tiene un firewall de capa 7

#### Tipos de balanceadores de carga
  - External HTTP(S) / Internal HTTP(S)
    - Tipo de trafico http o https
    - Global, IPv4, IPv6 / Regional, IPv4
    - http utiliza los puertos 80 o 8080, y https el 443
    - La única diferencia es si soporta conectividad SSL
      > [!NOTE] SSL es un protocolo de seguridad que cifra los datos
  - SSL Proxy / TCP Proxy
    - Puede utilizar cualquier puerto
    - -Pueden 'correr' en cualquier puerto-
        > -No sé si correr en un puerto es el concepto correcto, investigar cómo funciona-
      > El concepto correcto es que detecta y envía tráfico desde cualquier puerto
  - Network TCP/UDP
    - TCP/UDP sin SSL
    - Regional, IPv4
  - Internal TCP/UDP
    - Regional, IPv4
    - El único interno junto a Internal HTTP(S)

> [!IMPORTANT]
> Importante saber: Global vs Regional y Cuáles son de capa 4 (TCP/UDP, SSL Proxy) y cuáles de capa 7 (HTTP(S))

### Productos

- Spanner: es una base de datos relacional que utiliza redes globales, es la más básica base de datos
- Cloud SQL: base de datos en la nube para mySQL, PostgreSQL y SQL Server
- Bigtable: ofrece bases de datos de baja latencia y en gran escala, además de plataforma de análisis de datos, útil para soluciones que requieren de mucho flujo y disponibilidad de datos
- Cloud Storage: servicio de almacenamiento de objetos

- BigQuery: permite guardar data en un sistema relacional de warehouse (almacén de datos) especializado en el análisis de datos y estadísticas
- Dataflow: servicio de datos en tiempo real para analizar datos con ayuda de ai
- Pub/Sub: es un servicio de mensajería para transferencia y entrega de eventos
- App Engine: Servicio Serverless basado en el código

- Compute Engine: Máquinas virtuales en la nube
- Cloud Run: permite ejecutar apps en contenedores de manera más simple y en entorno serverless y ofrece administración parcial, útil para casos de usos más sencillos
- GKE: permite ejecutar aplicaciones en contenedores, ofrece administración total, útil para casos de usos con arquitecturas complejas
- Cloud Run Functions (o Cloud Functions): procesamiento controlado por eventos para servicios o apps en la nube, por ejemplo interceptar con apis y generar procesos en entornos serverless

## Sección 3: Desplegar e implementar soluciones

### Compute Engine
- Inicializar una instancia de VM con Consola y Shell, asignar discos, políticas, llaves [[1729601391-ssh|SSH]]
- Crear grupos administrados de instancias auto escalables usando plantillas de instancias 
- Generar y subir llaves SSH personalizadas para las instancias
- Instalar y configurar Cloud Monitoring y Agentes de Logs
- Evaluar cuotas de cómputo y incrementar las necesidades

> [!NOTE]
> Para configuraciones de MySQL customizadas, no es posible usar Cloud SQL porque no permite la personalización de funcionalidades, en este caso se recomienda crear una VMs y configurarla par MySQL, se recomienda el uso de un tipo de máquina N2 por sobre las E2

#### Tipos de Máquinas
Standard, Alta memoria, alto cpu, memoria optimizada, compute optimizado, cores compartidos, custom

> Los discos persistentes existen fuera de las máquinas virtuales y se comunican a través de la red

Tipos de actualización de grupos de instancia administradas
  - Oportunista: actualiza cuando la máquina naturalmente se reinicia, no es recomendado para asegurar la actualización de alguna característica importante
  - Proactiva: actualiza las máquinas automáticamente progresivamente una por una, asegura que la actualización se realiza en el menor tiempo, es más barata

> max surge refiere a la cantidad de máquinas extras para una actividad específica en las máquinas virtuales 

#### Grupos de instancias administradas
- Asegura que todas las instancias estén corriendo
- Buena práctica para manejar instancias de VMs
- Generalmente auto escala
- Puede cambiar de tamaño de instancias
- Puede ser Zonal (más barata pero prospecta a fallos críticos) o Regional

### Kubernetes Engine
Es la recomendación de Google para desplegar aplicaciones
Clusters con AutoPilots no permite realizar cambios de bajo nivel al cluster ya que las configuraciones corren de manera automática
> Investigar las características de los standard clusters

Existe una imagen altamente optimizada que no permite modificaciones pero que permite una gran rendimiento de de nuestros contenedores 

### Cloud Run y Cloud Functions
- Desplegar aplicaciones y actualizar escalamientos, versiones y división de tráfico
- App que recibe eventos de GC, por ejemplo pub/sub, cambios en objetos de almacenamiento, request http, etc

> App Engine está detrás de Run y functions, no suele ser la mejor opción

#### Run

- App Contenerizada
- Serverless
- Expone un endpoint para comunicarse con la app
  - Regional y replicada por las zonas
- Escala basado en los Requests

#### Functions
> google.storage.object.finalize/deleted/archived/metadataUpdated son los únicos eventos para escuchar cambios en el storage 
[!TODO] Estudiar Eventos 

- Ejecución de funciones serverless
- Basados en eventos
- Se lanzan cuando ocurre un evento al que escuchan
- Escala con el número de eventos
- No tienen estados (sí internos, no externos)

### Datos
- Productos como Cloud SQL, Firestore, BigQuery, Spanner, Pub/Sub, Bigtabe, Dataproc, Dataflow, Cloud Storage
- Cargar datos, por ejemplo subir datos mediante CLI, transferencia por API, cargar datos desde Storage o stremear datos a Pub/Sub

#### Storage
Al crear un bucket con CLI `gcloud storage buckets create` y no especificamos un `--location` por default es US Multi-Region

> [!IMPORTANT]
> Storage NO es para datos estructurada

#### Cloud SQL
- Para casos de fallos
  - `--availability-type` sirve para especificar el alcance de del failover
  - `--seconday-zone` especifica qué zona es a la que iremos en caso de fallos

- Configurando instancias de Cloud SQL
  1. Crear la instancias
  2. Seleccionar el tipo de base de dato
  3. Elegir un nombre
  4. Elegr unnnnna contraseña para el usuario root
  5. Elegir una versión correcta
  6. Elegir Region y zona
  7. Elegir zona primarya y secundaria
  8. Configuraciones


#### BigQuery
  - Podemos cargar datos a BigQuery desde archivos (Json, CSV, etc), Dataflow, y BigQuery Data transfer que es un SaaS de Google auto administrado para manejar cargas de datos desde otras fuentes, suele ser la mejor solución y más fácil de implementar

### Redes
- Crear [Virtual Private Cloud](void/1729731486-virtual-private-cloud.md) con subnets
  - custom-mode vpc, shared vpc
- Lanzar Vms con configuraciones de redes personalizadas
  - internal-only IP address, Google private access, static external and private ip address, network tags
- Crear reglas de firewall para ingresos y egresos de trafico para una VPC 
  - IP subnets, network tags, service account
- Crear balanceadores de carga para distribuir tráfico a una aplicación
  - global https load balancer, global SSL proxy load balancer, global TCP proxy load balancer, regional network load balancer, regional internal load balancer

#### Existen dos tipos de VPC en Google
  - Auto mode network (por defecto)
    - un subnet por región
    - se crea automáticamente
    - nuevos subnets son agregados cuando nuevas regiones se conectan 
    - ip addresses se originan de espacios predeterminados
  - Custom mode network
    - Permite más control de los subnets 
    - Más flexible
    - Control total de los subnets y regiones
    - Recomendado para producción


### Cloud Marketplace

Por qué?
  - Solución o específica solución que pueda estar creada y podemos utilizar

### Infraestructura como código

- Terraform
  - init - plan - apply
  - install dependencies - verify syntax and preview - apply configuration

## Sección 4: Asegurar el éxito de las operaciones de una solución en la nube 

### 4.2 GKE
`apply` es la manera declarativa de 

`neg` referencia en el objeto de configuración del servicio para internal https load balancers
`si en ingress.class en gce` permite crear load balancers http externos

