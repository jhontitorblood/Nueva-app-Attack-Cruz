# Nueva-app-Attack-Cruz ⚔️

RPG de hábitos diarios ambientado en Santa Cruz de la Sierra. Beta 0.1.0.

## Subir a GitHub y obtener la APK
1. Crea en github.com un repositorio llamado `Nueva-app-Attack-Cruz` (vacío, sin README).
2. Desde una computadora, dentro de la carpeta descomprimida:
   ```bash
   git init
   git add -A
   git commit -m "Beta 0.1.0"
   git branch -M main
   git remote add origin https://github.com/TU_USUARIO/Nueva-app-Attack-Cruz.git
   git push -u origin main
   ```
   Hazlo con git (o GitHub Desktop): al arrastrar archivos en la web se pueden perder carpetas ocultas como `.github`.
3. Abre la pestaña **Actions** y espera a que termine "Compilar APK".
4. En el celular, entra a **Releases** del repositorio y descarga `AttackCruz-beta.apk`.
   Si el repositorio es privado, inicia sesión en GitHub.
5. Ábrela y permite "instalar apps de esta fuente". Acepta el permiso de notificaciones.

## Reglas
- Nivel 1: 100 XP. Cada nivel siguiente pide 50% más (100, 150, 225, 338...). La barra se reinicia y conserva el sobrante.
- Misiones: Fácil 10, Normal 20, Difícil 35, Épica 50 XP. Se cumplen una vez por día, solo en su día programado.
- Cada nivel da 5 puntos de estadística.
- Jefe semanal: vida = 200 + 40 × tu nivel al empezar la semana (lunes). La XP de misiones le quita vida.
  Al vencerlo: 300–900 de oro y 50–150 de XP al azar.
- El oro sale de los jefes y de conquistar puntos del mapa.
- El mapa es esquemático, con posiciones aproximadas. Los puntos se conquistan en orden.

## Desarrollo
```bash
npm ci
npm test
npx cap sync android
```
| Archivo | Contenido |
|---|---|
| `www/js/logic.js` | Reglas, jefes, tienda, cartas y puntos del mapa |
| `www/js/app.js` | Pantallas, guardado y alertas |
| `www/js/art.js` | Jefes, mapa y música generados por código |

## Limitaciones de la beta
- El progreso se guarda solo en el celular. Usa **Opciones → Copiar respaldo**.
- Las alertas se programan para los próximos 14 días (máximo 200) y se renuevan al abrir la app.
  Android puede retrasarlas. Para mayor puntualidad, permite "Alarmas y recordatorios" y quita la restricción de batería.
- El cumplimiento de tareas se basa en tu honestidad; cambiar el reloj no se bloquea por completo.
- `signing/beta-debug.keystore` usa la clave pública estándar de depuración. Sirve solo para la beta.
  Para publicar en Play Store se necesita una llave privada nueva, fuera del repositorio.
