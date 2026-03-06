# Santabarbara

Equipo Santabarbara 

Nombrado en honor de nuestro compañero Rodrigo Santabárbara Murrieta 2004-2025

Genaro Alejandro Barradas Sánchez

Omar Morales García 

Martinez Ramirez Alejandro


# Gestor de Series - API de Seguimiento "Por Ver"

Este proyecto consiste en una aplicación web que permite gestionar una lista de series pendientes por ver. Utiliza una API propia construida en Node.js que consume datos reales de la API pública de TVMaze para obtener detalles técnicos de las producciones.

## 1. Descripción del API Consumido
La aplicación integra la **API de TVMaze** para enriquecer la experiencia del usuario. Al buscar una serie, el sistema no solo valida el nombre, sino que recupera información oficial como el elenco principal, el año de estreno y la cadena de transmisión.

## 2. Endpoints de la API (Backend)

| Método | Endpoint | Descripción |
| :--- | :--- | :--- |
| **GET** | `/api/serie?nombre=...` | Busca y sanitiza información en tiempo real desde TVMaze. |
| **GET** | `/api/listas` | Consulta el estado global de las listas (Favoritas, Por Ver, Calificaciones). |
| **POST** | `/api/por-ver` | Agrega un nuevo título a la lista de pendientes del usuario. |
| **PATCH** | `/api/por-ver/:nombre` | Permite corregir parcialmente el nombre de una serie ya registrada. |
| **DELETE** | `/api/por-ver/:nombre` | Elimina definitivamente una serie de la lista de pendientes. |

## 3. Ejemplos de Request y Response

### Búsqueda de Serie (GET)
* **Request:** `GET http://localhost:3000/api/serie?nombre=chuck`
* **Response (JSON):**
```json
{
  "busqueda_original": "chuck",
  "titulo_sanitizado": "Chuck",
  "titulo_oficial": "Chuck",
  "actores_principales": ["Zachary Levi", "Yvonne Strahovski", "Joshua Gomez"],
  "ano_inicio": "2007",
  "plataforma_streaming": "NBC"
}
