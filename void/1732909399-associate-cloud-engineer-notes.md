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

Finanzas y operaciones son administradas de manera separada.
