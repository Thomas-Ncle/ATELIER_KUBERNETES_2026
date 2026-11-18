# Rendu — Atelier Kubernetes

> Complétez ce fichier au fil de l'atelier, puis faites un commit et un push (voir la section « Rendu » du README).

**Nom / Prénom : NICOLLE / Thomas**
**Groupe : ING3 APP-RS2**

---

## Exercice 1 — Cluster

1. Combien de nœuds affiche `kubectl get nodes` ? Quel est le rôle de chacun ?
   > Il affiche 3 nodes, le controlplane(server) et deux workers (agent0 et 1). Le controlplane sera le gestionnaire des pods et les workers permettront d'accueillir les pods.
2. Que montre `docker ps` ? Qu'est-ce qu'un « nœud » dans k3d, concrètement ?
   > Docker ps montre un container en plus, le loadbalancer. Un noeud c'est une machine avec un des deux rôles (controleppane ou worker).

## Exercice 2 — Premier déploiement

3. Quels objets Kubernetes ont été créés par `kubectl create deployment` ? (indice : `kubectl get all`)
   > 3 objets ont été créés : un pod, un service, un deployment et un replicatset.
4. Vous avez supprimé le pod `web-...` : que s'est-il passé, et pourquoi ?
   > Un nouveau pod c'est créé, car le replicatset est set à 1.

## Exercice 3 — Modifier un conteneur en direct

5. Après suppression du pod, votre message « Bienvenue... » a-t-il survécu ? Pourquoi ?
   > Non, car le container est recréé avec l'image ngix de base.
6. Pourquoi le `port-forward` a-t-il cessé de fonctionner après la suppression du pod ?
   > Le port-forward ne s'attache qu'a 1 seul pod.

## Exercice 4 — Déclaratif

7. Quelle différence entre `kubectl create` et `kubectl apply` ?
   > kubectl apply permet d'appliquer une configuration à une ressource, alors que create va créer la ressource.
8. À quoi sert le `selector` d'un Service ? Que se passe-t-il s'il ne correspond à aucun pod ?
   > Le selector d’un Service indique quels Pods il cible, en faisant correspondre leurs labels. Par exemple, selector: app: web sélectionne les Pods portant le label app=web. Kubernetes utilise ces Pods comme points de terminaison du Service et répartit le trafic entre eux. Le Service et les Pods doivent être dans le même namespace. S’il ne correspond à aucun Pod, le Service existe toujours, mais il n’a aucun endpoint vers lequel acheminer le trafic : les connexions au Service ne peuvent donc pas atteindre d’application.

## Exercice 5 — Scaling & mises à jour

9. Sur quels nœuds se trouvent vos 3 réplicas ? Collez la sortie de `kubectl get pods -l app=site -o wide`.
```  
NAME                   READY   STATUS    RESTARTS   AGE     IP          NODE               NOMINATED NODE   READINESS GATES
site-75775484b-bjrmb   1/1     Running   0          7m9s    10.42.0.9   k3d-lab-agent-0    <none>           <none>
site-75775484b-mrdqz   1/1     Running   0          7m10s   10.42.1.6   k3d-lab-agent-1    <none>           <none>
site-75775484b-nqtgh   1/1     Running   0          7m9s    10.42.2.6   k3d-lab-server-0   <none>           <none>
```  
10. Avec l'image `nginx:9.99`, quel statut avait le pod ? Quelle commande vous a donné la cause ?
    >
11. Pendant la panne, le site restait-il accessible ? Pourquoi ?
    >

## Exercice 6 — Portainer & Mario

12. URL publique de votre Mario :
    >
13. Retrouvez le Deployment `mario` en ligne de commande. Portainer et `kubectl` parlent-ils au même composant ? Lequel ?
    >

## Bonus (facultatif)

14. Bonus réalisés et remarques :
    >

---

**Score obtenu avec `./scripts/check.sh` :** ... / ...
