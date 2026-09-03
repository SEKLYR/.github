# SEKLYR

### L'ERP des sociétés de sécurité privée.

**SEKLYR** est une plateforme SaaS conçue pour les entreprises françaises de sécurité privée et de gardiennage.

Elle centralise l'exploitation, le terrain, la conformité des agents, la gestion des sites clients et la **protection du travailleur isolé (PTI / DATI)** dans une seule plateforme.

> **Moins de paperasse. Plus de contrôle. Une exploitation réellement connectée au terrain.**

---

## ✦ Pourquoi SEKLYR ?

Les sociétés de sécurité privée jonglent quotidiennement entre :

* plannings et vacations ;
* agents et remplacements ;
* sites et consignes ;
* mains courantes ;
* rondes et points de contrôle ;
* registres visiteurs et clés ;
* cartes professionnelles et qualifications ;
* documents administratifs ;
* incidents ;
* protection des agents isolés ;
* clients, contrats, devis et facturation.

SEKLYR rassemble ces opérations dans un même environnement.

L'objectif est simple :

**donner à une société de sécurité une vision complète de son exploitation, du bureau jusqu'au terrain.**

---

# 🛡️ Fonctionnalités

| Module                  | Fonctionnalités                                                                 |
| ----------------------- | ------------------------------------------------------------------------------- |
| 📅 **Planning**         | Vacations, affectations, disponibilités, congés, remplacements et heures        |
| 🤖 **Auto-planning**    | Génération automatique de planning à partir des besoins des sites               |
| 🏢 **Sites**            | Sites clients, consignes, zones, géofence, documents et fiches réflexes         |
| 👮 **Agents**           | Profils, affectations, habilitations, carrière et suivi administratif           |
| 📋 **Main courante**    | Événements horodatés, modèles, observations et archivage légal                  |
| 📍 **Rondes**           | Circuits de ronde, points de contrôle QR / NFC signés et validation terrain     |
| 🔐 **PTI / DATI**       | SOS, chute, immobilité, agression silencieuse, perte de liaison, levée de doute |
| 👥 **Visiteurs**        | Registre visiteurs et traçabilité des entrées / sorties                         |
| 🔑 **Clés**             | Registre et suivi des clés confiées                                             |
| 🚨 **Incidents**        | Déclaration, suivi et traitement des incidents, y compris par le client         |
| 📑 **Conformité**       | Cartes professionnelles CNAPS, qualifications SSIAP, formations et échéances    |
| 🗂️ **Documents**       | Centralisation et partage des documents opérationnels et administratifs         |
| 💼 **Clients**          | Entreprises clientes, contrats, sites et espace client dédié                    |
| 💶 **Facturation**      | Devis, factures Factur-X, trésorerie et rentabilité                             |
| 🧾 **Paie**             | Récapitulatif des heures et dossier de préparation de paie                      |
| 🏬 **Agences**          | Multi-implantations, responsables d'exploitation, sous-traitants                |
| 📨 **Recrutement**      | Formulaire de candidature public intégrable                                     |
| 💬 **Messagerie**       | Messagerie interne entre le bureau et le terrain                                |
| 🧠 **IA**               | Rapports IA auto-hébergés et assistant IA (MCP)                                 |
| 🔌 **API & Webhooks**   | Espace développeur, webhooks signés, API REST documentée                        |

---

# 🚨 PTI / DATI

La protection du travailleur isolé est un élément central de SEKLYR.

Lorsqu'un agent travaille seul, certaines situations doivent pouvoir déclencher une alerte :

* 🆘 **SOS manuel**
* 🧍 **immobilité prolongée**
* 🤕 **détection de chute**
* 🤫 **agression silencieuse**
* 📡 **perte de liaison**
* ⚠️ autres scénarios configurés par l'entreprise

Lorsqu'une alerte est déclenchée, SEKLYR permet de la transmettre aux **veilleurs désignés par l'employeur** et d'en assurer le suivi opérationnel.

### Une alerte, du déclenchement à la levée de doute

```text
Agent
  │
  │ Déclenchement PTI
  ▼
SEKLYR
  │
  ├── Identification de l'agent
  ├── Identification du site
  ├── Horodatage
  └── Création de l'alerte
          │
          ▼
     Veilleur(s)
          │
          ├── Réception
          ├── Levée de doute
          └── Traitement de l'incident
                  │
                  ▼
             Traçabilité
```

### 📱 Messagerie

SEKLYR **n'est pas un opérateur de télécommunication** et n'exploite pas un service SMS ou vocal mutualisé pour ses clients.

Chaque société configure ses propres fournisseurs de communication, par exemple **smsmode** ou **Twilio**, dans son espace SEKLYR.

Les communications :

* sont envoyées via le compte du client ;
* restent sous le contrat et la facturation du client auprès du fournisseur ;
* sont destinées exclusivement aux salariés désignés comme veilleurs ;
* sont limitées aux communications transactionnelles liées à la sécurité ;
* ne sont pas utilisées à des fins publicitaires ou marketing.

Exemple :

```text
[SEKLYR] SOS déclenché - Jean D.
Site : Entrepôt Nord
12/09/2026 03:14

https://app.seklyr.com/pti/alerts/…
```

Les volumes sont volontairement faibles : une alerte PTI correspond à un événement opérationnel, et non à une campagne de messagerie.

---

# 🏗️ Architecture

SEKLYR est pensé comme une plateforme **multi-tenant** : chaque entreprise dispose de son propre environnement logique et de ses propres données.

```text
                        ┌─────────────────────┐
                        │       SEKLYR        │
                        │       Platform      │
                        └──────────┬──────────┘
                                   │
             ┌─────────────────────┼─────────────────────┐
             │                     │                     │
             ▼                     ▼                     ▼
        Exploitation           Terrain              Administration
             │                     │                     │
       ┌─────┼─────┐         ┌─────┼─────┐        ┌─────┼─────┐
       │     │     │         │     │     │        │     │     │
    Planning Agents Sites   Main  Rondes PTI   Clients Docs Facturation
                           courante
                                   │
                                   ▼
                              Alerting
                         ┌─────────┼─────────┐
                         │         │         │
                        SMS      Vocal   HTTP signé
                         │         │         │
                         └────── Client ──────┘
```

---

# 🧱 Technologie

SEKLYR est une plateforme **API-first**, hébergée en France, disponible sur le web, Android et iOS.

* architecture multi-tenant avec isolation stricte des données par entreprise ;
* API REST documentée pour les intégrations ;
* traitements IA auto-hébergés — aucune donnée transmise à un fournisseur d'IA tiers ;
* sauvegardes chiffrées ;
* fonctionnement hors ligne partiel de l'application terrain.

---

# 🗺️ Roadmap

SEKLYR est développé progressivement autour des besoins réels des sociétés de sécurité privée.

### Exploitation

* [x] Gestion des sociétés
* [x] Gestion des sites (types, sites saisonniers, géofence)
* [x] Gestion des agents (avec ou sans compte)
* [x] Planning, congés, absences et remplacements
* [x] Génération automatique de planning (solveur déterministe)
* [x] Récap des heures et dossier de préparation de paie
* [x] Agences multi-implantations
* [x] Sous-traitants
* [x] Équipe et collaborateurs staff
* [x] Messagerie interne
* [x] Recrutement (formulaire public)
* [ ] Export paie
* [ ] Astreintes

### Terrain

* [x] Main courante électronique (types, modèles, archive annuelle)
* [x] Rondes et circuits QR / NFC
* [x] QR codes signés
* [x] Registre visiteurs
* [x] Registre des clés
* [x] Incidents
* [x] Fiches réflexes
* [x] Matériel incendie
* [x] Carburant et kilométrage
* [x] Trajets GPS et périmètre de pointage
* [x] Rapports IA (LLM auto-hébergé)

### PTI / DATI

* [x] SOS
* [x] Détection de chute
* [x] Détection d'immobilité
* [x] Agression silencieuse
* [x] Perte de liaison
* [x] Levée de doute et gestion des alertes
* [x] Scénarios d'alerte configurables
* [x] Canaux de notification BYO (SMS, appel vocal, HTTP signé)
* [x] Journal complet des événements
* [ ] Transmission vers centres de télésurveillance (SIA DC-09)

### Conformité

* [x] Cartes professionnelles CNAPS (multi-activités, NUB, annuaire public)
* [x] Qualifications et SSIAP (ERP / IGH, registre)
* [x] Moteur de conformité unifié (échéances graduées à 90 jours)
* [x] Alertes de renouvellement
* [x] Formations
* [x] Audits

### Administration

* [x] Documents et partage
* [x] Clients et espace client
* [x] Contrats (reconduction tacite, avenants)
* [x] Devis (formulaire public)
* [x] Factures (cancel-replace)
* [x] Factur-X
* [x] Trésorerie et rentabilité
* [x] Webhooks et espace développeur
* [x] Assistant IA (MCP)
* [ ] Facturation récurrente
* [ ] Transmission PA / e-reporting

> La roadmap évolue en fonction des besoins opérationnels et des retours des entreprises utilisant SEKLYR.

---

# 🔐 Sécurité & conformité

SEKLYR traite des données opérationnelles pouvant être sensibles pour une société de sécurité privée.

La sécurité est donc considérée comme une **fonctionnalité fondamentale**, et non comme une couche ajoutée après coup.

Les principaux axes sont :

* isolation stricte des données par entreprise ;
* contrôle d'accès basé sur les rôles ;
* politiques de sécurité PostgreSQL / RLS ;
* journalisation des événements ;
* traçabilité des opérations ;
* protection des secrets et credentials ;
* limitation des privilèges ;
* validation côté serveur ;
* sécurisation des intégrations externes ;
* sauvegardes chiffrées ;
* tests d'intrusion réguliers.

SEKLYR est destiné à des entreprises relevant du **Livre VI du Code de la sécurité intérieure** et opérant dans le cadre réglementaire du **CNAPS**.

> **Important :** SEKLYR est un outil logiciel. Il ne remplace pas les obligations légales, réglementaires ou opérationnelles de l'entreprise utilisatrice.

---

# 📊 État du projet

> 🚧 **SEKLYR est actuellement en développement actif.**

Certaines fonctionnalités présentées dans ce README sont en cours d'implémentation et peuvent évoluer.

L'objectif n'est pas de construire un simple logiciel de planning, mais une **plateforme d'exploitation complète pour les entreprises de sécurité privée**.

SEKLYR est un logiciel propriétaire. Le code source n'est pas ouvert.

---

# 📬 Contact

**Email :** [contact@seklyr.fr](mailto:contact@seklyr.fr)

**Site web :** [seklyr.fr](https://seklyr.fr) (*Attention, le site vitrine n'est pas encore en ligne*)
