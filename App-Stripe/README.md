# Application 1 : Stripe Checkout

**Projet E5 5SDWANA Metz**  
**Test effectué le 4 novembre 2026**  
**Statut : paiement de test validé**

## Présentation

Cette application permet de simuler un achat en ligne à l'aide de **Stripe Checkout**, dans un environnement de test. Elle est déployée sur **Minikube / Kubernetes** et communique avec Stripe pour traiter le paiement.

## Vérifications réalisées

- L'application est accessible depuis un poste Windows grâce à un transfert de port Kubernetes vers le service `stripe-service-ch-04-11-2026` dans le namespace `preprod-ch-04-11-2026`.
- Une requête HTTP vers l'application a retourné le code **200 OK**.
- Un achat fictif de **250,00 €** a été effectué avec une carte de test Stripe.
- Le paiement apparaît avec le statut **« Réussi »** dans le Dashboard Stripe en mode test.
- Le navigateur a été redirigé vers la page de confirmation après le paiement.

## Captures d'écran

### 1. Paiement confirmé dans Stripe

![Paiement de test de 250 euros confirmé dans Stripe](paiement-reussi.png)

### 2. Confirmation affichée par l'application

![Page de confirmation après le paiement](confirmation-web.png)

### 3. Transfert du port Kubernetes

![Commande kubectl port-forward pour accéder à l'application](port-forward.png)

### 4. Vérification HTTP depuis Windows

![Réponse HTTP 200 depuis le poste Windows](test-http-200.png)

## Bilan

Le **parcours de paiement Stripe en environnement de test fonctionne** : l'application est joignable, la transaction de 250 € est confirmée sur Stripe et une page de confirmation s'affiche.

Ces captures ne démontrent **pas encore** le fonctionnement des trois replicas, du HPA ou le déploiement dans les trois namespaces. Ces points seront validés séparément pendant le TP.

[Retour au README principal](../../README.md)
