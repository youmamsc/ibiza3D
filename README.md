# IBIZA 3D — demo interactiva

Un prototipo original de explorador 3D de la isla de Ibiza, inspirado **en la idea** de geneva3d.ch (no copia código ni activos visuales del sitio original).

## Abrir

1. Abre `index.html` en Chrome, Safari, Edge o Firefox actualizado. Necesita Internet y WebGL.
2. Si el navegador limita las peticiones de archivos locales, ejecuta desde esta carpeta:

   ```bash
   python -m http.server 8080
   ```

   Visita `http://localhost:8080`.
3. Para publicarlo gratis, sube `index.html` a un repositorio público y activa GitHub Pages (raíz de la rama principal). No necesita compilación ni clave de mapas.

## Funcionalidad incluida

- Cartografía vectorial de Ibiza, con navegación por mouse y pantalla táctil.
- Edificios en 3D cuando se acerca el zoom a zonas urbanas (OpenFreeMap, basado en OSM).
- Relieve de la isla en 3D (raster DEM Terrarium AWS/Mapzen).
- 10 lugares emblemáticos con cámara programada, marcadores y ventanas explicativas.
- Buscar lugares, filtros, selección de estilos, vista 2D/3D, noche visual y controles de capas.
- Meteorología **actual** para Eivissa mediante Open-Meteo, únicamente cuando la petición responde con éxito.

## Limitaciones, importantes

- **No es aún una réplica completa de Genève 3D**: no hay transporte en tiempo real, vuelos, barcos AIS, reconstrucción histórica, texturas fotorrealistas, edificios fotogramétricos ni modelos 3D detallados de monumentos.
- Los edificios se extruyen a partir de OSM; donde faltan alturas se muestra una aproximación. El relieve usa un conjunto de elevaciones global, no el LiDAR balear de máxima resolución.
- El modo noche es un filtro visual; no corresponde al cálculo astronómico preciso del sol.
- Se cargan cartografía, DEM y meteo desde servicios de terceros en tiempo real. El prototipo depende de su disponibilidad y de sus condiciones de uso.
- Los diez puntos se han introducido como referencias geográficas orientativas, no como inventario exhaustivo de destinos.
- Antes de ponerlo en producción a gran escala, revisar las condiciones de uso y la atribución de cada proveedor y evaluar el alojamiento de teselas propio.
- Esta entrega no se ha validado end-to-end con redes externas, dado que el entorno de desarrollo no puede contactar directamente con dichos servicios.

## Fuentes y atribuciones

- [MapLibre GL JS](https://maplibre.org/maplibre-gl-js/docs/) (licencia BSD-3-Clause)
- [OpenFreeMap](https://openfreemap.org/), datos [© colaboradores de OpenStreetMap](https://www.openstreetmap.org/copyright)
- [Mapzen / AWS Terrain Tiles](https://registry.opendata.aws/terrain-tiles/) (las fuentes DEM originales tienen sus propias atribuciones)
- [Open-Meteo](https://open-meteo.com/)
- Datasets para una segunda fase: [PNOA LiDAR](https://pnoa.ign.es/pnoa-lidar/productos-a-descarga), [IDEIB Cartografía Balear](https://ideib.caib.es/geoserveis/rest/services/public/2021BTIB5000/MapServer).

## Próxima fase sugerida

1. Sustituir DEM global por datos PNOA-LiDAR/IDEIB procesados en mosaicos optimizados.
2. Integrar edificios oficiales con alturas verificadas, y desarrollar modelos de Dalt Vila.
3. Añadir vuelos OpenSky solo a través de un backend/cache con credenciales y límites correctos.
4. Añadir puertos, rutas de autobús y barcos únicamente donde existan feeds legalmente accesibles y verificables.
5. Optimizar móviles, SEO, analítica consentida si se requiere y despliegue automatizado GitHub Pages.