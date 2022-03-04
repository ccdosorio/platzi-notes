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

#### Data Transfer Object DTO

Información de transferencia al API, hay una diferencia en lo que enviamos y lo que recibimos.

* Se puede crear otra interfaz específica para enviar esa información, pero esta no sería la mejor práctica.
* Se aplica una técnica de extender (extends) y omitimos los valores que no necesitamos

```TypeScript
export interface Product {
    id: string;
    title: string;
    price: number;
    images: string[];
    description: string;
    category: Category;
}

export interface CreateProductDTO extends Omit<Product, 'id' | 'category'> {
    categoryId: number;
}

```

### Solicitud PUT y PATCH

* PUT: Debemos enviar siempre toda la información, independientemente si cambiamos solo un valor. Enviamos todo el cuerpo del objeto
* PATCH: Solo enviamos lo que modificamos.

* Para indicar en la interfaz que todos los atributos serán opcionales y no reutilizar código, se aplica el método propiamente de TypeScript: **Partial**

```TypeScript
export interface updateProductDTO extends Partial<CreateProductDTO>{ }
```

### Solicitud DELETE

Eliminar un registro.

## URL Parameters

* Parámetros que viajan en la URL, se usa usualmente para realizar filtros o paginación.

### Paginación con limit & offset

* Limit: número de elementos que quiero obtener
* Offset: indicador de cuántos elementos quiero escapar, apuntador desde donde inicio. El offset se va corriendo en dependencia de cuántos elementos necesito y desde donde quiero empezar a obtener esos elementos.
