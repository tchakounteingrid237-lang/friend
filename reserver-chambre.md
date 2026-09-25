Acteur principal : Client ou Agent de voyage
Précondition : l'hôtel et les chambres sont configurés, et les dates sont valides.
Scénario nominal :
Le client saisit les dates du séjour et le nombre d'occupants.
Le système consulte les disponibilités.
Le système affiche les chambres disponibles.
Le client choisit une chambre.
Le système vérifie que le nombre d'occupants respecte la capacité.
Le système crée la réservation.
Si nécessaire, le système demande les arrhes.
Le paiement est effectué.
Le système confirme la réservation.


sequenceDiagram
    autonumber
    actor U as Client / Agent
    participant S as Système
    participant B as Base de données

    Note over U, B: Précondition : Hôtel/Chambres configurés et dates valides

    U->>S: Saisit dates et nombre d'occupants
    activate S
    S->>B: Consulte les disponibilités
    activate B
    B-->>S: Renvoie les chambres libres
    deactivate B
    S-->>U: Affiche les chambres disponibles
    deactivate S

    U->>S: Choisit une chambre
    activate S
    S->>S: Vérifie la capacité de la chambre
    S->>B: Crée la réservation
    activate B
    B-->>S: Confirmation création
    deactivate B

    opt Si nécessaire
        S-->>U: Demande les arrhes
        U->>S: Effectue le paiement
    end

    S-->>U: Confirme la réservation
    deactivate S