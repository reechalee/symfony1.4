symfony1.4.9
============
unforunately this app is not a simple drop in.  
since it is set up to NOT run in the httpd dir, its easiest to just add another listener port that serves requests for this symfony app.

add to httpd.conf:
```
 <VirtualHost *:8080>
   DocumentRoot "/home/qa/PhpSetupHome/sfprojects/jobeet/web"
   DirectoryIndex index.php
   <Directory "/home/qa/PhpSetupHome/sfprojects/jobeet/web">
     AllowOverride All
     Allow from All
   </Directory>

   Alias /sf /home/qa/PhpSetupHome/sfprojects/jobeet/lib/vendor/symfony/data/web/sf
   <Directory "/home/qa/PhpSetupHome/sfprojects/jobeet/lib/vendor/symfony/data/web/sf">
     AllowOverride All
     Allow from All
   </Directory>
 </VirtualHost>
```
