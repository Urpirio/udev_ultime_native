# Solución de Problemas - udev_ultime_native

Esta guía te ayudará a resolver los problemas más comunes al usar la librería udev_ultime_native.

## Tabla de Contenidos

- [Problemas de Instalación](#problemas-de-instalación)
- [Problemas de Configuración](#problemas-de-configuración)
- [Problemas de Componentes](#problemas-de-componentes)
- [Problemas de Rendimiento](#problemas-de-rendimiento)
- [Problemas de TypeScript](#problemas-de-typescript)
- [Problemas de Compilación](#problemas-de-compilación)

---

## Problemas de Instalación

### Error: "Cannot find module 'react-native-reanimated'"

**Causa**: La dependencia `react-native-reanimated` no está instalada.

**Solución**:
```bash
npm install react-native-reanimated
```

Si ya está instalada, intenta limpiar la caché:
```bash
npm start -- --reset-cache
```

### Error: "Cannot find module 'react-native-safe-area-context'"

**Causa**: La dependencia `react-native-safe-area-context` no está instalada.

**Solución**:
```bash
npm install react-native-safe-area-context
```

Para iOS, también ejecuta:
```bash
cd ios && pod install && cd ..
```

### Error: "Incompatible peer dependencies"

**Causa**: Versiones incompatibles de dependencias peer.

**Solución**:
Verifica las versiones requeridas en `package.json`:
```json
{
  "peerDependencies": {
    "react": "*",
    "react-native": "*",
    "react-native-reanimated": ">=3.0.0",
    "react-native-safe-area-context": "^5.6.1"
  }
}
```

Actualiza tus dependencias a versiones compatibles.

---

## Problemas de Configuración

### FloatingButton no se anima

**Causa**: El plugin de Babel para react-native-reanimated no está configurado.

**Solución**:
Agrega el plugin en `babel.config.js`:
```javascript
module.exports = {
  presets: ['module:@react-native/babel-preset'],
  plugins: ['react-native-reanimated/plugin'], // Debe ser el ÚLTIMO plugin
};
```

Reinicia el metro bundler:
```bash
npm start -- --reset-cache
```

### SafeAreaView no funciona con LayoutScreen

**Causa**: `SafeAreaProvider` no está configurado en el root de la aplicación.

**Solución**:
Envuelve tu aplicación con `SafeAreaProvider`:
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

### Los estilos por defecto no se aplican

**Causa**: Los estilos personalizados están sobrescribiendo completamente los estilos por defecto.

**Solución**:
Los componentes fusionan estilos internamente, pero si usas arrays de estilos, asegúrate de no sobrescribir propiedades importantes:

```javascript
// ✅ Correcto: Los estilos se fusionan
<Button
  style_button={{ backgroundColor: 'blue' }}
/>

// ⚠️ Cuidado: Puede sobrescribir todo
<Button
  style_button={[myStyles.button]}
/>
```

---

## Problemas de Componentes

### InputPassword no muestra el icono de toggle

**Causa**: No se han proporcionado los iconos `iconPasswordShow` y `iconPasswordHide`.

**Solución**:
Pasa los iconos como props:
```javascript
import Icon from 'react-native-vector-icons/Ionicons';

<InputPassword
  iconPasswordShow={<Icon name="eye" size={20} />}
  iconPasswordHide={<Icon name="eye-off" size={20} />}
  value={password}
  onChangeText={setPassword}
/>
```

### DropDown no muestra las opciones

**Causa 1**: El array `data_option` está vacío o mal formado.

**Solución**:
Verifica que el array tenga la estructura correcta:
```javascript
const options = [
  { label: 'Opción 1', value: 'opt1' },
  { label: 'Opción 2', value: 'opt2' },
];

<DropDown data_option={options} />
```

**Causa 2**: Los estilos del contenedor de opciones están ocultos.

**Solución**:
Revisa los estilos de `style_container_option`:
```javascript
<DropDown
  style_container_option={{
    maxHeight: 200,  // Asegúrate de que tenga altura
    backgroundColor: 'white',
  }}
/>
```

### RadioButton no cambia de estado

**Causa**: El estado no se está actualizando correctamente.

**Solución**:
Asegúrate de usar `setValue` correctamente:
```javascript
const [selected, setSelected] = useState('');

<RadioButton
  value="option1"
  value_selected={selected}
  setValue={setSelected}  // Función setState
  label="Opción 1"
/>
```

### TabPanel no muestra el contenido

**Causa**: La propiedad `description` en `Data_Tabs` está undefined o vacía.

**Solución**:
Verifica que cada pestaña tenga `description`:
```javascript
<TabPanel
  Data_Tabs={[
    {
      label: "Tab 1",
      description: "Contenido de la pestaña 1",  // ✅ No debe estar vacío
      value: "tab1"
    }
  ]}
/>
```

### ProgressBar no se ve

**Causa**: El color de la barra de progreso es igual al color del contenedor.

**Solución**:
Establece colores contrastantes:
```javascript
<ProgressBar
  progress={50}
  bg_color_progress="blue"      // Color de la barra
  bg_container_bar="#f0f0f0"    // Color del fondo
  height_bar={20}
/>
```

### FloatingButton no responde

**Causa**: Las opciones de `Data_Button` no tienen la función `onPress` definida.

**Solución**:
Asegúrate de que cada botón tenga un `onPress`:
```javascript
<FloatingButton
  Data_Button={[
    {
      icon: <Icon name="home" />,
      onPress: () => console.log('Home'),  // ✅ Requerido
      style_button: { backgroundColor: 'blue' }
    }
  ]}
  SelectFun_onPress="Data_Button"
/>
```

---

## Problemas de Rendimiento

### La aplicación se siente lenta al usar múltiples componentes

**Solución 1**: Usa `useMemo` para datos complejos:
```javascript
const options = useMemo(() => [
  { label: 'Opción 1', value: '1' },
  { label: 'Opción 2', value: '2' },
  // ... más opciones
], []);
```

**Solución 2**: Usa `useCallback` para funciones:
```javascript
const handlePress = useCallback(() => {
  console.log('Pressed');
}, []);
```

**Solución 3**: Implementa virtualización para listas largas:
```javascript
import { FlatList } from 'react-native';

// Usa FlatList en lugar de renderizar múltiples componentes
<FlatList
  data={items}
  renderItem={({ item }) => <Card_Simple {...item} />}
  keyExtractor={(item) => item.id}
/>
```

### Las animaciones del FloatingButton son lentas

**Causa**: El valor de `timing_animation_buttons` es muy alto.

**Solución**:
Reduce la duración de la animación:
```javascript
<FloatingButton
  timing_animation_buttons={300}  // Valor en milisegundos
/>
```

### InputText tiene lag al escribir

**Causa**: El componente padre se re-renderiza en cada cambio.

**Solución**:
Optimiza el componente padre con `React.memo`:
```javascript
const InputForm = React.memo(({ value, onChange }) => {
  return (
    <InputText
      value={value}
      onChangeText={onChange}
    />
  );
});
```

---

## Problemas de TypeScript

### Error: "Type 'X' is not assignable to type 'Y'"

**Causa**: Las props no coinciden con los tipos esperados.

**Solución**:
Verifica la definición de tipos en tu editor (hovering sobre el componente) y ajusta tus props:
```typescript
// ✅ Correcto
<Button
  title="Mi Botón"
  type_button="TouchableOpacity"
/>

// ❌ Incorrecto
<Button
  title="Mi Botón"
  type_button="SomeOtherType"  // TypeScript mostrará un error
/>
```

### Error: "Property 'X' does not exist on type 'ComponentProps'"

**Causa**: Estás intentando usar una prop que no existe en el componente.

**Solución**:
Revisa la documentación de la API del componente o usa el autocompletado de tu editor para ver las props disponibles.

### Los tipos no aparecen en el autocompletado

**Causa**: TypeScript no está leyendo correctamente las definiciones de tipos.

**Solución**:
1. Verifica que tienes `"types": "./lib/typescript/src/index.d.ts"` en package.json
2. Reinicia el servidor de lenguaje de TypeScript en tu editor
3. Ejecuta `yarn typecheck` para verificar

---

## Problemas de Compilación

### Error: "Unable to resolve module 'udev_ultime_native'"

**Causa 1**: La librería no está instalada correctamente.

**Solución**:
Reinstala la librería:
```bash
rm -rf node_modules
npm install
```

**Causa 2**: Metro bundler no reconoce los cambios.

**Solución**:
Reinicia el bundler con caché limpia:
```bash
npm start -- --reset-cache
```

### Error en iOS: "Undefined symbols for architecture arm64"

**Causa**: Los pods no están instalados o actualizados.

**Solución**:
```bash
cd ios
rm -rf Pods Podfile.lock
pod install
cd ..
```

### Error en Android: "Execution failed for task ':app:checkDebugDuplicateClasses'"

**Causa**: Hay clases duplicadas en las dependencias.

**Solución**:
Limpia el proyecto de Android:
```bash
cd android
./gradlew clean
cd ..
```

Si el problema persiste, verifica que no haya versiones duplicadas de dependencias.

### Build falla en producción

**Causa**: Faltan configuraciones para producción.

**Solución**:
Para iOS, asegúrate de tener el scheme correcto:
```bash
cd ios
xcodebuild -workspace YourApp.xcworkspace -scheme YourApp -configuration Release
```

Para Android, verifica `android/app/build.gradle`:
```gradle
buildTypes {
    release {
        minifyEnabled true
        proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
    }
}
```

---

## Problemas Comunes en Producción

### Los iconos no se muestran en el build de producción

**Causa**: Los assets no están incluidos en el bundle.

**Solución**:
Verifica que los iconos estén importados correctamente y que las fuentes de iconos estén vinculadas.

Para react-native-vector-icons:
```bash
npx react-native link react-native-vector-icons
```

### Los estilos se ven diferentes en producción

**Causa**: Las diferencias entre modo desarrollo y producción.

**Solución**:
- Prueba tu app en modo release antes de publicar
- Verifica que los estilos no dependan de variables de entorno

```bash
# iOS
npx react-native run-ios --configuration Release

# Android
npx react-native run-android --variant=release
```

---

## Reporte de Bugs

Si encuentras un bug que no está listado aquí:

1. Verifica que estés usando la última versión de la librería
2. Revisa los [issues abiertos en GitHub](https://github.com/Urpirio/udev_ultime_native/issues)
3. Si el problema persiste, [abre un nuevo issue](https://github.com/Urpirio/udev_ultime_native/issues/new) con:
   - Descripción detallada del problema
   - Pasos para reproducir el error
   - Versión de la librería y React Native
   - Código de ejemplo (mínimo y reproducible)
   - Screenshots o videos si es relevante

## Recursos Adicionales

- [Documentación de React Native](https://reactnative.dev/docs/getting-started)
- [react-native-reanimated Docs](https://docs.swmansion.com/react-native-reanimated/)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [React Native Community](https://github.com/react-native-community)

---

¿Solucionaste un problema que no está aquí? ¡Considera [contribuir a la documentación](../udev_ultime_native/CONTRIBUTING.md)!
