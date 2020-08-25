<p align="center"><img src="https://raw.githubusercontent.com/laravel/art/master/laravel-logo.png" width="400"></p>

Small study documentation of the PHP <a href="https://laravel.com/">👉 Laravel framework 👈</a>, developing an ecommerce platform.

<p align="center">
    <a href="#">
        <img alt="Passing" src="https://img.shields.io/circleci/build/github/MagicalStrangeQuark/ecommerce-laravel">
    </a>
    <a href="https://opensource.org/licenses/MIT">
        <img alt="License" src="https://img.shields.io/badge/License-MIT-yellow.svg">
    </a>
    <a href="#">
        <img alt="License" src="https://img.shields.io/github/languages/count/MagicalStrangeQuark/ecommerce-laravel">
    </a>
    <a href="#">
        <img alt="License" src="https://img.shields.io/github/last-commit/MagicalStrangeQuark/ecommerce-laravel">
    </a>
    <a href="#">
        <img alt="License" src="https://img.shields.io/github/followers/MagicalStrangeQuark?style=social">
    </a>
</p>

## Configuring the machine to start the application

🔏 Installing Apache

   `sudo pacman -S apache`

🔏  Installation of tools that will be needed later

   `sudo pacman -S curl git unzip`

🔏  Installing Composer

   `sudo su`

   `curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer`

🔏  Installing the  <a href="https://addons.mozilla.org/pt-BR/firefox/addon/restclient">👉 RESTClient 👈</a> extension

   🪔 `To test the use of API's and other features within our application, it is recommended to use a tool to perform the request simulation.`

## Starting a new Laravel project

### 🐉 Create a new project

    `composer create-project --prefer-dist laravel/laravel some-project-name`

### 🐲 Installation of project dependencies

    `composer install`

## Visual Studio Code Extensions

🦝 <a href="https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv">🌖 DotENV 🌘</a>

🦝 <a href="https://marketplace.visualstudio.com/items?itemName=onecentlin.laravel5-snippets">💐 Laravel Snippets 🪐</a>

🦝 <a href="https://marketplace.visualstudio.com/items?itemName=onecentlin.laravel-blade">🌾 Laravel Blade Snippets 🌚 </a>

🦝 <a href="https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client">💫 PHP Intelephense 🌻</a>

## Run the project from the current project

> `git clone https://github.com/MagicalStrangeQuark/ecommerce-laravel.git`

## Create and configure the database (MariaDB)

> `CREATE DATABASE laravel`

> `CREATE USER 'laravel'@'localhost' IDENTIFIED BY 'P@ssw0rd'`

> `GRANT ALL PRIVILEGES ON * . * TO 'laravel'@'localhost'`

> `FLUSH PRIVILEGES`

### Configure the .env file

> `cd ecommerce-laravel && cp .env.example .env && php artisan key:generate`

> `php artisan config:clear && php artisan cache:clear && php artisan config:cache`

> `composer install && composer update`

> `npm install && npm audit fix && npm run watch`

> `sudo systemctl start mariadb`

> `php artisan migrate:fresh --seed`

### Run `php artisan serve` inside `ecommerce-laravel` directory

### Open the link <http://127.0.0.1:8000>

## TODO - Version 1.0

👹 `Implementar a rotina de alteração de senha dentro do sistema.`

👹 `Implementar a rotina de restauração de senha através do e-mail cadastrado no usuário.`

👹 `Realizar o upload de imagens para o usuário, exibindo-a ao lado do nome.`

👹 `Realizar o cadastro de n imagens para um determinado produto.`

👹 `Na listagem, criar um carousel para exibição das imagens para um determinado produto.`

👹 `Desenvolver o cadastro dos locais de estoque.`

👹 `Desenvolver as regras para entrada / saída de itens dentro do sistema.`

👹 `Desenvolver a lógica de quantidade do produto por local de estoque.`

👹 `Realizar a exportação de XML e CSV para os módulos que possuam CSV.`

👹 `Criar o módulo Order, assim como o vínculo de n produtos para o mesmo.`

👹 `Criar o módulo forma de pagamento.`

👹 `Realizar o pagamento desse pedido.`

👹 `Criar os testes para todo o sistema.`

👹 `Documentar o sistema no estado atual.`

👹 `Lançar a primeira versão do sistema.`