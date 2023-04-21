<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400"></a></p>

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing).
- [Powerful dependency injection container](https://laravel.com/docs/container).
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
- Database agnostic [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues).
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, powerful, and provides tools required for large, robust applications.

## Learning Laravel

Laravel has the most extensive and thorough [documentation](https://laravel.com/docs) and video tutorial library of all modern web application frameworks, making it a breeze to get started with the framework.

If you don't feel like reading, [Laracasts](https://laracasts.com) can help. Laracasts contains over 1500 video tutorials on a range of topics including Laravel, modern PHP, unit testing, and JavaScript. Boost your skills by digging into our comprehensive video library.

## Laravel Sponsors

We would like to extend our thanks to the following sponsors for funding Laravel development. If you are interested in becoming a sponsor, please visit the Laravel [Patreon page](https://patreon.com/taylorotwell).

### Premium Partners

- **[Vehikl](https://vehikl.com/)**
- **[Tighten Co.](https://tighten.co)**
- **[Kirschbaum Development Group](https://kirschbaumdevelopment.com)**
- **[64 Robots](https://64robots.com)**
- **[Cubet Techno Labs](https://cubettech.com)**
- **[Cyber-Duck](https://cyber-duck.co.uk)**
- **[Many](https://www.many.co.uk)**
- **[Webdock, Fast VPS Hosting](https://www.webdock.io/en)**
- **[DevSquad](https://devsquad.com)**
- **[Curotec](https://www.curotec.com/services/technologies/laravel/)**
- **[OP.GG](https://op.gg)**
- **[CMS Max](https://www.cmsmax.com/)**
- **[WebReinvent](https://webreinvent.com/?utm_source=laravel&utm_medium=github&utm_campaign=patreon-sponsors)**

## Contributing

Thank you for considering contributing to the Laravel framework! The contribution guide can be found in the [Laravel documentation](https://laravel.com/docs/contributions).

## Code of Conduct

In order to ensure that the Laravel community is welcoming to all, please review and abide by the [Code of Conduct](https://laravel.com/docs/contributions#code-of-conduct).

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell via [taylor@laravel.com](mailto:taylor@laravel.com). All security vulnerabilities will be promptly addressed.

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).



### Instalando nuevo proyecto laravel
	composer create-project laravel/laravel websiteadmin  8.6

## configurar el .env

## agregando tabla proyectos
	php artisan make:migration proyectos

## migrando
	php artisan migrate


## instalando UI estandar de laravel
	composer require laravel/ui 

## instalando dependencia de boostrap auth
	php artisan ui bootstrap --auth 

## instalando npm nesesario 
	npm install

## instalar dependencia de npm  , es opcional verificar si el proyecto lo requiere
	npm install resolve-url-loader@^5.0.0 --save-dev --legacy-peer-deps


### Añadir plandilla css js
## En directorio del proyecto laravel /public migrar las carpetas css y js de la plantila

## en resourcers/views/layouts  copiar y pegar el archivo app.blade.php y la copia renombrarla como tenplate.blade.php
## opcional, en la plantilla welcome , borrar y redireccionar hacia template.blade.php 

	@extends('layouts.template')

### CREANDO CRUD PARA ADMINISTRAR CONTENIDO
## instalando paquete de crud ibex/crud-generator
	composer require ibex/crud-generator --dev

## este paquete instalara controladores, modelos vistas 
	php artisan vendor:publish --tag=crud

	php artisan make:crud proyectos

## agregar ruta para crud de proyectos

	Route::resource('/proyectos', App\Http\Controllers\ProyectoController::class);

## crear un controllador para administrar el contenido de un portafolio

	php artisan make:controller PortafolioController
	
## La arquitectura sera un modelo => 2 controladores
## model proyecto => PortafolioController , ProyectoController


        <?php

        namespace App\Http\Controllers;
        use App\Models\Proyecto;
        use Illuminate\Http\Request;

        class PortafolioController extends Controller
        {
            public function index()
            {
                $proyectos = Proyecto::paginate();

                return view('proyecto.index', compact('proyectos'))
                    ->with('i', (request()->input('page', 1) - 1) * $proyectos->perPage());
            }
        }



## Añadiendo ruta

	Route::get('/', App\Http\Controllers\PortafolioController::class, 'index' );

## AJUSTES EN LA PLANTILLA

# Ajustando grid de portafolio

### Ajustando login 

## Probar formulario de registro y registrar un usuario

# ejemolo 

# admin@gmail.com
# Pumas10.


## añadir auth en  ProyectoController

 public function __construct()
    {
        $this->middleware('auth');
    }

	
