# AWS

## Topology
### Regions
- Regions are independent network where we can operate
- Traffic of data between regions costs money

### Availability Zones
- AZ are locations in a region that we can use to replicate data
- An AZ is composed of several data centers
		
## Amazon Resource Name
- partition: partición en la que se encuentra el recurso. Para las regiones estándar de AWS, la partición es aws. Si tiene recursos en otras particiones, la partición es aws-partitionname.
servicio
- Espacio de nombres del servicio que identifica el producto de AWS (por ejemplo, Amazon S3, IAM o Amazon RDS).
region
- Región en la que reside el recurso. Algunos recursos no requiere una región, podría omitirse.
account
- ID de la cuenta de AWS, sin los guiones. Por ejemplo, 123456789012. Podría omitirse.
resource, resourcetype:resource o resourcetype/resource
- El contenido de esta parte del ARN varía en función del servicio. A menudo, incluye un indicador del tipo de recurso (por ejemplo, un usuario de IAM o una base de datos de Amazon RDS) seguido por una barra diagonal (/) o un signo de dos puntos (:) y, a continuación, el nombre del recurso en sí. Algunos servicios permiten rutas en los nombres de recursos, tal y como se describe en Rutas de los ARN.

AWS
Topology
Regions
	•	Regions are independent network where we can operate
	•	Traffic of data between regions costs money
Availability Zones
	•	AZ are locations in a region that we can use to replicate data
	•	An AZ is composed of several data centers
Amazon Resource Name
	•	partition: partición en la que se encuentra el recurso. Para las regiones estándar de AWS, la partición es aws. Si tiene recursos en otras particiones, la partición es aws-partitionname. servicio
	•	Espacio de nombres del servicio que identifica el producto de AWS (por ejemplo, Amazon S3, IAM o Amazon RDS). region
	•	Región en la que reside el recurso. Algunos recursos no requiere una región, podría omitirse. account
	•	ID de la cuenta de AWS, sin los guiones. Por ejemplo, 123456789012. Podría omitirse. resource, resourcetype:resource o resourcetype/resource
	•	El contenido de esta parte del ARN varía en función del servicio. A menudo, incluye un indicador del tipo de recurso (por ejemplo, un usuario de IAM o una base de datos de Amazon RDS) seguido por una barra diagonal (/) o un signo de dos puntos (:) y, a continuación, el nombre del recurso en sí. Algunos servicios permiten rutas en los nombres de recursos, tal y como se describe en Rutas de los ARN. # Seguridad de sistemas
ADFS
Active Directory Federation Services (ADFS) is a Single Sign-On (SSO) solution created by Microsoft. As a component of Windows Server operating systems, it provides users with authenticated access to applications that are not capable of using Integrated Windows Authentication (IWA) through Active Directory (AD)
