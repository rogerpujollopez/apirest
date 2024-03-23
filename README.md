
# API de Acceso a Datos de Gaolos

## Descripción
La API de Gaolos proporciona un acceso estructurado a los datos a través de varios endpoints diseñados para facilitar la gestión y recuperación de información específica. Este documento describe el funcionamiento y la utilización de los diferentes endpoints, incluyendo la definición de los parámetros de entrada y el formato de la respuesta.

## Uso

### Obtener Factura
Para solicitar los datos de una factura específica, se debe realizar una petición al endpoint siguiente:

```
https://api.gaolos.com/xxx/apirestgetfactura?paramsin=
```

#### Parámetros de Entrada
La solicitud debe incluir los siguientes parámetros en formato JSON:

```json
{
  "parameters": {
    "RefNeg": "Referencia negocio",
    "ClaveSesion": "Token",
    "ParamsKeys": ["id_fac"],
    "ParamsValues": [4011118]
  }
}
```

- `RefNeg`: Referencia del negocio.
- `ClaveSesion`: Token de autenticación.
- `ParamsKeys`: Clave de identificación de la factura.
- `ParamsValues`: Identificador de la factura que se desea obtener.

**Nota:** `ParamsValues` debe contener el identificador único de la factura. La API devuelve los datos de una única factura por solicitud.

### Respuesta de la API

#### Formato de la Respuesta
La API devuelve los siguientes campos para la factura y sus vencimientos:

- **Factura:**
  - `id_fac`: Identificador de la factura.
  - `fe_fa`: Fecha de la factura.
  - `usu`: Usuario que generó la factura.
  - `sicob`: Estado de cobro (totalmente cobrada o no).
  - `serie`: Serie de la factura.
  - `emp`: Cliente.
  - `admin`: Administrador relacionado (si aplica).
  - `id_adm2`: Identificador del administrador relacionado (si aplica).
  - `base`: Importe base.
  - `total`: Importe total.
  - `numenv`: Número de envíos por correo electrónico.
  - `ven`: Lista de vencimientos.

- **Vencimiento:**
  - `fe_ve`: Fecha de vencimiento.
  - `imp`: Importe.
  - `forma`: Forma de pago.
  - `cuecli`: IBAN del cliente.
  - `cueneg`: IBAN de destino.
  - `fe_cob`: Fecha de cobro, si está cobrada.
  - `fe_dev`: Fecha de la última devolución, si ha sido devuelta.
  - `enespera`: Fecha de negociación del cobro, si está por negociar.

## Ejemplo de Respuesta

```json
{
  "obj": {
    "id_fac": 4011118,
    "fe_fa": "2024-03-22T00:00:00",
    "usu": "Juan Perez",
    "sicob": true,
    "serie": "R24-",
    "emp": "CONSTRUCCIONES MANOLO, S.L. ",
    "admin": "",
    "id_adm2": "",
    "base": -24,
    "total": -29.04,
    "numenv": 1,
    "ven": [
      {
        "fe_Ve": "2024-03-22T00:00:00",
        "imp": -29.04,
        "forma": "Compensado",
        "cuecli": null,
        "cueneg": null,
        "fe_cob": "2024-03-22T00:00:00",
        "fe_dev": null,
        "enespera": null
      }
    ]
  },
  "err": {
    "mensaje": null,
    "eserror": false
  }
}
```



### Obtener Presupuesto
Para solicitar los datos de un presupuesto específico, se debe realizar una petición al endpoint siguiente:

```
https://api.gaolos.com/xxx/apirestgetpresupuesto?paramsin=
```

#### Parámetros de Entrada
La solicitud debe incluir los siguientes parámetros en formato JSON:

```json
{
  "parameters": {
    "RefNeg": "Referencia negocio",
    "ClaveSesion": "Token",
    "ParamsKeys": ["id_pres2"],
    "ParamsValues": [4011118]
  }
}
```

- `RefNeg`: Referencia del negocio.
- `ClaveSesion`: Token de autenticación.
- `ParamsKeys`: Clave de identificación del presupuesto.
- `ParamsValues`: Identificador del presupuesto que se desea obtener.

**Nota:** `ParamsValues` debe contener el identificador único del presupuesto. La API devuelve los datos de un único presupuesto por solicitud.

### Respuesta de la API

#### Formato de la Respuesta
La API devuelve los siguientes campos para el presupuesto:

- **Factura:**
  - `id_pres2`: Identificador del presupuesto.
  - `fe_al`: Fecha de creación.
  - `tipopres`: Tipo presupuesto, si procede.
  - `breve`: Breve comentario.
  - `cli`: Cliente.
  - `id_cli2`: Identificador del cliente.
  - `admin`: Administrador relacionado (si aplica).
  - `id_adm2`: Identificador del administrador relacionado (si aplica).
  - `base`: Importe base.
  - `total`: Importe total.
  - `numenv`: Número de envíos por correo electrónico.




---

## Obtener Mantenimiento
Para solicitar los datos de mantenimiento específico, se debe realizar una petición al endpoint siguiente:

```
https://api.gaolos.com/xxx/apirestgetmantenimiento?paramsin=
```

#### Parámetros de Entrada
*Detalles sobre los parámetros de entrada serán definidos aquí.*

### Respuesta de la API
*El formato de la respuesta será definido aquí.*

---

## Obtener Documento
Para solicitar un documento específico, se debe realizar una petición al endpoint siguiente:

```
https://api.gaolos.com/xxx/apirestgetdocumento?paramsin=
```

#### Parámetros de Entrada
*Detalles sobre los parámetros de entrada serán definidos aquí.*

### Respuesta de la API
*El formato de la respuesta será definido aquí.*
