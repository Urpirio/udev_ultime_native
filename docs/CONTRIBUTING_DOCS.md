# Guía para Contribuir a la Documentación

¡Gracias por tu interés en mejorar la documentación de udev_ultime_native! Esta guía te ayudará a contribuir de manera efectiva.

## 📝 Tipos de Contribuciones

Puedes contribuir a la documentación de las siguientes formas:

1. **Corregir errores**: Typos, errores gramaticales, código incorrecto
2. **Mejorar explicaciones**: Hacer más claras las descripciones existentes
3. **Agregar ejemplos**: Nuevos casos de uso o ejemplos más completos
4. **Traducir**: Ayudar con traducciones a otros idiomas
5. **Actualizar**: Mantener la documentación al día con nuevas versiones
6. **Crear tutoriales**: Guías paso a paso para casos específicos

## 🗂️ Estructura de la Documentación

```
docs/
├── README.md                    # Índice principal de documentación
├── GETTING_STARTED.md          # Guía de inicio rápido
├── QUICK_REFERENCE.md          # Referencia rápida
├── ARCHITECTURE.md             # Arquitectura del proyecto
├── TROUBLESHOOTING.md          # Solución de problemas
├── CONTRIBUTING_DOCS.md        # Esta guía
├── api/
│   └── README.md               # Referencia completa de API
└── examples/
    └── README.md               # Ejemplos de uso
```

## ✍️ Estilo de Escritura

### Idioma

- **Documentación principal**: Español
- **Código y ejemplos**: Comentarios en español, código en inglés
- **Nombres de variables**: En inglés (convención de programación)

### Tono

- **Claro y directo**: Evita ambigüedades
- **Amigable**: Usa un tono accesible pero profesional
- **Instructivo**: Proporciona pasos claros y concretos
- **Inclusivo**: Usa lenguaje neutral y accesible

### Formato

#### Títulos

```markdown
# Título Principal (H1)
## Sección (H2)
### Subsección (H3)
#### Detalles (H4)
```

#### Código

Usa bloques de código con el lenguaje especificado:

```markdown
\```javascript
// Tu código aquí
const example = 'hello';
\```
```

#### Énfasis

- **Negrita** para términos importantes: `**importante**`
- *Cursiva* para énfasis suave: `*énfasis*`
- `Código inline` para código: `` `código` ``

#### Listas

```markdown
- Lista no ordenada
- Otro elemento

1. Lista ordenada
2. Segundo elemento
```

#### Tablas

```markdown
| Prop | Tipo | Descripción |
|------|------|-------------|
| value | string | Valor del campo |
```

#### Enlaces

```markdown
[Texto del enlace](./ruta/al/archivo.md)
```

## 📋 Plantillas

### Documentación de Componente

```markdown
## NombreComponente

Breve descripción del componente y su propósito.

### Props

| Prop | Tipo | Requerido | Descripción |
|------|------|-----------|-------------|
| propName | tipo | Sí/No | Descripción detallada |

### Características

- Característica 1
- Característica 2

### Ejemplo Básico

\```javascript
import { NombreComponente } from 'udev_ultime_native';

<NombreComponente
  prop1="valor1"
  prop2={valor2}
/>
\```

### Ejemplo Avanzado

\```javascript
// Ejemplo más complejo
\```

### Notas

Información adicional importante.
```

### Ejemplo de Uso

```markdown
## Título del Ejemplo

Descripción breve del caso de uso.

\```javascript
import React, { useState } from 'react';
import { View, StyleSheet } from 'react-native';
import { Component1, Component2 } from 'udev_ultime_native';

export default function ExampleScreen() {
  const [state, setState] = useState('');

  return (
    <View style={styles.container}>
      <Component1 />
      <Component2 />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
  },
});
\```

### Explicación

Descripción detallada del ejemplo.
```

## 🔍 Proceso de Revisión

### Antes de Enviar

1. **Lee la documentación existente** para mantener consistencia
2. **Verifica la ortografía y gramática**
3. **Prueba el código** de los ejemplos
4. **Revisa los enlaces** para asegurarte de que funcionan
5. **Usa un editor Markdown** para previsualizar

### Herramientas Útiles

- **Editor Markdown**: VSCode con extensión Markdown Preview
- **Corrector ortográfico**: LanguageTool o similar
- **Formateador**: Prettier para código

### Checklist de Calidad

- [ ] La ortografía y gramática son correctas
- [ ] El código de ejemplo funciona
- [ ] Los enlaces están correctos
- [ ] El formato Markdown es correcto
- [ ] La estructura sigue las convenciones existentes
- [ ] Se incluyen ejemplos cuando es apropiado
- [ ] Las imágenes (si las hay) tienen texto alternativo

## 🚀 Cómo Contribuir

### 1. Fork y Clone

```bash
# Fork el repositorio en GitHub
# Luego clona tu fork
git clone https://github.com/TU_USUARIO/udev_ultime_native.git
cd udev_ultime_native
```

### 2. Crea una Rama

```bash
git checkout -b docs/descripcion-del-cambio
```

Usa el prefijo `docs/` para cambios de documentación.

### 3. Haz tus Cambios

- Edita los archivos de documentación
- Agrega nuevos archivos si es necesario
- Actualiza el índice si agregas nuevas páginas

### 4. Previsualiza

Previsualiza tus cambios para asegurarte de que se ven bien:

- Usa la vista previa de Markdown de tu editor
- O usa una herramienta como `grip` para previsualizar GitHub Markdown

```bash
# Instalar grip
pip install grip

# Previsualizar
grip docs/README.md
```

### 5. Commit

```bash
git add docs/
git commit -m "docs: descripción clara del cambio"
```

Formato de mensajes de commit:
- `docs: agregar ejemplo de formulario de login`
- `docs: corregir typo en API reference`
- `docs: mejorar explicación de LayoutScreen`
- `docs: actualizar guía de instalación`

### 6. Push y Pull Request

```bash
git push origin docs/descripcion-del-cambio
```

Luego crea un Pull Request en GitHub con:

- **Título claro**: "docs: descripción del cambio"
- **Descripción detallada**: Qué cambios hiciste y por qué
- **Referencias**: Enlaces a issues relacionados si aplica

## 📐 Estándares de Código

### Ejemplos de Código

1. **Usa sintaxis moderna de JavaScript**:
```javascript
// ✅ Correcto
const [state, setState] = useState('');

// ❌ Incorrecto
var state = '';
```

2. **Incluye imports**:
```javascript
// ✅ Correcto
import React, { useState } from 'react';
import { View } from 'react-native';
import { Button } from 'udev_ultime_native';

// ❌ Incorrecto (sin imports)
<Button />
```

3. **Usa nombres descriptivos**:
```javascript
// ✅ Correcto
const [email, setEmail] = useState('');
const [password, setPassword] = useState('');

// ❌ Incorrecto
const [e, setE] = useState('');
const [p, setP] = useState('');
```

4. **Incluye estilos cuando sean relevantes**:
```javascript
// ✅ Correcto
<Button
  title="Enviar"
  style_button={styles.button}
/>

const styles = StyleSheet.create({
  button: {
    backgroundColor: 'blue',
    padding: 15,
  },
});
```

## 🐛 Reportar Problemas en la Documentación

Si encuentras un problema en la documentación pero no puedes arreglarlo tú mismo:

1. Abre un issue en GitHub
2. Usa el título: "docs: descripción del problema"
3. Incluye:
   - Qué documentación tiene el problema
   - Cuál es el problema específico
   - Sugerencias de mejora (opcional)

Ejemplo:

```
Título: docs: ejemplo de InputPassword no funciona

La documentación en docs/api/README.md muestra un ejemplo de InputPassword
que no funciona porque falta importar useState.

Ubicación: docs/api/README.md, línea 150

Sugerencia: Agregar el import de useState al inicio del ejemplo.
```

## ❓ Preguntas Frecuentes

### ¿Puedo contribuir si no sé programar?

¡Sí! Puedes contribuir de muchas formas:
- Corregir errores de ortografía
- Mejorar explicaciones
- Sugerir ejemplos
- Reportar problemas en la documentación

### ¿Qué pasa si mi inglés/español no es perfecto?

No te preocupes. Lo importante es el contenido. La comunidad ayudará a
pulir la redacción. ¡Lo importante es que contribuyas!

### ¿Puedo agregar documentación en otro idioma?

Sí, traducciones son bienvenidas. Contacta a los mantenedores para
coordinar la estructura de documentación multiidioma.

### ¿Cómo mantengo la consistencia con la documentación existente?

Lee varios documentos existentes para entender el estilo y estructura.
Sigue las plantillas proporcionadas en esta guía.

## 📞 Contacto

Si tienes preguntas sobre cómo contribuir a la documentación:

- Abre un issue en GitHub con la etiqueta `question`
- Revisa las discusiones existentes
- Consulta la [Guía de Contribución](../udev_ultime_native/CONTRIBUTING.md) general

## 🎉 Agradecimientos

Gracias por ayudar a mejorar la documentación de udev_ultime_native.
¡Tu contribución hace que la librería sea más accesible para todos!

---

**Última actualización**: 2025-01-18
