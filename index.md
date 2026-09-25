Ensemble des acteurs du système:

-le client,

-l'agent de voyage,

-le gérant,

-le personnel de restauration,

-le service de payement externe.




Diagramme effectué:

flowchart LR

    %% =========================
    %% ACTEURS
    %% =========================

    Client([Client])
    Agent([Agent de voyage])
    Gerant([Gérant])
    Paiement([Service de paiement externe])
    Resto([Personnel de restauration])

    %% =========================
    %% SYSTÈME
    %% =========================

    subgraph Systeme["Système de gestion des réservations et séjours"]

        Reserver([Réserver])
        Dispo([Consulter les disponibilités])
        Arrhes([Verser les arrhes])
        Annuler([Annuler une réservation])
        Consommer([Consommer])

        Admin([Administrer])
        Occupation([Consulter les taux d'occupation])
        Facture([Facturer le départ])

        Arrivee([Enregistrer l'arrivée])
        EnregConso([Enregistrer les consommations])
        Calcul([Calculer le montant du séjour])
        Solder([Solder le séjour])
        Encaisser([Encaisser les paiements])

        Editer([Éditer les réservations])
        AnnulerNonConf([Annuler les réservations non-confirmées])
        Planifier([Planifier les dates])
        Rembourser([Rembourser les réservations])

        Planificateur([Planificateur])
    end

    %% =========================
    %% ASSOCIATIONS ACTEURS
    %% =========================

    Client --> Reserver
    Client --> Dispo
    Client --> Annuler
    Client --> Consommer

    Agent --> Reserver
    Agent --> Dispo
    Agent --> Annuler
    Agent --> Arrhes
    Agent --> Editer
    Agent --> Planifier

    Gerant --> Admin
    Gerant --> Occupation
    Gerant --> Facture
    Gerant --> Arrivee
    Gerant --> Solder
    Gerant --> Editer

    Paiement --> Arrhes
    Paiement --> Encaisser
    Paiement --> Rembourser

    Resto --> Consommer
    Resto --> EnregConso

    %% =========================
    %% INCLUDE
    %% =========================

    Reserver -. "<<include>>" .-> Dispo
    Reserver -. "<<include>>" .-> Arrhes

    Consommer -. "<<include>>" .-> EnregConso
    Consommer -. "<<include>>" .-> Calcul

    Solder -. "<<include>>" .-> Calcul
    Solder -. "<<include>>" .-> Encaisser

    Facture -. "<<include>>" .-> Calcul

    Admin -. "<<include>>" .-> Occupation

    %% =========================
    %% EXTEND
    %% =========================

    AnnulerNonConf -. "<<extend>>" .-> Annuler
    Rembourser -. "<<extend>>" .-> Annuler
    Editer -. "<<extend>>" .-> Reserver
    Planifier -. "<<extend>>" .-> Reserver