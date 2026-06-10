# Gestion des artefacts sur Cloud Pi Native

Vous en êtes à l'étape 3 de la formation CPiN :
1. [Gestion des projets CPiN](https://github.com/cloud-pi-native/formation-cpin-gestion-projet)
2. [Application d'exemple pour déploiement sur CPiN](https://github.com/cloud-pi-native/formation-cpin-repo-applicatif)
3. ➡️ [Gestion des artefacts sur CPiN](https://github.com/cloud-pi-native/formation-cpin-harbor-trivy)
4. [Chart Helm de démonstration sur CPiN](https://github.com/cloud-pi-native/formation-cpin-deploiement)
5. [Gestion des secrets sur CPIN](https://github.com/cloud-pi-native/formation-cpin-gestion-secret)
6. [Observabilité sur CPiN](https://github.com/cloud-pi-native/formation-cpin-observabilite)

## Stockage des artefacts

Lors du build précédent, l'image docker créée se nomme ***java-demo*** et a été envoyé sur le gestionnaire d'artefacts 
de CPiN Harbor.

### Harbor

Harbor est le gestionnaire d'artefact de CPiN. À ce titre, il stocke l'ensemble des images construites via Gitlab-CI. 
Il est également possible de faire récupérer des images externes à travers Harbor, c'est notamment le cas lors 
d'utilisation d'images fournies par un éditeur dont le projet ou le ministère ne possède pas le code source.

Il est possible de récupérer les références Harbor des images construites de plusieurs façons :  

#### Récupération depuis la console

▶️ Depuis la console CPiN, cliquez sur le bouton `Afficher les secrets des services`. Il est possible de voir 
l'URL de son projet sur Harbor : 

![secret des services](./img/secret-des-services.png)

#### Récupération depuis Gitlab-CI

Depuis Gitlab, lors de l'étape de construction du projet, il est possible de voir l'upload de son image dans les logs
du pipeline Gitlab-CI : 

▶️ Pour cela, allez sur Gitlab dans le dépôt *app-java* et dans le menu de gauche, sélectionnez `build`>`pipelines`.
Sur votre dernier build réussi, cliquez sur la dernière des 3 coches vertes d'étapes de build et sur l'étape 
*docker-build* dans le panneau qui se déplie.

![build stage docker](./img/build-stage-docker.png)

La fin des logs indique l'étape d'upload de l'image sur Harbor. Vous y retrouvez l'URL d'upload de votre image :

![build upload Harbor](./img/logs-build-to-harbor.png)

#### Récupération depuis Harbor

▶️ Depuis la console, dans l'onglet `Services externes`, cliquez sur la tuile Harbor pour accéder directement à votre
espace projet :

![services externes](./img/services-externes.png)

Vous accédez directement à votre espace projet et vous pouvez y retrouver toutes vos images :

![images harbor](./img/harbor-espace-projet.png)

▶️ Cliquez sur votre image. Il est possible de voir les différents tags de votre image, dans notre cas, il n'y en a 
qu'un seul : *tuto*. Il est également possible de voir les informations de signature de l'image, de taille et du nombre
de vulnérabilités *Trivy*.

![Harbor details d'une image](./img/harbor-detail-image.png)

▶️ Cliquez sur le sha de l'image pour en afficher tous les détails. Vous y retrouvez la liste des vulnérabilités 
remontées par Trivy.

> [!NOTE] 
> À noter qu'un dashboard dédié à Trivy sur Grafana est également présent dans les dashboards par défaut (au MI).

Bravo, vous avez terminé la partie 3 de la formation CPiN sur Harbor et Trivy.

Vous pouvez passer à l'étape 4 : [Chart Helm de démonstration sur CPiN](https://github.com/cloud-pi-native/formation-cpin-deploiement)