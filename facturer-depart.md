Vous détaillez le cas Facturer le départ.

Acteur principal : Agent d'hôtel
Précondition : le client est arrivé et son séjour est enregistré.

Scénario nominal :

L'agent recherche le séjour du client.
Le système récupère la chambre, les dates et le nombre d'occupants.
Le système calcule le prix de la chambre.
Le système récupère les consommations : restaurant, bar, téléphone.
Le système calcule le montant des consommations.
Le système calcule la taxe de séjour.
Le système calcule le montant total.
Le système affiche la facture.
Le client paie.
Le service de paiement confirme le paiement.
Le système clôture le séjour.



sequenceDiagram
    autonumber
    actor A as Agent d'hôtel
    actor C as Client
    participant S as Système
    participant P as Service de paiement

    Note over A, S: Précondition : Client arrivé et séjour enregistré

    A->>S: Recherche le séjour du client
    activate S
    S->>S: Récupère chambre, dates et nombre d'occupants
    S->>S: Calcule le prix de la chambre
    S->>S: Récupère les consommations (restaurant, bar, téléphone)
    S->>S: Calcule le montant des consommations
    S->>S: Calcule la taxe de séjour
    S->>S: Calcule le montant total
    S-->>A: Affiche la facture
    deactivate S

    A-->>C: Transmet la facture
    C->>P: Effectue le paiement
    activate P
    P-->>S: Confirme le paiement
    deactivate P

    activate S
    S->>S: Clôture le séjour
    S-->>A: Confirmation de la clôture
    deactivate S
    
