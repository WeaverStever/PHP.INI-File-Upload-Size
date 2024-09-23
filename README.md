# PHP.INI-File-Upload-Size
<b>Keywords:</b> upload_max_filesize, post_max_size, wordpress, All-in-One WP Migration and Backup

Goal: increase the PHP upload filesize -- Ubuntu 22.04, php 8.1

To find the php.ini file that is active.
````
php -i | grep "Configuration File"
````

To find all of your php.ini files
````
sudo apt install plocate
sudo updatedb; locate php.ini
````
My active php.ini file is located at /etc/php/8.1/cli/php.ini

The two areas we are concerned with:
````
; Maximum allowed size for uploaded files.
; https://php.net/upload-max-filesize
upload_max_filesize = 2M
````
and 
````
; Maximum size of POST data that PHP will accept.
; Its value may be 0 to disable the limit. It is ignored if POST data reading
; is disabled through enable_post_data_reading.
; https://php.net/post-max-size
post_max_size = 8M
````
I use the nano editor, (your file location may be different)
````
sudo nano /etc/php/8.1/cli/php.ini
````
<b>The "post_max_size" setting must be larger than the "upload_max_filesize"</b>

use CTRL + w for the "find" function in nano. 

use CTRL + x to save and exit nano

<h2>Restart Ubuntu (not the webserver), for changes to take effect.</h2>

