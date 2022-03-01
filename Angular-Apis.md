# Curso de Consumo de APIs RES con Angular
    Angular nos ofrece un módulo para trabajar con peticiones HTTP: <b>HttpClientModule</b>

    En nuestros servicios, lo inyectaremos de la siguiente manera:

    ```
    constructor(private http: HttpClient) { }
    ```

## Solicitudes GET
    Nos servirá para obtener información.

    ```
    this.http.post<Product>(`${this._apiUrl}`);
    ```

## Solicitud POST
    Crear un nuevo registro

    ```
    this.http.post<Product>(`${this._apiUrl}`, data);
    ```

    Como segundo parámetro enviamos la información a recibir por medio de nuestro body.