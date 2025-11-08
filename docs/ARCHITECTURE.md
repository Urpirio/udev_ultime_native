# Arquitectura de udev_ultime_native

## Visión General

**udev_ultime_native** es una librería de componentes UI para React Native diseñada con principios de modularidad, reutilización y tipado fuerte con TypeScript. Esta guía explica la arquitectura interna y las decisiones de diseño.

## Estructura del Proyecto

```
udev_ultime_native/
├── src/
│   ├── Components/          # Componentes UI individuales
│   │   ├── Button.tsx
│   │   ├── InputText.tsx
│   │   ├── InputPassword.tsx
│   │   ├── InputTextarea.tsx
│   │   ├── DropDown.tsx
│   │   ├── ProgressBar.tsx
│   │   ├── Card_Simple.tsx
│   │   ├── FloatingButton.tsx
│   │   ├── RadioButton.tsx
│   │   ├── ButtonBar.tsx
│   │   └── TabPanel.tsx
│   ├── LayOut/              # Sistema de layouts
│   │   ├── LayoutScreen.tsx
│   │   ├── Layout_Objects_Components.tsx
│   │   └── Layout_Types.tsx
│   ├── types.tsx            # Definiciones de tipos TypeScript
│   ├── index.tsx            # Punto de entrada principal
│   └── __tests__/           # Tests unitarios
├── docs/                    # Documentación
├── example/                 # Aplicación de ejemplo
└── package.json
```

## Principios de Diseño

### 1. Componentes Modulares

Cada componente está diseñado para ser independiente y reutilizable:

- **Responsabilidad única**: Cada componente tiene una función específica
- **Props configurables**: Todos los componentes aceptan props para personalización
- **Estilos por defecto**: Los componentes funcionan sin configuración adicional
- **Composición sobre herencia**: Los componentes se pueden combinar para crear interfaces complejas

### 2. TypeScript First

La librería está completamente escrita en TypeScript:

- **Tipado fuerte**: Todas las props y estados están tipados
- **Autocompletado**: Los editores pueden sugerir props y valores
- **Detección de errores**: Los errores de tipo se detectan en tiempo de compilación
- **Documentación integrada**: Los tipos sirven como documentación

### 3. Optimización de Rendimiento

Estrategias implementadas para mantener el rendimiento:

- **Animaciones nativas**: Uso de `react-native-reanimated` para animaciones fluidas
- **Memorización**: Componentes optimizados con `memo` cuando es necesario
- **Lazy loading**: Carga diferida de componentes pesados
- **Estilos optimizados**: StyleSheet.create para mejor rendimiento

### 4. Accesibilidad

Todos los componentes incluyen soporte para accesibilidad:

- **Labels descriptivos**: Props para etiquetas accesibles
- **Eventos de accesibilidad**: Soporte para onAccessibilityAction, onAccessibilityTap, etc.
- **Navegación por teclado**: Compatibilidad con dispositivos de asistencia
- **Contraste apropiado**: Estilos por defecto con buena legibilidad

## Categorías de Componentes

### Componentes de Entrada

Componentes para capturar información del usuario:

#### InputText
- Campo de texto genérico con soporte para iconos
- Validación personalizable
- Estados: normal, enfocado, error

#### InputPassword
- Campo específico para contraseñas
- Toggle para mostrar/ocultar contraseña
- Manejo interno del estado de visibilidad

#### InputTextarea
- Campo de texto multilínea
- Ajuste automático de altura (opcional)
- Soporte para conteo de caracteres

#### DropDown
- Menú desplegable con opciones
- Búsqueda integrada (opcional)
- Soporte para opciones agrupadas

### Componentes de Acción

Componentes que responden a interacciones del usuario:

#### Button
- Botón versátil con múltiples estilos
- Soporte para iconos izquierda/derecha
- Tres tipos de interacción: TouchableOpacity, Pressable, TouchableHighlight

#### ButtonBar
- Barra de botones para navegación
- Múltiples tipos de botón en un solo componente
- Layout flexible con distribución automática

#### FloatingButton
- Botón flotante con menú expandible
- Animaciones suaves con Reanimated
- Opciones configurables con iconos

### Componentes de Visualización

Componentes para mostrar información:

#### ProgressBar
- Barra de progreso visual
- Estados coloreados configurables
- Soporte para iconos y porcentajes

#### Card_Simple
- Tarjeta con imagen, título y descripción
- Layout responsive
- Botón de acción integrado

### Componentes de Navegación

Componentes para estructurar la navegación:

#### TabPanel
- Sistema de pestañas horizontal
- Contenido dinámico por pestaña
- Scroll horizontal automático

#### RadioButton
- Botón de opción para selección única
- Diseño circular personalizable
- Manejo de estado externo

### Sistema de Layout

#### LayoutScreen
- Sistema completo de layout para pantallas
- Tres tipos de barra inferior:
  - Default: Barra estándar
  - Bar_Floating: Barra flotante centrada
  - BarWithFloatingButton: Barra con botón flotante
- Integración con SafeAreaProvider
- Soporte para scroll y vista estática

## Gestión de Estado

### Estado Local vs. Estado Externo

La librería sigue estas convenciones:

**Estado Local (Interno)**:
- InputPassword: Maneja su propio estado de visibilidad
- FloatingButton: Maneja el estado de expansión del menú
- TabPanel: Maneja la pestaña seleccionada

**Estado Externo (Props)**:
- InputText: El valor debe ser controlado por el componente padre
- DropDown: La selección se controla desde el padre
- RadioButton: El valor seleccionado viene del padre

### Patrón de Props

Todos los componentes siguen un patrón consistente de props:

```typescript
interface ComponentProps {
  // Props funcionales (requeridas)
  value?: string;
  onPress?: () => void;
  
  // Props de estilo (opcionales)
  style_container?: StyleProp<ViewStyle>;
  style_text?: StyleProp<TextStyle>;
  
  // Props de contenido (opcionales)
  iconLeft?: ReactNode;
  iconRight?: ReactNode;
  
  // Props de accesibilidad (opcionales)
  onAccessibilityAction?: () => void;
  onAccessibilityTap?: () => void;
}
```

## Dependencias

### Dependencias Peer

La librería requiere las siguientes dependencias como peer dependencies:

1. **react-native**: Framework base
2. **react-native-reanimated**: Para animaciones del FloatingButton
3. **react-native-safe-area-context**: Para manejo de áreas seguras en LayoutScreen

### Por qué Peer Dependencies

- **Evitar duplicación**: No se instalan múltiples versiones de React Native
- **Compatibilidad**: El usuario puede elegir versiones compatibles con su proyecto
- **Tamaño reducido**: El bundle final es más pequeño

## Patrones de Diseño Utilizados

### 1. Composition Pattern

Los componentes se pueden componer para crear interfaces complejas:

```typescript
<LayoutScreen
  topBar={<CustomTopBar />}
  bodyScreen={
    <View>
      <InputText />
      <Button />
    </View>
  }
  bottomBar={<CustomBottomBar />}
/>
```

### 2. Render Props Pattern

Algunos componentes aceptan elementos personalizados como props:

```typescript
<Card_Simple
  Button={<CustomButton />}
  label={<CustomLabel />}
/>
```

### 3. Compound Components Pattern

El sistema de layout utiliza componentes compuestos:

```typescript
<LayoutScreen
  type_BottomBar="Default"
  Data_BottomBar={[...]}
/>
```

## Convenciones de Código

### Nomenclatura

- **Componentes**: PascalCase (Button, InputText)
- **Props de estilo**: snake_case con prefijo style_ (style_container, style_button)
- **Props de datos**: camelCase (dataOption, selectedValue)
- **Tipos**: PascalCase con sufijo Type o Props (ButtonProps, LayoutType)

### Estructura de Archivos

Cada componente sigue esta estructura:

```typescript
import React from 'react';
import { View, Text, StyleSheet } from 'react-native';

// Tipos e interfaces
interface ComponentNameProps {
  // Props definidas aquí
}

// Componente principal
export const ComponentName: React.FC<ComponentNameProps> = (props) => {
  // Lógica del componente
  
  return (
    // JSX
  );
};

// Estilos por defecto
const styles = StyleSheet.create({
  // Estilos aquí
});
```

## Extensibilidad

### Cómo Agregar Nuevos Componentes

1. Crear archivo en `src/Components/`
2. Definir interfaces TypeScript
3. Implementar componente con estilos por defecto
4. Exportar desde `src/index.tsx`
5. Agregar tests en `src/__tests__/`
6. Documentar en `docs/api/`

### Cómo Personalizar Componentes

Los usuarios pueden personalizar componentes de varias formas:

1. **Estilos personalizados**: Usando las props style_*
2. **Iconos personalizados**: Pasando componentes JSX
3. **Comportamiento personalizado**: Usando callbacks y handlers
4. **Composición**: Combinando múltiples componentes

## Testing

### Estrategia de Testing

- **Tests unitarios**: Para lógica de componentes individuales
- **Tests de integración**: Para sistemas complejos como LayoutScreen
- **Tests de snapshot**: Para detectar cambios visuales no intencionados

### Herramientas

- Jest para ejecución de tests
- React Native Testing Library para tests de componentes
- TypeScript para validación de tipos en tiempo de compilación

## Roadmap Futuro

### Componentes Planeados

- Checkbox component
- Switch component
- Slider component
- Modal component
- DatePicker component

### Mejoras Planeadas

- Temas personalizables (dark mode)
- Internacionalización (i18n)
- Animaciones más avanzadas
- Mejoras de accesibilidad
- Optimizaciones de rendimiento

## Conclusión

La arquitectura de udev_ultime_native está diseñada para ser:

- **Modular**: Componentes independientes y reutilizables
- **Extensible**: Fácil de agregar nuevos componentes
- **Mantenible**: Código limpio y bien estructurado
- **Performante**: Optimizado para rendimiento en dispositivos móviles
- **Accesible**: Soporte para usuarios con necesidades especiales

Para más información sobre componentes específicos, consulta la [Referencia de API](./api/README.md).
