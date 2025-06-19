# Pokemon API

La API de Pokemon te permite acceder a información detallada sobre todos los Pokemon, sus estadísticas, habilidades y más.

![Pokemon Battle](/img/pokemon-battle.jpg)

## Endpoints Disponibles

### Listar Pokemon

```http
GET /v1/pokemon
```

Obtiene una lista paginada de todos los Pokemon disponibles.

**Parámetros de query:**

| Parámetro | Tipo | Descripción |
|-----------|------|-------------|
| `type` | string | Filtrar por tipo (fuego, agua, eléctrico, etc.) |
| `generation` | integer | Filtrar por generación (1-8) |
| `page` | integer | Número de página (default: 1) |
| `limit` | integer | Elementos por página (default: 20, max: 100) |

**Ejemplo de respuesta:**

```json
{
    "data": [
        {
            "id": 25,
            "name": "Pikachu",
            "type": ["Eléctrico"],
            "generation": 1,
            "sprite": "https://api.pokemon.com/sprites/pikachu.png"
        }
    ],
    "pagination": {
        "page": 1,
        "limit": 20,
        "total": 151,
        "total_pages": 8
    }
}
```

### Obtener Pokemon por ID

```http
GET /v1/pokemon/{id}
```

Obtiene información detallada de un Pokemon específico.

=== "Request"

    ```bash
    curl -H "Authorization: Bearer tu_api_key" \
         https://api.pokemon.com/v1/pokemon/25
    ```

=== "Response"

    ```json
    {
        "id": 25,
        "name": "Pikachu",
        "type": ["Eléctrico"],
        "generation": 1,
        "stats": {
            "hp": 35,
            "attack": 55,
            "defense": 40,
            "sp_attack": 50,
            "sp_defense": 50,
            "speed": 90,
            "total": 320
        },
        "abilities": [
            "Electricidad Estática",
            "Pararrayos"
        ],
        "moves": [
            "Impactrueno",
            "Ataque Rápido",
            "Rayo",
            "Trueno"
        ],
        "evolution": {
            "evolves_from": "Pichu",
            "evolves_to": "Raichu",
            "level": 22
        },
        "sprites": {
            "front": "https://api.pokemon.com/sprites/pikachu-front.png",
            "back": "https://api.pokemon.com/sprites/pikachu-back.png"
        }
    }
    ```

!!! tip "Sprites de Alta Calidad"
    Todos los sprites están disponibles en resolución 256x256 para una mejor experiencia visual.

### Buscar Pokemon

```http
GET /v1/pokemon/search?q={query}
```

Busca Pokemon por nombre o características.

**Ejemplo:**
```bash
curl -H "Authorization: Bearer tu_api_key" \
     "https://api.pokemon.com/v1/pokemon/search?q=pika"
```

## Códigos de Error

- **404**: Pokemon no encontrado
- **400**: Parámetros inválidos
- **429**: Límite de rate excedido

Para más información sobre autenticación, consulta la [guía de autenticación](../guia/autenticacion.md).
