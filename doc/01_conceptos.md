# Data Usage Agreement (DUA) y su Integración con GAIA-X

## 1. Introducción

Un Data Usage Agreement (DUA) es un acuerdo formal que especifica cómo pueden utilizarse uno o varios conjuntos de datos, cuáles son los límites de uso permitidos y cuáles son las obligaciones tanto legales como técnicas para todas las partes implicadas. En ecosistemas avanzados de intercambio de datos, como GAIA-X, los DUAs se transforman en objetos verificables digitalmente que pueden automatizar procesos y permitir flujos de intercambio confiables.

Esta documentación explica:

- Qué es un DUA a nivel general.
- Cómo GAIA-X redefine y estructura un DUA.
- El esquema formal propuesto por GAIA-X.
- Los servicios que GAIA-X ofrece y cómo se interconectan.
- Cómo se puede integrar un DUA digital con blockchain (idea inicial).

## 2. Qué es un Data Usage Agreement (DUA)

Un DUA tradicional es un contrato legal entre:

- Productor de datos (Data Producer)
- Proveedor de datos (Data Provider)
- Consumidor de datos (Data Consumer)

El objetivo es establecer:

- Los usos permitidos de los datos.
- Restricciones y obligaciones.
- Medidas de seguridad y privacidad.
- Responsabilidades legales.
- Condiciones de vigencia, terminación y revocación.

Los DUAs tradicionales suelen ser documentos textuales (PDF, Word), firmados manualmente o mediante sistemas de firma electrónica.

## 3. DUA en GAIA-X: Un Enfoque Digital, Estructurado y Verificable

GAIA-X transforma el concepto de DUA desde un documento legal a un **artefacto digital formalizado**, expresado en formato **JSON-LD**(JSON for Linking Data, es un formato de datos basado en JSON diseñado para representar información estructurada con significado semántico) y estructurado como una **Self-Description**.

GAIA-X busca:

- Interoperabilidad en espacios de datos europeos.
- Control de uso, soberanía y trazabilidad.
- Validación automática de acuerdos.
- Identidad digital confiable.
- Cumplimiento con el marco regulatorio europeo.

### Características clave del DUA en GAIA-X

- Formato estructurado JSON-LD.
- Validación automática por máquinas.
- Firma criptográfica de todos los participantes.
- Relación directa con el Data Product.
- Uso de autoridades de confianza (trust anchors).
- Integración con catálogo federado y servicios de conformidad.

Un DUA en GAIA-X no es un PDF, sino un objeto digital verificable.

## 4. Explicación del Schema GAIA-X DataUsageAgreement

El siguiente esquema describe la estructura del objeto `DataUsageAgreement` dentro del modelo GAIA-X.

### producedBy (DataProducer)

- Referencia verificable al productor de los datos.
- Debe apuntar a una Self-Description de tipo `DataProducer`.
- Obligatorio.

### providedBy (DataProvider)

- Entidad que pone a disposición los datos.
- Puede ser distinta al productor.
- Se exige su existencia como Self-Description.
- Obligatorio.

### licensedBy

- Lista de entidades que poseen derechos de licencia sobre los datos.
- Multivaluada.
- Opcional según el dataset, pero presente en el modelo.

### dataUsageAgreementTrustAnchor

- Enlace a una autoridad de confianza.
- Valida identidades, roles y políticas.
- Obligatorio.

### dataProduct (DataProduct)

- Enlace verificable al Data Product.
- Es obligatorio que el Data Product esté declarado mediante Self-Description.
- Conecta el DUA directamente con el recurso de datos.

### signers (SignatureCheckType)

- Lista de firmas requeridas.
- Cada entrada define clave pública, método de firma y entidad.
- Permite multifirma y validación criptográfica.
- Obligatorio.

## 5. Servicios de GAIA-X Relacionados

### 5.1 GAIA-X Trust Framework

Define el conjunto de reglas y mecanismos que permiten:

- Validar identidades.
- Acreditar organizaciones.
- Garantizar la integridad de las Self-Descriptions.
- Controlar autorías y roles.

### 5.2 Conformity Assessment Service

Servicio encargado de validar:

- Estructura sintáctica (JSON Schema).
- Reglas semánticas (SHACL).
- Firmas criptográficas.
- Cumplimiento con el Trust Framework.

Devuelve informes que indican si un DUA es conforme o no.

### 5.3 Service Clearing House

Mantiene registro de:

- DUAs.
- Certificaciones.
- Versiones de Self-Descriptions.
- Resultados de validaciones.

### 5.4 Federated Catalogue

Un catálogo federado donde se publican:

- Productos de datos.
- Servicios.
- DUAs.
- Identidades verificadas.

Permite descubrir y verificar recursos en la federación.

### 5.5 Identity & Access Framework

Gestiona:

- Identidad verificable.
- Acceso basado en reglas.
- Firmas.
- Autorizaciones.

## 6. Integración con Blockchain

Aunque GAIA-X no requiere blockchain, puede integrarse de forma efectiva.

### Posibles integraciones

1. Registro en blockchain del hash del DUA.
2. Registro de firmas de aceptación.
3. Enlace entre DUA y representaciones tokenizadas de datos (NFTs).
4. Control de acceso mediante smart contracts.
5. Registro inmutable de auditoría.

Estas integraciones no exponen datos personales, ya que únicamente se registran hashes y metadatos no sensibles.

## 7. Arquitectura de Interconexión entre DUA, GAIA-X y Blockchain

A nivel conceptual, el flujo puede estructurarse así:

```
                 GAIA-X Trust Framework
                           |
                           v
                  Data Usage Agreement
                        (Self-Description)
                           |
          +----------------+----------------+
          |                                 |
   producedBy                         providedBy
          |                                 |
          v                                 v
    DataProducer                      DataProvider
          |                                 |
          +---------------+-----------------+
                          |
                          v
                     Data Product
                          |
                          v
                     Signers List
                          |
                          v
           Conformity Assessment Service
                          |
                          v
                 Federated Catalogue
                          |
                          v
                   Blockchain (opcional)
```

Esta arquitectura combina:

- Metadatos estructurados.
- Firmas criptográficas.
- Identidades verificadas.
- Validación automática.
- Opcionalmente trazabilidad inmutable.

## 8. Implementación en un Servicio Propio

Un servicio puede implementar las siguientes funciones:

1. Recepción de un DUA en formato GAIA-X.
2. Validación de estructura JSON-LD.
3. Verificación de identidades y trust anchors.
4. Validación de firmas.
5. Registro de aceptación.
6. Registro en blockchain del hash del DUA.
7. Publicación en un catálogo federado.

Este enfoque permite automatizar acuerdos de uso de datos con garantías legales y técnicas.
