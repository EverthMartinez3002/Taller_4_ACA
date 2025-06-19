# Endpoints de la API

Esta es la referencia completa de todos los endpoints disponibles en la Pokemon API.

## Base URL

```
https://api.pokemon.com/v1/
```

## Endpoints Principales

| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/pokemon` | Lista todos los Pokemon |
| GET | `/pokemon/{id}` | Obtiene un Pokemon específico |
| GET | `/pokemon/{id}/stats` | Estadísticas del Pokemon |
| POST | `/battle` | Crear una nueva batalla |
| GET | `/trainers` | Lista de entrenadores |

!!! info "Autenticación"
    Todos los endpoints requieren un header `Authorization: Bearer API_KEY`

## Ejemplos de Uso

### Obtener Lista de Pokemon

=== "Request"

    ```http
    GET /v1/pokemon HTTP/1.1
    Host: api.pokemon.com
    Authorization: Bearer tu_api_key
    Content-Type: application/json
    ```

=== "Response"

    ```json
    {
        "data": [
            {
                "id": 1,
                "name": "Bulbasaur",
                "type": ["Planta", "Veneno"]
            },
            {
                "id": 25,
                "name": "Pikachu", 
                "type": ["Eléctrico"]
            }
        ],
        "total": 151,
        "page": 1
    }
    ```

### Crear Batalla

=== "Request"

    ```http
    POST /v1/battle HTTP/1.1
    Host: api.pokemon.com
    Authorization: Bearer tu_api_key
    Content-Type: application/json
    
    {
        "pokemon1_id": 25,
        "pokemon2_id": 6,
        "terrain": "campo"
    }
    ```

=== "Response"

    ```json
    {
        "battle_id": "battle_123456",
        "winner": {
            "id": 25,
            "name": "Pikachu"
        },
        "duration": "00:02:34",
        "moves_used": 8
    }
    ```

## Códigos de Estado

- **200 OK**: Petición exitosa
- **201 Created**: Recurso creado exitosamente
- **400 Bad Request**: Error en los parámetros
- **401 Unauthorized**: API key inválida
- **404 Not Found**: Recurso no encontrado
- **500 Internal Server Error**: Error del servidor

!!! warning "Rate Limits"
    Máximo 1000 peticiones por hora para cuentas gratuitas.

## Filtros y Paginación

Puedes filtrar y paginar los resultados usando parámetros de query:

```
GET /pokemon?type=fuego&page=2&limit=20
```

Para más detalles sobre endpoints específicos, consulta:
- [Pokemon API](../api/pokemon.md)
- [Batallas API](../api/batallas.md)
- [Entrenadores API](../api/entrenadores.md)