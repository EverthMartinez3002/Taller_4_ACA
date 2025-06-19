# Entrenadores API

Gestiona perfiles de entrenadores Pokemon, sus equipos y estadísticas de batalla.

## Crear Entrenador

```http
POST /v1/trainers
```

Crea un nuevo perfil de entrenador.

**Ejemplo:**

=== "Request"

    ```json
    {
        "name": "Ash Ketchum",
        "hometown": "Pueblo Paleta",
        "age": 16,
        "favorite_type": "Eléctrico"
    }
    ```

=== "Response"

    ```json
    {
        "id": 12345,
        "name": "Ash Ketchum",
        "hometown": "Pueblo Paleta", 
        "age": 16,
        "favorite_type": "Eléctrico",
        "badges": 0,
        "wins": 0,
        "losses": 0,
        "team": [],
        "created_at": "2025-06-18T10:30:00Z"
    }
    ```

## Gestionar Equipo Pokemon

### Agregar Pokemon al Equipo

```http
POST /v1/trainers/{trainer_id}/team
```

```json
{
    "pokemon_id": 25,
    "nickname": "Pika",
    "level": 25
}
```

### Ver Equipo Completo

```http
GET /v1/trainers/{trainer_id}/team
```

**Respuesta:**

```json
{
    "trainer_id": 12345,
    "team": [
        {
            "pokemon_id": 25,
            "name": "Pikachu",
            "nickname": "Pika",
            "level": 25,
            "experience": 15750,
            "moves": ["Impactrueno", "Ataque Rápido"]
        }
    ],
    "team_size": 1,
    "max_team_size": 6
}
```

## Estadísticas del Entrenador

| Estadística | Descripción |
|-------------|-------------|
| **Batallas Ganadas** | Total de victorias |
| **Batallas Perdidas** | Total de derrotas |
| **Ratio de Victoria** | Porcentaje de victorias |
| **Pokemon Capturados** | Total de Pokemon únicos |
| **Badges** | Medallas de gimnasio obtenidas |

!!! success "Achievements"
    Los entrenadores pueden desbloquear logros especiales:
    - 🔥 **Maestro de Fuego**: Ganar 10 batallas con Pokemon tipo Fuego
    - ⚡ **Velocidad Máxima**: Ganar batallas en menos de 30 segundos
    - 🏆 **Campeón**: Obtener las 8 medallas de gimnasio

## Rankings

```http
GET /v1/trainers/rankings
```

Obtiene el ranking global de entrenadores ordenado por victorias.

Para comenzar tu aventura como entrenador, revisa nuestra [Guía de Inicio](../guia/inicio.md).
