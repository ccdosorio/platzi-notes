# Curso de Consumo de APIs RES con Angular

Angular nos ofrece un módulo para trabajar con peticiones HTTP: **HttpClientModule**

## Uso del módulo HttClienteModule

* Para empezar a utilizar peticiones HTTP, debemos de importar el modulo correspondiente en nuestro *app.module.ts* de la siguiente manera:

`Import { HttpClientModule } from '@angular/common/http';`

* En nuestros servicios, lo inyectaremos de la siguiente manera:

```TypeScript
    constructor(private http: HttpClient) { }
```

## Peticiones Http

### Solicitudes GET

Nos servirá para obtener información.

* Para utilizarlo debemos hacer uso del método *get()* el cuál nos provee nuestro módulo *HttpClient*. Eso nos retornará un *Observable* y nos podremos subscribir a él desde nuestro componente.

```TypeScript
this.http.post<Product>(`${this._apiUrl}`);
```

### Solicitud POST

Crear un nuevo registro.

* Para utilizarlo debemos hacer uso del método *post()* el cuál nos provee nuestro módulo *HttpClient*. Como segundo parámetro enviamos la información a recibir por medio de nuestro body y nos retornará un *Observable*.

```TypeScript
this.http.post<Product>(`${this._apiUrl}`, data);
```
