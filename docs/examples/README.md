# Ejemplos de Uso - udev_ultime_native

Esta sección contiene ejemplos prácticos de cómo usar los componentes de la librería en casos de uso reales.

## Índice

1. [Formulario de Login](#formulario-de-login)
2. [Formulario de Registro](#formulario-de-registro)
3. [Perfil de Usuario](#perfil-de-usuario)
4. [Pantalla con Navegación](#pantalla-con-navegación)
5. [Dashboard con Progreso](#dashboard-con-progreso)
6. [Configuración de App](#configuración-de-app)
7. [Galería de Tarjetas](#galería-de-tarjetas)
8. [Formulario de Encuesta](#formulario-de-encuesta)

---

## Formulario de Login

Un formulario simple de inicio de sesión con validación básica.

```javascript
import React, { useState } from 'react';
import { View, Text, StyleSheet, Alert } from 'react-native';
import { InputText, InputPassword, Button } from 'udev_ultime_native';
import Icon from 'react-native-vector-icons/Ionicons';

export default function LoginScreen() {
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');

  const handleLogin = () => {
    if (!email || !password) {
      Alert.alert('Error', 'Por favor completa todos los campos');
      return;
    }
    
    // Aquí iría tu lógica de autenticación
    console.log('Login:', { email, password });
  };

  return (
    <View style={styles.container}>
      <Text style={styles.title}>Iniciar Sesión</Text>
      
      <InputText
        placeholder="Correo electrónico"
        value={email}
        onChangeText={setEmail}
        keyboardType="email-address"
        iconLeft={<Icon name="mail-outline" size={20} color="#666" />}
        style_container={styles.input}
      />
      
      <InputPassword
        placeholder="Contraseña"
        value={password}
        onChangeText={setPassword}
        iconPasswordShow={<Icon name="eye-outline" size={20} color="#666" />}
        iconPasswordHide={<Icon name="eye-off-outline" size={20} color="#666" />}
        style_container={styles.input}
      />
      
      <Button
        title="Iniciar Sesión"
        onPress={handleLogin}
        type_button="TouchableOpacity"
        style_button={styles.loginButton}
        style_text={styles.loginButtonText}
      />
      
      <Button
        title="¿Olvidaste tu contraseña?"
        onPress={() => console.log('Recuperar contraseña')}
        type_button="Pressable"
        style_button={styles.forgotButton}
        style_text={styles.forgotButtonText}
      />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    padding: 20,
    justifyContent: 'center',
    backgroundColor: '#f5f5f5',
  },
  title: {
    fontSize: 28,
    fontWeight: 'bold',
    marginBottom: 30,
    textAlign: 'center',
    color: '#333',
  },
  input: {
    marginBottom: 15,
    backgroundColor: 'white',
    borderRadius: 8,
    borderWidth: 1,
    borderColor: '#ddd',
    paddingHorizontal: 15,
  },
  loginButton: {
    backgroundColor: '#007AFF',
    padding: 15,
    borderRadius: 8,
    marginTop: 10,
  },
  loginButtonText: {
    color: 'white',
    fontSize: 16,
    fontWeight: 'bold',
    textAlign: 'center',
  },
  forgotButton: {
    marginTop: 15,
    padding: 10,
  },
  forgotButtonText: {
    color: '#007AFF',
    fontSize: 14,
    textAlign: 'center',
  },
});
```

---

## Formulario de Registro

Formulario completo de registro con múltiples campos y validación.

```javascript
import React, { useState } from 'react';
import { View, Text, StyleSheet, ScrollView, Alert } from 'react-native';
import {
  InputText,
  InputPassword,
  DropDown,
  RadioButton,
  Button,
} from 'udev_ultime_native';
import Icon from 'react-native-vector-icons/Ionicons';

export default function RegisterScreen() {
  const [name, setName] = useState('');
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');
  const [confirmPassword, setConfirmPassword] = useState('');
  const [country, setCountry] = useState('');
  const [gender, setGender] = useState('');

  const countries = [
    { label: 'Argentina', value: 'ar' },
    { label: 'Chile', value: 'cl' },
    { label: 'Colombia', value: 'co' },
    { label: 'México', value: 'mx' },
    { label: 'Perú', value: 'pe' },
  ];

  const handleRegister = () => {
    if (!name || !email || !password || !confirmPassword) {
      Alert.alert('Error', 'Por favor completa todos los campos requeridos');
      return;
    }

    if (password !== confirmPassword) {
      Alert.alert('Error', 'Las contraseñas no coinciden');
      return;
    }

    console.log('Registro:', { name, email, password, country, gender });
    Alert.alert('Éxito', 'Cuenta creada exitosamente');
  };

  return (
    <ScrollView style={styles.container} contentContainerStyle={styles.content}>
      <Text style={styles.title}>Crear Cuenta</Text>

      <InputText
        placeholder="Nombre completo *"
        value={name}
        onChangeText={setName}
        iconLeft={<Icon name="person-outline" size={20} color="#666" />}
        style_container={styles.input}
      />

      <InputText
        placeholder="Correo electrónico *"
        value={email}
        onChangeText={setEmail}
        keyboardType="email-address"
        iconLeft={<Icon name="mail-outline" size={20} color="#666" />}
        style_container={styles.input}
      />

      <InputPassword
        placeholder="Contraseña *"
        value={password}
        onChangeText={setPassword}
        iconPasswordShow={<Icon name="eye-outline" size={20} />}
        iconPasswordHide={<Icon name="eye-off-outline" size={20} />}
        style_container={styles.input}
      />

      <InputPassword
        placeholder="Confirmar contraseña *"
        value={confirmPassword}
        onChangeText={setConfirmPassword}
        iconPasswordShow={<Icon name="eye-outline" size={20} />}
        iconPasswordHide={<Icon name="eye-off-outline" size={20} />}
        style_container={styles.input}
      />

      <DropDown
        placeholder="Selecciona tu país"
        data_option={countries}
        Value={country}
        setValue={setCountry}
        icon={<Icon name="chevron-down" size={20} color="#666" />}
        style_container={styles.input}
      />

      <View style={styles.genderContainer}>
        <Text style={styles.label}>Género:</Text>
        <RadioButton
          value="male"
          value_selected={gender}
          setValue={setGender}
          label="Masculino"
          style_container={styles.radioButton}
        />
        <RadioButton
          value="female"
          value_selected={gender}
          setValue={setGender}
          label="Femenino"
          style_container={styles.radioButton}
        />
        <RadioButton
          value="other"
          value_selected={gender}
          setValue={setGender}
          label="Otro"
          style_container={styles.radioButton}
        />
      </View>

      <Button
        title="Crear Cuenta"
        onPress={handleRegister}
        type_button="TouchableOpacity"
        style_button={styles.registerButton}
        style_text={styles.registerButtonText}
      />

      <Text style={styles.termsText}>
        Al crear una cuenta, aceptas nuestros Términos y Condiciones
      </Text>
    </ScrollView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#f5f5f5',
  },
  content: {
    padding: 20,
  },
  title: {
    fontSize: 28,
    fontWeight: 'bold',
    marginBottom: 30,
    textAlign: 'center',
    color: '#333',
  },
  input: {
    marginBottom: 15,
    backgroundColor: 'white',
    borderRadius: 8,
    borderWidth: 1,
    borderColor: '#ddd',
    paddingHorizontal: 15,
  },
  genderContainer: {
    marginBottom: 20,
    backgroundColor: 'white',
    borderRadius: 8,
    borderWidth: 1,
    borderColor: '#ddd',
    padding: 15,
  },
  label: {
    fontSize: 16,
    fontWeight: '600',
    marginBottom: 10,
    color: '#333',
  },
  radioButton: {
    marginBottom: 10,
  },
  registerButton: {
    backgroundColor: '#34C759',
    padding: 15,
    borderRadius: 8,
    marginTop: 10,
  },
  registerButtonText: {
    color: 'white',
    fontSize: 16,
    fontWeight: 'bold',
    textAlign: 'center',
  },
  termsText: {
    marginTop: 15,
    textAlign: 'center',
    fontSize: 12,
    color: '#666',
  },
});
```

---

## Perfil de Usuario

Pantalla de perfil con información del usuario y opciones.

```javascript
import React, { useState } from 'react';
import { View, Text, StyleSheet, Image, ScrollView } from 'react-native';
import { Card_Simple, Button, TabPanel } from 'udev_ultime_native';
import Icon from 'react-native-vector-icons/Ionicons';

export default function ProfileScreen() {
  const [activeTab, setActiveTab] = useState('info');

  const tabData = [
    {
      label: 'Información',
      value: 'info',
      description: 'Nombre: Juan Pérez\nEmail: juan@example.com\nPaís: México',
    },
    {
      label: 'Actividad',
      value: 'activity',
      description: 'Última conexión: Hoy\nPublicaciones: 42\nSeguidores: 128',
    },
    {
      label: 'Configuración',
      value: 'settings',
      description: 'Notificaciones: Activadas\nPrivacidad: Pública\nIdioma: Español',
    },
  ];

  return (
    <ScrollView style={styles.container}>
      <View style={styles.header}>
        <Image
          source={{ uri: 'https://via.placeholder.com/150' }}
          style={styles.avatar}
        />
        <Text style={styles.name}>Juan Pérez</Text>
        <Text style={styles.bio}>Desarrollador | Creador de contenido</Text>
      </View>

      <TabPanel
        Data_Tabs={tabData}
        border_tab_selected="#007AFF"
        style_container={styles.tabPanel}
      />

      <View style={styles.actions}>
        <Button
          title="Editar Perfil"
          type_button="TouchableOpacity"
          iconLeft={<Icon name="create-outline" size={18} color="white" />}
          style_button={styles.editButton}
          style_text={styles.editButtonText}
          onPress={() => console.log('Editar perfil')}
        />

        <Button
          title="Cerrar Sesión"
          type_button="TouchableOpacity"
          iconLeft={<Icon name="log-out-outline" size={18} color="white" />}
          style_button={styles.logoutButton}
          style_text={styles.logoutButtonText}
          onPress={() => console.log('Cerrar sesión')}
        />
      </View>

      <View style={styles.statsContainer}>
        <Card_Simple
          title="Logros"
          description="Has completado 15 desafíos este mes"
          text_button="Ver todos"
          style_container={styles.card}
        />
      </View>
    </ScrollView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#f5f5f5',
  },
  header: {
    alignItems: 'center',
    padding: 20,
    backgroundColor: 'white',
    borderBottomWidth: 1,
    borderBottomColor: '#ddd',
  },
  avatar: {
    width: 100,
    height: 100,
    borderRadius: 50,
    marginBottom: 15,
  },
  name: {
    fontSize: 24,
    fontWeight: 'bold',
    color: '#333',
  },
  bio: {
    fontSize: 14,
    color: '#666',
    marginTop: 5,
  },
  tabPanel: {
    margin: 15,
    backgroundColor: 'white',
    borderRadius: 8,
  },
  actions: {
    padding: 15,
  },
  editButton: {
    backgroundColor: '#007AFF',
    padding: 15,
    borderRadius: 8,
    marginBottom: 10,
  },
  editButtonText: {
    color: 'white',
    fontSize: 16,
    fontWeight: 'bold',
    textAlign: 'center',
  },
  logoutButton: {
    backgroundColor: '#FF3B30',
    padding: 15,
    borderRadius: 8,
  },
  logoutButtonText: {
    color: 'white',
    fontSize: 16,
    fontWeight: 'bold',
    textAlign: 'center',
  },
  statsContainer: {
    padding: 15,
    alignItems: 'center',
  },
  card: {
    marginVertical: 10,
  },
});
```

---

## Pantalla con Navegación

Ejemplo de pantalla completa usando LayoutScreen con navegación inferior.

```javascript
import React, { useState } from 'react';
import { View, Text, StyleSheet } from 'react-native';
import { LayoutScreen, FloatingButton } from 'udev_ultime_native';
import Icon from 'react-native-vector-icons/Ionicons';

export default function MainScreen() {
  const [currentScreen, setCurrentScreen] = useState('home');

  const bottomBarData = [
    {
      label: 'Inicio',
      onPress: () => setCurrentScreen('home'),
      icon_in: <Icon name="home" size={24} color="#007AFF" />,
      icon_out: <Icon name="home-outline" size={24} color="#666" />,
      isInScreen: currentScreen === 'home',
    },
    {
      label: 'Buscar',
      onPress: () => setCurrentScreen('search'),
      icon_in: <Icon name="search" size={24} color="#007AFF" />,
      icon_out: <Icon name="search-outline" size={24} color="#666" />,
      isInScreen: currentScreen === 'search',
    },
    {
      label: 'Perfil',
      onPress: () => setCurrentScreen('profile'),
      icon_in: <Icon name="person" size={24} color="#007AFF" />,
      icon_out: <Icon name="person-outline" size={24} color="#666" />,
      isInScreen: currentScreen === 'profile',
    },
  ];

  const floatingButtonOptions = [
    {
      icon: <Icon name="camera" size={20} color="white" />,
      onPress: () => console.log('Cámara'),
      style_button: { backgroundColor: '#34C759' },
    },
    {
      icon: <Icon name="image" size={20} color="white" />,
      onPress: () => console.log('Galería'),
      style_button: { backgroundColor: '#007AFF' },
    },
  ];

  const renderContent = () => {
    switch (currentScreen) {
      case 'home':
        return (
          <View style={styles.content}>
            <Text style={styles.contentTitle}>Inicio</Text>
            <Text>Bienvenido a la pantalla de inicio</Text>
          </View>
        );
      case 'search':
        return (
          <View style={styles.content}>
            <Text style={styles.contentTitle}>Buscar</Text>
            <Text>Pantalla de búsqueda</Text>
          </View>
        );
      case 'profile':
        return (
          <View style={styles.content}>
            <Text style={styles.contentTitle}>Perfil</Text>
            <Text>Tu perfil de usuario</Text>
          </View>
        );
      default:
        return null;
    }
  };

  return (
    <LayoutScreen
      type_Body="ScrollView"
      topBar={
        <View style={styles.topBar}>
          <Text style={styles.topBarTitle}>Mi App</Text>
        </View>
      }
      type_BottomBar="Bar_Floating"
      Data_BottomBar={bottomBarData}
      bodyScreen={renderContent()}
      floating_button={
        <FloatingButton
          icon_hide={<Icon name="add" size={28} color="white" />}
          icon_show={<Icon name="close" size={28} color="white" />}
          Data_Button={floatingButtonOptions}
          SelectFun_onPress="Data_Button"
          SelectFun_onLongPress="onLongPress"
        />
      }
    />
  );
}

const styles = StyleSheet.create({
  topBar: {
    backgroundColor: '#007AFF',
    padding: 20,
    paddingTop: 50,
  },
  topBarTitle: {
    color: 'white',
    fontSize: 20,
    fontWeight: 'bold',
    textAlign: 'center',
  },
  content: {
    padding: 20,
  },
  contentTitle: {
    fontSize: 24,
    fontWeight: 'bold',
    marginBottom: 10,
  },
});
```

---

## Dashboard con Progreso

Dashboard mostrando múltiples indicadores de progreso.

```javascript
import React from 'react';
import { View, Text, StyleSheet, ScrollView } from 'react-native';
import { ProgressBar, Card_Simple } from 'udev_ultime_native';
import Icon from 'react-native-vector-icons/Ionicons';

export default function DashboardScreen() {
  const statusBar = [
    { color: '#FF3B30', status: 'Bajo', progress: 25 },
    { color: '#FF9500', status: 'Medio', progress: 50 },
    { color: '#FFCC00', status: 'Bueno', progress: 75 },
    { color: '#34C759', status: 'Excelente', progress: 100 },
  ];

  return (
    <ScrollView style={styles.container}>
      <Text style={styles.title}>Panel de Control</Text>

      <View style={styles.section}>
        <Text style={styles.sectionTitle}>Progreso del Proyecto</Text>
        <ProgressBar
          progress={75}
          show_percentage={true}
          height_bar={25}
          status_bar={statusBar}
          iconLeft={<Icon name="rocket" size={20} color="#007AFF" />}
          style_container={styles.progressBar}
        />
      </View>

      <View style={styles.section}>
        <Text style={styles.sectionTitle}>Tareas Completadas</Text>
        <ProgressBar
          progress={60}
          show_percentage={true}
          bg_color_progress="#34C759"
          height_bar={20}
          style_container={styles.progressBar}
        />
      </View>

      <View style={styles.section}>
        <Text style={styles.sectionTitle}>Objetivos del Mes</Text>
        <ProgressBar
          progress={45}
          show_percentage={true}
          bg_color_progress="#FF9500"
          height_bar={20}
          style_container={styles.progressBar}
        />
      </View>

      <View style={styles.cardsContainer}>
        <Card_Simple
          title="Proyectos"
          description="12 proyectos activos este mes"
          text_button="Ver detalles"
          style_container={styles.card}
        />
        <Card_Simple
          title="Equipo"
          description="24 miembros colaborando"
          text_button="Ver equipo"
          style_container={styles.card}
        />
      </View>
    </ScrollView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#f5f5f5',
  },
  title: {
    fontSize: 28,
    fontWeight: 'bold',
    padding: 20,
    color: '#333',
  },
  section: {
    backgroundColor: 'white',
    padding: 15,
    marginHorizontal: 15,
    marginBottom: 15,
    borderRadius: 8,
    shadowColor: '#000',
    shadowOffset: { width: 0, height: 2 },
    shadowOpacity: 0.1,
    shadowRadius: 4,
    elevation: 3,
  },
  sectionTitle: {
    fontSize: 16,
    fontWeight: '600',
    marginBottom: 15,
    color: '#333',
  },
  progressBar: {
    marginVertical: 5,
  },
  cardsContainer: {
    flexDirection: 'row',
    flexWrap: 'wrap',
    justifyContent: 'space-around',
    padding: 10,
  },
  card: {
    margin: 5,
  },
});
```

---

## Configuración de App

Pantalla de configuración con múltiples opciones.

```javascript
import React, { useState } from 'react';
import { View, Text, StyleSheet, ScrollView, Switch } from 'react-native';
import { Button, DropDown, RadioButton } from 'udev_ultime_native';
import Icon from 'react-native-vector-icons/Ionicons';

export default function SettingsScreen() {
  const [notifications, setNotifications] = useState(true);
  const [darkMode, setDarkMode] = useState(false);
  const [language, setLanguage] = useState('es');
  const [fontSize, setFontSize] = useState('medium');

  const languages = [
    { label: 'Español', value: 'es' },
    { label: 'English', value: 'en' },
    { label: 'Português', value: 'pt' },
    { label: 'Français', value: 'fr' },
  ];

  return (
    <ScrollView style={styles.container}>
      <Text style={styles.title}>Configuración</Text>

      <View style={styles.section}>
        <Text style={styles.sectionTitle}>Apariencia</Text>
        
        <View style={styles.settingRow}>
          <Text style={styles.settingLabel}>Modo Oscuro</Text>
          <Switch
            value={darkMode}
            onValueChange={setDarkMode}
            trackColor={{ false: '#ddd', true: '#007AFF' }}
          />
        </View>

        <View style={styles.settingRow}>
          <Text style={styles.settingLabel}>Notificaciones</Text>
          <Switch
            value={notifications}
            onValueChange={setNotifications}
            trackColor={{ false: '#ddd', true: '#34C759' }}
          />
        </View>
      </View>

      <View style={styles.section}>
        <Text style={styles.sectionTitle}>Idioma</Text>
        <DropDown
          data_option={languages}
          Value={language}
          setValue={setLanguage}
          placeholder="Selecciona idioma"
          style_container={styles.dropdown}
        />
      </View>

      <View style={styles.section}>
        <Text style={styles.sectionTitle}>Tamaño de Fuente</Text>
        <RadioButton
          value="small"
          value_selected={fontSize}
          setValue={setFontSize}
          label="Pequeña"
          style_container={styles.radioButton}
        />
        <RadioButton
          value="medium"
          value_selected={fontSize}
          setValue={setFontSize}
          label="Mediana"
          style_container={styles.radioButton}
        />
        <RadioButton
          value="large"
          value_selected={fontSize}
          setValue={setFontSize}
          label="Grande"
          style_container={styles.radioButton}
        />
      </View>

      <View style={styles.actions}>
        <Button
          title="Guardar Cambios"
          type_button="TouchableOpacity"
          iconLeft={<Icon name="save-outline" size={18} color="white" />}
          style_button={styles.saveButton}
          style_text={styles.saveButtonText}
          onPress={() => console.log('Guardar')}
        />

        <Button
          title="Restablecer Configuración"
          type_button="TouchableOpacity"
          iconLeft={<Icon name="refresh-outline" size={18} color="#666" />}
          style_button={styles.resetButton}
          style_text={styles.resetButtonText}
          onPress={() => console.log('Restablecer')}
        />
      </View>
    </ScrollView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#f5f5f5',
  },
  title: {
    fontSize: 28,
    fontWeight: 'bold',
    padding: 20,
    color: '#333',
  },
  section: {
    backgroundColor: 'white',
    padding: 15,
    marginHorizontal: 15,
    marginBottom: 15,
    borderRadius: 8,
  },
  sectionTitle: {
    fontSize: 18,
    fontWeight: '600',
    marginBottom: 15,
    color: '#333',
  },
  settingRow: {
    flexDirection: 'row',
    justifyContent: 'space-between',
    alignItems: 'center',
    paddingVertical: 10,
  },
  settingLabel: {
    fontSize: 16,
    color: '#333',
  },
  dropdown: {
    borderWidth: 1,
    borderColor: '#ddd',
    borderRadius: 8,
    padding: 10,
  },
  radioButton: {
    marginBottom: 10,
  },
  actions: {
    padding: 15,
  },
  saveButton: {
    backgroundColor: '#34C759',
    padding: 15,
    borderRadius: 8,
    marginBottom: 10,
  },
  saveButtonText: {
    color: 'white',
    fontSize: 16,
    fontWeight: 'bold',
    textAlign: 'center',
  },
  resetButton: {
    backgroundColor: 'transparent',
    padding: 15,
    borderRadius: 8,
    borderWidth: 1,
    borderColor: '#ddd',
  },
  resetButtonText: {
    color: '#666',
    fontSize: 16,
    textAlign: 'center',
  },
});
```

---

## Galería de Tarjetas

Ejemplo de galería mostrando múltiples tarjetas.

```javascript
import React from 'react';
import { View, StyleSheet, ScrollView, Text } from 'react-native';
import { Card_Simple } from 'udev_ultime_native';

export default function GalleryScreen() {
  const items = [
    {
      title: 'Montaña',
      description: 'Hermosas vistas de las montañas al atardecer',
      imageUri: 'https://via.placeholder.com/300x200/4A90E2/ffffff?text=Mountain',
    },
    {
      title: 'Playa',
      description: 'Playas paradisíacas con aguas cristalinas',
      imageUri: 'https://via.placeholder.com/300x200/50C878/ffffff?text=Beach',
    },
    {
      title: 'Ciudad',
      description: 'Vida urbana y arquitectura moderna',
      imageUri: 'https://via.placeholder.com/300x200/FF6B6B/ffffff?text=City',
    },
    {
      title: 'Bosque',
      description: 'Naturaleza verde y tranquila',
      imageUri: 'https://via.placeholder.com/300x200/228B22/ffffff?text=Forest',
    },
    {
      title: 'Desierto',
      description: 'Paisajes áridos y dunas infinitas',
      imageUri: 'https://via.placeholder.com/300x200/DEB887/ffffff?text=Desert',
    },
    {
      title: 'Océano',
      description: 'Profundidades marinas y vida acuática',
      imageUri: 'https://via.placeholder.com/300x200/1E90FF/ffffff?text=Ocean',
    },
  ];

  return (
    <ScrollView style={styles.container}>
      <Text style={styles.title}>Galería</Text>
      <View style={styles.gallery}>
        {items.map((item, index) => (
          <Card_Simple
            key={index}
            title={item.title}
            description={item.description}
            imageUri={item.imageUri}
            text_button="Ver más"
            style_container={styles.card}
            onPress={() => console.log(`Pressed ${item.title}`)}
          />
        ))}
      </View>
    </ScrollView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#f5f5f5',
  },
  title: {
    fontSize: 28,
    fontWeight: 'bold',
    padding: 20,
    color: '#333',
  },
  gallery: {
    flexDirection: 'row',
    flexWrap: 'wrap',
    justifyContent: 'space-around',
    padding: 10,
  },
  card: {
    marginBottom: 20,
  },
});
```

---

## Formulario de Encuesta

Formulario de encuesta con diferentes tipos de preguntas.

```javascript
import React, { useState } from 'react';
import { View, Text, StyleSheet, ScrollView, Alert } from 'react-native';
import {
  InputText,
  InputTextarea,
  RadioButton,
  DropDown,
  Button,
  ProgressBar,
} from 'udev_ultime_native';

export default function SurveyScreen() {
  const [name, setName] = useState('');
  const [age, setAge] = useState('');
  const [satisfaction, setSatisfaction] = useState('');
  const [category, setCategory] = useState('');
  const [comments, setComments] = useState('');

  const categories = [
    { label: 'Tecnología', value: 'tech' },
    { label: 'Educación', value: 'education' },
    { label: 'Entretenimiento', value: 'entertainment' },
    { label: 'Salud', value: 'health' },
  ];

  const calculateProgress = () => {
    let filled = 0;
    if (name) filled += 20;
    if (age) filled += 20;
    if (satisfaction) filled += 20;
    if (category) filled += 20;
    if (comments) filled += 20;
    return filled;
  };

  const handleSubmit = () => {
    if (calculateProgress() < 100) {
      Alert.alert('Incompleto', 'Por favor completa todas las preguntas');
      return;
    }

    console.log('Encuesta:', {
      name,
      age,
      satisfaction,
      category,
      comments,
    });
    Alert.alert('Enviado', 'Gracias por completar la encuesta');
  };

  return (
    <ScrollView style={styles.container}>
      <Text style={styles.title}>Encuesta de Satisfacción</Text>

      <ProgressBar
        progress={calculateProgress()}
        show_percentage={true}
        bg_color_progress="#34C759"
        height_bar={20}
        style_container={styles.progress}
      />

      <View style={styles.question}>
        <Text style={styles.questionText}>1. ¿Cuál es tu nombre?</Text>
        <InputText
          placeholder="Tu nombre"
          value={name}
          onChangeText={setName}
          style_container={styles.input}
        />
      </View>

      <View style={styles.question}>
        <Text style={styles.questionText}>2. ¿Cuál es tu rango de edad?</Text>
        <DropDown
          placeholder="Selecciona tu edad"
          data_option={[
            { label: '18-25', value: '18-25' },
            { label: '26-35', value: '26-35' },
            { label: '36-50', value: '36-50' },
            { label: '51+', value: '51+' },
          ]}
          Value={age}
          setValue={setAge}
          style_container={styles.input}
        />
      </View>

      <View style={styles.question}>
        <Text style={styles.questionText}>3. ¿Qué tan satisfecho estás?</Text>
        <RadioButton
          value="very"
          value_selected={satisfaction}
          setValue={setSatisfaction}
          label="Muy satisfecho"
          style_container={styles.radio}
        />
        <RadioButton
          value="satisfied"
          value_selected={satisfaction}
          setValue={setSatisfaction}
          label="Satisfecho"
          style_container={styles.radio}
        />
        <RadioButton
          value="neutral"
          value_selected={satisfaction}
          setValue={setSatisfaction}
          label="Neutral"
          style_container={styles.radio}
        />
        <RadioButton
          value="unsatisfied"
          value_selected={satisfaction}
          setValue={setSatisfaction}
          label="Insatisfecho"
          style_container={styles.radio}
        />
      </View>

      <View style={styles.question}>
        <Text style={styles.questionText}>4. ¿Qué categoría te interesa?</Text>
        <DropDown
          placeholder="Selecciona una categoría"
          data_option={categories}
          Value={category}
          setValue={setCategory}
          style_container={styles.input}
        />
      </View>

      <View style={styles.question}>
        <Text style={styles.questionText}>5. Comentarios adicionales</Text>
        <InputTextarea
          placeholder="Escribe tus comentarios aquí..."
          value={comments}
          onChangeText={setComments}
          numberOfLines={4}
          style_container={styles.textarea}
        />
      </View>

      <Button
        title="Enviar Encuesta"
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
    backgroundColor: '#f5f5f5',
  },
  title: {
    fontSize: 28,
    fontWeight: 'bold',
    padding: 20,
    textAlign: 'center',
    color: '#333',
  },
  progress: {
    marginHorizontal: 20,
    marginBottom: 20,
  },
  question: {
    backgroundColor: 'white',
    padding: 15,
    marginHorizontal: 15,
    marginBottom: 15,
    borderRadius: 8,
  },
  questionText: {
    fontSize: 16,
    fontWeight: '600',
    marginBottom: 15,
    color: '#333',
  },
  input: {
    borderWidth: 1,
    borderColor: '#ddd',
    borderRadius: 8,
    padding: 10,
  },
  textarea: {
    borderWidth: 1,
    borderColor: '#ddd',
    borderRadius: 8,
    padding: 10,
    minHeight: 100,
  },
  radio: {
    marginBottom: 10,
  },
  submitButton: {
    backgroundColor: '#007AFF',
    padding: 15,
    borderRadius: 8,
    marginHorizontal: 15,
    marginBottom: 30,
  },
  submitButtonText: {
    color: 'white',
    fontSize: 16,
    fontWeight: 'bold',
    textAlign: 'center',
  },
});
```

---

## Consejos para Usar los Ejemplos

1. **Importa los iconos**: La mayoría de ejemplos usan `react-native-vector-icons`. Instálalo con:
   ```bash
   npm install react-native-vector-icons
   ```

2. **Personaliza los estilos**: Los estilos de ejemplo son un punto de partida. Modifícalos según tu diseño.

3. **Maneja el estado**: Los ejemplos usan `useState` de React. Considera usar Redux o Context para estado global.

4. **Valida los formularios**: Agrega validación más robusta para aplicaciones en producción.

5. **Optimiza las imágenes**: Usa imágenes optimizadas y considera lazy loading para mejores performances.

## Más Ejemplos

Para más ejemplos y casos de uso, visita:
- [Aplicación de ejemplo](../../example/)
- [Tests unitarios](../../udev_ultime_native/src/__tests__/)
- [Repositorio GitHub](https://github.com/Urpirio/udev_ultime_native)
