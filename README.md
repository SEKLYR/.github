# SEKLYR

**Logiciel de gestion pour les entreprises de sécurité privée.**

SEKLYR est un éditeur de logiciel (SaaS) destiné aux sociétés de sécurité privée et de gardiennage soumises au Code de la sécurité intérieure (Livre VI) et au contrôle du CNAPS. La plateforme couvre le quotidien d'une société de sécurité : planning des vacations, main courante électronique, rondes par points de contrôle, conformité des agents (cartes professionnelles, qualifications SSIAP), gestion des sites clients et **protection du travailleur isolé (PTI / DATI)**.

## Ce que fait la plateforme

| Domaine | Fonction |
|---|---|
| Exploitation | Planning des agents, affectation par site, gestion des congés et des heures |
| Terrain | Main courante électronique horodatée, rondes QR/NFC, registre visiteurs et clés |
| Conformité | Suivi des cartes professionnelles CNAPS, qualifications, aptitudes médicales |
| Sécurité des agents | Protection du travailleur isolé : détection de chute, SOS, perte de liaison, levée de doute tracée |
| Administration | Documents, contrats clients, devis et factures au format Factur-X |

## Utilisation de services de messagerie (SMS, appel vocal, WhatsApp)

La fonction **PTI / DATI** (Protection du Travailleur Isolé / Dispositif d'Alarme pour Travailleur Isolé) alerte les responsables désignés d'une société lorsqu'un agent de sécurité seul sur un site est en difficulté : SOS déclenché, chute détectée, immobilité prolongée, agression silencieuse ou perte de liaison du téléphone.

SEKLYR **n'opère aucun canal SMS, vocal ou WhatsApp pour le compte de ses clients**. Le modèle est le suivant :

- chaque société cliente renseigne **son propre compte** prestataire (par exemple Twilio) dans son espace de configuration ;
- les messages sont envoyés **par ce compte**, sous le contrat et la facturation de la société cliente ;
- les destinataires sont exclusivement des **salariés de cette société** (« veilleurs ») désignés nommément par leur employeur pour recevoir les alertes de sécurité ;
- les messages sont **uniquement transactionnels et liés à la sécurité des personnes** : aucune prospection, aucun marketing, aucun message vers le grand public.

Un message type ressemble à :

```
[SEKLYR] SOS déclenché - Jean D.
Site : Entrepôt Nord - 12/09/2026 03:14
https://app.seklyr.com/pti/alerts/…
```

Les volumes sont faibles par nature (une alerte est un événement exceptionnel) : de l'ordre de quelques dizaines de messages par mois et par société cliente, en France métropolitaine.

## Contact

Site : **Non disponible pour le moment**
Contact : chteau@proton.me
