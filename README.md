# PrestaShop con Docker

### Imagen para PrestaShop 1.6.1.13 + XAMPP
* `1.6.1.13 (Español)`

## Qué es PrestaShop

PrestaShop es una aplicación libre y gratuita de eCommerce, diseñada para proporcionar la mejor experiencia de compra para los comerciantes y clientes. Está escrito en PHP, es altamente personalizable, soporta todos los servicios de pago más importantes, está traducido en muchos idiomas y está localizado en muchos países, tiene un diseño totalmente responsive, etc.

## Cómo ejecutar esta imagen

Actualmente, la forma más sencilla de ejecutar este contenedor es:

```
docker run --name prestashop16-xampp -p 41061:22 -p 41062:80 -d -v ~/my_web_pages:/www oddworldng/prestashop16-xampp
```

Abre esta ruta en tu navegador para comenzar la instalación: `http://localhost:41062/prestashop`.


## PhpMyAdmin - Configurar la base de datos

En este contenedor disponemos de PhpMyAdmin, en el cual debemos configurar nuestra base de datos para instalar Prestashop.

Para acceder a la interfaz web de PhpMyAdmin, accedemos a la siguiente URL `http://localhost:41062/phpmyadmin`

## Acceso mediante SSH

Podemos acceder a nuestro contenedor mediante SSH con el siguiente comando:

```
ssh root@localhost -p 41061
```
La contraseña es: **root**

## Eliminar la carpeta /install después de la instalación

Accedemos mediante SSH (ver apartado anterior) a nuestro contenedor y borramos la carpeta `/install` utilizando el comando:

```
rm -rf /opt/lampp/htdocs/prestashop/install/
```

## Error: no entra el backoffice

Uno de los problemas que ocurre es que cuando termina la instalación de Prestashop con el contenedor, no entra en el backoffice de Prestashop.

Para solucionar esto, podemos renombrar la carpeta admin (nos conectamos mediante SSH) utilizando el siguiente comando:

```
mv /opt/lampp/htdocs/prestashop/admin /opt/lampp/htdocs/prestashop/admin1234
```

Con este cambio, ahora podremos acceder a nuestro backoffice mediante la siguiente URL: 

`http://localhost:41062/prestashop/admin1234`

## Licencia

Prestashop 1.6 utiliza la licencia [Academic Free License ("AFL") v. 3.0](https://opensource.org/licenses/AFL-3.0)

Consulta [más información](https://www.prestashop.com/en/osl-license) sobre las licencias que utliza Prestashop.

## Documentación

Puedes encontrar la documentación oficial de Prestashop 1.6 (en Español) en el siguiente enlace:

* [PrestaShop 1.6](http://doc.prestashop.com/pages/viewpage.action?pageId=26148899)

## Nota

Este proyecto ha sido basado en el contenedor https://hub.docker.com/r/tomsik68/xampp/