# Getting started

Before creating your first GustavPHP project, you should ensure that your local machine has [PHP](https://www.php.net/) and [Composer](https://getcomposer.org/) installed.

After you have installed PHP and Composer, you may create a new GustavPHP project via the `create-project` command:

```bash
composer create-project gustav-php/starter example-app
```

After the project has been created, start GustavPHP's local development server using the serve command:

```bash
cd example-app

php gustav serve
```

Once you have started the Artisan development server, your application will be accessible in your web browser at `http://localhost:4201`.
