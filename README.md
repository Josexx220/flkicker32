# FLKicker 0.7 — 32 bits

Cliente de Kick para Tiny Core / FLinux de 32 bits. Escrito en C++ con FLTK.

## Cómo funciona

FLKicker se conecta a la API pública de Kick sin necesidad de cuenta:

- **Canales en vivo**: consulta `api.kick.com` para listar los directos activos.
- **Búsqueda**: filtra canales por nombre mientras escribes (hasta 10 sugerencias).
- **Verificación por nombre exacto**: con Enter comprueba si un canal existe aunque no esté en las sugerencias.
- **Reproducción**: al reproducir, refresca el `playback_url` con token, obtiene el `master.m3u8` y lo pasa por `ffmpeg` → `mplayer` (con `-zoom` para pantalla completa).
- **Favoritos**: guarda tus canales con 👍 en `~/.flkickerrc`.
- **Punto rojo**: en la búsqueda, marca los canales que están apagados.
- **Spinner verde**: la K del logo gira mientras carga datos.
- **Modo claro/oscuro**: cambia el tema de la interfaz.
- **Config remota**: descarga configuración firmada con Ed25519.

### Dependencias

```
curl.tcz
json-c.tcz
mplayer-cli.tcz
ffmpeg4.tcz
libEGL.tcz
openssl.tcz
```

## Instalación en FLinux 32 bits

1. Descarga los 3 archivos:
   - `flkicker32.tcz`
   - `flkicker32.tcz.dep`
   - `flkicker32.tcz.md5.txt`

2. Verifica la integridad:
   ```
   md5sum -c flkicker32.tcz.md5.txt
   ```

3. Copia a tu directorio tce (para que persista):
   ```
   cp flkicker32.tcz /etc/sysconfig/tcedir/optional/
   ```

4. Instala:
   ```
   tce-load -i flkicker32.tcz
   ```

5. Ejecuta:
   ```
   flkicker
   ```

6. Para el icono en el wbar:
   ```
   sudo wbar_update.sh flkicker
   ```

## Código fuente

`flkicker.cpp` — fuente completo en C++/FLTK (versión 0.7).

## Licencia

GPL-3.0. Cliente no oficial, sin afiliación con Kick.
