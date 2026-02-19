# Mi Perfil — Taller Básico de Laravel (UNAB)

Aplicación web desarrollada en **Laravel** que presenta un perfil personal estructurado en cuatro secciones: **Perfil**, **Intereses**, **Habilidades** y **Metas**. El proyecto utiliza rutas en `web.php`, vistas Blade y CSS propio sin dependencias externas como Bootstrap.

---

## Tabla de contenidos

- [Requisitos del sistema](#requisitos-del-sistema)
- [Instalación](#instalación)
  - [Opción A — Clonar con Git](#opción-a--clonar-con-git)
  - [Opción B — Descargar ZIP](#opción-b--descargar-zip)
- [Ejecución del proyecto](#ejecución-del-proyecto)
  - [Servidor integrado de Laravel (recomendado)](#servidor-integrado-de-laravel-recomendado)
  - [XAMPP / Apache (alternativa)](#xampp--apache-alternativa)
- [Rutas disponibles](#rutas-disponibles)
- [Estructura de archivos](#estructura-de-archivos)
- [Solución de problemas](#solución-de-problemas)
- [Autor](#autor)

---

## Requisitos del sistema

| Herramienta | Versión mínima | Notas |
|---|---|---|
| PHP | 8.1 | Incluir extensiones: `mbstring`, `xml`, `bcmath`, `curl`, `zip` |
| Composer | Cualquiera reciente | [getcomposer.org](https://getcomposer.org) |
| Servidor local | — | `php artisan serve` o XAMPP/WAMP/Laragon |
| Node.js + NPM | Cualquiera reciente | Opcional, solo si se usan assets compilados |
| Git | Cualquiera reciente | Opcional, solo para clonar el repositorio |

---

## Instalación

### Opción A — Clonar con Git
```bash
# 1. Clonar el repositorio
git clone <URL_DEL_REPOSITORIO>

# 2. Entrar a la carpeta del proyecto
cd nombre-del-proyecto

# 3. Instalar dependencias de PHP
composer install

# 4. Crear el archivo de entorno
cp .env.example .env          # Linux / macOS / Git Bash
# copy .env.example .env      # Windows CMD
# Copy-Item .env.example .env # Windows PowerShell

# 5. Generar la clave de la aplicación
php artisan key:generate
```

### Opción B — Descargar ZIP

1. Descarga el proyecto como archivo `.zip` desde el repositorio.
2. Descomprime el contenido en una carpeta local (por ejemplo: `Documentos/mi-perfil-laravel/`).
3. Abre una terminal dentro de esa carpeta y ejecuta:
```bash
composer install

cp .env.example .env          # Linux / macOS / Git Bash
# copy .env.example .env      # Windows CMD
# Copy-Item .env.example .env # Windows PowerShell

php artisan key:generate
```

#### Instalación de PHP en Linux (Ubuntu / Debian)

Si aún no tienes PHP instalado en tu sistema:
```bash
sudo apt update
sudo apt install php php-cli php-mbstring php-xml php-bcmath php-curl php-zip unzip curl

# Instalar Composer
curl -sS https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/composer
sudo chmod +x /usr/local/bin/composer
```

En Windows se recomienda instalar PHP mediante [XAMPP](https://www.apachefriends.org) o [Laragon](https://laragon.org), y Composer desde [getcomposer.org/Composer-Setup.exe](https://getcomposer.org/Composer-Setup.exe).

---

## Ejecución del proyecto

### Servidor integrado de Laravel (recomendado)
```bash
php artisan serve
```

La aplicación quedará disponible en `http://127.0.0.1:8000`. Para detener el servidor presiona `Ctrl + C`.

### XAMPP / Apache (alternativa)

1. Coloca la carpeta del proyecto dentro de `htdocs/` (XAMPP) o el directorio raíz de tu servidor.
2. Configura el servidor para que el *document root* apunte a `nombre-del-proyecto/public/`.
3. Accede desde el navegador:
```
http://localhost/nombre-del-proyecto/public/perfil
```

---

## Rutas disponibles

| Ruta | Vista Blade | Descripción |
|---|---|---|
| `/perfil` | `perfil.blade.php` | Información general del perfil |
| `/perfil/intereses` | `intereses.blade.php` | Intereses y pasatiempos |
| `/perfil/habilidades` | `habilidades.blade.php` | Habilidades técnicas y blandas |
| `/perfil/metas` | `metas.blade.php` | Metas a corto y largo plazo |

---

## Estructura de archivos
```
nombre-del-proyecto/
├── routes/
│   └── web.php                   # Definición de rutas del proyecto
├── resources/
│   └── views/
│       ├── perfil.blade.php
│       ├── intereses.blade.php
│       ├── habilidades.blade.php
│       └── metas.blade.php
└── public/
    └── css/
        └── estilos.css           # Estilos CSS propios (sin Bootstrap)
```

Las vistas enlazan la hoja de estilos mediante el helper `asset()` de Laravel:
```html
<link rel="stylesheet" href="{{ asset('css/estilos.css') }}">
```

## Autor

**Tomás Enrique Urieles Chuscano**  
Taller introduccion a laravel de la asignatura Backend — UNAB  
Fecha: 2026-02-18
