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

###### Calculo Retención en la Fuente Prima de Servicios:
| Descripción | Cálculo |
|-------------|--------|
| 1           | 2     |

###### Modelo de Datos Actual:
<img width="973" height="550" alt="image" src="https://github.com/user-attachments/assets/befec64e-eece-4fef-a7ee-a9bfb5199bd0" />

###### Actualización Modelo de Datos Propuesto:
[PENDIENTE]

###### Validaciones Adicionales:
* Si escoge la opción de sueldo base, internamente se realizará también el cálculo de promedio mensual, con el objetivo de validar que el sueldo base y promedio mensual sean iguales. Si el resultado no es el mismo, se mostrará una aviso al usuario para que se asegure que si tomó la opción correcta, dado que el empleado al parecer tuvo un cambio de salario en el semestre, y así pueda evaluar la liquidación.

### Detalle técnico Calculo Retención en la Fuente.

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
