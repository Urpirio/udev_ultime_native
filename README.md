# udev_ultime_native

[![npm version](https://img.shields.io/npm/v/udev_ultime_native.svg)](https://www.npmjs.com/package/udev_ultime_native)
[![npm downloads](https://img.shields.io/npm/dm/udev_ultime_native.svg)](https://www.npmjs.com/package/udev_ultime_native)
[![license](https://img.shields.io/npm/l/udev_ultime_native.svg)](https://github.com/Urpirio/udev_ultime_native/blob/main/LICENSE)
[![TypeScript](https://img.shields.io/badge/TypeScript-Ready-blue.svg)](https://www.typescriptlang.org/)
[![React Native](https://img.shields.io/badge/React%20Native-%3E%3D0.70-green.svg)](https://reactnative.dev/)

Librería de componentes UI optimizada para React Native que ofrece una colección completa de elementos de interfaz listos para usar: botones personalizables con múltiples tipos de interacción, campos de texto avanzados con soporte para iconos y validación, áreas de texto multilínea, campos de contraseña con visibilidad controlada, menús desplegables dinámicos, barras de progreso configurables, tarjetas simples y botones flotantes con animaciones. Diseñada con TypeScript para mejor tipado y rendimiento optimizado.

## 📚 Documentación Completa

¿Nuevo en la librería? Consulta nuestra **[Documentación Completa](./docs/README.md)** que incluye:

- **[Guía de Inicio Rápido](./docs/GETTING_STARTED.md)** - Instalación y configuración paso a paso
- **[Referencia de API](./docs/api/README.md)** - Documentación detallada de todos los componentes
- **[Referencia Rápida](./docs/QUICK_REFERENCE.md)** - Guía rápida con ejemplos concisos
- **[Ejemplos de Uso](./docs/examples/README.md)** - Casos de uso reales y ejemplos prácticos
- **[Arquitectura](./docs/ARCHITECTURE.md)** - Estructura interna y decisiones de diseño
- **[Solución de Problemas](./docs/TROUBLESHOOTING.md)** - Guía para resolver problemas comunes
- **[Changelog](./CHANGELOG.md)** - Historial de cambios y versiones

## Installation

```sh
npm install udev_ultime_native react-native-reanimated react-native-safe-area-context
```

> **Nota**: `react-native-reanimated` es requerido para las animaciones del `FloatingButton`, y `react-native-safe-area-context` es requerido para el manejo de áreas seguras en `LayoutScreen`. Consulta la [Guía de Inicio Rápido](./docs/GETTING_STARTED.md) para instrucciones de configuración detalladas.

## Versión Actual: 3.8.0

### Cambios Recientes (v3.8.0)

- ✅ **RadioButton**: Componente de botón de opción con selección única y estilos personalizables
- ✅ **ButtonBar**: Barra de botones con múltiples tipos de interacción (Pressable, TouchableOpacity, TouchableHighlight)
- ✅ **TabPanel**: Sistema de pestañas horizontal con descripción dinámica y navegación por scroll
- ✅ **Mejoras de exportación**: Todos los componentes nuevos exportados desde el índice principal
- ✅ **TypeScript completo**: Tipado fuerte para todos los componentes nuevos

### Cambios Anteriores (v3.7.0)

- ✅ **LayoutScreen System**: Sistema completo de layouts para estructurar pantallas con topBar, bottomBar y bodyScreen
- ✅ **Tres tipos de BottomBar**: `Default`, `Bar_Floating`, y `BarWithFloatingButton` con estilos predefinidos
- ✅ **SafeAreaProvider Integration**: Manejo automático de áreas seguras en dispositivos con notch o barras de estado
- ✅ **Navegación Configurable**: Sistema de botones de navegación con iconos activos/inactivos y estados personalizables
- ✅ **Body Types**: Soporte para `ScrollView` y `View` como contenedores del contenido principal
- ✅ **Floating Button Support**: Integración nativa de botones flotantes en el layout con positioning automático
- ✅ **TypeScript completo**: Tipado fuerte para todas las props del sistema de layout
- ✅ **Documentación detallada**: Guías completas de implementación y ejemplos de uso

## Componentes

Esta librería incluye los siguientes componentes:

### Button

Componente de botón personalizable que soporta diferentes tipos de interacción con estilos por defecto.

```js
import { Button } from 'udev_ultime_native';

<Button
  title="Mi Botón"
  type_button="TouchableOpacity"
  onPress={() => console.log('Presionado')}
  style_button={{ backgroundColor: 'blue', padding: 10 }}
  style_text={{ color: 'white' }}
  iconLeft={<Icon name="star" />}
  iconRight={<Icon name="arrow" />}
/>
```

**Props:**

- `title` (string): Texto del botón
- `type_button` ('TouchableOpacity' | 'Pressable' | 'TouchableHighlight', opcional): Tipo de componente de botón
- `onPress` (function, opcional): Función ejecutada al presionar
- `onLongPress` (function, opcional): Función ejecutada al presionar prolongadamente
- `onPressIn` (function, opcional): Función ejecutada al iniciar presión
- `onPressOut` (function, opcional): Función ejecutada al finalizar presión
- `onShowUnderlay` (function, opcional): Función ejecutada al mostrar underlay (TouchableHighlight)
- `onHideUnderlay` (function, opcional): Función ejecutada al ocultar underlay (TouchableHighlight)
- `onAccessibilityAction` (function, opcional): Función para acciones de accesibilidad
- `onAccessibilityEscape` (function, opcional): Función para escape de accesibilidad
- `onAccessibilityTap` (function, opcional): Función para tap de accesibilidad
- `onBlur` (function, opcional): Función ejecutada al perder foco
- `onFocus` (function, opcional): Función ejecutada al ganar foco
- `onLayout` (function, opcional): Función ejecutada al cambiar layout
- `onMagicTap` (function, opcional): Función para magic tap de accesibilidad
- `style_button` (StyleProp\<ViewStyle>, opcional): Estilos del contenedor del botón (tiene estilos por defecto)
- `style_text` (StyleProp\<TextStyle>, opcional): Estilos del texto (tiene estilos por defecto)
- `iconLeft` (JSX.Element, opcional): Icono a la izquierda del texto
- `iconRight` (JSX.Element, opcional): Icono a la derecha del texto

### InputText

Campo de texto con funcionalidades avanzadas como iconos, modo contraseña y estilos por defecto.

```js
import { InputText } from 'udev_ultime_native';

<InputText
  placeholder="Ingresa tu texto"
  value={text}
  onChangeText={setText}
  keyboardType="email-address"
  secureTextEntry={isPassword}
  iconLeft={<Icon name="user" />}
  iconPasswordShow={<Icon name="eye" />}
  iconPasswordHide={<Icon name="eye-off" />}
  setShowPassword={setShowPassword}
  ShowPassword={showPassword}
  label={<Text>Email:</Text>}
/>
```

**Props:**

- `value` (string, opcional): Valor del campo de texto
- `onChangeText` (function, opcional): Función ejecutada al cambiar el texto
- `placeholder` (string, opcional): Texto de placeholder
- `keyboardType` ('default' | 'numeric' | 'email-address' | 'phone-pad', opcional): Tipo de teclado
- `secureTextEntry` (boolean, opcional): Modo contraseña
- `editable` (boolean, opcional): Si el campo es editable
- `multiline` (boolean, opcional): Soporte para múltiples líneas
- `numberOfLines` (number, opcional): Número de líneas para el input
- `readOnly` (boolean, opcional): Campo de solo lectura
- `clearTextOnFocus` (boolean, opcional): Limpiar texto al enfocar
- `selectTextOnFocus` (boolean, opcional): Seleccionar texto al enfocar
- `showSoftInputOnFocus` (boolean, opcional): Mostrar teclado al enfocar
- `style_input` (StyleProp\<TextStyle>, opcional): Estilos del input (tiene estilos por defecto)
- `style_container` (StyleProp\<ViewStyle>, opcional): Estilos del contenedor (tiene estilos por defecto)
- `placeholderTextColor` (string, opcional): Color del placeholder (por defecto 'gray')
- `iconLeft` (JSX.Element, opcional): Icono a la izquierda
- `iconRight` (JSX.Element, opcional): Icono a la derecha
- `iconPasswordShow` (JSX.Element, opcional): Icono para mostrar contraseña
- `iconPasswordHide` (JSX.Element, opcional): Icono para ocultar contraseña
- `setShowPassword` (function, opcional): Función para controlar visibilidad de contraseña
- `ShowPassword` (boolean, opcional): Estado de visibilidad de contraseña
- `label` (JSX.Element, opcional): Etiqueta o label del campo
- `onFocus` (function, opcional): Función ejecutada al ganar foco
- `onBlur` (function, opcional): Función ejecutada al perder foco
- `onLayout` (function, opcional): Función ejecutada al cambiar layout
- `onSubmitEditing` (function, opcional): Función ejecutada al enviar
- `onKeyPress` (function, opcional): Función ejecutada al presionar tecla
- `onChange` (function, opcional): Función ejecutada al cambiar
- `onContentSizeChange` (function, opcional): Función ejecutada al cambiar tamaño del contenido
- `onEndEditing` (function, opcional): Función ejecutada al terminar edición
- `onSelectionChange` (function, opcional): Función ejecutada al cambiar selección
- `onTextInput` (function, opcional): Función ejecutada en input de texto
- `onPress` (function, opcional): Función ejecutada al presionar
- `onPressIn` (function, opcional): Función ejecutada al iniciar presión
- `onPressOut` (function, opcional): Función ejecutada al finalizar presión
- `onAccessibilityAction` (function, opcional): Función para acciones de accesibilidad
- `onAccessibilityEscape` (function, opcional): Función para escape de accesibilidad
- `onAccessibilityTap` (function, opcional): Función para tap de accesibilidad
- `onMagicTap` (function, opcional): Función para magic tap de accesibilidad

### InputPassword

Campo de entrada específico para contraseñas con funcionalidad de mostrar/ocultar y manejo interno del estado.

```js
import { InputPassword } from 'udev_ultime_native';

<InputPassword
  placeholder="Ingresa tu contraseña"
  value={password}
  onChangeText={setPassword}
  iconPasswordShow={<Icon name="eye" />}
  iconPasswordHide={<Icon name="eye-off" />}
  style_container={{ borderWidth: 1, borderColor: 'gray', padding: 10 }}
  style_input={{ fontSize: 16 }}
  placeholderTextColor="gray"
/>
```

**Props:**

- `value` (string, opcional): Valor del campo de contraseña
- `onChangeText` (function, opcional): Función ejecutada al cambiar el texto
- `placeholder` (string, opcional): Texto de placeholder
- `placeholderTextColor` (string, opcional): Color del placeholder (por defecto 'gray')
- `style_input` (StyleProp\<TextStyle>, opcional): Estilos del input (tiene estilos por defecto)
- `style_container` (StyleProp\<ViewStyle>, opcional): Estilos del contenedor (tiene estilos por defecto con flexDirection row)
- `iconPasswordShow` (JSX.Element, opcional): Icono para mostrar contraseña
- `iconPasswordHide` (JSX.Element, opcional): Icono para ocultar contraseña
- Todos los eventos de accesibilidad y interacción disponibles

**Nota:** El estado de visibilidad de contraseña (`ShowPassword`) se maneja internamente por el componente.

### InputTextarea

Campo de texto multilínea optimizado para entradas de texto extensas con soporte completo para eventos y personalización.

```js
import { InputTextarea } from 'udev_ultime_native';

<InputTextarea
  placeholder="Escribe tu mensaje aquí..."
  value={message}
  onChangeText={setMessage}
  numberOfLines={4}
  style_container={{
    borderWidth: 1,
    borderColor: 'gray',
    borderRadius: 10,
    padding: 10
  }}
  iconLeft={<Icon name="message" />}
  iconRight={<Icon name="send" />}
/>
```

**Props:**

- `value` (string, opcional): Valor del campo de texto
- `onChangeText` (function, opcional): Función ejecutada al cambiar el texto
- `placeholder` (string, opcional): Texto de placeholder
- `placeholderTextColor` (string, opcional): Color del placeholder (por defecto 'gray')
- `style_input` (StyleProp\<TextStyle>, opcional): Estilos del input (tiene estilos por defecto)
- `style_container` (StyleProp\<ViewStyle>, opcional): Estilos del contenedor (tiene estilos por defecto)
- `iconLeft` (JSX.Element, opcional): Icono a la izquierda
- `iconRight` (JSX.Element, opcional): Icono a la derecha
- `numberOfLines` (number, opcional): Número de líneas para el textarea
- Todos los eventos de interacción y accesibilidad disponibles

**Nota:** El componente está optimizado para texto multilínea con `multiline={true}` habilitado por defecto.

### DropDown

Componente de menú desplegable personalizable con opciones dinámicas y estilos configurables.

```js
import { DropDown } from 'udev_ultime_native';

<DropDown
  data_option={[
    { label: "Opción 1", value: "option1" },
    { label: "Opción 2", value: "option2" },
    { label: "Opción 3", value: "option3" }
  ]}
  placeholder="Selecciona una opción"
  setValue={setSelectedValue}
  Value={selectedValue}
  icon={<Icon name="chevron-down" />}
/>
```

**Props:**

- `style_container` (StyleProp\<ViewStyle>, opcional): Estilos del contenedor principal (tiene estilos por defecto)
- `style_container_option` (StyleProp\<ViewStyle>, opcional): Estilos del contenedor de opciones
- `style_button_option` (StyleProp\<ViewStyle>, opcional): Estilos de cada botón de opción
- `style_text_option` (StyleProp\<TextStyle>, opcional): Estilos del texto de opciones
- `style_text_placeholder` (StyleProp\<TextStyle>, opcional): Estilos del texto placeholder
- `style_text_selected` (StyleProp\<TextStyle>, opcional): Estilos del texto de la opción seleccionada
- `style_buttonOpen_option` (StyleProp\<ViewStyle>, opcional): Estilos del botón para abrir opciones
- `setValue` (function, opcional): Función para establecer el valor seleccionado
- `Value` (string | number | undefined, opcional): Valor actualmente seleccionado
- `data_option` (array, opcional): Array de objetos con `label` y `value` para las opciones
- `placeholder` (string, opcional): Texto mostrado cuando no hay selección
- `icon` (JSX.Element, opcional): Icono mostrado junto al texto del botón

### ProgressBar

Barra de progreso altamente personalizable con soporte para iconos, porcentajes y estados coloreados.

```js
import { ProgressBar } from 'udev_ultime_native';

<ProgressBar
  progress={75}
  show_percentage={true}
  bg_color_progress="blue"
  bg_container_bar="#f0f0f0"
  height_bar={20}
  status_bar={[
    { color: '#ff4444', status: 'Bajo', progress: 25 },
    { color: '#ffaa00', status: 'Medio', progress: 50 },
    { color: '#44ff44', status: 'Alto', progress: 75 },
    { color: '#0088ff', status: 'Completo', progress: 100 }
  ]}
  iconLeft={<Icon name="star" />}
  iconRight={<Icon name="check" />}
/>
```

**Props:**

- `progress` (number, requerido): Porcentaje de progreso (0-100)
- `height_bar` (number, opcional): Altura de la barra (por defecto 30)
- `bg_color_progress` (string, opcional): Color de la barra de progreso
- `bg_container_bar` (string, opcional): Color del contenedor de la barra (por defecto '#f8f9fa')
- `style_container` (StyleProp\<ViewStyle>, opcional): Estilos del contenedor principal
- `style_progress_bar` (StyleProp\<ViewStyle>, opcional): Estilos de la barra de progreso
- `show_percentage` (boolean, opcional): Mostrar el porcentaje como texto
- `text_style_percentage` (StyleProp\<TextStyle>, opcional): Estilos del texto de porcentaje
- `text_percentage` (JSX.Element, opcional): Elemento personalizado para mostrar el porcentaje
- `iconRight` (JSX.Element, opcional): Icono a la derecha del porcentaje
- `iconLeft` (JSX.Element, opcional): Icono a la izquierda del porcentaje
- `status_bar` (array, opcional): Array de objetos con `color`, `status` y `progress` para estados coloreados

### Card_Simple

Tarjeta simple y elegante con imagen, título, descripción y botón personalizable.

```js
import { Card_Simple } from 'udev_ultime_native';

<Card_Simple
  title="Mi Tarjeta"
  description="Esta es una descripción de ejemplo para la tarjeta"
  imageUri="https://ejemplo.com/imagen.jpg"
  text_button="Ver más"
  style_container={{ margin: 10 }}
/>
```

**Props:**

- `title` (string, opcional): Título de la tarjeta (por defecto 'Title Simple')
- `description` (string, opcional): Descripción de la tarjeta (tiene texto por defecto)
- `imageUri` (string, opcional): URL de la imagen (tiene imagen por defecto)
- `text_button` (string, opcional): Texto del botón (por defecto 'Click Me')
- `style_title` (StyleProp\<TextStyle>, opcional): Estilos del título
- `style_description` (StyleProp\<TextStyle>, opcional): Estilos de la descripción
- `style_container` (StyleProp\<ViewStyle>, opcional): Estilos del contenedor principal (tiene estilos por defecto)
- `style_image` (StyleProp\<ImageStyle>, opcional): Estilos de la imagen
- `style_button` (StyleProp\<ViewStyle>, opcional): Estilos del botón
- `style_text_button` (StyleProp\<TextStyle>, opcional): Estilos del texto del botón
- `style_container_button` (StyleProp\<ViewStyle>, opcional): Estilos del contenedor del botón
- `Button` (JSX.Element, opcional): Botón personalizado para reemplazar el por defecto

**Nota:** La tarjeta tiene un diseño responsivo con ancho fijo de 300px y sombra por defecto. El título se trunca automáticamente después de 25 caracteres.

### FloatingButton

Botón flotante con opciones expandibles y animaciones suaves usando react-native-reanimated.

```js
import { FloatingButton } from 'udev_ultime_native';

<FloatingButton
  icon_hide={<Icon name="plus" />}
  icon_show={<Icon name="close" />}
  Data_Button={[
    {
      icon: <Icon name="home" />,
      onPress: () => console.log('Home pressed'),
      style_button: { backgroundColor: 'blue' }
    },
    {
      icon: <Icon name="settings" />,
      onPress: () => console.log('Settings pressed'),
      style_button: { backgroundColor: 'green' }
    }
  ]}
  SelectFun_onPress="Data_Button"
  SelectFun_onLongPress="onLongPress"
  timing_animation_buttons={400}
/>
```

**Props:**

- `icon_hide` (ReactNode, requerido): Icono mostrado cuando el menú está cerrado
- `icon_show` (ReactNode, opcional): Icono mostrado cuando el menú está abierto
- `Data_Button` (array, opcional): Array de objetos con `icon`, `onPress`, `style_button` y `onLongPress` para las opciones
- `timing_animation_buttons` (number, opcional): Duración de las animaciones en milisegundos (por defecto 500ms para mostrar, 300ms para ocultar)
- `style_floating_button` (StyleProp\<ViewStyle>, opcional): Estilos del botón principal (tiene estilos por defecto)
- `style_container_button` (StyleProp\<ViewStyle>, opcional): Estilos del contenedor de opciones
- `style_main_container` (StyleProp\<ViewStyle>, opcional): Estilos del contenedor principal
- `onPress` (function, opcional): Función ejecutada al presionar el botón principal
- `onLongPress` (function, opcional): Función ejecutada al presionar prolongadamente el botón principal
- `SelectFun_onPress` ('onPress' | 'Data_Button', requerido): Selecciona qué función ejecutar al presionar (función personalizada o mostrar/ocultar opciones)
- `SelectFun_onLongPress` ('onLongPress' | 'Data_Button', requerido): Selecciona qué función ejecutar al presionar prolongadamente

**Nota:** El componente utiliza `react-native-reanimated` para animaciones suaves de opacidad y escala. Las opciones aparecen con animación desde el botón principal hacia arriba.

### RadioButton

Componente de botón de opción para selección única con diseño personalizable y manejo de estado externo.

```js
import { RadioButton } from 'udev_ultime_native';

<RadioButton
  value="option1"
  value_selected={selectedValue}
  label="Primera opción"
  setValue={setSelectedValue}
/>
```

**Props:**

- `value` (string, opcional): Valor único del botón de opción
- `value_selected` (string | undefined, requerido): Valor actualmente seleccionado
- `label` (string, opcional): Texto de la etiqueta del botón
- `setValue` (Dispatch<SetStateAction<string | undefined>>, requerido): Función para actualizar el valor seleccionado
- `style_container` (object, opcional): Estilos del contenedor principal (con flexDirection row por defecto)
- `style_label` (object, opcional): Estilos del texto de la etiqueta
- `style_radio` (object, opcional): Estilos del círculo del botón (20x20px por defecto)
- `style_point_radio` (object, opcional): Estilos del punto interior cuando está seleccionado (10x10px por defecto)

**Nota:** El componente requiere manejo de estado externo para el valor seleccionado. El diseño incluye un círculo con borde y un punto interior que aparece cuando está seleccionado.

### ButtonBar

Barra de botones que permite elegir entre diferentes tipos de componentes táctiles con estilos unificados.

```js
import { ButtonBar } from 'udev_ultime_native';

<ButtonBar
  type_button="TouchableOpacity"
  text="Mi Botón Personalizado"
  onPress={() => console.log('Pressed')}
  style_button={{ backgroundColor: '#007bff' }}
/>
```

**Props:**

- `type_button` ('Pressable' | 'Button' | 'TouchableOpacity' | 'TouchableHighlight', requerido): Tipo de botón a renderizar
- `onPress` (function, opcional): Función ejecutada al presionar el botón
- `onLongPress` (function, opcional): Función ejecutada al presionar prolongadamente
- `style_button` (StyleProp<ViewStyle>, opcional): Estilos del contenedor del botón (con flex: 1 por defecto)
- `style_text` (StyleProp<ViewStyle>, opcional): Estilos del texto del botón
- `text` (string | any, opcional): Texto personalizado a mostrar en el botón

**Tipos disponibles:**

- **Pressable**: Botón moderno con texto personalizable (si no se proporciona `text`, muestra "Pressable")
- **Button**: Botón nativo de React Native con título personalizable (si no se proporciona `text`, muestra "Button")
- **TouchableOpacity**: Botón con efecto de opacidad y texto personalizable (si no se proporciona `text`, muestra "TouchableOpacity")
- **TouchableHighlight**: Botón con efecto de resaltado y texto personalizable (si no se proporciona `text`, muestra "TouchableHighlight")

**Nota:** El contenedor tiene `flexDirection: 'row'` y `justifyContent: 'space-between'` por defecto. Cada botón ocupa el espacio disponible con `flex: 1`. La propiedad `text` permite personalizar el contenido mostrado en cada tipo de botón.

### TabPanel

Sistema de pestañas horizontal con navegación por scroll y contenido dinámico basado en la pestaña seleccionada.

```js
import { TabPanel } from 'udev_ultime_native';

<TabPanel
  Data_Tabs={[
    {
      label: "Inicio",
      description: "Contenido de la pestaña Inicio",
      value: "home"
    },
    {
      label: "Perfil", 
      description: "Información del perfil de usuario",
      value: "profile"
    }
  ]}
  border_tab_selected="#007bff"
/>
```

**Props:**

- `Data_Tabs` (array, opcional): Array de objetos con configuración de pestañas
  - `label` (string, requerido): Texto mostrado en la pestaña
  - `description` (string | undefined, opcional): Contenido mostrado al seleccionar la pestaña
  - `value` (string, requerido): Identificador único de la pestaña
  - `style_description` (StyleProp<TextStyle>, opcional): Estilos específicos para la descripción de esta pestaña
- `style_container` (object, opcional): Estilos del contenedor principal (con borde y padding por defecto)
- `style_tab_container` (object, opcional): Estilos del contenedor de pestañas (con borde inferior por defecto)
- `style_text_tab` (object, opcional): Estilos del texto de las pestañas
- `style_description` (object, opcional): Estilos globales de la descripción
- `border_tab_selected` (string, opcional): Color del borde y texto de la pestaña seleccionada (por defecto '#000000')
- `border_tab_unselected` (string, opcional): Color del borde y texto de pestañas no seleccionadas (por defecto '#ffffff' y 'gray')

**Características:**
- Navegación horizontal con scroll automático
- Selección automática de la primera pestaña al cargar
- Indicador visual con borde inferior en la pestaña activa
- Contenido dinámico que cambia según la pestaña seleccionada
- Soporte para scroll horizontal cuando hay muchas pestañas

**Nota:** El componente maneja internamente el estado de la pestaña seleccionada y actualiza automáticamente el contenido mostrado. El diseño es responsivo con scroll horizontal para pestañas que excedan el ancho de la pantalla.

### LayoutScreen

Sistema de layout completo para estructurar pantallas con topBar, bottomBar y bodyScreen personalizables.

```js
import { LayoutScreen } from 'udev_ultime_native';

<LayoutScreen
  type_Body="ScrollView"
  topBar={
    <View style={{ backgroundColor: 'black', padding: 20 }}>
      <Text style={{ textAlign: 'center', color: 'white' }}>Top Bar</Text>
    </View>
  }
  type_BottomBar="Bar_Floating"
  Data_BottomBar={[
    {
      label: "Home",
      onPress: () => console.log("Home Pressed"),
      icon_in: <Icon name="home" />,
      icon_out: <Icon name="home-outline" />,
      isInScreen: true,
    },
    {
      label: "Settings",
      onPress: () => console.log("Settings Pressed"),
      icon_in: <Icon name="settings" />,
      icon_out: <Icon name="settings-outline" />,
      isInScreen: false,
    }
  ]}
  floating_button={
    <TouchableOpacity style={{ /* estilos */ }}>
      <Text>+</Text>
    </TouchableOpacity>
  }
  bodyScreen={
    <View>
      {/* Contenido de la pantalla */}
    </View>
  }
/>
```

**Props:**

- `topBar` (ReactNode, opcional): Componente personalizado para la barra superior
- `bottomBar` (ReactNode, opcional): Componente personalizado para la barra inferior
- `type_BottomBar` ('Default' | 'Bar_Floating' | 'BarWithFloatingButton', opcional): Tipo de barra inferior predefinida
- `style_bottomBar` (StyleProp\<ViewStyle>, opcional): Estilos personalizados para la barra inferior
- `bodyScreen` (ReactNode, requerido): Contenido principal de la pantalla
- `type_Body` ('ScrollView' | 'View', opcional): Tipo de contenedor para el cuerpo de la pantalla
- `Data_BottomBar` (array, opcional): Array de objetos para configurar los botones de la barra inferior
- `floating_button` (ReactNode, opcional): Botón flotante personalizado (usado con 'BarWithFloatingButton')
- `style_container_floating_button` (StyleProp\<ViewStyle>, opcional): Estilos del contenedor del botón flotante

**Estructura de Data_BottomBar:**

- `label` (string, opcional): Texto del botón
- `onPress` (function, requerido): Función ejecutada al presionar
- `icon_in` (ReactNode, requerido): Icono cuando está activo/en pantalla
- `icon_out` (ReactNode, opcional): Icono cuando está inactivo
- `isInScreen` (boolean, opcional): Indica si es la pantalla actual (para mostrar icon_in o icon_out)
- `style_text` (StyleProp\<TextStyle>, opcional): Estilos del texto del botón
- `style_button` (StyleProp\<ViewStyle>, opcional): Estilos del contenedor del botón
- `onLongPress` (function, opcional): Función ejecutada al presionar prolongadamente

**Tipos de BottomBar:**

- `Default`: Barra inferior estándar con botones distribuidos uniformemente
- `Bar_Floating`: Barra flotante centrada con bordes redondeados
- `BarWithFloatingButton`: Barra estándar con un botón flotante posicionado arriba

**Nota:** El componente utiliza `SafeAreaProvider` de `react-native-safe-area-context` para manejar áreas seguras en dispositivos con notch o barras de estado.

## Instalación de Dependencias

```sh
npm install udev_ultime_native react-native-reanimated react-native-safe-area-context
```

**Importante:**

- Para usar `FloatingButton`, es necesario instalar y configurar `react-native-reanimated` siguiendo la [documentación oficial](https://docs.swmansion.com/react-native-reanimated/docs/fundamentals/installation).
- Para usar `LayoutScreen`, es necesario instalar `react-native-safe-area-context` siguiendo la [documentación oficial](https://github.com/th3rdwave/react-native-safe-area-context).

## Uso

```js
import {
  Button,
  InputText,
  InputPassword,
  InputTextarea,
  DropDown,
  ProgressBar,
  Card_Simple,
  FloatingButton,
  LayoutScreen
} from 'udev_ultime_native';

// Usar cualquiera de los componentes en tu aplicación
<Button title="Mi Botón" onPress={() => console.log('Presionado')} />
<InputText placeholder="Escribe aquí..." />
<FloatingButton 
  icon_hide={<YourIcon />}
  Data_Button={[...]}
  SelectFun_onPress="Data_Button"
  SelectFun_onLongPress="onLongPress"
/>
```

## Ejemplo de uso completo

```js
import React, { useState } from 'react';
import { View, Text } from 'react-native';
import { 
  Button, 
  InputText, 
  InputPassword, 
  InputTextarea, 
  DropDown, 
  ProgressBar,
  Card_Simple,
  FloatingButton
} from 'udev_ultime_native';

export default function App() {
  const [text, setText] = useState('');
  const [password, setPassword] = useState('');
  const [message, setMessage] = useState('');
  const [selectedValue, setSelectedValue] = useState('');
  const [progress, setProgress] = useState(65);

  const options = [
    { label: 'Opción 1', value: 'option1' },
    { label: 'Opción 2', value: 'option2' },
    { label: 'Opción 3', value: 'option3' },
  ];

  const floatingOptions = [
    {
      icon: <Text>🏠</Text>,
      onPress: () => console.log('Home pressed'),
      style_button: { backgroundColor: 'blue' }
    },
    {
      icon: <Text>⚙️</Text>,
      onPress: () => console.log('Settings pressed'),
      style_button: { backgroundColor: 'green' }
    }
  ];

  return (
    <View style={{ padding: 20, flex: 1 }}>
      <InputText
        placeholder="Ingresa tu nombre"
        value={text}
        onChangeText={setText}
        style_container={{ marginBottom: 10 }}
      />
      
      <InputPassword
        placeholder="Ingresa tu contraseña"
        value={password}
        onChangeText={setPassword}
        style_container={{ marginBottom: 10 }}
      />
      
      <InputTextarea
        placeholder="Escribe tu mensaje..."
        value={message}
        onChangeText={setMessage}
        style_container={{ marginBottom: 10 }}
        numberOfLines={3}
      />
      
      <DropDown
        placeholder="Selecciona una opción"
        data_option={options}
        Value={selectedValue}
        setValue={setSelectedValue}
        style_container={{ marginBottom: 10 }}
      />
      
      <ProgressBar
        progress={progress}
        height_bar={35}
        show_percentage={true}
        style_container={{ marginBottom: 10 }}
      />

      <Card_Simple
        title="Tarjeta de Ejemplo"
        description="Esta es una tarjeta simple con todos los elementos"
        text_button="Ver Detalles"
        style_container={{ marginBottom: 20, alignSelf: 'center' }}
      />
      
      <Button
        title="Enviar"
        type_button="TouchableOpacity"
        onPress={() => console.log('Datos enviados')}
        style_button={{ backgroundColor: 'blue', padding: 15, borderRadius: 5 }}
        style_text={{ color: 'white', textAlign: 'center' }}
      />

      <FloatingButton
        icon_hide={<Text>+</Text>}
        icon_show={<Text>×</Text>}
        Data_Button={floatingOptions}
        SelectFun_onPress="Data_Button"
        SelectFun_onLongPress="onLongPress"
        style_main_container={{ position: 'absolute', bottom: 20, right: 20 }}
      />
    </View>
  );
}
```

## Contributing

- [Development workflow](udev_ultime_native/CONTRIBUTING.md#development-workflow)
- [Sending a pull request](udev_ultime_native/CONTRIBUTING.md#sending-a-pull-request)
- [Code of conduct](udev_ultime_native/CODE_OF_CONDUCT.md)

## License

Apache 2.0 - Consulta el archivo [LICENSE](./LICENSE) para más detalles.

---

Made with ❤️ by [UrpirioDev](https://github.com/Urpirio)
