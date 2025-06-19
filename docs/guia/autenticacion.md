# Autenticación

La Pokemon API utiliza autenticación basada en API Keys para proteger los recursos.

![API Security](/img/security.png)

## Tipos de Autenticación

| Método | Uso | Nivel de Acceso |
|--------|-----|-----------------|
| API Key | Desarrollo y producción | Completo |
| OAuth 2.0 | Aplicaciones de terceros | Limitado |
| JWT Token | Sesiones de usuario | Temporal |

## Obtener tu API Key

1. **Registro**: Crea una cuenta en [portal.pokemon-api.com](https://portal.pokemon-api.com)
2. **Verificación**: Confirma tu email
3. **Dashboard**: Accede a tu panel de desarrollador
4. **Generar Key**: Crea una nueva API key

!!! warning "Seguridad"
    Nunca compartas tu API key públicamente. Guárdala como una variable de entorno.

## Uso de la API Key

=== "JavaScript"

    ```javascript
    // Variable de entorno
    const API_KEY = process.env.POKEMON_API_KEY;
    
    const headers = {
        'Authorization': `Bearer ${API_KEY}`,
        'Content-Type': 'application/json'
    };
    
    fetch('https://api.pokemon.com/v1/pokemon', { headers })
        .then(response => response.json())
        .then(data => console.log(data));
    ```

=== "Python"

    ```python
    import os
    import requests
    
    # Variable de entorno
    API_KEY = os.getenv('POKEMON_API_KEY')
    
    headers = {
        'Authorization': f'Bearer {API_KEY}',
        'Content-Type': 'application/json'
    }
    
    response = requests.get(
        'https://api.pokemon.com/v1/pokemon',
        headers=headers
    )
    ```