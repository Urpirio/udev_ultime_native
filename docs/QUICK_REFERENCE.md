# Referencia Rápida - udev_ultime_native

Guía de referencia rápida para consultar props y ejemplos básicos de todos los componentes.

---

## Importar Componentes

```javascript
import {
  // Entrada
  InputText,
  InputPassword,
  InputTextarea,
  DropDown,
  
  // Acción
  Button,
  ButtonBar,
  FloatingButton,
  
  // Selección
  RadioButton,
  
  // Visualización
  ProgressBar,
  Card_Simple,
  TabPanel,
  
  // Layout
  LayoutScreen,
} from 'udev_ultime_native';
```

---

## InputText

```javascript
<InputText
  value={text}
  onChangeText={setText}
  placeholder="Texto"
  keyboardType="default" // "default" | "numeric" | "email-address" | "phone-pad"
  iconLeft={<Icon />}
  iconRight={<Icon />}
  style_container={{}}
  style_input={{}}
/>
```

**Props clave:** `value`, `onChangeText`, `placeholder`, `keyboardType`

---

## InputPassword

```javascript
<InputPassword
  value={password}
  onChangeText={setPassword}
  placeholder="Contraseña"
  iconPasswordShow={<Icon name="eye" />}
  iconPasswordHide={<Icon name="eye-off" />}
  style_container={{}}
/>
```

**Props clave:** `value`, `onChangeText`, `iconPasswordShow`, `iconPasswordHide`

**Nota:** Maneja el estado de visibilidad internamente

---

## InputTextarea

```javascript
<InputTextarea
  value={text}
  onChangeText={setText}
  placeholder="Mensaje"
  numberOfLines={4}
  iconLeft={<Icon />}
  style_container={{}}
/>
```

**Props clave:** `value`, `onChangeText`, `numberOfLines`

---

## DropDown

```javascript
const options = [
  { label: 'Opción 1', value: 'opt1' },
  { label: 'Opción 2', value: 'opt2' },
];

<DropDown
  data_option={options}
  Value={selected}
  setValue={setSelected}
  placeholder="Seleccionar"
  icon={<Icon />}
  style_container={{}}
/>
```

**Props clave:** `data_option`, `Value`, `setValue`

**Estructura de data_option:** `{ label: string, value: string | number }`

---

## Button

```javascript
<Button
  title="Mi Botón"
  type_button="TouchableOpacity" // "TouchableOpacity" | "Pressable" | "TouchableHighlight"
  onPress={() => {}}
  onLongPress={() => {}}
  iconLeft={<Icon />}
  iconRight={<Icon />}
  style_button={{}}
  style_text={{}}
/>
```

**Props clave:** `title` (requerido), `onPress`, `type_button`

---

## ButtonBar

```javascript
<ButtonBar
  type_button="TouchableOpacity" // "Pressable" | "Button" | "TouchableOpacity" | "TouchableHighlight"
  text="Texto del botón"
  onPress={() => {}}
  style_button={{}}
/>
```

**Props clave:** `type_button` (requerido), `text`, `onPress`

---

## FloatingButton

```javascript
const buttonOptions = [
  {
    icon: <Icon name="home" />,
    onPress: () => {},
    style_button: { backgroundColor: 'blue' },
  },
];

<FloatingButton
  icon_hide={<Icon name="add" />}
  icon_show={<Icon name="close" />}
  Data_Button={buttonOptions}
  SelectFun_onPress="Data_Button" // "Data_Button" | "onPress"
  SelectFun_onLongPress="onLongPress" // "Data_Button" | "onLongPress"
  timing_animation_buttons={300}
  style_main_container={{ position: 'absolute', bottom: 20, right: 20 }}
/>
```

**Props clave:** `icon_hide`, `Data_Button`, `SelectFun_onPress`, `SelectFun_onLongPress`

**Estructura de Data_Button:** `{ icon, onPress, style_button?, onLongPress? }`

---

## RadioButton

```javascript
const [selected, setSelected] = useState('');

<RadioButton
  value="option1"
  value_selected={selected}
  setValue={setSelected}
  label="Opción 1"
  style_container={{}}
  style_radio={{}}
/>
```

**Props clave:** `value`, `value_selected` (requerido), `setValue` (requerido)

**Nota:** Requiere estado externo con useState

---

## ProgressBar

```javascript
const statusBar = [
  { color: '#ff0000', status: 'Bajo', progress: 25 },
  { color: '#00ff00', status: 'Alto', progress: 75 },
];

<ProgressBar
  progress={75} // 0-100 (requerido)
  show_percentage={true}
  bg_color_progress="blue"
  bg_container_bar="#f0f0f0"
  height_bar={20}
  status_bar={statusBar}
  iconLeft={<Icon />}
  iconRight={<Icon />}
/>
```

**Props clave:** `progress` (requerido, 0-100), `show_percentage`

---

## Card_Simple

```javascript
<Card_Simple
  title="Título"
  description="Descripción de la tarjeta"
  imageUri="https://example.com/image.jpg"
  text_button="Ver más"
  style_container={{}}
  style_title={{}}
  style_description={{}}
  Button={<CustomButton />} // Opcional
/>
```

**Props clave:** `title`, `description`, `imageUri`, `text_button`

---

## TabPanel

```javascript
const tabs = [
  {
    label: "Tab 1",
    description: "Contenido 1",
    value: "tab1",
  },
  {
    label: "Tab 2",
    description: "Contenido 2",
    value: "tab2",
  },
];

<TabPanel
  Data_Tabs={tabs}
  border_tab_selected="#007AFF"
  border_tab_unselected="#ddd"
  style_container={{}}
/>
```

**Props clave:** `Data_Tabs`

**Estructura de Data_Tabs:** `{ label, description?, value, style_description? }`

---

## LayoutScreen

```javascript
const bottomBarData = [
  {
    label: "Inicio",
    onPress: () => {},
    icon_in: <Icon name="home" />,
    icon_out: <Icon name="home-outline" />,
    isInScreen: true,
  },
];

<LayoutScreen
  type_Body="ScrollView" // "ScrollView" | "View"
  type_BottomBar="Default" // "Default" | "Bar_Floating" | "BarWithFloatingButton"
  topBar={<CustomTopBar />}
  bottomBar={<CustomBottomBar />} // Opcional si usas type_BottomBar
  Data_BottomBar={bottomBarData}
  floating_button={<CustomFloatingButton />}
  bodyScreen={<YourContent />} // Requerido
  style_bottomBar={{}}
/>
```

**Props clave:** `bodyScreen` (requerido), `type_BottomBar`, `Data_BottomBar`

**Tipos de BottomBar:**
- `Default` - Barra estándar
- `Bar_Floating` - Barra flotante centrada
- `BarWithFloatingButton` - Barra con botón flotante

**Estructura de Data_BottomBar:**
```javascript
{
  label?: string,
  onPress: () => void, // requerido
  icon_in: ReactNode, // requerido
  icon_out?: ReactNode,
  isInScreen?: boolean,
  style_text?: StyleProp<TextStyle>,
  style_button?: StyleProp<ViewStyle>,
  onLongPress?: () => void,
}
```

---

## Estilos Comunes

Todos los componentes aceptan props de estilo con el prefijo `style_`:

```javascript
// Ejemplos comunes
style_container={{
  backgroundColor: 'white',
  borderRadius: 8,
  padding: 15,
  margin: 10,
}}

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

style_input={{
  fontSize: 16,
  color: '#333',
}}
```

---

## Patrones de Estado

### Estado Local (useState)

```javascript
import { useState } from 'react';

const [text, setText] = useState('');
const [selected, setSelected] = useState('');
```

### Lista de Opciones

```javascript
const options = [
  { label: 'Etiqueta 1', value: 'valor1' },
  { label: 'Etiqueta 2', value: 'valor2' },
];
```

### Datos de Navegación

```javascript
const navData = [
  {
    label: "Home",
    onPress: () => navigation.navigate('Home'),
    icon_in: <Icon name="home" />,
    icon_out: <Icon name="home-outline" />,
    isInScreen: currentScreen === 'home',
  },
];
```

---

## Iconos (react-native-vector-icons)

```javascript
import Icon from 'react-native-vector-icons/Ionicons';

// Uso común
<Icon name="home" size={24} color="#007AFF" />
<Icon name="home-outline" size={24} color="#666" />
<Icon name="eye" size={20} color="#333" />
<Icon name="eye-off" size={20} color="#333" />
```

**Instalación:**
```bash
npm install react-native-vector-icons
```

---

## Tipos de Teclado

Para `InputText` keyboardType:

- `"default"` - Teclado estándar
- `"numeric"` - Solo números
- `"email-address"` - Optimizado para email
- `"phone-pad"` - Teclado telefónico

---

## Eventos Comunes

```javascript
// Eventos de interacción
onPress={() => {}}
onLongPress={() => {}}
onPressIn={() => {}}
onPressOut={() => {}}

// Eventos de campo de texto
onChangeText={(text) => {}}
onFocus={() => {}}
onBlur={() => {}}
onSubmitEditing={() => {}}

// Eventos de accesibilidad
onAccessibilityTap={() => {}}
onAccessibilityAction={() => {}}
```

---

## Validación de Formularios (Ejemplo)

```javascript
const handleSubmit = () => {
  // Validar campos vacíos
  if (!email || !password) {
    Alert.alert('Error', 'Completa todos los campos');
    return;
  }
  
  // Validar formato email
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  if (!emailRegex.test(email)) {
    Alert.alert('Error', 'Email inválido');
    return;
  }
  
  // Validar longitud password
  if (password.length < 8) {
    Alert.alert('Error', 'Contraseña muy corta');
    return;
  }
  
  // Enviar formulario
  console.log('Form valid', { email, password });
};
```

---

## SafeAreaProvider (Requerido para LayoutScreen)

```javascript
import { SafeAreaProvider } from 'react-native-safe-area-context';

export default function App() {
  return (
    <SafeAreaProvider>
      <YourApp />
    </SafeAreaProvider>
  );
}
```

---

## Babel Config (Requerido para FloatingButton)

```javascript
// babel.config.js
module.exports = {
  presets: ['module:@react-native/babel-preset'],
  plugins: ['react-native-reanimated/plugin'], // Debe ser el último
};
```

---

## Dependencias Requeridas

```bash
# Instalación completa
npm install udev_ultime_native react-native-reanimated react-native-safe-area-context

# Solo si usas iconos
npm install react-native-vector-icons
```

---

## Tips de Rendimiento

1. **Usa useCallback para funciones:**
```javascript
const handlePress = useCallback(() => {
  console.log('Pressed');
}, []);
```

2. **Usa useMemo para datos complejos:**
```javascript
const options = useMemo(() => [
  { label: 'Option 1', value: '1' },
  { label: 'Option 2', value: '2' },
], []);
```

3. **Usa React.memo para componentes:**
```javascript
const MyComponent = React.memo(({ data }) => {
  return <View>{data}</View>;
});
```

---

## Recursos

- [Documentación Completa](./README.md)
- [API Reference](./api/README.md)
- [Ejemplos](./examples/README.md)
- [Troubleshooting](./TROUBLESHOOTING.md)
- [GitHub](https://github.com/Urpirio/Udev_Native)

---

**Última actualización:** 2024-11-08
