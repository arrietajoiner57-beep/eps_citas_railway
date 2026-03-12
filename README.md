# EPS Citas App — Deploy en Railway

## Pasos para subir a Railway

### 1. Crear repositorio en GitHub
```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/TU_USUARIO/eps-citas-app.git
git push -u origin main
```

### 2. Crear proyecto en Railway
1. Ve a [railway.app](https://railway.app) e inicia sesión.
2. Haz clic en **New Project → Deploy from GitHub repo**.
3. Selecciona el repositorio `eps-citas-app`.

### 3. Agregar base de datos MySQL
1. Dentro del proyecto en Railway, haz clic en **New → Database → MySQL**.
2. Railway creará automáticamente las variables de entorno:
   - `MYSQLHOST`, `MYSQLUSER`, `MYSQLPASSWORD`, `MYSQLDATABASE`, `MYSQLPORT`

### 4. Conectar la app a la base de datos
1. Ve al servicio de tu app (el que viene del repo de GitHub).
2. En la pestaña **Variables**, añade referencias a las variables del servicio MySQL.
3. Agrega además: `SECRET_KEY` → un valor seguro único.

### 5. Inicializar la base de datos
Ejecuta el contenido de `eps_citas_workbench.sql` en la base de datos de Railway usando el panel **Data** del servicio MySQL o un cliente como TablePlus/DBeaver.

### Variables de entorno requeridas
| Variable       | Descripción                    |
|----------------|--------------------------------|
| MYSQLHOST      | Host de la base de datos       |
| MYSQLUSER      | Usuario MySQL                  |
| MYSQLPASSWORD  | Contraseña MySQL               |
| MYSQLDATABASE  | Nombre de la base de datos     |
| MYSQLPORT      | Puerto MySQL (por defecto 3306)|
| SECRET_KEY     | Clave secreta de Flask         |

> Railway inyecta `PORT` automáticamente — no necesitas configurarla.
