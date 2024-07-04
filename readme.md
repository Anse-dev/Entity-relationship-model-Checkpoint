

# Gestion de Gymnases - ERD

## Introduction

Ce projet vise à gérer les inscriptions et les sessions pour une chaîne de gymnases. Le système doit gérer plusieurs gymnases, les membres inscrits, les sessions proposées, et les entraîneurs qui dirigent ces sessions. Ce README décrit les entités, leurs attributs, et les relations entre elles.

## Entités et Attributs

### Gymnasium
Représente un gymnase appartenant à la chaîne.
- `gym_id`: Identifiant unique du gymnase (PK)
- `name`: Nom du gymnase
- `address`: Adresse du gymnase
- `phone_number`: Numéro de téléphone du gymnase

### Member
Représente un membre inscrit dans un gymnase.
- `member_id`: Identifiant unique du membre (PK)
- `last_name`: Nom de famille du membre
- `first_name`: Prénom du membre
- `address`: Adresse du membre
- `dob`: Date de naissance du membre
- `gender`: Genre du membre

### Session
Représente une session de sport dans un gymnase.
- `session_id`: Identifiant unique de la session (PK)
- `type_of_sport`: Type de sport pratiqué durant la session
- `schedule`: Horaire de la session
- `gym_id`: Référence au gymnase où se déroule la session (FK)

### Coach
Représente un entraîneur qui dirige des sessions.
- `coach_id`: Identifiant unique de l'entraîneur (PK)
- `last_name`: Nom de famille de l'entraîneur
- `first_name`: Prénom de l'entraîneur
- `age`: Âge de l'entraîneur
- `specialty`: Spécialité de l'entraîneur

## Relations

### Gymnasium to Session (1:N)
Un gymnase peut organiser plusieurs sessions.
- `gym_id` dans `Gymnasium` correspond à `gym_id` dans `Session`.

### Member to Session (N:M)
Un membre peut assister à plusieurs sessions et une session peut accueillir plusieurs membres.
- Relation de type many-to-many entre `Member` et `Session`.

### Session to Coach (N:M)
Une session peut être dirigée par plusieurs entraîneurs et un entraîneur peut diriger plusieurs sessions.
- Relation de type many-to-many entre `Session` et `Coach`.

## Diagramme ER

```plaintext
          +------------+
          | Gymnasium  |
          +------------+
          | gym_id     |
          | name       |
          | address    |
          | phone_number|
          +------------+
                |
                | 1
                |
                | *
         +------v-------+
         |   Session    |
         +--------------+
         | session_id   |
         | type_of_sport|
         | schedule     |
         | gym_id (FK)  |
         +--------------+
         /|\           /|\
          |             |
          |             |
          | *           | *
    +-----v---+     +---v-----+
    | Member  |     |  Coach  |
    +---------+     +---------+
    | member_id|     | coach_id|
    | last_name|     | last_name|
    | first_name|    | first_name|
    | address  |     | age      |
    | dob      |     | specialty|
    | gender   |     +---------+
    +---------+
```

## Utilisation

Ce diagramme de relation entre entités (ERD) est conçu pour gérer efficacement les membres, sessions, et entraîneurs d'une chaîne de gymnases. Il peut être utilisé comme base pour créer la base de données relationnelle nécessaire au bon fonctionnement du système de gestion.

## Contribution

Les contributions sont les bienvenues ! Si vous avez des suggestions ou des améliorations, veuillez soumettre une pull request ou ouvrir une issue.
