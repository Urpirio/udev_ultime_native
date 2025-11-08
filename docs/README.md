# Documentación de udev_ultime_native

Bienvenido a la documentación completa de **udev_ultime_native**, una librería de componentes UI optimizada para React Native.

## 📚 Índice de Documentación

### Guías de Usuario

#### [Guía de Inicio Rápido](./GETTING_STARTED.md)
Aprende a instalar y configurar la librería en tu proyecto React Native. Incluye:
- Requisitos previos
- Instalación paso a paso
- Configuración de dependencias
- Tu primer componente
- Ejemplo de formulario completo

#### [Referencia Rápida](./QUICK_REFERENCE.md)
Guía de consulta rápida con ejemplos concisos de todos los componentes:
- Sintaxis básica de cada componente
- Props más comunes
- Patrones de uso frecuentes
- Tips de rendimiento
- Validación de formularios

#### [Ejemplos de Uso](./examples/README.md)
Colección completa de ejemplos prácticos para casos de uso reales:
- Formulario de login
- Formulario de registro
- Perfil de usuario
- Pantalla con navegación
- Dashboard con progreso
- Configuración de app
- Galería de tarjetas
- Formulario de encuesta

#### [Referencia de API](./api/README.md)
Documentación completa de todos los componentes disponibles:
- **Componentes de Entrada**: InputText, InputPassword, InputTextarea, DropDown
- **Componentes de Acción**: Button, ButtonBar, FloatingButton
- **Componentes de Selección**: RadioButton
- **Componentes de Visualización**: ProgressBar, Card_Simple, TabPanel
- **Componentes de Layout**: LayoutScreen

### Guías Técnicas

#### [Arquitectura del Proyecto](./ARCHITECTURE.md)
Comprende la estructura interna y las decisiones de diseño:
- Estructura del proyecto
- Principios de diseño
- Categorías de componentes
- Gestión de estado
- Patrones de diseño utilizados
- Convenciones de código
- Extensibilidad

#### [Solución de Problemas](./TROUBLESHOOTING.md)
Guía para resolver problemas comunes:
- Problemas de instalación
- Problemas de configuración
- Problemas de componentes específicos
- Problemas de rendimiento
- Problemas de TypeScript
- Problemas de compilación
- Reporte de bugs

## 🚀 Inicio Rápido

### Instalación

```bash
npm install udev_ultime_native react-native-reanimated react-native-safe-area-context
```

### Uso Básico

```javascript
import { Button, InputText } from 'udev_ultime_native';

<InputText
  placeholder="Tu nombre"
  value={name}
  onChangeText={setName}
/>

<Button
  title="Enviar"
  onPress={() => console.log('Pressed')}
  type_button="TouchableOpacity"
/>
```

## 📖 Recursos Adicionales

### Documentación del Proyecto

- [README Principal](../README.md) - Visión general del proyecto
- [Changelog](../CHANGELOG.md) - Historial de cambios y versiones
- [Guía de Contribución](../udev_ultime_native/CONTRIBUTING.md) - Cómo contribuir al proyecto
- [Código de Conducta](../udev_ultime_native/CODE_OF_CONDUCT.md) - Normas de la comunidad
- [Licencia](../LICENSE) - Términos de uso (Apache 2.0)

### Enlaces Externos

- [Repositorio en GitHub](https://github.com/Urpirio/Udev_Native)
- [NPM Package](https://www.npmjs.com/package/udev_ultime_native)
- [React Native Docs](https://reactnative.dev/)
- [react-native-reanimated](https://docs.swmansion.com/react-native-reanimated/)
- [react-native-safe-area-context](https://github.com/th3rdwave/react-native-safe-area-context)

## 🎯 Componentes Principales

### Componentes de Entrada
- **InputText** - Campo de texto con iconos y validación
- **InputPassword** - Campo de contraseña con toggle de visibilidad
- **InputTextarea** - Área de texto multilínea
- **DropDown** - Menú desplegable con opciones

### Componentes de Acción
- **Button** - Botón personalizable con múltiples estilos
- **ButtonBar** - Barra de botones para navegación
- **FloatingButton** - Botón flotante con menú expandible

### Componentes de Visualización
- **ProgressBar** - Barra de progreso con estados coloreados
- **Card_Simple** - Tarjeta con imagen, título y descripción
- **TabPanel** - Panel de pestañas con contenido dinámico
- **RadioButton** - Botón de opción para selección única

### Sistema de Layout
- **LayoutScreen** - Sistema completo de layout con topBar, bottomBar y bodyScreen

## 💡 Características Principales

- ✅ **TypeScript**: Tipado fuerte para todas las props
- ✅ **Personalizable**: Estilos configurables en cada componente
- ✅ **Optimizado**: Rendimiento optimizado para móviles
- ✅ **Accesible**: Soporte completo de accesibilidad
- ✅ **Animaciones**: Usando react-native-reanimated
- ✅ **Documentación**: Completa y detallada

## 🛠️ Configuración Recomendada

### Editor de Código
- VSCode con extensiones:
  - ES7+ React/Redux/React-Native snippets
  - React Native Tools
  - TypeScript Hero

### Desarrollo
```bash
# Instalar dependencias
npm install

# Iniciar Metro Bundler
npm start

# Ejecutar en iOS
npm run ios

# Ejecutar en Android
npm run android
```

## 📱 Compatibilidad

- React Native >= 0.70
- iOS >= 12.0
- Android >= API 21 (Android 5.0)
- TypeScript >= 4.0

## 🤝 Contribuir

¿Quieres contribuir al proyecto? ¡Genial! Consulta nuestra [Guía de Contribución](../udev_ultime_native/CONTRIBUTING.md).

### Formas de Contribuir
- Reportar bugs
- Sugerir nuevas funcionalidades
- Mejorar la documentación - ver [Guía para Contribuir a la Documentación](./CONTRIBUTING_DOCS.md)
- Enviar pull requests
- Compartir ejemplos de uso

## 📝 Licencia

Este proyecto está bajo la licencia Apache 2.0. Ver [LICENSE](../LICENSE) para más detalles.

## 👤 Autor

**UrpirioDev**
- GitHub: [@Urpirio](https://github.com/Urpirio)
- NPM: [urpiriodev](https://www.npmjs.com/~urpiriodev)

## 🌟 Soporte

Si encuentras útil esta librería, considera:
- Darle una ⭐ en [GitHub](https://github.com/Urpirio/Udev_Native)
- Compartirla con otros desarrolladores
- Contribuir al proyecto
- Reportar bugs y sugerir mejoras

---

**Última actualización**: 2024-11-08

¿Tienes preguntas? Abre un [issue en GitHub](https://github.com/Urpirio/Udev_Native/issues).
