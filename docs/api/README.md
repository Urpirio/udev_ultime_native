# Referencia de API - udev_ultime_native

Esta es la referencia completa de todos los componentes disponibles en la librería udev_ultime_native.

## Índice de Componentes

### Componentes de Entrada
- [InputText](#inputtext) - Campo de texto general
- [InputPassword](#inputpassword) - Campo de contraseña
- [InputTextarea](#inputtextarea) - Área de texto multilínea
- [DropDown](#dropdown) - Menú desplegable

### Componentes de Acción
- [Button](#button) - Botón personalizable
- [ButtonBar](#buttonbar) - Barra de botones
- [FloatingButton](#floatingbutton) - Botón flotante con menú

### Componentes de Selección
- [RadioButton](#radiobutton) - Botón de opción única

### Componentes de Visualización
- [ProgressBar](#progressbar) - Barra de progreso
- [Card_Simple](#card_simple) - Tarjeta simple
- [TabPanel](#tabpanel) - Panel de pestañas

### Componentes de Layout
- [LayoutScreen](#layoutscreen) - Sistema de layout completo

---

## InputText

Campo de texto con funcionalidades avanzadas como iconos, modo contraseña y estilos personalizables.

### Props

| Prop | Tipo | Requerido | Descripción |
|------|------|-----------|-------------|
| `value` | `string` | No | Valor del campo de texto |
| `onChangeText` | `(text: string) => void` | No | Función ejecutada al cambiar el texto |
| `placeholder` | `string` | No | Texto de placeholder |
| `keyboardType` | `'default' \| 'numeric' \| 'email-address' \| 'phone-pad'` | No | Tipo de teclado |
| `secureTextEntry` | `boolean` | No | Modo contraseña |
| `editable` | `boolean` | No | Si el campo es editable |
| `multiline` | `boolean` | No | Soporte para múltiples líneas |
| `numberOfLines` | `number` | No | Número de líneas para el input |
| `style_input` | `StyleProp<TextStyle>` | No | Estilos del input |
| `style_container` | `StyleProp<ViewStyle>` | No | Estilos del contenedor |
| `placeholderTextColor` | `string` | No | Color del placeholder (default: 'gray') |
| `iconLeft` | `JSX.Element` | No | Icono a la izquierda |
| `iconRight` | `JSX.Element` | No | Icono a la derecha |
| `iconPasswordShow` | `JSX.Element` | No | Icono para mostrar contraseña |
| `iconPasswordHide` | `JSX.Element` | No | Icono para ocultar contraseña |
| `setShowPassword` | `(show: boolean) => void` | No | Función para controlar visibilidad de contraseña |
| `ShowPassword` | `boolean` | No | Estado de visibilidad de contraseña |
| `label` | `JSX.Element` | No | Etiqueta o label del campo |
| `onFocus` | `() => void` | No | Ejecutado al ganar foco |
| `onBlur` | `() => void` | No | Ejecutado al perder foco |

### Ejemplo

```javascript
import { InputText } from 'udev_ultime_native';
import Icon from 'react-native-vector-icons/Ionicons';

<InputText
  placeholder="Ingresa tu email"
  value={email}
  onChangeText={setEmail}
  keyboardType="email-address"
  iconLeft={<Icon name="mail" size={20} color="gray" />}
  style_container={{
    borderWidth: 1,
    borderColor: '#ddd',
    borderRadius: 8,
    padding: 10,
  }}
/>
```

---

## InputPassword

Campo de entrada específico para contraseñas con funcionalidad de mostrar/ocultar contraseña y manejo interno del estado.

### Props

| Prop | Tipo | Requerido | Descripción |
|------|------|-----------|-------------|
| `value` | `string` | No | Valor del campo de contraseña |
| `onChangeText` | `(text: string) => void` | No | Función ejecutada al cambiar el texto |
| `placeholder` | `string` | No | Texto de placeholder |
| `placeholderTextColor` | `string` | No | Color del placeholder (default: 'gray') |
| `style_input` | `StyleProp<TextStyle>` | No | Estilos del input |
| `style_container` | `StyleProp<ViewStyle>` | No | Estilos del contenedor |
| `iconPasswordShow` | `JSX.Element` | No | Icono para mostrar contraseña |
| `iconPasswordHide` | `JSX.Element` | No | Icono para ocultar contraseña |

### Características

- **Manejo interno de estado**: El componente maneja automáticamente el estado de visibilidad
- **Toggle de visibilidad**: Toca el icono para mostrar/ocultar la contraseña
- **Estilos por defecto**: Incluye estilos flexDirection row

### Ejemplo

```javascript
import { InputPassword } from 'udev_ultime_native';
import Icon from 'react-native-vector-icons/Ionicons';

<InputPassword
  placeholder="Contraseña"
  value={password}
  onChangeText={setPassword}
  iconPasswordShow={<Icon name="eye" size={20} />}
  iconPasswordHide={<Icon name="eye-off" size={20} />}
  style_container={{
    borderWidth: 1,
    borderColor: '#ddd',
    borderRadius: 8,
    padding: 10,
  }}
/>
```

---

## InputTextarea

Campo de texto multilínea optimizado para entradas de texto extensas.

### Props

| Prop | Tipo | Requerido | Descripción |
|------|------|-----------|-------------|
| `value` | `string` | No | Valor del campo de texto |
| `onChangeText` | `(text: string) => void` | No | Función ejecutada al cambiar el texto |
| `placeholder` | `string` | No | Texto de placeholder |
| `placeholderTextColor` | `string` | No | Color del placeholder (default: 'gray') |
| `style_input` | `StyleProp<TextStyle>` | No | Estilos del input |
| `style_container` | `StyleProp<ViewStyle>` | No | Estilos del contenedor |
| `iconLeft` | `JSX.Element` | No | Icono a la izquierda |
| `iconRight` | `JSX.Element` | No | Icono a la derecha |
| `numberOfLines` | `number` | No | Número de líneas para el textarea |

### Características

- **Multiline habilitado**: Optimizado para texto multilínea
- **Altura dinámica**: Se ajusta al contenido
- **Soporte para iconos**: Iconos decorativos izquierda/derecha

### Ejemplo

```javascript
import { InputTextarea } from 'udev_ultime_native';

<InputTextarea
  placeholder="Escribe tu mensaje aquí..."
  value={message}
  onChangeText={setMessage}
  numberOfLines={4}
  style_container={{
    borderWidth: 1,
    borderColor: '#ddd',
    borderRadius: 8,
    padding: 10,
    minHeight: 100,
  }}
/>
```

---

## DropDown

Componente de menú desplegable personalizable con opciones dinámicas.

### Props

| Prop | Tipo | Requerido | Descripción |
|------|------|-----------|-------------|
| `style_container` | `StyleProp<ViewStyle>` | No | Estilos del contenedor principal |
| `style_container_option` | `StyleProp<ViewStyle>` | No | Estilos del contenedor de opciones |
| `style_button_option` | `StyleProp<ViewStyle>` | No | Estilos de cada botón de opción |
| `style_text_option` | `StyleProp<TextStyle>` | No | Estilos del texto de opciones |
| `style_text_placeholder` | `StyleProp<TextStyle>` | No | Estilos del texto placeholder |
| `style_text_selected` | `StyleProp<TextStyle>` | No | Estilos del texto de opción seleccionada |
| `style_buttonOpen_option` | `StyleProp<ViewStyle>` | No | Estilos del botón para abrir opciones |
| `setValue` | `(value: string \| number) => void` | No | Función para establecer valor seleccionado |
| `Value` | `string \| number \| undefined` | No | Valor actualmente seleccionado |
| `data_option` | `Array<{label: string, value: string \| number}>` | No | Array de opciones |
| `placeholder` | `string` | No | Texto mostrado cuando no hay selección |
| `icon` | `JSX.Element` | No | Icono junto al texto del botón |

### Ejemplo

```javascript
import { DropDown } from 'udev_ultime_native';

const countries = [
  { label: 'Argentina', value: 'ar' },
  { label: 'Chile', value: 'cl' },
  { label: 'Colombia', value: 'co' },
];

<DropDown
  data_option={countries}
  placeholder="Selecciona un país"
  Value={selectedCountry}
  setValue={setSelectedCountry}
  style_container={{
    borderWidth: 1,
    borderColor: '#ddd',
    borderRadius: 8,
  }}
/>
```

---

## Button

Componente de botón personalizable que soporta diferentes tipos de interacción.

### Props

| Prop | Tipo | Requerido | Descripción |
|------|------|-----------|-------------|
| `title` | `string` | Sí | Texto del botón |
| `type_button` | `'TouchableOpacity' \| 'Pressable' \| 'TouchableHighlight'` | No | Tipo de componente de botón |
| `onPress` | `() => void` | No | Ejecutado al presionar |
| `onLongPress` | `() => void` | No | Ejecutado al presionar prolongadamente |
| `style_button` | `StyleProp<ViewStyle>` | No | Estilos del contenedor del botón |
| `style_text` | `StyleProp<TextStyle>` | No | Estilos del texto |
| `iconLeft` | `JSX.Element` | No | Icono a la izquierda del texto |
| `iconRight` | `JSX.Element` | No | Icono a la derecha del texto |

### Tipos de Botón

- **TouchableOpacity**: Reduce opacidad al presionar (default)
- **Pressable**: Botón moderno con mejor control de estados
- **TouchableHighlight**: Muestra un color de resaltado al presionar

### Ejemplo

```javascript
import { Button } from 'udev_ultime_native';
import Icon from 'react-native-vector-icons/Ionicons';

<Button
  title="Enviar"
  type_button="TouchableOpacity"
  onPress={() => console.log('Pressed')}
  iconLeft={<Icon name="send" size={18} color="white" />}
  style_button={{
    backgroundColor: '#007AFF',
    padding: 15,
    borderRadius: 8,
  }}
  style_text={{
    color: 'white',
    fontSize: 16,
    fontWeight: 'bold',
  }}
/>
```

---

## ButtonBar

Barra de botones que permite elegir entre diferentes tipos de componentes táctiles.

### Props

| Prop | Tipo | Requerido | Descripción |
|------|------|-----------|-------------|
| `type_button` | `'Pressable' \| 'Button' \| 'TouchableOpacity' \| 'TouchableHighlight'` | Sí | Tipo de botón a renderizar |
| `onPress` | `() => void` | No | Ejecutado al presionar el botón |
| `onLongPress` | `() => void` | No | Ejecutado al presionar prolongadamente |
| `style_button` | `StyleProp<ViewStyle>` | No | Estilos del contenedor del botón |
| `style_text` | `StyleProp<ViewStyle>` | No | Estilos del texto del botón |
| `text` | `string \| any` | No | Texto personalizado a mostrar |

### Ejemplo

```javascript
import { ButtonBar } from 'udev_ultime_native';

<ButtonBar
  type_button="TouchableOpacity"
  text="Mi Botón"
  onPress={() => console.log('Pressed')}
  style_button={{
    backgroundColor: '#007bff',
    padding: 10,
    borderRadius: 5,
  }}
/>
```

---

## FloatingButton

Botón flotante con opciones expandibles y animaciones suaves.

### Props

| Prop | Tipo | Requerido | Descripción |
|------|------|-----------|-------------|
| `icon_hide` | `ReactNode` | Sí | Icono cuando el menú está cerrado |
| `icon_show` | `ReactNode` | No | Icono cuando el menú está abierto |
| `Data_Button` | `Array<ButtonOption>` | No | Array de opciones del menú |
| `timing_animation_buttons` | `number` | No | Duración de animaciones en ms |
| `style_floating_button` | `StyleProp<ViewStyle>` | No | Estilos del botón principal |
| `style_container_button` | `StyleProp<ViewStyle>` | No | Estilos del contenedor de opciones |
| `style_main_container` | `StyleProp<ViewStyle>` | No | Estilos del contenedor principal |
| `onPress` | `() => void` | No | Función al presionar el botón principal |
| `onLongPress` | `() => void` | No | Función al presionar prolongadamente |
| `SelectFun_onPress` | `'onPress' \| 'Data_Button'` | Sí | Selecciona función para onPress |
| `SelectFun_onLongPress` | `'onLongPress' \| 'Data_Button'` | Sí | Selecciona función para onLongPress |

### ButtonOption Type

```typescript
interface ButtonOption {
  icon: ReactNode;
  onPress: () => void;
  style_button?: StyleProp<ViewStyle>;
  onLongPress?: () => void;
}
```

### Ejemplo

```javascript
import { FloatingButton } from 'udev_ultime_native';
import Icon from 'react-native-vector-icons/Ionicons';

<FloatingButton
  icon_hide={<Icon name="add" size={24} color="white" />}
  icon_show={<Icon name="close" size={24} color="white" />}
  Data_Button={[
    {
      icon: <Icon name="home" size={20} color="white" />,
      onPress: () => console.log('Home'),
      style_button: { backgroundColor: 'blue' },
    },
    {
      icon: <Icon name="settings" size={20} color="white" />,
      onPress: () => console.log('Settings'),
      style_button: { backgroundColor: 'green' },
    },
  ]}
  SelectFun_onPress="Data_Button"
  SelectFun_onLongPress="onLongPress"
  style_main_container={{
    position: 'absolute',
    bottom: 20,
    right: 20,
  }}
/>
```

---

## RadioButton

Componente de botón de opción para selección única.

### Props

| Prop | Tipo | Requerido | Descripción |
|------|------|-----------|-------------|
| `value` | `string` | No | Valor único del botón de opción |
| `value_selected` | `string \| undefined` | Sí | Valor actualmente seleccionado |
| `label` | `string` | No | Texto de la etiqueta |
| `setValue` | `Dispatch<SetStateAction<string \| undefined>>` | Sí | Función para actualizar el valor |
| `style_container` | `object` | No | Estilos del contenedor principal |
| `style_label` | `object` | No | Estilos del texto de la etiqueta |
| `style_radio` | `object` | No | Estilos del círculo del botón |
| `style_point_radio` | `object` | No | Estilos del punto interior seleccionado |

### Ejemplo

```javascript
import { RadioButton } from 'udev_ultime_native';
import { useState } from 'react';

const [gender, setGender] = useState('');

<View>
  <RadioButton
    value="male"
    value_selected={gender}
    setValue={setGender}
    label="Masculino"
  />
  <RadioButton
    value="female"
    value_selected={gender}
    setValue={setGender}
    label="Femenino"
  />
</View>
```

---

## ProgressBar

Barra de progreso altamente personalizable con soporte para iconos y porcentajes.

### Props

| Prop | Tipo | Requerido | Descripción |
|------|------|-----------|-------------|
| `progress` | `number` | Sí | Porcentaje de progreso (0-100) |
| `height_bar` | `number` | No | Altura de la barra (default: 30) |
| `bg_color_progress` | `string` | No | Color de la barra de progreso |
| `bg_container_bar` | `string` | No | Color del contenedor (default: '#f8f9fa') |
| `style_container` | `StyleProp<ViewStyle>` | No | Estilos del contenedor principal |
| `style_progress_bar` | `StyleProp<ViewStyle>` | No | Estilos de la barra de progreso |
| `show_percentage` | `boolean` | No | Mostrar el porcentaje como texto |
| `text_style_percentage` | `StyleProp<TextStyle>` | No | Estilos del texto de porcentaje |
| `text_percentage` | `JSX.Element` | No | Elemento personalizado para porcentaje |
| `iconRight` | `JSX.Element` | No | Icono a la derecha del porcentaje |
| `iconLeft` | `JSX.Element` | No | Icono a la izquierda del porcentaje |
| `status_bar` | `Array<StatusBar>` | No | Array de estados coloreados |

### StatusBar Type

```typescript
interface StatusBar {
  color: string;
  status: string;
  progress: number;
}
```

### Ejemplo

```javascript
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
    { color: '#0088ff', status: 'Completo', progress: 100 },
  ]}
/>
```

---

## Card_Simple

Tarjeta simple y elegante con imagen, título, descripción y botón.

### Props

| Prop | Tipo | Requerido | Descripción |
|------|------|-----------|-------------|
| `title` | `string` | No | Título de la tarjeta (default: 'Title Simple') |
| `description` | `string` | No | Descripción de la tarjeta |
| `imageUri` | `string` | No | URL de la imagen |
| `text_button` | `string` | No | Texto del botón (default: 'Click Me') |
| `style_title` | `StyleProp<TextStyle>` | No | Estilos del título |
| `style_description` | `StyleProp<TextStyle>` | No | Estilos de la descripción |
| `style_container` | `StyleProp<ViewStyle>` | No | Estilos del contenedor principal |
| `style_image` | `StyleProp<ImageStyle>` | No | Estilos de la imagen |
| `style_button` | `StyleProp<ViewStyle>` | No | Estilos del botón |
| `style_text_button` | `StyleProp<TextStyle>` | No | Estilos del texto del botón |
| `style_container_button` | `StyleProp<ViewStyle>` | No | Estilos del contenedor del botón |
| `Button` | `JSX.Element` | No | Botón personalizado |

### Ejemplo

```javascript
import { Card_Simple } from 'udev_ultime_native';

<Card_Simple
  title="Mi Tarjeta"
  description="Esta es una descripción de ejemplo"
  imageUri="https://example.com/image.jpg"
  text_button="Ver más"
  style_container={{
    margin: 10,
    shadowColor: '#000',
    shadowOffset: { width: 0, height: 2 },
    shadowOpacity: 0.25,
    shadowRadius: 3.84,
    elevation: 5,
  }}
/>
```

---

## TabPanel

Sistema de pestañas horizontal con navegación por scroll y contenido dinámico.

### Props

| Prop | Tipo | Requerido | Descripción |
|------|------|-----------|-------------|
| `Data_Tabs` | `Array<TabData>` | No | Array de configuración de pestañas |
| `style_container` | `object` | No | Estilos del contenedor principal |
| `style_tab_container` | `object` | No | Estilos del contenedor de pestañas |
| `style_text_tab` | `object` | No | Estilos del texto de las pestañas |
| `style_description` | `object` | No | Estilos globales de la descripción |
| `border_tab_selected` | `string` | No | Color del borde de pestaña seleccionada |
| `border_tab_unselected` | `string` | No | Color del borde de pestañas no seleccionadas |

### TabData Type

```typescript
interface TabData {
  label: string;
  description?: string | undefined;
  value: string;
  style_description?: StyleProp<TextStyle>;
}
```

### Ejemplo

```javascript
import { TabPanel } from 'udev_ultime_native';

<TabPanel
  Data_Tabs={[
    {
      label: "Inicio",
      description: "Contenido de la pestaña Inicio",
      value: "home",
    },
    {
      label: "Perfil",
      description: "Información del perfil de usuario",
      value: "profile",
    },
    {
      label: "Configuración",
      description: "Ajustes de la aplicación",
      value: "settings",
    },
  ]}
  border_tab_selected="#007bff"
  border_tab_unselected="#dddddd"
/>
```

---

## LayoutScreen

Sistema de layout completo para estructurar pantallas con topBar, bottomBar y bodyScreen.

### Props

| Prop | Tipo | Requerido | Descripción |
|------|------|-----------|-------------|
| `topBar` | `ReactNode` | No | Componente personalizado para barra superior |
| `bottomBar` | `ReactNode` | No | Componente personalizado para barra inferior |
| `type_BottomBar` | `'Default' \| 'Bar_Floating' \| 'BarWithFloatingButton'` | No | Tipo de barra inferior predefinida |
| `style_bottomBar` | `StyleProp<ViewStyle>` | No | Estilos personalizados para barra inferior |
| `bodyScreen` | `ReactNode` | Sí | Contenido principal de la pantalla |
| `type_Body` | `'ScrollView' \| 'View'` | No | Tipo de contenedor para el cuerpo |
| `Data_BottomBar` | `Array<BottomBarButton>` | No | Array para configurar botones de barra inferior |
| `floating_button` | `ReactNode` | No | Botón flotante personalizado |
| `style_container_floating_button` | `StyleProp<ViewStyle>` | No | Estilos del contenedor del botón flotante |

### BottomBarButton Type

```typescript
interface BottomBarButton {
  label?: string;
  onPress: () => void;
  icon_in: ReactNode;
  icon_out?: ReactNode;
  isInScreen?: boolean;
  style_text?: StyleProp<TextStyle>;
  style_button?: StyleProp<ViewStyle>;
  onLongPress?: () => void;
}
```

### Tipos de BottomBar

1. **Default**: Barra inferior estándar con botones distribuidos uniformemente
2. **Bar_Floating**: Barra flotante centrada con bordes redondeados
3. **BarWithFloatingButton**: Barra estándar con un botón flotante posicionado arriba

### Ejemplo

```javascript
import { LayoutScreen } from 'udev_ultime_native';
import Icon from 'react-native-vector-icons/Ionicons';

<LayoutScreen
  type_Body="ScrollView"
  topBar={
    <View style={{ backgroundColor: 'black', padding: 20 }}>
      <Text style={{ color: 'white', textAlign: 'center' }}>
        Mi App
      </Text>
    </View>
  }
  type_BottomBar="Bar_Floating"
  Data_BottomBar={[
    {
      label: "Inicio",
      onPress: () => navigation.navigate('Home'),
      icon_in: <Icon name="home" size={24} color="#007AFF" />,
      icon_out: <Icon name="home-outline" size={24} color="gray" />,
      isInScreen: true,
    },
    {
      label: "Perfil",
      onPress: () => navigation.navigate('Profile'),
      icon_in: <Icon name="person" size={24} color="#007AFF" />,
      icon_out: <Icon name="person-outline" size={24} color="gray" />,
      isInScreen: false,
    },
  ]}
  bodyScreen={
    <View style={{ padding: 20 }}>
      <Text>Contenido de la pantalla</Text>
    </View>
  }
/>
```

---

## Estilos Comunes

Todos los componentes aceptan props de estilo estándar de React Native:

- `style_container`: Estilos del contenedor principal
- `style_button`: Estilos de botones
- `style_text`: Estilos de texto
- `style_input`: Estilos de campos de entrada

Los estilos se fusionan con los estilos por defecto, permitiendo personalización completa mientras se mantienen valores sensatos por defecto.

## Eventos de Accesibilidad

Muchos componentes soportan eventos de accesibilidad:

- `onAccessibilityAction`
- `onAccessibilityEscape`
- `onAccessibilityTap`
- `onMagicTap`

Estos eventos mejoran la experiencia para usuarios con dispositivos de asistencia.

---

Para más ejemplos y guías, consulta la [documentación completa](../README.md).
