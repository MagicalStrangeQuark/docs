<p align="center"><img src="https://raw.githubusercontent.com/laravel/art/master/laravel-logo.png" width="400"></p>

<p align="center">Small study documentation of the PHP <a href="https://laravel.com/">👉 Laravel framework 👈</a>, developing an ecommerce platform.</p>

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

<h2 align="center">Configuring the machine to start the application</h2>

🔏 Installing Apache

   `sudo pacman -S apache`

🔏  Installation of tools that will be needed later

   `sudo pacman -S curl git unzip`

🔏  Installing Composer

   `sudo su`

   `curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer`

🔏  Installing the  <a href="https://addons.mozilla.org/pt-BR/firefox/addon/restclient">👉 RESTClient 👈</a> extension

   🪔 `To test the use of API's and other features within our application, it is recommended to use a tool to perform the request simulation.`

<h2 align="center">Starting a new Laravel project</h2>

<h3 align="center">🐉 Create a new project</h3>

```bash
    composer create-project --prefer-dist laravel/laravel some-project-name
```

<h3 align="center">🐲 Installation of project dependencies</h3

```bash
    composer install
```

<h2 align="center">Visual Studio Code Extensions</h2>

🦝 <a href="https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv">🌖 DotENV 🌘</a>

🦝 <a href="https://marketplace.visualstudio.com/items?itemName=onecentlin.laravel5-snippets">💐 Laravel Snippets 🪐</a>

🦝 <a href="https://marketplace.visualstudio.com/items?itemName=onecentlin.laravel-blade">🌾 Laravel Blade Snippets 🌚 </a>

🦝 <a href="https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client">💫 PHP Intelephense 🌻</a>

<h2 align="center">Run the project from the current project</h2>

> `git clone https://github.com/MagicalStrangeQuark/ecommerce-laravel.git`

<h2 align="center">Create and configure the database (MariaDB)</h2>

> `CREATE DATABASE laravel`

> `CREATE USER 'laravel'@'localhost' IDENTIFIED BY 'P@ssw0rd'`

> `GRANT ALL PRIVILEGES ON * . * TO 'laravel'@'localhost'`

> `FLUSH PRIVILEGES`

<h3 align="center">Configure the .env file

> `cd ecommerce-laravel && cp .env.example .env && php artisan key:generate`

> `php artisan config:clear && php artisan cache:clear && php artisan config:cache`

> `composer install && composer update`

> `npm install && npm audit fix && npm run watch`

> `sudo systemctl start mariadb`

> `php artisan migrate:fresh --seed`

<h4>Run `php artisan serve` inside `ecommerce-laravel` directory<h4>

<h4>Open the link <http://127.0.0.1:8000></h4>

<h2 align="center">Form Validation</h2>

No objeto request é possível acessar o método validate, bastando inserir um array associativo com a chave contendo o name do campo e o valor required, sendo
validado se existe conteúdo. No exemplo abaixo, estamos verificando se o campo color foi informado:

```
    $request->validate([
        "color" => "required"
    ]);
```

Para inserir mais validações simultaneamente, basta concatenar usando o pipe. No exemplo abaixo, não queremos mais de 10 caracteres no mesmo campo color.

```
    $request->validate([
        "color" => "required|max:10"
    ]);
```

Para validação única, basta informar `unique:<nome-da-tabela>`, para o campo desejado, o seguinte exemplo pode ser útil:

```
    $request->validate([
        "color" => "required|unique:colors",
        "hexadecimal" => "required|min:6|max:6|unique:colors,hexadecimal"
    ]);
```

Exemplo de validação de email:

```
    $request->validate([
        "email" => "required|email",
    ]);
```

Para utilização de mensagens não genéricas, pode-se usar uma chave com o nome da validação, com a mensagem, sendo passsado o placeholder `:attribute`. Exemplo:

```
    $request->validate([
            "color" => "required|unique:colors",
            "hexadecimal" => "required|min:6|max:6|unique:colors"
        ],[
            "hexadecimal.min" => "O hexadecimal deve conter seis caracteres",
            "unique" => "O atributo :attribute deve ser único"
    ]);
```

Para criação de mensagens abaixo do campo com erro / sucesso, o Laravel possui, dentro do objeto $errors, um método chamado `has()`, em que é passado o name, sendo retornado um booleano indicando se aquele campo contém erros.

<h2>Helpers</h2>

Para realizar a criação de um arquivo helper, criaremos um arquivo chamado `Html.php`, dentro do diretório `app/Helpers`.

No arquivo `composer.json`, inserir o código abaixo dentro da chave autoload e rodar o comando `composer dump-autoload`.

```
    "files": [
        "app/Helpers/Html.php"
    ]
```

Adicionar, no diretório config, no arquivo app.php, em aliases, a linha `'Helper' => App\Helpers\Helper::class`

<h2>Models</h2>

<h3>Configuração do Banco de Dados e das Migrações</h3>

```
    1. Realizar a instalação do SGBD mysql

    2. Habilitar o driver do mysql extension=pdo_mysql

    3. Verificar se o driver está habilitado corretamente, rodando o seguinte comando:

        php -r "echo defined('PDO::ATTR_DRIVER_NAME');";

    4. Rodar as migrações e seeds `php artisan migrate:fresh --seed`
```

<h3>Criação de uma migração</h3>

Criação de uma tabela chamada colors

    `php artisan make:migration create_colors_table`

Adicionar um campo chamado color a uma tabela chamada chemical_elements

    `php artisan make:migration add_color_to_chemical_elements`

Criação de um relacionamento muitos para muitos

```
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('products_categories', function (Blueprint $table) {
            $table->bigIncrements('id');
            $table->unsignedBigInteger('product_id');
            $table->foreign('product_id')->references('id')->on('products');
            $table->unsignedBigInteger('category_id');
            $table->foreign('category_id')->references('id')->on('categories');
            $table->softDeletes();
            $table->timestamps();
        });
    }
```

```
    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('products_categories');
    }
```

Criação de um modelo para a tabela colors

    php artisan make:model Color

Criação de um registro para a color, através do tinker

    php artisan tinker;

    use App\Color;

    $colors = Color::create(['color' => 'Black', 'hexadecimal' => '000000']);

Listagem de todos os registros para a color, através do tinker

    use \App\Color;
        
    php Color::all();

Número de registros

    use App\Color;

    Color::count();

Select usando where

    use App\Color;

    Color::where('id', '>=', 2)->first();

    Color::where('id', 2)->get();

    Color::whereBetween('id', [1,2])->get();

    Color::whereNotBetween('id', [2, 3])->get();

    Color::whereIn('id', [2, 3])->get();

    Color::whereNotIn('id', [2, 3])->get();

    Color::where('color', 'like', '%k')->get();

> As duas consultas abaixo são equivalentes

    Color::where('color', 'like', 'B%')->orWhere('id', '>=', 7)->get();

    Color::where(function($query){$query->where('color', 'like', 'B%')->orWhere('id', '>=', 7);})->get();

    Color::where(function($query){
            $query->where('color', 'like', 'B%')->orWhere('id', '>=', 7);
        })->where(function($query) {
                $query->where('color', 'like', '%e%')
                ->where('id', '>=', 10 );
            })->get();

    Color::where('id', '>', '1')->orderBy('color', 'ASC')->get();

    Color::where('id', '>', '1')->get()->pluck('id')->sum();

Set Custom Primary Key

    No model, incluir a linha `protected $primaryKey = 'id'`

Atualizar um campo

```
    use App\Color;

    $Color = Color::find(2);
    $Color->color = "Black";
    $Color->save();
```

```
    Color::find(6)->update(['color' => 'Green']);
```

Soft Delete

    No model, incluir a trait, usando `use SoftDeletes` e incluir o namespace da mesma, com `use Illuminate\Database\Eloquent\SoftDeletes`

    Inclusão do campo, através da seguinte migração `$table->softDeletes()`

Listar incluive os registros deletados

    use App\Color;

    Color::withTrashed->get();

Verificar se um registro em particular, no caso, o id de número 2, está deletado

    use App\Color;

    Color::withTrashed()->find(2)->trashed();

Excluir um registro de id igual a 3 com SoftDelete

    use App\Color;

    Color::find(5)->forceDelete();

<h2>Views</h2>

<h3>Blade</h3>

<h4>Condicional</h4>

```
    @if
        <code>
    @else
        <code>
    @endif
```

<h4>Foreach</h4>

```
    @foreach
        <code>
    @endforeach
```

O framework disponibiliza um objeto chamado $loop, que possibilita obter o primeiro e último elemento do laço de repetição.
 
Reference: <https://tutsforweb.com/loop-variable-foreach-blade-laravel/>

<h3>For</h3>

```
    @for
        <code>
    @endfor
```

<h4>Vazio</h4>

```
    @empty
        <code>
    @endempty
```

<h3>Section</h3>

<h4>Passagem de variáveis como parâmetro</h4>

```
    @yield('variable')

    @section('<variable>', '<string>')
```

<h4>Passagem de um trecho de código HTML como parâmetro</h4>

```
    @yield('<string>')

    @section('<string>')

        <html-code-here>

    @endsection('<string>')
```

<h2 align="center">GIT</h2>

```
    story/102030-some-user-history-message
    
    hotfix/103031-some-hotfix-message

    bugfix/102032-some-bugfix-message
```

<h2 align="center">TODO - Version 1.0</h2>

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