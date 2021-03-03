layout: page
title: "Nomina"
permalink: /Nomina.md

## Nomina Electronica (DRAFT)
A continuacion se muestra la informacion general para la nomina electronica.

El ejemplo en JSON contiene la informacion minima requerida y en la tabla inferior se muestran la descripcion de cada uno de estos campos.

# Ejemplo de un JSON con los campos minimos

```JSON
{ 
 "Periodo": {
    "FechaIngreso": "2021-02-02",
    "FechaLiquidacionInicio": "2021-02-02",
    "FechaLiquidacionFin": "2021-02-02",
    "TiempoLaborado": "20",
    "FechaGen": "2021-02-02"
  },
  "NumeroSecuenciaXML": {
    "Prefijo": "",
    "Consecutivo": "2"
  },
  "LugarGeneracionXML": {
    "Pais": "CO",
    "DepartamentoEstado": "11",
    "MunicipioCiudad": "11001",
    "Idioma": "es"
  },
  "InformacionGeneral": {
    "Version": "V1.0: Documento Soporte de Pago de Nómina Electrónica",
    "Ambiente": "1",
    "TipoXML": "102",
    "FechaHoraGen": "2021-02-02T00:00:00",
    "PeriodoNomina": "6",
    "TipoMoneda": "COP",
  },
  "Empleador": {
    "NIT": "80844005",
    "DV": "1",
    "Pais": "CO",
    "DepartamentoEstado": "11",
    "MunicipioCiudad": "11001",
    "Direccion": "avenida lejos"
  },
  "Trabajador": {
    "TipoTrabajador": "01",
    "SubTipoTrabajador": "00",
    "AltoRiegoPension": "false",
    "TipoDocumento": "13",
    "NumeroDocumento": "80844005",
    "PrimerApellido": "Serrano",
    "SegundoApellido": "Sanchez",
    "PrimerNombre": "Felipe",
    "LugarTrabajoPais": "CO",
    "LugarTrabajoDepartamentoEstado": "11",
    "LugarTrabajoMunicipioCiudad": "11001",
    "LugarTrabajoDireccion": "Avenida Cerquita",
    "SalarioIntegral": "false",
    "TipoContrato": "2",
    "Sueldo": "400000",
  },
  "Pago": {
    "Forma": "1",
    "Metodo": "1",
  },
  "FechasPagos": [
    {
      "FechaPago": "2021-02-02"
    }
  ],
  "Devengados": {
    "Basico": {
      "DiasTrabajados": "30",
      "SueldoTrabajado": "200"
    },
  },
  "Deducciones": {
    "Salud": {
      "Porcentaje": "4",
      "Deduccion": "20"
    },
    "FondoPension": {
      "Porcentaje": "4",
      "Deduccion": "20"
    },
  },
  "DevengadosTotal": "20",
  "DeduccionesTotal": "20",
  "ComprobanteTotal": "20",
  "CorrelationDocumentId": "POSTMAN-{{$timestamp}}"
}
```
Tabla de Obligatoriedad

Title | Format | Data Element | Observaciones
----- |  ------ | ------------ | -------------
Periodo |||
FechaIngreso |YYYY-MM-DD||
FechaLiquidacionInicio |YYYY-MM-DD||
FechaLiquidacionFin |YYYY-MM-DD||
TiempoLaborado ||numeral 8.3.1|Se debe enviar en dias ( 1 año = 360 Dias 1 mes = 30 dias)
FechaGen |YYYY-MM-DD||
NumeroSecuenciaXML |||
Prefijo |||
Consecutivo |||
LugarGeneracionXML |||
Pais ||ISO 3166-1|2 caracteres
DepartamentoEstado ||ISO 3166-2|2 caracteres
MunicipioCiudad ||Codigo Municipios ( pag 144)|5 caracteres
Idioma ||ISO 639-1|2 caracteres
InformacionGeneral |||
Version |||"debe ir ""V1.0: Documento Soporte de Pago de Nómina Electrónica"""
Ambiente ||Tabla 5.1.1|1 Carácter (1 prod 2 pruebas)
TipoXML ||Tabla 5.5.7|2 Caracteres ( 102 y 103)
FechaHoraGen |YYYY-MM-DDTHHMMSS||
PeriodoNomina ||Tabla 5.5.1|1 carácter (1 Semanal, 2 Decenal, 3 Catorcenal, 4 quincenal, 5 Mensual, 6 Otro)
TipoMoneda ||Tabla 5.3.2|Para colombia debe ir COP
Empleador |||
NIT |||
DV |||2 Caracteres
Pais ||ISO 3166-1|2 caracteres
DepartamentoEstado ||ISO 3166-2|2 caracteres
MunicipioCiudad ||Codigo Municipios ( pag 144)|5 caracteres
Direccion |||
Trabajador |||
TipoTrabajador ||Tabla 5.5.3|2 Caracteres
SubTipoTrabajador ||Tabla 5.5.4|2 Caracteres
AltoRiegoPension |||"Se debe colocar "" true"" o ""false"""
TipoDocumento ||Tabla 5.2.1|2 Caracteres
NumeroDocumento |||
PrimerApellido |||60 Caracteres
SegundoApellido |||60 Caracteres
PrimerNombre |||60 Caracteres
LugarTrabajoPais ||ISO 3166-1|3 Caracteres
LugarTrabajoDepartamentoEstado ||ISO 3166-2|2 caracteres
LugarTrabajoMunicipioCiudad ||Codigo Municipios ( pag 144)|5 caracteres
LugarTrabajoDireccion |||
SalarioIntegral |||"Se debe colocar "" true"" o ""false"""
TipoContrato ||Tabla 5.5.2|1 Carácter
Sueldo |||
Pago |||
Forma ||Tabla 5.3.3.1|1 Carácter
Metodo ||Tabla 5.3.3.2|2 Caracteres
FechasPagos |||
FechaPago |YYYY-MM-DD||
Devengados |||
Basico |||
DiasTrabajados |||1-2 caracteres
SueldoTrabajado |||
Deducciones |||
Salud |||
Porcentaje |||
Deduccion |||
FondoPension |||
Porcentaje |||
Deduccion |||
DevengadosTotal |||
DeduccionesTotal |||
ComprobanteTotal |||
CorrelationDocumentId |||Campo solicitado por Saphety


Para mayor informacion sobre la documentacion OPENApi del sistema Saphety los invitamos a revisar la documentacion en swagger https://api-factura-electronica-co-qa.saphety.com/swagger/index.html
