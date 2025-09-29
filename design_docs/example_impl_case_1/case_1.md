## RFC: Cálculo de Prima de Servicios
* Ticket Number: [NOMI-111](http://#) Epica - Calculo Prima de Servicios - Contexto Colombia

## Descripción Cambio
* La Prima de Servicios es una prestación social que existe en Colombia y algunos países de latinoamérica. En el caso Colombiano, equivale a 30 días de salario por cada año trabajado, que el empleador debe pagar a sus trabajadores en 2 cuotas semestrales:
* La primera en el mes de Junio.
* La segunda en el mes de Diciembre.
En el siguiente [Documento](https://docs.google.com/document/d/12fiT9fERlCFEsJBnuv19cvETwrXEca2wK8LtLfxcPqg/edit?tab=t.0) puede tener mas detalle de la Epica. 

## Objetivos y Requisitos
* ✅ R1. Metodologías para el cálculo de la prima de servicios. El cliente puede seleccionar/definir la metodología que más se adapta a sus necesidades para el cálculo de la prima de servicio del trabajador.
* ✅ R2. Regla de cálculo de la base de la prima de servicios.
Realizar el cálculo de la prima de servicios teniendo en cuenta los promedios según semestre y teniendo en cuenta la sumatoria de todos los pagos constitutivos del sueldo.
* ✅ R3. Contabilización de Días y Manejo de Ausencias.
Tener en cuenta ausencias no remuneradas y configuración de los días del año calendario para la división del cálculo de la prima.
* ✅ R4. Retención en la fuente por prima.
Dado que la prima de servicio es una ganancia adicional, se debe calcular el descuento de Retención en la fuente.
* ✅ R5. Módulo de Parametrización y Configuración Avanzada.
Capacidad de realizar configuraciones que permitan flexibilidad para el cálculo de la prima de servicios.

## Documentación Técnica
Arquitectura elegida. La implementación sigue con el uso del patrón MVC en Monolito Legacy de Ruby on Rails. En el siguiente diagrama se describe los componentes del motor de reglas de cálculo de prima con sus interacciones más importantes.
<img width="1202" height="616" alt="image" src="https://github.com/user-attachments/assets/e76c6203-c6f0-4aee-8307-976f8c7d92f8" />

###### Calculo Retención en la Fuente Prima de Servicios:
Retención en la fuente por prima.  La retención en la fuente es un adelanto de impuesto que se aplica en Colombia a toda ganancia que recibe el colaborador, el monto calculado se debe expresar como un descuento.
* Renta Exenta: El 25% del valor de la prima bruta es una renta exenta, pero solo hasta un límite anual de 790 UVT. Deberás considerar si la prima actual, sumada a otras primas del año (si las hubiera, aunque para este ejercicio puedes asumir que no hay otras primas para simplificar si lo deseas), supera este límite anual.
* Base Gravable: Una vez aplicada la renta exenta, el valor restante constituye la base gravable.
* Aplicación de la Tabla del Artículo 383 del Estatuto Tributario: Si la base gravable de la prima (después de aplicar la exención del 25%) supera las 95 UVT, se le debe aplicar la tabla de retención en la fuente del artículo 383 del Estatuto Tributario. Para simplificar, puedes asumir que la prima es el único ingreso para la aplicación de esta tabla.
* Valor UVT: Puedes asumir que el valor de la UVT para el año actual es de $47.065 COP.
* Se considera la aplicación de este descuento solo en aquellos sueldos que superan el monto mínimo establecido ley (cuando Base_UVT es este 0 a 90 UVT).

| Descripción | Cálculo |
|-------------|---------|
| <img width="500" height="422" alt="image" src="https://github.com/user-attachments/assets/71d5b04e-3d6c-48fd-ae32-e9b7b46c0f38" /> | <img width="400" height="250" alt="image" src="https://github.com/user-attachments/assets/247b2586-3a2d-4f4b-bed5-05b451db7740" /> |

###### Modelo de Datos Actual:
<img width="973" height="550" alt="image" src="https://github.com/user-attachments/assets/befec64e-eece-4fef-a7ee-a9bfb5199bd0" />

###### Actualización Modelo de Datos Propuesto:
[PENDIENTE]

###### Validaciones Adicionales:
* Si escoge la opción de sueldo base, internamente se realizará también el cálculo de promedio mensual, con el objetivo de validar que el sueldo base y promedio mensual sean iguales. Si el resultado no es el mismo, se mostrará una aviso al usuario para que se asegure que si tomó la opción correcta, dado que el empleado al parecer tuvo un cambio de salario en el semestre, y así pueda evaluar la liquidación.

## Pruebas
[PENDIENTE]

## Monitoreo, KPIs, Evidencias
[PENDIENTE]

## Monitoreo, KPIs, Evidencias
[PENDIENTE]

## Estrategia de Despliegue
* Despliegue de la nueva versión 1.12.2.
* En caso de ocurrir algún problema, Rollback a la versión 1.12.1.
* Despliegue Canary al 1% para comprobar que el proyecto levanta correctamente.
* Despliegue Canary al 30% durante 30 minutos para monitorear que todo vaya bien.
* Despliegue Blue Green para asentar la nueva versión. 

###### Plantilla Docs Designs: https://github.com/charliesbot/design-docs/tree/main/spanish#
