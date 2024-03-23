
# API de Acceso a Datos de Gaolos

## Descripción
La API de Gaolos proporciona un acceso estructurado a los datos a través de varios endpoints diseñados para facilitar la gestión y recuperación de información específica. Este documento describe el funcionamiento y la utilización del endpoint `obtener factura`, incluyendo la definición de los parámetros de entrada y el formato de la respuesta.

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
    "ClaveSesion": "Token de sesión",
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
La API devuelve los siguientes campos para las facturas y sus vencimientos:

- **Factura:**
  - `id_fac`: Identificador de la factura.
  - `fe_fa`: Fecha de emisión.
  - `usu`: Usuario que generó la factura.
  - `sicob`: Estado de cobro (totalmente cobrada o no).
  - `serie`: Serie de la factura.
  - `emp`: Empresa emisora.
  - `admin`: Administrador relacionado (si aplica).
  - `id_adm2`: Identificador del administrador relacionado (si aplica).
  - `base`: Importe base.
  - `total`: Importe total.
  - `numenv`: Número de envíos por correo electrónico.
  - `ven`: Vencimientos.

- **Vencimiento:**
  - `fe_ve`: Fecha de vencimiento.
  - `imp`: Importe.
  - `forma`: Forma de pago.
  - `cuecli`: IBAN del cliente.
  - `cueneg`: IBAN de destino.
  - `fe_cob`: Fecha de cobro.
  - `fe_dev`: Fecha de la última devolución.
  - `enespera`: Fecha de negociación del cobro.

