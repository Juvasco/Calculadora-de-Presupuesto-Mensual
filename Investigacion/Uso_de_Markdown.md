# MARKDOWN

## 1. ¿Qué es Markdown y por qué se utiliza en proyectos de software?

Markdown es un lenguaje de marcado ligero que permite dar formato a
textos de manera sencilla utilizando símbolos y caracteres comunes (como
#, \*, o -). Fue creado por John Gruber en 2004 con el objetivo de ser
fácil de leer y escribir, incluso sin convertirlo a HTML.

En el contexto de la ingeniería de software, Markdown se utiliza
ampliamente para documentar proyectos, escribir archivos README,
manuales técnicos, reportes, e incluso documentación de APIs.

Su uso en proyectos de software es importante porque:

-   Facilita la lectura y comprensión del contenido, incluso sin
    herramientas adicionales.
-   Permite mantener la documentación junto al código en el mismo
    repositorio (por ejemplo, en GitHub).
-   Favorece la colaboración, ya que varios usuarios pueden editar y
    versionar la documentación fácilmente mediante sistemas de control
    de versiones como Git.
-   Se puede convertir fácilmente a HTML, lo que lo hace ideal para
    documentación en línea.

## 2. Ejemplo práctico de uso de Markdown

A continuación se presentan los elementos más comunes utilizados en
documentación de software con Markdown:

### Encabezados

Los encabezados se crean usando el símbolo \# seguido de un espacio. El
número de \# determina el nivel jerárquico:

# Título Principal del Proyecto

## Sección de Instalación

### Requisitos Previos

#### Paso 1: Configuración

### Listas

**Lista desordenada (con viñetas):** - Requerimientos funcionales -
Requerimientos no funcionales - Plan de pruebas

**Lista ordenada (numerada):** 1. Clonar el repositorio desde GitHub 2.
Instalar las dependencias necesarias 3. Ejecutar el sistema en modo
desarrollo 4. Realizar pruebas de funcionalidad

### Tablas

Las tablas permiten organizar información de forma estructurada y son
muy útiles para documentar especificaciones:

  Requerimiento   Prioridad   Estado
  --------------- ----------- -------------
  RF-001          Alta        Completado
  RF-002          Alta        En progreso
  RNF-001         Media       Pendiente

### Enlaces

[Repositorio del proyecto en
GitHub](https://github.com/Juvasco/-Calculadora-de-presupuesto-mensual.git)

### Imágenes

![GitHub Icon](https://cdn-icons-png.flaticon.com/512/25/25231.png)

### Formato de texto

**Texto en negrita** se usa para destacar términos importantes. *Texto
en cursiva* se emplea para énfasis o términos técnicos.
`código en línea` se utiliza para mencionar comandos o variables.

### Bloques de código

Para mostrar fragmentos de código, se usan tres comillas invertidas
seguidas del lenguaje:

``` javascript
function calcularBalance(ingresos, gastos) {
    return ingresos - gastos;
}
```

## 3. Ventajas de utilizar Markdown en combinación con GitHub

El uso de **Markdown** junto con **GitHub** ofrece una integración muy
poderosa para el desarrollo colaborativo y la documentación profesional.
Algunas ventajas destacadas son:

-   **Documentación integrada:** GitHub interpreta automáticamente los
    archivos `.md` y los muestra con formato legible dentro del
    repositorio.
-   **Control de versiones:** Permite mantener un historial de cambios
    de la documentación, igual que con el código.
-   **Colaboración en equipo:** Varios desarrolladores pueden editar la
    misma documentación y realizar revisiones mediante pull requests.
-   **Visualización inmediata:** Los archivos Markdown se renderizan
    directamente en la interfaz web de GitHub, facilitando la lectura
    sin necesidad de herramientas externas.
-   **Compatibilidad:** Markdown se usa también en wikis, issues y pull
    requests, lo que unifica el formato de comunicación técnica dentro
    de la plataforma.
