# Changelog

Todos los cambios notables en este proyecto serán documentados en este archivo.

El formato está basado en [Keep a Changelog](https://keepachangelog.com/es/1.0.0/),
y este proyecto adhiere a [Semantic Versioning](https://semver.org/lang/es/).

## [3.8.1] - 2024-11-08

### Agregado
- Documentación completa del proyecto
  - Guía de inicio rápido (GETTING_STARTED.md)
  - Arquitectura del proyecto (ARCHITECTURE.md)
  - Referencia completa de API (api/README.md)
  - Guía de solución de problemas (TROUBLESHOOTING.md)
  - Changelog (CHANGELOG.md)
  - Ejemplos de uso (examples/README.md)

## [3.8.0] - 2024-11-07

### Agregado
- **RadioButton**: Componente de botón de opción con selección única
  - Diseño circular con punto interior
  - Estilos personalizables para contenedor, label, radio y punto
  - Integración con useState para manejo de estado externo
  - Diseño responsivo con flexDirection row

- **ButtonBar**: Barra de botones con múltiples tipos de interacción
  - Soporte para Pressable, Button, TouchableOpacity y TouchableHighlight
  - Propiedad `text` para personalizar el contenido del botón
  - Cada botón muestra su nombre por defecto si no se proporciona `text`
  - Diseño responsivo con flexDirection row y justifyContent space-between

- **TabPanel**: Sistema de pestañas horizontal con contenido dinámico
  - Navegación horizontal con ScrollView
  - Estado interno para pestaña seleccionada
  - Contenido dinámico basado en selección
  - Indicador visual con borde inferior
  - Scroll horizontal automático
  - Selección de primera pestaña por defecto

### Mejorado
- Exportaciones actualizadas en `src/index.tsx` para incluir todos los nuevos componentes
- TypeScript completo con tipado fuerte para todos los componentes nuevos

## [3.7.0] - 2024-10-15

### Agregado
- **LayoutScreen**: Sistema completo de layouts para estructurar pantallas
  - Tres tipos de BottomBar predefinidos:
    - `Default`: Barra inferior estándar
    - `Bar_Floating`: Barra flotante centrada con bordes redondeados
    - `BarWithFloatingButton`: Barra estándar con botón flotante integrado
  - Integración con SafeAreaProvider para manejo automático de áreas seguras
  - Soporte para ScrollView y View como contenedores del contenido principal
  - Sistema de botones de navegación con iconos activos/inactivos
  - Configuración completa mediante `Data_BottomBar`
  - TopBar personalizable
  - Floating Button Support con positioning automático

### Dependencias
- Agregada `react-native-safe-area-context` como peer dependency

## [3.6.0] - 2024-09-20

### Agregado
- **FloatingButton**: Botón flotante con opciones expandibles
  - Animaciones suaves usando react-native-reanimated
  - Menú expandible con múltiples opciones
  - Iconos personalizables para estados expandido/colapsado
  - Configuración de timing de animaciones
  - Soporte para onPress y onLongPress personalizados

### Mejorado
- Todas las animaciones ahora utilizan react-native-reanimated para mejor rendimiento

### Dependencias
- Agregada `react-native-reanimated` >= 3.0.0 como peer dependency

## [3.5.0] - 2024-08-15

### Agregado
- **Card_Simple**: Tarjeta simple y elegante
  - Imagen, título, descripción y botón integrados
  - Diseño responsive con ancho fijo de 300px
  - Sombra por defecto para efecto elevado
  - Título se trunca automáticamente después de 25 caracteres
  - Botón personalizable o uso del botón por defecto

### Mejorado
- ProgressBar ahora soporta estados coloreados con `status_bar` prop
- Mejoras en la documentación de todos los componentes

## [3.4.0] - 2024-07-10

### Agregado
- **ProgressBar**: Barra de progreso altamente personalizable
  - Soporte para iconos izquierda/derecha
  - Mostrar porcentaje como texto
  - Estados coloreados configurables
  - Altura personalizable
  - Colores personalizables para barra y contenedor

## [3.3.0] - 2024-06-05

### Agregado
- **DropDown**: Componente de menú desplegable
  - Opciones dinámicas mediante array de objetos
  - Estilos personalizables para contenedor, opciones y texto
  - Placeholder configurable
  - Soporte para iconos
  - Manejo de estado externo para valor seleccionado

## [3.2.0] - 2024-05-01

### Agregado
- **InputTextarea**: Campo de texto multilínea
  - Optimizado para entradas de texto extensas
  - Soporte para numberOfLines
  - Iconos decorativos izquierda/derecha
  - Estilos por defecto con borde y padding

### Mejorado
- InputText ahora soporta prop `label` para etiquetas personalizadas
- Mejoras en la accesibilidad de todos los componentes de entrada

## [3.1.0] - 2024-04-15

### Agregado
- **InputPassword**: Campo específico para contraseñas
  - Manejo interno del estado de visibilidad
  - Toggle de mostrar/ocultar contraseña
  - Iconos personalizables para estados visible/oculto
  - Estilos por defecto con flexDirection row

## [3.0.0] - 2024-03-20

### Agregado
- **InputText**: Campo de texto avanzado
  - Soporte para iconos izquierda/derecha
  - Modo contraseña opcional
  - Múltiples tipos de teclado
  - Estilos personalizables para contenedor e input
  - Eventos de accesibilidad completos

- **Button**: Botón personalizable
  - Tres tipos de interacción: TouchableOpacity, Pressable, TouchableHighlight
  - Soporte para iconos izquierda/derecha
  - Estilos por defecto profesionales
  - Múltiples eventos: onPress, onLongPress, onPressIn, onPressOut
  - Soporte completo de accesibilidad

### Cambiado
- **BREAKING**: Reestructuración completa del proyecto
- Migración a TypeScript completo
- Nueva estructura de carpetas para mejor organización
- Sistema de exportaciones mejorado

### Mejorado
- Mejor sistema de tipado con TypeScript
- Documentación completa de todas las props
- Ejemplos de uso para cada componente
- Performance optimizada en todos los componentes

## [2.0.0] - 2024-02-01

### Agregado
- Sistema de tipado con TypeScript
- Tests unitarios básicos
- Configuración de ESLint y Prettier

### Cambiado
- Migración de JavaScript a TypeScript
- Reestructuración del código para mejor mantenibilidad

## [1.0.0] - 2024-01-01

### Agregado
- Lanzamiento inicial de la librería
- Componentes básicos de UI
- Configuración inicial del proyecto
- README con instalación básica

---

## Convenciones del Changelog

### Tipos de Cambios
- `Agregado` para funcionalidades nuevas
- `Cambiado` para cambios en funcionalidades existentes
- `Deprecado` para funcionalidades que serán removidas
- `Removido` para funcionalidades removidas
- `Corregido` para corrección de bugs
- `Seguridad` para correcciones de vulnerabilidades

### Versionado Semántico
- **Major** (X.0.0): Cambios incompatibles con versiones anteriores
- **Minor** (0.X.0): Nuevas funcionalidades compatibles
- **Patch** (0.0.X): Corrección de bugs y mejoras menores

---

## Enlaces
- [Código de Conducta](./udev_ultime_native/CODE_OF_CONDUCT.md)
- [Guía de Contribución](./udev_ultime_native/CONTRIBUTING.md)
- [Licencia](./LICENSE)
