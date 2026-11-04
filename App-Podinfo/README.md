# Application 2 : Podinfo (Go)

**Projet E5 5SDWANA Metz — Groupe Mohamed CHAOUAY TISSIR et Mattéo HEIB**  
**État : application accessible, premier test HTTP validé — 04/11/2026**

## Présentation

Podinfo est une petite application web développée en **Go**, utilisée pour tester les déploiements Kubernetes et, plus tard, l'autoscaling avec le HPA.

Nous avons choisi l'image Docker Hub [`stefanprodan/podinfo:6.17.0`](https://hub.docker.com/r/stefanprodan/podinfo), légère et facile à démarrer.

## Configuration observée

| Élément | Valeur |
|---|---|
| Application | Podinfo v6.17.0 |
| Namespace | `preprod-ch-04-11-2026` |
| Deployment | `podinfo-deployment-ch-04-11-2026` |
| Service | `podinfo-service-ch-04-11-2026` |
| Port applicatif | `9898` |
| Accès testé | Transfert de port Kubernetes |

## Tests réalisés

- Ouverture de l'interface Podinfo depuis un poste Windows : **page affichée correctement**.
- Vérification de la réponse HTTP depuis PowerShell : **`200 OK`**.
- Vérification du transfert de port vers le Service Kubernetes.

Commande utilisée pour le test d'accès :

```bash
kubectl port-forward -n preprod-ch-04-11-2026 \
  svc/podinfo-service-ch-04-11-2026 9898:9898 --address 0.0.0.0
```

Le paramètre `--address 0.0.0.0` a servi au test depuis un autre poste. Il expose le port sur toutes les interfaces de la VM : à limiter au réseau de test et à arrêter après utilisation. Ce transfert temporaire ne prouve pas encore l'accès externe définitif par le Service.

## Captures de vérification

**1. Interface Podinfo**

![Interface Podinfo v6.17.0](interface-podinfo.png)

**2. Test HTTP 200 depuis Windows**

![Réponse HTTP 200](test-http-200.png)

**3. Transfert de port Kubernetes**

![Commande port-forward du service Podinfo](port-forward.png)

## À poursuivre

Vérifier les **3 replicas**, confirmer le type de Service prévu pour l'accès externe, puis réaliser les tests de charge k6 et le HPA de **3 à 20 pods**. Répéter ensuite le déploiement dans les environnements `mlops` et `prod`.
