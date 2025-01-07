# laravel-htaccess

```bash
<IfModule mod_rewrite.c>
    <IfModule mod_negotiation.c>
        Options -MultiViews
    </IfModule>
    RewriteEngine On
    RewriteRule ^update - [L]
    RewriteCond %{REQUEST_FILENAME} -d [OR]
    RewriteCond %{REQUEST_FILENAME} -f
    RewriteRule ^ %$1 [N]

    RewriteCond %{REQUEST_METHOD} ^(POST|PUT|DELETE)$
    RewriteRule .* - [E=HTTP_METHOD:%{REQUEST_METHOD}]

    RewriteCond %{REQUEST_URI} (\.\w+$) [NC]
    RewriteRule ^(.*)$ public/$1

    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteRule ^ index.php
</IfModule>
```
