# Propuesta de Mantenimiento

## Calculadora de Presupuesto Mensual

------------------------------------------------------------------------

## 1. INTRODUCCIÓN

### 1.1 Propósito del Documento

Este documento describe las estrategias y actividades de mantenimiento
para la Calculadora de Presupuesto Mensual, asegurando su correcto
funcionamiento, adaptación a nuevas necesidades y mejora continua.

### 1.2 Alcance

El plan cubre tres tipos de mantenimiento: - **Correctivo**: Corrección
de errores y defectos - **Adaptativo**: Adaptación a cambios del
entorno - **Perfectivo**: Mejoras en funcionalidad y rendimiento

------------------------------------------------------------------------

## 2. TIPOS DE MANTENIMIENTO

### 2.1 Mantenimiento Correctivo

El mantenimiento correctivo se enfoca en identificar y corregir errores
o defectos del sistema después de su puesta en producción.

#### 2.1.1 Problemas Identificados

##### ERROR 001: Cálculo Incorrecto con Decimales

**Descripción**: En algunos casos, el balance muestra más de 2 decimales
o realiza redondeos incorrectos.

**Severidad**: Alta\
**Prioridad**: Crítica\
**Ejemplo**: - Ingreso: \$1000.33 - Gasto: \$500.11 - Balance mostrado:
\$500.219999999 (incorrecto) - Balance esperado: \$500.22

**Solución Propuesta**:

``` javascript
// Implementar función de redondeo
function roundToTwo(num) {
    return Math.round((num + Number.EPSILON) * 100) / 100;
}

// Aplicar en todos los cálculos
balance = roundToTwo(totalIngresos - totalGastos);
```

**Tiempo Estimado**: 2 horas\
**Responsable**: Desarrollador\
**Fecha Objetivo**: Inmediata

------------------------------------------------------------------------

##### ERROR 002: Transacciones No Persisten Después de Cerrar la Aplicación

**Descripción**: Los datos ingresados se pierden cuando el usuario
cierra y vuelve a abrir la aplicación.

**Severidad**: Alta\
**Prioridad**: Alta\
**Impacto**: Los usuarios pierden todo su historial financiero

**Solución Propuesta**:

``` javascript
// Implementar almacenamiento local
function guardarTransacciones(transacciones) {
    localStorage.setItem('transacciones', JSON.stringify(transacciones));
}

function cargarTransacciones() {
    const data = localStorage.getItem('transacciones');
    return data ? JSON.parse(data) : [];
}
```

**Tiempo Estimado**: 4 horas\
**Responsable**: Desarrollador\
**Fecha Objetivo**: Dentro de 1 semana

------------------------------------------------------------------------

##### ERROR 003: Categorías Duplicadas en el Selector

**Descripción**: Al agregar transacciones, algunas categorías aparecen
duplicadas en el menú desplegable.

**Severidad**: Media\
**Prioridad**: Media\
**Causa Raíz**: Falta de validación al cargar las categorías

**Solución Propuesta**:

``` javascript
// Eliminar duplicados en el array de categorías
const categoriasUnicas = [...new Set(categorias)];
```

**Tiempo Estimado**: 1 hora\
**Responsable**: Desarrollador\
**Fecha Objetivo**: Dentro de 2 semanas

------------------------------------------------------------------------

### 2.2 Mantenimiento Adaptativo

El mantenimiento adaptativo ajusta el sistema a cambios en el entorno
operativo, tecnológico o de negocio.

#### 2.2.1 Adaptaciones Propuestas

##### ADAPTACIÓN 001: Soporte Multi-Moneda

**Justificación**: Usuarios en diferentes países necesitan usar su
moneda local.

**Cambios Necesarios**: - Agregar selector de moneda (USD, EUR, COP,
MXN, etc.) - Guardar preferencia del usuario - Mostrar símbolo de moneda
correspondiente - Permitir conversión entre monedas (opcional)

**Implementación**:

``` javascript
const monedas = {
    USD: { simbolo: '$', nombre: 'Dólar' },
    EUR: { simbolo: '€', nombre: 'Euro' },
    COP: { simbolo: '$', nombre: 'Peso Colombiano' },
    MXN: { simbolo: '$', nombre: 'Peso Mexicano' }
};

// Guardar preferencia
localStorage.setItem('moneda', monedaSeleccionada);
```

**Tiempo Estimado**: 8 horas\
**Costo Estimado**: \$0 (desarrollo propio)\
**Beneficio**: Ampliar base de usuarios internacionales\
**Fecha Objetivo**: Próxima versión (v2.0)

------------------------------------------------------------------------

##### ADAPTACIÓN 002: Modo Oscuro

**Justificación**: Tendencia actual de diseño y preferencia de usuarios
para reducir fatiga visual.

**Cambios Necesarios**: - Implementar paleta de colores para tema
oscuro - Agregar interruptor de cambio de tema - Guardar preferencia del
usuario - Asegurar contraste adecuado (WCAG)

**Implementación**:

``` css
/* Tema oscuro */
.dark-mode {
    --bg-color: #1a1a1a;
    --text-color: #ffffff;
    --card-bg: #2d2d2d;
    --border-color: #404040;
}
```

**Tiempo Estimado**: 6 horas\
**Beneficio**: Mejor experiencia de usuario\
**Fecha Objetivo**: Próxima versión (v2.0)

------------------------------------------------------------------------

##### ADAPTACIÓN 003: Compatibilidad con Dispositivos Móviles

**Justificación**: Más del 60% de usuarios acceden desde dispositivos
móviles.

**Cambios Necesarios**: - Optimizar layout para pantallas pequeñas
(320px - 768px) - Implementar gestos táctiles (swipe para eliminar) -
Ajustar tamaño de botones para touch (mínimo 44x44px) - Mejorar
formularios para teclados móviles

**Implementación**:

``` css
/* Diseño responsive mejorado */
@media (max-width: 768px) {
    .transaction-card {
        font-size: 16px;
        padding: 16px;
    }

    .btn {
        min-height: 44px;
        min-width: 44px;
    }
}
```

**Tiempo Estimado**: 12 horas\
**Prioridad**: Alta\
**Fecha Objetivo**: Versión 1.5

------------------------------------------------------------------------

##### ADAPTACIÓN 004: Exportación de Datos a Excel

**Justificación**: Usuarios necesitan analizar datos en herramientas
externas o compartir reportes.

**Funcionalidad**: - Botón "Exportar a Excel" - Generar archivo .xlsx
con todas las transacciones - Incluir hoja de resumen con totales

**Tiempo Estimado**: 10 horas\
**Librería Sugerida**: SheetJS (xlsx)\
**Fecha Objetivo**: Versión 2.0

------------------------------------------------------------------------

### 2.3 Mantenimiento Perfectivo

El mantenimiento perfectivo mejora el rendimiento, usabilidad y
mantenibilidad del sistema sin corregir errores.

#### 2.3.1 Mejoras Propuestas

##### MEJORA 001: Gráficos Visuales Interactivos

**Descripción**: Agregar gráficos de pastel y barras para visualizar
distribución de gastos.

**Funcionalidad**: - Gráfico circular de gastos por categoría - Gráfico
de barras de evolución mensual - Interactividad al pasar el cursor
(tooltips)

**Implementación**:

``` javascript
// Usar librería Chart.js
import Chart from 'chart.js';

const ctx = document.getElementById('gastosPorCategoria');
new Chart(ctx, {
    type: 'pie',
    data: {
        labels: categorias,
        datasets: [{
            data: montosPorCategoria,
            backgroundColor: colores
        }]
    }
});
```

**Beneficios**: - Mayor claridad visual - Mejor comprensión de patrones
de gasto - Interfaz más atractiva

**Tiempo Estimado**: 15 horas\
**Prioridad**: Media\
**Fecha Objetivo**: Versión 2.0

------------------------------------------------------------------------

(Truncated for brevity in Python block; full content continues...)
