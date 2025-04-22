# Installation et configuration de Velociraptor

Ce document décrit les étapes suivies pour installer et configurer Velociraptor dans le cadre de notre projet de simulation d’attaque APT41.

---

## 1. Création du répertoire de travail

Un dossier a été créé pour organiser les fichiers d'installation de Velociraptor :
```bash
mkdir /home/Velociraptor
cd /home/Velociraptor
```

## 2. Récupération et préparation du binaire

Le binaire Linux de Velociraptor (version 0.73.4) a été téléchargé et rendu exécutable :
```bash
chmod +x /home/magatte/velociraptor-v0.73.4-linux-amd64
mv /home/magatte/velociraptor-v0.73.4-linux-amd64 .
```

## 3. Génération du fichier de configuration du serveur

La configuration du serveur a été créée via une interface interactive :
```bash
./velociraptor-v0.73.4-linux-amd64 config generate -i
```

Cela a généré un fichier `server.config.yaml` à utiliser pour le déploiement.

## 4. Lancement du serveur Velociraptor

Le serveur a été lancé avec le fichier de configuration généré :
```bash
./velociraptor-v0.73.4-linux-amd64 --config server.config.yaml debian server --binary velociraptor-v0.73.4-linux-amd64
```

## 5. Ajout d'un utilisateur administrateur

Pour accéder à l'interface web et administrer Velociraptor, un utilisateur admin a été créé :
```bash
sudo velociraptor --config /etc/velociraptor/server.config.yaml user add admin --role administrator
```

## 6. Génération de la configuration client

Enfin, pour connecter une machine cible au serveur, la configuration de l'agent client a été générée à partir de la configuration serveur :
```bash
./velociraptor-v0.73.4-linux-amd64 --config /etc/velociraptor/server.config.yaml config client > client.config.yaml
```

Le fichier `client.config.yaml` a ensuite été transféré sur la machine Windows cible pour lancer l’agent client.

## 7. Contrôles réseaux

Quelques vérifications ont été effectuées pour s'assurer que le service était bien actif :
```bash
sudo systemctl status velociraptor_server
sudo netstat -tulnp | grep 8000
```

---

