# Autentication

## Messaggi Fabio Pacfici
01. composer require laravel/breeze --dev
02. php artisan breeze:install
03. composer require pacificdev/laravel_9_preset
04. php artisan preset:ui bootstrap --auth
05. npm i
06. prima di eseguire run dev devi modificare il file vite.config.js in vite.config.cjs
07. ora puoi eseguire npm run dev
08. ora committa
09. php artisan make:controller Admin/DashboardController
10. popola il db: php artisan db:seed --class=PostSeeder


Usiamo breeze

Dopo aver creato il progetto installiamo laravel/breeze

### compose require laravel/breeze --dev 

Il progetto sarà organizzato come:

V views
 V admin
 |  home.blade.php
 > auth
 V guests
 | home.blade.php
 > layouts


 Dopo aver installato l'autenticazione e fatto tutti i passi indicati
 nel file autentication.txt
 Modifichiamo env per accedere al db

 Dopo aver modificato env, effettuiam ouna migration così il db sarà costituito
 ### php artisan migrate

 A questo punto dovrebbe apparire la pagina per il login

 Dopo questo facciamo il controller per la dashboard
 ### php artisan make:controller Admin/DashboardController

 Spostiamo quello che sta nella rotta (web.php nel controller appena creato)

 Se lasciamo il mondo come sta quando ci colleghiamo andiamo in dashboard che adesso non c'è più 
 Adesso c'è admin.
 Per evitare questo redirect diretto a dasboard andiamo nel file
 app\RouteServiceProvider.php e modifichiamo
 public const HOME = '/dasboard';
 in 
 public const HOME = '/admin';

 A questo punto vuole modificare qualcosa (non so bene cosa)
 Va in resources/layouts/app.blade.php

 e questo
   <div class="dropdown-menu dropdown-menu-right" aria-labelledby="navbarDropdown">
                                <a class="dropdown-item" href="{{ url('dashboard') }}">{{__('Dashboard')}}</a>
                                <a class="dropdown-item" href="{{ url('profile') }}">{{__('Profile')}}</a>
                                <a class="dropdown-item" href="{{ route('logout') }}" onclick="event.preventDefault();
                                                     document.getElementById('logout-form').submit();">
                                    {{ __('Logout') }}
                                </a>
viene cambiato in 
  <div class="dropdown-menu dropdown-menu-right" aria-labelledby="navbarDropdown">
                                <a class="dropdown-item" href="{{ url('admin') }}">{{__('Dashboard')}}</a>
                                <a class="dropdown-item" href="{{ url('profile') }}">{{__('Profile')}}</a>
                                <a class="dropdown-item" href="{{ route('logout') }}" onclick="event.preventDefault();
                                                     document.getElementById('logout-form').submit();">
                                    {{ __('Logout') }}
                                </a>