# Curso de Consumo de APIs RES con Angular

  Angular nos ofrece un módulo para trabajar con peticiones HTTP: **HttpClientModule**

## Utilizar Modulo HTTP

* Para empezar a utilizar peticiones HTTP, debemos de importar el modulo correspondiente en nuestro *app.module.ts*

    `Import { HttpClientModule } from '@angular/common/http';`

    Este debemos agregarlo a la seccion de *imports*

* Como siguiente paso, debemos ir al servicio o componente que realizara la peticion, e importar el **Servicio** HttpClient

    `Import { HttpClient } from '@angular/common/http';`

    Como *HttpClient* es un servicio, debemos declararlo en el *constructor*

    ```TypeScript
        export class ProductService{
            constructor(
                private http: HttpClient;
            ){}
        }
    ```

## Tipos de peticiones

### Get

Las peticiones de tipo *GET* nos permiten obtener informacion

* Para realizar una peticion de tipo GET debemos de utilizar el metodo *get()* del servicio *HttpClient*.

Esto nos devolvera un observable con lo que retorne la API

```TypeScript
        export class ProductService{
            constructor(
                private http: HttpClient;
            ){}
            getAllProducts(){
                return this.http.get<Product[]>('https://young-sands-07814.herokuapp.com/api/products')
            }
        }
```