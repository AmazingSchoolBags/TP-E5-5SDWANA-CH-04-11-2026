# Application 3 : Dashboard Maker (interne)

**Projet :** TP E5 5SDWANA Metz  
**Groupe :** Mohamed CHAOUAY TISSIR et Mattéo HEIB  
**Statut :** service interne accessible, réponse HTTP 200 vérifiée.

## Objectif

Déployer la troisième application du TP dans Kubernetes avec un accès **interne uniquement**, grâce à un Service de type `ClusterIP`.

## Configuration relevée

| Élément | Valeur |
|---|---|
| Application choisie | Dashboard Maker (Flask) |
| Namespace | `preprod-ch-04-11-2026` |
| Deployment | `interne-deployment-ch-04-11-2026` |
| Service | `interne-service-ch-04-11-2026` |
| Type de Service | `ClusterIP` |
| Port | `5000` |
| Adresse IP observée | `10.100.46.117` (attribuée par le cluster, susceptible de changer) |

## Vérifications réalisées

1. **Vérification du manifeste** avec `kubectl apply --dry-run=client -f app3-interne.yaml`. Kubernetes indique que le Deployment et le Service seraient inchangés : cette commande contrôle le manifeste mais **ne réalise pas un nouveau déploiement**.
2. **Vérification du Service** avec `kubectl get svc -n preprod-ch-04-11-2026`. Le Service interne apparaît en `ClusterIP`, sur le port `5000`.
3. **Test HTTP depuis le nœud Minikube** avec `curl -i 10.100.46.117:5000`. Le serveur répond `HTTP/1.1 200 OK` et renvoie une page HTML.

## Captures

**Vérification du manifeste (dry-run)**

![Vérification du YAML](verification-dry-run.png)

**Service interne ClusterIP**

![Service ClusterIP](service-clusterip.png)

**Réponse HTTP 200 depuis Minikube**

![Réponse HTTP de l'application interne](test-http-200-interne.png)

## Étapes restantes

- Vérifier la référence exacte de l'image Docker dans le Deployment et confirmer les **3 replicas**.
- Tester le HPA (**3 à 20 pods**) avec k6 et analyser les métriques.
- Reproduire et vérifier l'application dans `mlops` et `prod`.

> Les captures démontrent un accès HTTP depuis le nœud Minikube. Elles ne prouvent pas encore l'autoscaling ni les trois replicas. Le Service `ClusterIP` n'est pas exposé directement à l'extérieur.
