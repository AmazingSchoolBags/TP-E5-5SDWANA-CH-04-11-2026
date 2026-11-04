# Difficultés rencontrées et solutions apportées

**Projet :** TP E5 5SDWANA Metz  
**Date :** 4 novembre 2026  
**Groupe :** Mohamed CHAOUAY TISSIR et Mattéo HEIB

## 1. Découverte et configuration de Netdata

**Difficulté rencontrée :**

La mise en place de Netdata a été l'une des parties les plus nouvelles pour notre groupe.

Nous avions déjà travaillé sur les Deployments, les Services et les HPA pendant les cours, mais nous connaissions moins les outils d'observabilité.

Nous avons donc consacré davantage de temps à comprendre le fonctionnement de Netdata et à interpréter les graphiques CPU et RAM.

**Solution apportée :**

Nous avons installé Netdata dans un namespace dédié, `observability-ch-04-11-2026`, avec un Deployment et un Service NodePort.

Nous avons ensuite réalisé un test de charge CPU et observé son évolution dans l'interface Netdata.

Cette solution d'observabilité système a été validée par notre professeur.

**Ce que nous avons appris :**

L'observabilité permet de visualiser l'utilisation des ressources et de mieux comprendre le comportement d'un environnement pendant une montée en charge.

---

## 2. Disparition des événements Kubernetes

**Difficulté rencontrée :**

Lors de la récupération des événements Kubernetes, nous avons exécuté la commande suivante :

```bash
kubectl get events -A
```

Kubernetes nous a retourné :

```text
No resources found
```

Nous avons ensuite compris que les événements Kubernetes étaient temporaires et pouvaient être automatiquement supprimés après un certain délai.

Nous avions effectué certains tests plusieurs heures auparavant, ce qui expliquait l'absence d'événements lors de notre première tentative de récupération.

**Solution apportée :**

Heureusement, nous avions conservé des captures d'écran des événements pendant les tests HPA.

Nous avons également réalisé des exports des événements disponibles et organisé les fichiers de logs par namespace dans notre dépôt GitHub.

**Ce que nous avons appris :**

Il est important de récupérer les événements et les logs pendant les manipulations, plutôt que d'attendre la fin du projet.

---

## 3. Choix de la méthode de déploiement : Docker avant Kubernetes

**Difficulté évitée grâce à notre réflexion :**

Au début du projet, nous envisagions de déployer directement les applications sur Minikube.

Cependant, après réflexion et en suivant les conseils de notre professeur, nous avons décidé de commencer par tester les images avec Docker.

L'objectif était d'éviter de chercher une erreur Kubernetes alors que le problème pouvait simplement provenir de l'application ou de son image Docker.

**Méthode retenue :**

1. Sélectionner les applications et leurs images Docker.
2. Tester leur fonctionnement avec Docker.
3. Vérifier leur accessibilité et leurs ports.
4. Préparer les fichiers YAML Kubernetes.
5. Déployer les applications sur Minikube.
6. Vérifier les Services et les pods.
7. Réaliser les tests de charge et les tests HPA.

**Ce que nous avons appris :**

Il vaut mieux valider progressivement chaque composant plutôt que de tout déployer immédiatement.

Cette méthode nous a permis de mieux organiser notre travail et de faciliter les vérifications.

---

## 4. Bilan des difficultés

Ces situations nous ont permis de mieux comprendre l'importance de la préparation, de la documentation et des vérifications progressives.

Nous retenons principalement trois enseignements :

- Tester les applications avec Docker avant leur déploiement dans Kubernetes.
- Conserver les événements Kubernetes et les logs pendant les tests.
- Prendre le temps de comprendre les outils d'observabilité pour interpréter correctement les résultats.

Nous avons également compris qu'un projet ne consiste pas uniquement à faire fonctionner les applications, mais aussi à être capable d'expliquer les choix réalisés, les difficultés rencontrées et les solutions retenues.
