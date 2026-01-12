# 🌤️ App Clima

Aplicación web moderna de pronóstico del clima que proporciona información meteorológica en tiempo real utilizando API de servicios climáticos. Diseñada con una interfaz intuitiva y responsive para consultar el clima actual y pronósticos de cualquier ubicación del mundo.

![Estado del Proyecto](https://img.shields.io/badge/estado-activo-success.svg)
![Licencia](https://img.shields.io/badge/licencia-MIT-blue.svg)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)

---


## 🎯 Descripción

App Clima es una aplicación web que permite a los usuarios consultar el clima actual y pronósticos meteorológicos de cualquier ciudad del mundo. Utiliza servicios de API externos para obtener datos precisos y actualizados, presentándolos en una interfaz limpia y fácil de usar.

---


## ✨ Características

- 🌍 **Búsqueda Global**: Consulta el clima de cualquier ciudad del mundo
- 🌡️ **Temperatura en Tiempo Real**: Muestra temperatura actual, máxima y mínima
- 💧 **Información Detallada**: Incluye humedad, velocidad del viento y condiciones atmosféricas
- 🔍 **Geolocalización**: Detecta automáticamente tu ubicación para mostrar el clima local
- 📱 **Diseño Responsive**: Interfaz adaptada para dispositivos móviles, tablets y desktop
- 🎨 **Interfaz Moderna**: Diseño visual atractivo con animaciones y transiciones
- 🌈 **Iconos Dinámicos**: Representaciones visuales del clima según las condiciones
- 🔄 **Actualizaciones Automáticas**: Datos meteorológicos actualizados en tiempo real
- 🌓 **Formato 12/24 Horas**: Visualización personalizable del tiempo

---


## 🛠️ Tecnologías Utilizadas

- **HTML5**: Estructura semántica y moderna
- **CSS3**: Estilos avanzados con Flexbox/Grid y animaciones
- **JavaScript ES6+**: Lógica de aplicación y manejo de APIs
- **Fetch API**: Peticiones HTTP asíncronas
- **Geolocation API**: Detección de ubicación del usuario
- **OpenWeatherMap API**: Servicio de datos meteorológicos (o API similar)
- **Responsive Design**: Mobile-first approach

---


## 📋 Requisitos Previos

Para ejecutar este proyecto necesitas:

- Un navegador web moderno (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)
- Conexión a Internet (para consultas a la API)
- Clave API de OpenWeatherMap (o servicio meteorológico utilizado)
- Opcional: Servidor local para desarrollo (Live Server, http-server, etc.)

---


## 🚀 Instalación y Configuración

### Paso 1: Clonar el Repositorio

```bash
# Clonar el repositorio
git clone https://github.com/dulcemariaom1987/app-clima.git

# Navegar al directorio del proyecto
cd app-clima
```

### Paso 2: Obtener API Key

1. Registrarse en [OpenWeatherMap](https://openweathermap.org/api) (o servicio utilizado)
2. Obtener tu API Key gratuita
3. Copiar la clave API

### Paso 3: Configurar la API Key

Abre el archivo JavaScript y reemplaza `YOUR_API_KEY` con tu clave:

```javascript
const API_KEY = 'tu_clave_api_aqui';
const API_URL = 'https://api.openweathermap.org/data/2.5/weather';
```

### Paso 4: Ejecutar la Aplicación

**Opción A - Abrir directamente:**
```bash
# En Windows
start index.html

# En macOS
open index.html

# En Linux
xdg-open index.html
```

**Opción B - Con servidor local (recomendado):**
```bash
# Usando Python 3
python -m http.server 8000

# Usando Node.js (http-server)
npx http-server

# Usando PHP
php -S localhost:8000

# Luego abre http://localhost:8000 en tu navegador
```

---


## 📁 Estructura del Proyecto

```
app-clima/
│
├── index.html              # Página principal de la aplicación
├── css/
│   └── styles.css         # Estilos de la aplicación (si está separado)
├── js/
│   ├── app.js             # Lógica principal
│   ├── api.js             # Manejo de peticiones API
│   └── utils.js           # Funciones auxiliares
├── assets/
│   ├── icons/             # Iconos del clima
│   └── images/            # Imágenes de fondo
├── README.md              # Documentación del proyecto
```

---


## 💡 Uso de la Aplicación

### Buscar Clima por Ciudad

1. Ingresa el nombre de una ciudad en el campo de búsqueda
2. Presiona Enter o haz clic en el botón de búsqueda
3. La aplicación mostrará el clima actual de esa ubicación

### Usar Geolocalización

1. Haz clic en el botón de ubicación actual
2. Permite el acceso a tu ubicación cuando el navegador lo solicite
3. El clima de tu ubicación se mostrará automáticamente

### Interpretar la Información

La aplicación muestra:
- **Temperatura actual**: Temperatura en grados Celsius/Fahrenheit
- **Sensación térmica**: Cómo se siente realmente la temperatura
- **Condiciones**: Descripción del clima (soleado, nublado, lluvioso, etc.)
- **Humedad**: Porcentaje de humedad relativa
- **Viento**: Velocidad y dirección del viento
- **Presión atmosférica**: En milibares o pulgadas de mercurio
- **Visibilidad**: Distancia de visibilidad actual

---


## 🎨 Características Técnicas

### Integración con API

```javascript
// Ejemplo de llamada a la API
async function obtenerClima(ciudad) {
  try {
    const response = await fetch(
      `${API_URL}?q=${ciudad}&appid=${API_KEY}&units=metric&lang=es`
    );
    
    if (!response.ok) {
      throw new Error('Ciudad no encontrada');
    }
    
    const data = await response.json();
    mostrarClima(data);
  } catch (error) {
    mostrarError(error.message);
  }
}
```

### Geolocalización

```javascript
// Obtener ubicación del usuario
function obtenerUbicacion() {
  if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(
      (position) => {
        const { latitude, longitude } = position.coords;
        obtenerClimaPorCoordenadas(latitude, longitude);
      },
      (error) => {
        console.error('Error al obtener ubicación:', error);
      }
    );
  }
}
```

---


### Manejo de Errores

La aplicación maneja diversos escenarios de error:
- Ciudad no encontrada
- Error de red
- Límite de peticiones API excedido
- Permisos de geolocalización denegados
- Timeout de peticiones

---


## 🔧 Personalización

### Cambiar Unidades de Temperatura

Modifica el parámetro `units` en la petición API:

```javascript
// Celsius (métrico)
units=metric

// Fahrenheit (imperial)
units=imperial

// Kelvin (estándar)
units=standard
```

### Personalizar Estilos

Edita las variables CSS para cambiar el tema:

```css
:root {
  --color-primario: #2196F3;
  --color-secundario: #1976D2;
  --color-fondo: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  --color-texto: #333333;
  --border-radius: 15px;
  --sombra: 0 10px 30px rgba(0, 0, 0, 0.2);
}
```

### Agregar Idiomas

La mayoría de APIs soportan múltiples idiomas:

```javascript
// Español
lang=es

// Inglés
lang=en

// Francés
lang=fr
```

---


## 🌐 APIs Recomendadas

### OpenWeatherMap
- **URL**: https://openweathermap.org/api
- **Plan gratuito**: 60 llamadas/minuto
- **Datos**: Clima actual, pronósticos, históricos

### WeatherAPI
- **URL**: https://www.weatherapi.com
- **Plan gratuito**: 1 millón llamadas/mes
- **Datos**: Clima en tiempo real, pronósticos, astronomía

### AccuWeather
- **URL**: https://developer.accuweather.com
- **Plan gratuito**: 50 llamadas/día
- **Datos**: Alta precisión en pronósticos

---


## 🐛 Solución de Problemas

### La aplicación no muestra datos

- Verifica que tu API Key sea válida y esté correctamente configurada
- Asegúrate de tener conexión a Internet
- Revisa la consola del navegador para errores
- Verifica que no hayas excedido el límite de peticiones de tu plan

### Error de CORS

Si ejecutas desde `file://`, usa un servidor local:

```bash
# Instalar live-server globalmente
npm install -g live-server

# Ejecutar en el directorio del proyecto
live-server
```

### Geolocalización no funciona

- Asegúrate de usar HTTPS o localhost
- Verifica que el navegador tenga permisos de ubicación
- Comprueba la configuración de privacidad del navegador

---


## 📊 Límites de la API Gratuita

**OpenWeatherMap (Free Plan):**
- 60 llamadas por minuto
- 1,000,000 llamadas por mes
- Datos actualizados cada 2 horas
- Pronóstico de 5 días disponible

---

## 📝 Roadmap

Funcionalidades planeadas para futuras versiones:

- [ ] Pronóstico extendido de 7-14 días
- [ ] Gráficos de temperatura y precipitación
- [ ] Alertas meteorológicas y notificaciones
- [ ] Favoritos de ubicaciones
- [ ] Comparación de clima entre ciudades
- [ ] Mapas interactivos del clima
- [ ] Widget de clima para escritorio
- [ ] Modo oscuro/claro automático
- [ ] Soporte para múltiples idiomas
- [ ] Historial de búsquedas
- [ ] Exportar datos climáticos
- [ ] Integración con calendarios
- [ ] PWA (Progressive Web App)

---


## 🔒 Seguridad

- Nunca expongas tu API Key en el código del frontend
- Considera usar un backend proxy para ocultar credenciales
- Implementa rate limiting para prevenir abuso
- Valida y sanitiza todas las entradas de usuario

### Recomendación de Seguridad

Para producción, crea un backend simple:

```javascript
// backend/server.js (Node.js ejemplo)
const express = require('express');
const axios = require('axios');
const app = express();

app.get('/api/weather/:city', async (req, res) => {
  try {
    const response = await axios.get(
      `https://api.openweathermap.org/data/2.5/weather`,
      {
        params: {
          q: req.params.city,
          appid: process.env.API_KEY, // API Key en variable de entorno
          units: 'metric',
          lang: 'es'
        }
      }
    );
    res.json(response.data);
  } catch (error) {
    res.status(500).json({ error: 'Error al obtener clima' });
  }
});

app.listen(3000);
```

---


## 📱 Responsive Design

La aplicación está optimizada para:

- **Móviles**: 320px - 480px
- **Tablets**: 481px - 768px
- **Laptops**: 769px - 1024px
- **Desktop**: 1025px+

---


## ⚡ Rendimiento

Optimizaciones implementadas:

- Lazy loading de imágenes
- Debouncing en búsquedas
- Cache de peticiones API
- Minimización de reflows/repaints
- Carga asíncrona de recursos
- Compresión de assets

---


## 📄 Licencia

Este proyecto está bajo la Licencia MIT. Consulta el archivo `LICENSE` para más detalles.

```
MIT License

Copyright (c) 2025 Dulce María

Se concede permiso para usar, copiar, modificar y distribuir este software...
```

---


## 👩‍💻 Autora

**Dulce María**

- GitHub: [@dulcemariaom1987](https://github.com/dulcemariaom1987)
- Proyecto: [app-clima](https://github.com/dulcemariaom1987/app-clima)
- Email: [Contacto disponible en GitHub]

---


## 🙏 Agradecimientos

- [OpenWeatherMap](https://openweathermap.org) por proporcionar la API de datos meteorológicos
- Comunidad de desarrolladores por las mejores prácticas
- Diseñadores que inspiran interfaces modernas de clima
- Todos los contribuidores que mejoran este proyecto

---


## 📚 Recursos Adicionales

### Documentación Útil

- [OpenWeatherMap API Docs](https://openweathermap.org/api)
- [MDN Geolocation API](https://developer.mozilla.org/es/docs/Web/API/Geolocation_API)
- [Fetch API Guide](https://developer.mozilla.org/es/docs/Web/API/Fetch_API)
- [CSS Grid Layout](https://css-tricks.com/snippets/css/complete-guide-grid/)

---


### Tutoriales Relacionados

- Cómo consumir APIs REST con JavaScript
- Implementar geolocalización en aplicaciones web
- Diseño responsive con CSS Grid y Flexbox
- Manejo de errores en JavaScript asíncrono

---


## 📞 Soporte

Si tienes preguntas o necesitas ayuda:

- 📝 Abre un [Issue](https://github.com/dulcemariaom1987/app-clima/issues) en GitHub
- 💬 Consulta la documentación de la API utilizada
- 🔍 Revisa los issues existentes para ver si tu pregunta ya fue respondida
- 📧 Contacta a través de GitHub para consultas específicas

---


## 🌟 Insignias de Calidad

![Validación HTML](https://img.shields.io/badge/HTML-Válido-brightgreen)
![Validación CSS](https://img.shields.io/badge/CSS-Válido-brightgreen)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow)
![Responsive](https://img.shields.io/badge/Responsive-Sí-blue)
![Accesibilidad](https://img.shields.io/badge/A11y-AAA-success)

---

⭐ Si este proyecto te resulta útil, considera darle una estrella en GitHub

🌤️ **¡Consulta el clima y planifica tu día con App Clima!**

**Desarrollado con ❤️ por Dulce María**
