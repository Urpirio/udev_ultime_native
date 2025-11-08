# Guía de Inicio Rápido - udev_ultime_native

## Introducción

**udev_ultime_native** es una librería de componentes UI optimizada para React Native que ofrece una colección completa de elementos de interfaz listos para usar. Diseñada con TypeScript para mejor tipado y rendimiento optimizado.

## Requisitos Previos

Antes de comenzar, asegúrate de tener:

- Node.js (versión 14 o superior)
- React Native CLI o Expo CLI
- Un proyecto React Native existente (versión 0.70 o superior)
- Conocimientos básicos de React y React Native

## Instalación

### Paso 1: Instalar la librería principal

```bash
npm install udev_ultime_native
```

o con Yarn:

```bash
yarn add udev_ultime_native
```

### Paso 2: Instalar dependencias necesarias

La librería requiere algunas dependencias peer para funcionar correctamente:

```bash
npm install react-native-reanimated react-native-safe-area-context
```

o con Yarn:

```bash
yarn add react-native-reanimated react-native-safe-area-context
```

### Paso 3: Configurar react-native-reanimated

Para usar el componente `FloatingButton`, necesitas configurar `react-native-reanimated`:

1. Agrega el plugin de Babel en tu `babel.config.js`:

```javascript
module.exports = {
  presets: ['module:@react-native/babel-preset'],
  plugins: ['react-native-reanimated/plugin'], // Debe ser el último plugin
};
```

2. Limpia la caché y reinicia el bundler:

```bash
npm start -- --reset-cache
```

### Paso 4: Configurar Safe Area Context

Envuelve tu aplicación con `SafeAreaProvider` en tu archivo principal (`App.tsx` o `index.js`):

```javascript
import { SafeAreaProvider } from 'react-native-safe-area-context';

export default function App() {
  return (
    <SafeAreaProvider>
      {/* Tu aplicación aquí */}
    </SafeAreaProvider>
  );
}
```

## Tu Primer Componente

Vamos a crear una pantalla simple usando algunos componentes de la librería:

```javascript
import React, { useState } from 'react';
import { View, StyleSheet } from 'react-native';
import { Button, InputText } from 'udev_ultime_native';

export default function MyFirstScreen() {
  const [text, setText] = useState('');

  const handlePress = () => {
    console.log('Texto ingresado:', text);
  };

  return (
    <View style={styles.container}>
      <InputText
        placeholder="Ingresa tu nombre"
        value={text}
        onChangeText={setText}
        style_container={styles.input}
      />
      
      <Button
        title="Enviar"
        onPress={handlePress}
        type_button="TouchableOpacity"
        style_button={styles.button}
        style_text={styles.buttonText}
      />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    padding: 20,
    justifyContent: 'center',
  },
  input: {
    marginBottom: 20,
  },
  button: {
    backgroundColor: '#007AFF',
    padding: 15,
    borderRadius: 8,
  },
  buttonText: {
    color: 'white',
    fontSize: 16,
    fontWeight: 'bold',
  },
});
```

## Ejemplo: Formulario Completo

Aquí hay un ejemplo más completo de un formulario de registro:

```javascript
import React, { useState } from 'react';
import { View, Text, StyleSheet, ScrollView } from 'react-native';
import {
  InputText,
  InputPassword,
  InputTextarea,
  DropDown,
  Button,
} from 'udev_ultime_native';

export default function RegistrationForm() {
  const [name, setName] = useState('');
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');
  const [country, setCountry] = useState('');
  const [bio, setBio] = useState('');

  const countries = [
    { label: 'Argentina', value: 'ar' },
    { label: 'Chile', value: 'cl' },
    { label: 'Colombia', value: 'co' },
    { label: 'México', value: 'mx' },
    { label: 'Perú', value: 'pe' },
  ];

  const handleSubmit = () => {
    console.log({
      name,
      email,
      password,
      country,
      bio,
    });
  };

  return (
    <ScrollView style={styles.container}>
      <Text style={styles.title}>Registro de Usuario</Text>

      <InputText
        placeholder="Nombre completo"
        value={name}
        onChangeText={setName}
        style_container={styles.inputContainer}
      />

      <InputText
        placeholder="Correo electrónico"
        value={email}
        onChangeText={setEmail}
        keyboardType="email-address"
        style_container={styles.inputContainer}
      />

      <InputPassword
        placeholder="Contraseña"
        value={password}
        onChangeText={setPassword}
        style_container={styles.inputContainer}
      />

      <DropDown
        placeholder="Selecciona tu país"
        data_option={countries}
        Value={country}
        setValue={setCountry}
        style_container={styles.inputContainer}
      />

      <InputTextarea
        placeholder="Cuéntanos sobre ti..."
        value={bio}
        onChangeText={setBio}
        numberOfLines={4}
        style_container={styles.inputContainer}
      />

      <Button
        title="Registrarse"
        onPress={handleSubmit}
        type_button="TouchableOpacity"
        style_button={styles.submitButton}
        style_text={styles.submitButtonText}
      />
    </ScrollView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    padding: 20,
    backgroundColor: '#f5f5f5',
  },
  title: {
    fontSize: 24,
    fontWeight: 'bold',
    marginBottom: 20,
    textAlign: 'center',
  },
  inputContainer: {
    marginBottom: 15,
    backgroundColor: 'white',
    borderRadius: 8,
    borderWidth: 1,
    borderColor: '#ddd',
  },
  submitButton: {
    backgroundColor: '#007AFF',
    padding: 15,
    borderRadius: 8,
    marginTop: 10,
  },
  submitButtonText: {
    color: 'white',
    fontSize: 16,
    fontWeight: 'bold',
    textAlign: 'center',
  },
});
```

## Próximos Pasos

Ahora que has configurado la librería y creado tu primer formulario, puedes:

1. Explorar la [Referencia de API](./api/README.md) para conocer todos los componentes disponibles
2. Ver más [Ejemplos](./examples/README.md) de casos de uso comunes
3. Leer la [Guía de Arquitectura](./ARCHITECTURE.md) para entender cómo está estructurada la librería
4. Revisar la [Guía de Solución de Problemas](./TROUBLESHOOTING.md) si encuentras algún inconveniente

## Recursos Adicionales

- [Documentación oficial de React Native](https://reactnative.dev/)
- [react-native-reanimated](https://docs.swmansion.com/react-native-reanimated/)
- [react-native-safe-area-context](https://github.com/th3rdwave/react-native-safe-area-context)

## ¿Necesitas Ayuda?

Si tienes preguntas o encuentras problemas:

- Revisa la [documentación completa](../README.md)
- Abre un [issue en GitHub](https://github.com/Urpirio/Udev_Native/issues)
- Consulta la guía de [contribución](../udev_ultime_native/CONTRIBUTING.md)
