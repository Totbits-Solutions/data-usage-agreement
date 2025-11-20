# GAIA-X Implementation of Trusted Data Transactions

## Introducción

Habilitar la transformación digital y desarrollar servicios innovadores requiere **acceso oportuno a datos relevantes**, provenientes de múltiples fuentes y, a veces, transformados para obtener conocimientos valiosos.

**Nota:**
_"Datos" significa cualquier representación digital de hechos o información, o de compilaciones de estos._

Sin embargo, el intercambio de datos entre organizaciones se ve obstaculizado por:

- resistencia de los actores,
- políticas de gobernanza,
- falta de herramientas adecuadas,
- dificultades para cumplir normativas.

### Problemas para cada actor:

#### **Para productores de datos**

Compartir datos personales o no personales conlleva riesgos:

- legales (p. ej., violaciones GDPR por falta de consentimiento),
- industriales (p. ej., revelar secretos comerciales),
- reputacionales (p. ej., mal uso de datos compartidos),

mientras que los beneficios locales rara vez son evidentes.

#### **Para consumidores de datos**

Los derechos y restricciones de uso:

- son poco claros,
- no están formalmente definidos,
- o están escritos en términos legales difíciles de verificar o automatizar.

#### **Para equipos legales y de cumplimiento**

Los procesos de acceso y gobernanza están fragmentados y verificar un uso correcto es complejo.

Esto lleva al típico enfoque de _"parar y analizar"_ que **frena el intercambio de datos**.

## Solución de GAIA-X

Para superar estos obstáculos se necesitan **mecanismos de confianza** durante todo el proceso de intercambio de datos.

GAIA-X introduce un marco de confianza donde:

- Los **titulares de derechos** pueden definir y asegurar que se respeten las restricciones de uso.
- Los **consumidores de datos** pueden verificar la autenticidad y la autorización del uso.
- Los **proveedores de datos** pueden verificar si un consumidor está autorizado.

Este capítulo describe cómo ampliar el **GAIA-X Trust Framework** para implementar **Trusted Data Transactions** (TDT).

> El control del intercambio real de datos se estandariza fuera de GAIA-X, por ejemplo en **Eclipse Dataspace Working Group**.

### 5.1 **Modelo conceptual de Data Product**

El modelo conceptual define las relaciones:

- **Data Producer** → **Data Provider** → **Data Product** → **Data Consumer**

Los Data Products son servicios (Service Offerings) que representan datos.

Permiten:

- control soberano del uso de los datos (data sovereignty),
- cumplimiento con GDPR y la Data Act,
- verificación de identidad y derechos de todos los actores.

### 5.2 **Entendiendo el Data Usage Agreement (DUA)**

Antes de usar un conjunto de datos bajo una licencia específica, debe existir un **Data Usage Agreement firmado** entre:

- **Data Rights Holder** (productor o licenciante),
- **Data Consumer**.

El DUA firmado proporciona:

#### **(a) al Consummer**

autorización legal para usar los datos siguiendo las restricciones del titular.

#### **(b) al Data Rights Holder**

garantía de que el consumidor cumplirá las restricciones.

### Contenido del DUA

El DUA contiene dos tipos de restricciones:

#### **1. Data Access Prerequisites**

Cumplidos por el Data Provider antes de permitir el acceso.

#### **2. Data Usage Constraints**

Son responsabilidad del Data Consumer incluso después de obtener los datos.

## Notarización del DUA

Los DUAs son **notarizados por un DUA Notary**, que:

- valida que el DUA es legalmente vinculante,
- verifica que no esté revocado.

Antes de cada acceso a los datos, el Data Provider:

1. comprueba que el DUA no está revocado,
2. verifica que el consumidor cumple los prerrequisitos de acceso.

Incluso para reutilización interna, se recomienda volver a comprobar la revocación del DUA.

## Relación con GDPR y Data Act

El DUA unifica conceptos como:

- **Consentimiento (GDPR)**
- **Permisos (Data Act)**

**Referencias:** https://docs.gaia-x.eu/technical-committee/architecture-document/25.05/gaia-x_implementation_of_trusted_data_transactions/#understanding-data-usage-agreement-dua
