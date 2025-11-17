
# Caso 3: Calculadora de Presupuesto Mensual

## 1. Descripción del Caso
El sistema es una aplicación web sencilla accesible desde computadoras o dispositivos móviles. Está diseñada para facilitar la gestión de finanzas personales mediante el registro y control de ingresos y gastos mensuales. Su propósito es optimizar el proceso de registro, categorización y visualización de transacciones financieras, permitiendo a los usuarios tomar decisiones informadas sobre su presupuesto de manera rápida, confiable y organizada.

## 2. Objetivo
- Automatizar el registro, cálculo y visualización de ingresos y gastos.
- Reducir errores en el control manual de finanzas personales.
- Mejorar la capacidad del usuario para gestionar su presupuesto mensual.
- Garantizar la seguridad y disponibilidad de la información financiera personal.

## 3. Requerimientos funcionales

| ID | Nombre del requisito | Descripción | Criterios de aceptación |
|----|-----------------------|-------------|---------------------------|
| RF01 | Registro de ingresos | El sistema permitirá al usuario registrar ingresos mensuales indicando fecha, descripción, monto y categoría. | El sistema debe registrar el ingreso y mostrar un mensaje de confirmación exitosa en menos de 2 segundos. |
| RF02 | Registro de gastos | El sistema permitirá al usuario registrar gastos mensuales indicando fecha, descripción, monto y categoría. | El sistema debe registrar el gasto y actualizar el balance automáticamente en menos de 2 segundos. |
| RF03 | Categorización de transacciones | El sistema permitirá clasificar ingresos y gastos en categorías predefinidas. | El usuario debe poder asignar una categoría a cada transacción sin errores. |
| RF04 | Cálculo automático de balance | El sistema calculará automáticamente el balance mensual. | El balance debe actualizarse en tiempo real cuando se agregue, edite o elimine una transacción. |
| RF05 | Visualización de resumen mensual | Se mostrará un resumen del mes con totales por categoría y balance. | El usuario debe visualizar correctamente el resumen. |
| RF06 | Edición y eliminación de transacciones | El sistema permitirá modificar o eliminar transacciones. | El balance debe actualizarse tras editar o eliminar una transacción. |

### 3.1 Requerimientos no funcionales

| ID | Nombre del requisito | Descripción | Tipo | Criterios de aceptación |
|----|----------------------|-------------|------|-------------------------|
| RNF01 | Rendimiento y tiempo de respuesta | Tiempo menor a 2 segundos para operaciones básicas. | Producto (rendimiento) | No debe superar los 2 segundos en pruebas de funcionamiento. |
| RNF02 | Disponibilidad y persistencia de datos | Garantiza la disponibilidad y persistencia local de los datos. | Organización (Fiabilidad) | Los datos deben persistir tras cerrar la aplicación. |
| RNF03 | Cumplimiento de estándares y privacidad | Protege la información financiera del usuario. | Externo (Legal/Ético) | Los datos no se transmiten a terceros. |

## 4. Tabla de pruebas

ID Prueba | Tipo de pruebas | Requerimientos asociados | Datos de entrada | Resultados esperados | Resultados obtenidos
---------|----------------|-------------------------|------------------|---------------------|---------------------
PU-01 | Unitarias | RF01 - Registro de ingresos | Fecha: 15/11/2025, Descripción: "Salario", Monto: 1500.00, Categoría: "Salario" | El sistema registra el ingreso y muestra mensaje "Ingreso registrado exitosamente" en menos de 2 segundos. | Registrado correctamente. Tiempo: 1.8 s
PU-02 | Unitarias | RF02 - Registro de gastos | Fecha: 16/11/2025, Descripción: "Supermercado", Monto: 350.75, Categoría: "Alimentación" | El sistema registra el gasto y actualiza el balance en menos de 2 segundos. | Gasto registrado correctamente. Balance actualizado. Tiempo: 1.6 s
PU-03 | Unitarias | RF04 - Cálculo automático de balance | Ingresos: $1500.00, Gastos: $350.75 | El sistema calcula y muestra el balance correcto con precisión de 2 decimales en menos de 2 segundos. | Balance calculado correctamente: $1149.25
PV-01 | Validaciones | RF06 - Edición y eliminación de transacciones | Transacción ID #003, Acción: Editar monto de $350.75 a $400.00 y luego eliminar | El sistema actualiza la transacción correctamente, muestra mensaje "Transacción actualizada exitosamente" y permite eliminarla sin errores. | Transacción editada y eliminada correctamente. Mensajes mostrados según lo esperado.
PV-02 | Validaciones | RF05 - Visualización de resumen mensual | Acción: Consultar resumen del mes actual | El sistema muestra el resumen con totales de ingresos, gastos, balance y categorías, sin errores. | Resumen visualizado correctamente. Datos completos y ordenados cronológicamente.

## 5. Tipos de mantenimiento propuestos

### Situación 1: Cálculo incorrecto de balance con decimales

**Problema:** Redondeo incorrecto por manejo de punto flotante.

| Tipo de mantenimiento | Acción |
|-----------------------|--------|
| Correctivo | Implementación de funciones de redondeo precisas. |
| Preventivo | Pruebas unitarias para validar cálculos con decimales. |
| Perfectivo | Optimización del algoritmo y formato visual de moneda. |

### Situación 2: Pérdida de datos al cerrar la aplicación

**Problema:** No existía persistencia de datos.

| Tipo de mantenimiento | Acción |
|-----------------------|--------|
| Correctivo | Implementación de localStorage. |
| Preventivo | Sistema de respaldo automático cada 30 segundos. |
| Perfectivo | Indicadores de guardado automático y exportación de datos. |

### 5.1 Cambio funcional propuesto
**Nombre:** Módulo de Alertas Inteligentes y Metas de Presupuesto  
Incluye metas de ahorro, alertas por categoría, análisis predictivo, dashboard visual y comparaciones mensuales.

## 6. Reflexión sobre Control de Versiones y Markdown
El **control de versiones** es una herramienta esencial en la ingeniería de software moderna, ya que permite gestionar los cambios realizados en el código y la documentación de forma estructurada, trazable y colaborativa. Entre sus principales beneficios se encuentra la posibilidad de mantener un flujo de trabajo seguro, registrar cada cambio en pequeños incrementos y revertir fácilmente cualquier error. Además, fomenta la experimentación sin riesgos, al permitir crear ramas o versiones paralelas para probar nuevas funcionalidades sin afectar la versión estable del proyecto.

Como señala Pressman (2010), los procesos de desarrollo ágil y colaborativo requieren prácticas que reduzcan el riesgo de errores y mejoren la comunicación entre los integrantes del equipo; en este contexto, el control de versiones actúa como un mecanismo de soporte indispensable. Según Sommerville (2011), el mantenimiento del software exige procesos sistemáticos que garanticen la continuidad operativa y la calidad del sistema a lo largo de su ciclo de vida. En ese sentido, el control de versiones se convierte en un pilar fundamental para mantener la integridad del proyecto, reducir riesgos y facilitar el trabajo en equipo de forma organizada.

Herramientas como Git y plataformas como GitHub materializan estos principios al registrar cada modificación mediante "commits descriptivos", crear ramas para el desarrollo paralelo y restaurar versiones anteriores en caso de errores. Esto mejora la transparencia, fomenta la colaboración y fortalece la mantenibilidad del software.

De manera complementaria, el **lenguaje Markdown** ofrece una forma práctica y eficiente de documentar información técnica. Su sintaxis ligera mejora la claridad y accesibilidad de la documentación, permitiendo crear títulos, listas, tablas y enlaces sin depender de procesadores de texto complejos. Markdown promueve una escritura más directa y estandarizada. Al integrarse con sistemas de control de versiones como GitHub, permite que el código y la documentación evolucionen de forma coherente.

En conjunto, **Git/GitHub y Markdown** representan herramientas que fortalecen la calidad, sostenibilidad y trazabilidad de los proyectos de software. Ambas promueven la organización, la colaboración y la eficiencia, alineándose con los principios de mantenibilidad y gestión del cambio definidos por Sommerville (2011) y Pressman (2010). Su correcta aplicación no solo mejora la gestión técnica del sistema, sino también la experiencia y productividad de quienes lo desarrollan y documentan.
