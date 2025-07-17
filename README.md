# Laravel Quickstart Advanced

Laravel ofrece dos quickstarts oficiales:  
[quickstart-basic](https://github.com/laravel/quickstart-basic) y [quickstart-intermediate](https://github.com/laravel/quickstart-intermediate).  
Ambos están pensados como introducción rápida al framework, pero presentan limitaciones importantes a nivel de arquitectura y buenas prácticas.  
No aplican principios de diseño sólidos, ni separan responsabilidades de manera adecuada.

Por esa razón hice este proyecto: una guía de referencia avanzada para construir una API RESTful con Laravel, aplicando principios SOLID y una arquitectura modular mantenible.

## Objetivos del proyecto

Este repositorio busca servir como base estructural para proyectos que requieren:

- Separación clara de responsabilidades
- Código testable y escalable
- Estilo RESTful consistente
- Buenas prácticas alineadas con el ecosistema Laravel moderno

## Características principales

- Validaciones encapsuladas en **Form Requests**
- Serialización de respuestas mediante **Laravel API Resources**
- Lógica de negocio desacoplada en **clases de Servicio**
- **Eventos y Listeners** para operaciones asincrónicas
- **Envío de correos** mediante Mailables, encolados
- **Reglas personalizadas** de validación
- **Enums** para modelar estados y configuraciones constantes
- **Eloquent Scopes** reutilizables

## Entidades incluidas

- `Project`: incluye estado (`draft`, `active`, `archived`) mediante Enum, y scopes como `active()` o `dueSoon()`.
- `Task`: incluye prioridad como Enum, evento `TaskCreated` con listener asociado.
- `Comment`: dispara evento `CommentPosted` con envío de notificación por correo.
- `Tag`: CRUD parcial, relación many-to-many con `Task`.
- Regla personalizada: `ValidDeadline`, utilizada en la creación de proyectos.

## Estructura del proyecto

```
app/
├── Events/
├── Listeners/
├── Mail/
├── Models/
├── Services/
├── Rules/
├── Enums/
├── Http/
│   ├── Controllers/
│   ├── Requests/
│   └── Resources/
├── Providers/
├── Helpers/
```

## ¿Para qué sirve esta referencia?

- Para entender cómo estructurar un proyecto Laravel más allá del enfoque tradicional monolítico
- Para utilizar como punto de partida en desarrollos RESTful
- Para promover buenas prácticas de desarrollo desde las capas más básicas

## Requisitos

- PHP 8.3+
- Laravel 11
- Composer
- Docker (opcional)

## Instalación

```bash
git clone https://github.com/tu-usuario/laravel-quickstart-advanced.git
cd laravel-quickstart-advanced
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate --seed
php artisan test
```

## Licencia

MIT. Este proyecto puede utilizarse como base para aplicaciones propias o educativas.
