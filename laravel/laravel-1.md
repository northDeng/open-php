#生成key
```shell
php artisan key:generate
```
#视图文件获取数据
```php
$this->view('pages.show')->withPage(Page::all(); //此时pages为前端数据加载变量
@foreach ($pages as $page)
```
#执行创建表命令
```php
php artisan migrate
```
#创建 控制器 模型命令
```php
php artisan make:controller 加上控制器名称和相对地址
eg: php artisan make:controller Admin/AdminController
```
#填充数据命令 
```php
composer dump-autoload
php artisan db:seed
```
#创建模型类
```php
php artisan make:model 模型名称
```
#创建模型类 同时创建 对应表
```php
    php artisan --make:model Code --migration
    php artisan --make:model Code -m //两种都可以
```
#laravel5.3升级到laravel5.5是报错解决方案
> 报错信息：php artisan optimize PHP Fatal error: Uncaught Symfony\Component\Debug\Exception\FatalThrowableError: Call to undefined method Illuminate\Events\Dispatcher::dispatch()
>解决方案:
+    删除 bootstrap/cache/下的.php文件
+    php artisan cache:clear
+    php artisan view:clear
+    composer update

#修改表结构
>按照laravel提出的协同开发规范，应该新建一个迁移文件，命令如下:
```php
php artisan make:migration update_codes_table --table=codes
```
>然后进行对表结构的修改,代码如下:
```php
Schema::table('ws_codes', function (Blueprint $table) {
            $table->integer('status')->comment('兑换码状态')->default(0)->change();
            $table->integer('exchange_id')->nullable()->comment('兑换人 微商代理')->change();
        });
```
>然后运行migrate命令更新,命令如下：
```php
php artisan migrate
```

   


