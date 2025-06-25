# Nextcloud All-in-One
Méthode officielle d'installation Nextcloud. Nextcloud AIO offre un déploiement et une maintenance simple et rapide pour la plus part des fonctionnalités incluses dans cette instance Nextcloud unique.

Les fonctionnalités incluses sont :
- Nextcloud
- Un backend haute performance pour Nextcloud Files
- Nextcloud Office (Optionnel)
- Un backend haute eprformance pour Nextcloud Talk (visionconférence) et TURN-server (optionnels)
- Serveur d'enregistrement Nextcloud Talk (optionnel)
- Service de Backup intégré (optionnel, basé sur [BorgBackup](https://github.com/borgbackup/borg#what-is-borgbackup))
- Imaginary (service de miniature des fichiers (heic, pdf, heif, illustrator, svg, tiff and webp), optionnel)
- ClamAV (Service antivirus pour Nextcloud, optionnel)
- FulltextSearch (Recherche de fichiers, Optionnel)
- Whiteboard (optionnel)
- Docker Socket Proxy (requis pour [Nextcloud App API](https://github.com/cloud-py-api/app_api#nextcloud-appapi), optionnel)
- [Conteneurs communautaires](https://github.com/nextcloud/all-in-one/tree/main/community-containers#community-containers)
<details><summary>Et beaucoup plus :</summary>

Interface web ergonomique qui permet une facilité d'installation et de maintenance.
- Mises à jour incluses, simple à réaliser.
- Notifications de mise à jour et de sauvegarde.
- Les sauvegardes quotidiennes peuvent être activées à partir de l'interface AIO qui permet également de mettre à jour tous Nextcloud, tous les conteneurs et ses applications, de manière automatique.
- Restauration d'instance à partir de l'archive de sauvegarde via l'interface AIO (vous avez seulement besoin de l'archive et du mot de passe pour restaurer l'instance entière sur une nouvelle instance AIO).
- **APCu** comme cache local.
- **Redis** comme cache distribué et pour le verrouillage des fichiers.
- **Postgresql** comme base de données.
- **PHP-FPM** avec une configuration optimisée pour les performances (par exemple, Opcache et JIT activés par défaut). Opcache et JIT activés par défaut).
- Sécurité A+ dans le scan de sécurité Nextcloud.
- Prêt à être utilisé derrière un Reverse-Proxy existant.
- Peut être utilisé derrière Cloudflare (Tunnel notamment).
- Compatible Tailscale.
- Prêt pour des téléchargements de gros fichiers jusqu'à 10 GB sur des liens publics, ajustable (les utilisateurs connectés peuvent télécharger des fichiers beaucoup plus gros en utilisant l'interface web ou les clients mobiles/de bureau puisque le chunking est utilisé dans ce cas)
- Les timeouts de PHP et du serveur web sont réglés à 3600s, réglable (important pour les téléchargements de gros fichiers)
- 512 Mo de RAM maximum par processus PHP par défaut, réglable.
- TLS inclus (en utilisant Let's Encrypt).
- Compression Brotli activée par défaut pour les fichiers javascript, css et svg, ce qui réduit les temps de chargement de Nextcloud.
- HTTP/2 et HTTP/3 activés.
- Les "Pretty URLs" pour Nextcloud sont activés par défaut (supprime l'index.php de tous les liens)
- Les aperçus vidéo fonctionnent dès le départ et lorsque Imaginary est activé, de nombreux formats d'image récents également !
- Un seul domaine et non plusieurs domaines sont nécessaires pour que tout fonctionne (habituellement, vous devriez avoir un domaine pour chaque service, ce qui est beaucoup plus complexe).
- Emplacement ajustable du répertoire de données de Nextcloud (par ex. bon pour faciliter le partage de fichiers avec le système hôte sur Windows et MacOS).
- Par défaut confiné (bon pour la sécurité) mais peut permettre l'accès à des stockages supplémentaires afin de permettre l'utilisation de la fonction de stockage externe local.
- Possibilité incluse d'ajuster les applications Nextcloud installées par défaut.
- L'installation de Nextcloud n'est pas en lecture seule - cela signifie que vous pouvez appliquer des correctifs si vous en avez besoin (au lieu d'avoir à attendre la prochaine version pour qu'ils soient appliqués).
ffmpeg, smbclient, libreoffice et nodejs sont inclus par défaut.
- Possibilité d'ajouter en permanence des paquets OS supplémentaires dans le conteneur Nextcloud sans avoir à construire sa propre image Docker.
- Possibilité d'ajouter en permanence des extensions PHP supplémentaires dans le conteneur Nextcloud sans avoir à construire sa propre image Docker.
- Possibilité de passer le périphérique nécessaire pour le transcodage matériel au conteneur Nextcloud.
- Possibilité de stocker tous les fichiers liés à Nextcloud sur un disque séparé.
- LDAP peut être utilisé comme backend d'utilisateur pour Nextcloud.
- La migration de n'importe quelle ancienne installation Nextcloud vers AIO est possible. Voir cette documentation.
- Fail2Ban peut être ajouté.
- phpMyAdmin, Adminer ou pgAdmin peuvent être ajoutés.
- Un serveur mail peut être ajouté.
- Nextcloud peut être accédé localement via le domaine.
- Peut être installé localement (si vous ne voulez pas ou ne pouvez pas rendre l'instance publiquement accessible).
- IPv6-ready.
- Peut être utilisé avec Docker rootless (bon pour une sécurité supplémentaire).
- Fonctionne sur toutes les plates-formes supportées par Docker (par ex. également sur Windows et Macos).
- Les conteneurs inclus sont faciles à déboguer grâce à la possibilité de consulter leurs journaux directement à partir de l'interface AIO.
- Prêt pour Docker-compose.
- Peut être installé sans qu'un conteneur ait accès au socket Docker.
- Peut être installé avec Docker Swarm.
- Peut être installé avec Kubernetes.
- Presque tous les conteneurs inclus sont basés sur Alpine Linux (bon pour la sécurité et la taille des conteneurs).
- De nombreux conteneurs inclus fonctionnent en tant qu'utilisateur non root (bon pour la sécurité).
- De nombreux conteneurs inclus ont un root-FS en lecture seule (bon pour la sécurité).
- Les conteneurs inclus s'exécutent dans leur propre réseau Docker (bon pour la sécurité) et seuls les ports vraiment nécessaires sont exposés sur l'hôte.
- Plusieurs instances sur un serveur sont réalisables sans avoir à gérer des VM.
- Chemin de sauvegarde ajustable ou référentiel Borg distant depuis l'interface AIO (il est bon de placer les sauvegardes par exemple sur un lecteur différent si l'on utilise un chemin de sauvegarde local). sur un lecteur différent si vous utilisez un chemin de sauvegarde local).
- Possibilité incluse de sauvegarder également des volumes Docker externes ou des chemins d'hôte (peut être utilisé pour les sauvegardes d'hôte).
- La sauvegarde Borg peut être entièrement gérée à partir de l'interface AIO, y compris la création de sauvegarde, la restauration de sauvegarde, la vérification de l'intégrité de la sauvegarde et la réparation de l'intégrité.
- D'autres formes de sauvegarde à distance sont indirectement possibles.
- Les mises à jour et les sauvegardes peuvent être exécutées à partir d'un script externe. Voir cette documentation pour un exemple complet.
</details>

## Screenshots
| Première configuration | Après l'installation |
|---|---|
| ![image](https://github.com/user-attachments/assets/6ef5d7b5-86f2-402c-bc6c-b633af2ca7dd) | ![image](https://github.com/user-attachments/assets/939d0fdf-436f-433d-82d3-27548263a040) |

## Comment l'utiliser ?
> [!NOTE]
> Les instructions suivantes sont destinées à une installation sans serveur web ni reverse proxy (comme Apache, Nginx, Caddy, Tunnel Cloudflare ...) qui soient déjà configurés dans votre réseau. Si vous voulez configurer AIO derrière un serveur Web ou un reverse proxy (comme Apache, Nginx, Caddy, Tunnel Cloudflare ...), regardez la [documentation dédiée au reverse proxy](https://github.com/nextcloud/all-in-one/blob/main/reverse-proxy.md).
De plus, les instructions d'installations ci-dessous concernent spécifiquement et uniquement Linux. Pour les autres systèmes, consultez leur documentation ([MacOS](https://github.com/nextcloud/all-in-one?tab=readme-ov-file#how-to-run-aio-on-macos), [Windows](https://github.com/nextcloud/all-in-one?tab=readme-ov-file#how-to-run-aio-on-windows), [Synology](https://github.com/nextcloud/all-in-one?tab=readme-ov-file#how-to-run-aio-on-synology-dsm)).

1. Installer docker sur votre distribution Linux en suivant la documentation officielle : https://docs.docker.com/engine/install/#supported-platforms.
>[!WARNING]
> Vous pouvez utiliser le script de confort qui est ci-dessous pour installer docker. Toutefois, nous ne recommandons par de télécharger et exécuter le script aveuglement en tant que superutilisateur (sudo). Voir plus: 

<details>
    <summary>En utilisant le script rapide</summary>

```sh
curl -fsSL https://get.docker.com | sudo sh
```

</details>

2. Si vous avez besoin d'activer IPv6, vous devez l'activer comme indiqué dans la documentation : https://github.com/nextcloud/all-in-one/blob/main/docker-ipv6-support.md.
3. Exécuter la commande ci-dessous pour démarrer le conteneur sur linux et sans serveur Web ni reverse proxy (comme Apache, Nginx, Caddy, Tunnel Cloudflare ...) déjà configuré :
    ```
    # Pour Linux, sans werveur Web ni reverse Proxy (Comme Apache, Nginx, Caddy, Tunnel Cloudflare...) déjà installés:
    sudo docker run \
    --init \
    --sig-proxy=false \
    --name nextcloud-aio-mastercontainer \
    --restart always \
    --publish 80:80 \
    --publish 8080:8080 \
    --publish 8443:8443 \
    --volume nextcloud_aio_mastercontainer:/mnt/docker-aio-config \
    --volume /var/run/docker.sock:/var/run/docker.sock:ro \
    ghcr.io/nextcloud-releases/all-in-one:latest
    ```
    <details>
    <summary>Explications de la commande</summary>

    - `sudo docker run` Cette commande monte un nouveau conteneur docker. Les commandes optionnelles de Docker peuvent être utilisées sans `sudo` si l'utilisateur a été ajouté group d'utilisateur docker (ce n'est pas le même que docker rootless, consultez la FAQ plus bas).
    - `--init` Cette option assure qu'aucun processus zombie n'a été créé. Consultez la [documentation Docker](https://docs.docker.com/reference/cli/docker/container/run/#init) pour plus d'informations à ce sujet.
    - `--sig-proxy=false` Cette option permet de quitter le shell du conteneur qui est créé automatiquement à l'utilisation de `docker run`en utilisant `[CTRL] + C` sans éteindre le conteneur.
    - `--name nextcloud-aio-mastercontainer` C'est le nom du conteneur. Cette ligne ne doit pas être changée, sinon les mises à jour du masterContainer échoueront.
    - `--restart always` C'est la politique de redémarrage. Always signifie que le conteneur redémarrera toujours avec le Daemon Docker. Consultez la documentation pour plus de détails concernant les politiques de redémarrage : https://docs.docker.com/config/containers/start-containers-automatically/
    - `--publish 80:80` Le port 80 du conteneur sera publié surle port 80 de l'hôte (machine physique). Il est utilisé pour obtenir les certificats SSL pour l'interface de AIO si vous voulez utiliser le port 8443. Il n'est pas requis si vous utilisez AIO derrière un serveur Web ou un reverse proxy et peut être retiré de la commande, puisque vous pouvez simplement utiliser le port 8080 pour l'interface.
    - `--publish 8080:8080` Le port 8080 du conteneur est publié sur le port 8080 de l'hôte. Ce port est utilisé par l'interface AIO et utilise un certificat autosigné par défaut. Vous pouvez utiliser un port différent si le port 8080 est déjà utilisé par un autre processus sur votre hôte (machine physique). Par exemple, `--publish 8081:8080`(Rappel de la syntaxe : **port_hôte:port_conteneur**. Seul le port hôte change ici, car le service du conteneur écoute toujours en 8080).
    - `--publish 8443:8443` Le port 8443 du conteneur est publié sur le port 8443 de l'hôte (machine physique). Si vous publiez le port 80 et 8443 sur internet (publique), vous pourrez accéder à l'interface AIO via le port 8443, avec un certificat valide. Ce n'est pas nécessaire si vous utilisez AIO derrière un serveur Web ou un reverse proxy et peut être supprimé de la commande le cas échéant, puisque on peut simplement utiliser le port 8080.
    - `--volume nextcloud_aio_mastercontainer:/mnt/docker-aio-config` Permet de configurer le stockage des fichier. Les fichiers créé par le mastercontainer seront stockés dans un volume docker nommé `nextcloud_aio_mastercontainer`. Cette ligne ne doit pas être modifiée, sinon le système de backup intégré ne fonctionnera plus.
    - `--volume /var/run/docker.sock:/var/run/docker.sock:ro` La socket Docker est montée dans le onteneur qui est utilisé pour la mise en place de tous les autres conteneur et d'autres fonctionnalités. Il a besoin d'être ajusté/modifié sur Windows et MacOS et sur docker rootless. Consultez la documentation officielle. Si vous modifié ce paramètre, n'oubliez pas de définir `WATCHTOWER_DOCKER_SOCKET_PATH`! Si vous ne voulez pas faire de cette manière, consultez https://github.com/nextcloud/all-in-one/tree/main/manual-install.
    - `ghcr.io/nextcloud-releases/all-in-one:latest` C'est l'image du conteneur docker qui est utilisée.
    - Pluusieurs autres options peuvent être défini en utilisant les variables d'environnement, par exemple : `--env NEXTCLOUD_DATADIR="/mnt/ncdata"` (C'est un exemple pour Linux. Consultez la [documentation associée](https://github.com/nextcloud/all-in-one#how-to-change-the-default-location-of-nextclouds-datadir) pour les autres OS' et pour l'explication de ce que font chaque valeur. Cette valeur spécifiquement a besoin d'être spécifiée lors du première démarrage si vous voulez la changer pour un chemin spécifique à la place du chemin par défaut des volumes Docker. Pour plus d'explications et des exemples pour les autres variables (Comme changer la localisation du répertoire de données de Nextcloud ou monter des répertoires en tant que Stockage Externe dans le conteneur Nextcloud), consultez ce readme et regardez le fichier docker-compose associé : https://github.com/nextcloud/all-in-one/blob/main/compose.yaml
    </details>

    Note: Vous pourriez être vouloir changer le le répertoire de données de Nextcloud pour stocker les fichier à un endroit différent du volume docker par défaut. Consultez la [documentation](https://github.com/nextcloud/all-in-one#how-to-change-the-default-location-of-nextclouds-datadir) pour voir comment faire.

4. Après le premier démarrage, vous devriez pouvoir accéder à l'interface AIO sur le port 8080 de ce serveur.<br>
Exemple : `https://adresse.ip.de.ce.serveur:8080`<br>
⚠️ **Important:** Utilisez toujours une adresse IP si vous accédez à ce port, et non un domain car HSTS bloquera plus tard ! (Il est aussi attendu que ce port utilise un certificat auto-signé qui requiert une que vous acceptiez l'exception de sécurité depuis votre navigateur web<br><br>
Si votre pare-feu/routeur a les ports 80 et 8443 open/forwarded et que vous pointez un domaine vers votre serveur, vous pouvez obtenir un certificat automatiquement en ouvrant l'interface Nextcloud AIO via :<br>
`https://your-domain-that-points-to-this-server.tld:8443`
5. N'oubliez pas d'ouvrir les ports `3478/TCP` et `3478/UDP` dans votre pare-feu/routeur pour le conteneur Talk (visionconférence).

# FAQ
- [TOC](#faq)
    - [Où puis-je trouver de la documentation ?](#where-can-i-find-additional-documentation)
    - [Comment ça marche ?](#how-does-it-work)
    - [Comment contribuer ?](#how-to-contribute)
    - [Combien d'utilisateurs sont supportés?](#how-many-users-are-possible)
- [Réseaux](#network)
    - [Est-ce que les reverse proxy sont supportés ?](#are-reverse-proxies-supported)
    - [Quels ports doivent être ouverts dans mon pare-feu/routeur ?](#which-ports-are-mandatory-to-be-open-in-your-firewallrouter)
    - [Explication sur les ports utilisés](#explanation-of-used-ports)
    - [Notes sur Cloudflare (proxy/tunnels)](#notes-on-cloudflare-proxytunnel)
    - [Comment héberger Nextcloud derrière un tunnel Cloudflare ?](#how-to-run-nextcloud-behind-a-cloudflare-tunnel)
    - [Comment héberger Nextcloud via tailscale ?](#how-to-run-nextcloud-via-tailscale)
    - [Comment déployer Nextcloud avec ACME DNS-challenge ?](#how-to-get-nextcloud-running-using-the-acme-dns-challenge)
    - [Comment déployer Nextcloud en local ? Aucun domain publique ou accès intranet au sein d'un LAN.](#how-to-run-nextcloud-locally-no-domain-wanted-or-wanting-intranet-access-within-your-lan)
    - [Puis-je utiliser une adresse IP à la place d'un nom de domaine pour Nextcloud ?](#can-i-use-an-ip-address-for-nextcloud-instead-of-a-domain)
    - [Puis-je utiliser AIO hors-ligne ou il utilise un système de stockage externalisé ?](#can-i-run-aio-offline-or-in-an-airgapped-system)
    - [Est-ce que les certificats auto-signés sont supportés par Nextcloud ?](#are-self-signed-certificates-supported-for-nextcloud)
    - [Puis-je utiliser AIO avec plusieurs nom de domaine ?](#can-i-use-aio-with-multiple-domains)
    - [Est-ce que d'autres ports que le 443 par défaut sont supportés par Nextcloud ?](#are-other-ports-than-the-default-443-for-nextcloud-supported)
    - [Puis-je utiliser Nextcloud dans un sous-domaine ?](#can-i-run-nextcloud-in-a-subdirectory-on-my-domain)
    - [Comment accéder à Nextcloud localement ?](#how-can-i-access-nextcloud-locally)
    - [Comment ignorer la vérification de domaine ?](#how-to-skip-the-domain-validation)
    - [Comment résoudre les problèmes liés au pare-feu dans Fedora Linux, RHEL OS, CentOS, SUSE Linux et autres ?](#how-to-resolve-firewall-problems-with-fedora-linux-rhel-os-centos-suse-linux-and-others)
    - [Comment puis-je corriger "internal error" et "internal reserved ip-address error"](#what-can-i-do-to-fix-the-internal-or-reserved-ip-address-error)
- [Infrastructure](#infrastructure)
    - [Quel architecture CPU sont supportés ?](#which-cpu-architectures-are-supported)
    - [Quels fournisseurs VPS éviter ?](#disrecommended-vps-providers)
    - [Fournisseurs VPS recommandés](#recommended-vps)
    - [Note sur les options de stockage](#note-on-storage-options)
    - [Y a-t-il des problèmes connus quand SELinux est activé ?](#are-there-known-problems-when-selinux-is-enabled)
- [Personnalisation](#customization)
    - [Comment changer la localisation par défaut du répertoire de données Nextcloud ?](#how-to-change-the-default-location-of-nextclouds-datadir)
    - [Comment stocker les fichiers et les données d'installation sur des disques distincts ?](#how-to-store-the-filesinstallation-on-a-separate-drive)
    - [Comment aurotiser le conteneur nextcloud à accéder aux répertoire de la machine hôte ?](#how-to-allow-the-nextcloud-container-to-access-directories-on-the-host)
    - [Comment modifier le port pour Nextcloud Talk (visioconférence) ?](#how-to-adjust-the-talk-port)
    - [Comment modifier la limite d'upload de Nextcloud ?](#how-to-adjust-the-upload-limit-for-nextcloud)
    - [Comment modifier le temps meximal d'exécution pour Nextcloud ?](#how-to-adjust-the-max-execution-time-for-nextcloud)
    - [Comment modifier la limite de mémoire PHP de Nextcloud ?](#how-to-adjust-the-php-memory-limit-for-nextcloud)
    - [Comment changer les applications qui sont installées par défaut lors du premier démarrage ?](#how-to-change-the-nextcloud-apps-that-are-installed-on-the-first-startup)
    - [Comment ajouter des packages d'OS de manière permanente dans le conteneur Nextcloud ?](#how-to-add-os-packages-permanently-to-the-nextcloud-container)
    - [Comment ajouter des extensions PHP de manière permanente dans le conteneur Nextcloud ?](#how-to-add-php-extensions-permanently-to-the-nextcloud-container)
    - [Dites m'en plus sur l'extension PHP pdlib pour l'application de reconnaissance faciale](#what-about-the-pdlib-php-extension-for-the-facerecognition-app)
    - [Comment activer l'accélération matérielle pour Nextcloud ?](#how-to-enable-hardware-acceleration-for-nextcloud)
        - [Avec les drivers open-source MESA pour AMD, Intel et **new** drivers `Nouveau` pour Nvidia](#with-open-source-drivers-mesa-for-amd-intel-and-new-drivers-nouveau-for-nvidia)
        - [Avec les drivers propriétaire pour Nvidia :warning: BETA](#with-proprietary-drivers-for-nvidia-warning-beta)
    - [Comment désactiver des applications ?](#how-to-keep-disabled-apps)
    - [Comment "Faire confiance" aux autorités de certification définies par l'utilisateur ?](#how-to-trust-user-defined-certification-authorities-ca)
    - [Comment désactiver la fonctionnalité "Seccomp" de Collabora ?](#how-to-disable-collaboras-seccomp-feature)
    - [Comment modifier les options Java de Fulltextsearch ?](#how-to-adjust-the-fulltextsearch-java-options)
- [Guides](#guides)
    - [Comment utiliser AIO sur macOS ?](#how-to-run-aio-on-macos)
    - [Comment utiliser AIO sur Windows ?](#how-to-run-aio-on-windows)
    - [Comment utiliser AIO sur Synology DSM](#how-to-run-aio-on-synology-dsm)
    - [Comment utiliser AIO avec Portainer?](#how-to-run-aio-with-portainer)
    - [Puis-je utiliser AIO sur TrueNAS SCALE?](#can-i-run-aio-on-truenas-scale)
    - [Comment exécuter les commandes `occ` ?](#how-to-run-occ-commands)
    - [Comment résoudre `Security & setup warnings displays the "missing default phone region"` après la première installation ?](#how-to-resolve-security--setup-warnings-displays-the-missing-default-phone-region-after-initial-install)
    - [Comment utiliser plusieurs instances AIO sur un serveur ?](#how-to-run-multiple-aio-instances-on-one-server)
    - [FAQ : Protection contre les attaques par Brute Force](#bruteforce-protection-faq)
    - [Comment changer de chaîne ?](#how-to-switch-the-channel)
    - [Comment mettre à jour les conteneurs ?](#how-to-update-the-containers)
    - [Comment facilement s'identifier sur l'interface AIO ?](#how-to-easily-log-in-to-the-aio-interface)
    - [Comment changer mon nom de domaine ?](#how-to-change-the-domain)
    - [Comment remettre proprement à zéro une instance ?](#how-to-properly-reset-the-instance)
    - [Puis-je utiliser des répertoires CIFS/SMB comme répertoire de données pour Nextcloud ?](#can-i-use-a-cifssmb-share-as-nextclouds-datadir)
    - [Puis-je utiliser AIO avec Docker Swarm ?](#can-i-run-this-with-docker-swarm)
    - [Puis-je utiliser AIO avec Kubernetes ?](#can-i-run-this-with-kubernetes)
    - [Comment utiliser AIO avec Docker rootless ?](#can-i-run-this-with-podman-instead-of-docker)
    - [Puis-je utiliser AIO avec Podman plutôt que Docker ?](#can-i-run-this-with-podman-instead-of-docker)
    - [Accéder et modifier les fichiers et répertoire de Nextcloud manuellement](#accessedit-nextcloud-filesfolders-manually)
    - [Comment modifier le fichier de config.php de Nextcloud avec un éditeur de texte ?](#how-to-edit-nextclouds-configphp-file-with-a-texteditor)
    - [Comment changer les fichiers par défaut en créant un squelette d'arborescence ?](#how-to-change-default-files-by-creating-a-custom-skeleton-directory)
    - [Comment modifier la règle de rétention des versions et de la corbeille ?](#how-to-adjust-the-version-retention-policy-and-trashbin-retention-policy)
    - [Comment activer les mises à jour automatique sans réaliser de backup au préalable ?](#how-to-enable-automatic-updates-without-creating-a-backup-beforehand)
    - [Sécuriser l'interface AIO des accès non autorisé du ACME challenges](#securing-the-aio-interface-from-unauthorized-acme-challenges)
    - [Comment migrer depuis une instance Nextcloud vers une instance Nextcloud AIO ?](#how-to-migrate-from-an-already-existing-nextcloud-installation-to-nextcloud-aio)
- [Sauvegarde](#backup)
    - [Qu'est ce qui est sauvegardé par la solution de backup de AIO ?](#what-is-getting-backed-up-by-aios-backup-solution)
    - [Comment modifier la règle de rétention de Borg ?](#how-to-adjust-borgs-retention-policy)
    - [Comment migrer d'une instance AIO vers une nouvelle instance AIO ?](#how-to-migrate-from-aio-to-aio)
    - [Est-ce que les backup Borg dans le cloud sont supportées ?](#are-remote-borg-backups-supported)
    - [Echec de la backup dans les conteneurs LXC](#failure-of-the-backup-container-in-lxc-containers)
    - [Comment créer un volume de backup sur Windows ?](#how-to-create-the-backup-volume-on-windows)
    - [Pro-tip: Accéder aux archives de backup](#pro-tip-backup-archives-access)
    - [Supprimer manuellement les archives de backup](#delete-backup-archives-manually)
    - [Synchroniser régulièrement les backup sur un autre disque](#sync-local-backups-regularly-to-another-drive)
    - [Comment exclure le répertoire de données de Nextcloud du système de backup ?](#how-to-exclude-nextclouds-data-directory-or-the-preview-folder-from-backup)
    - [Comment arrêter/démarrer/mettre à jour les conteneurs ou déclencher la sauvegarde quotidienne à partir d'un script externe ?](#how-to-stopstartupdate-containers-or-trigger-the-daily-backup-from-a-script-externally)
    - [Comment désactiver la section de backup ?](#how-to-disable-the-backup-section)
- [Compléments](#addons)
    - [Fail2ban](#fail2ban)
    - [LDAP](#ldap)
    - [Netdata](#netdata)
    - [USER_SQL](#user_sql)
    - [phpMyAdmin, Adminer or pgAdmin](#phpmyadmin-adminer-or-pgadmin)
    - [Serveur mail](#mail-server)
- [Divers](#miscellaneous)
    - [Pré-requis pour intégrer de nouveau conteneurs](#requirements-for-integrating-new-containers)
    - [Politique de mise à jour](#update-policy)
    - [A quelle fréquence sont envoyées les notifications de mise à jour ?](#how-often-are-update-notifications-sent)
    - [Logs docker](#huge-docker-logs)

### Ou puis-je trouver plus de documentation ?
Une partie de la documentation se trouve à [GitHub Discussions](https://github.com/nextcloud/all-in-one/discussions/categories/wiki).

### Comment ça marche ?
Nextcloud AIO est inspiré par des projets comme Portainer qui gèrent le démon docker en lui parlant directement à travers le socket docker. Ce concept permet à un utilisateur d'installer un seul conteneur avec une seule commande qui fait le gros du travail de création et de gestion de tous les conteneurs qui sont nécessaires pour fournir une installation Nextcloud avec la plupart des fonctionnalités incluses. La mise à jour est également un jeu d'enfant et l'utilisateur n'est plus lié au système hôte (et à ses mises à jour lentes) puisque tout se trouve dans des conteneurs. En outre, il est très facile à manipuler du point de vue de l'utilisateur car une interface simple est fournie pour gérer votre installation Nextcloud AIO.

### Comment contribuer ?
Consultez [this issue](https://github.com/nextcloud/all-in-one/issues/5251) pour une liste de fonctionnalités qui nécessite de l'aide des contributeurs.

### Combien d'utilisateurs peut accueillir le serveur ?
Jusqu'à 100 utilisateurs peuvent être accueillis sur le serveur, au-délà, consultez : [Nextcloud Enterprise](https://nextcloud.com/all-in-one/)

## Réseau

### Est-ce que les reverse proxy sont supportés ?
Oui, il faut se référer aux instructions de la documentation disponible à [reverse-proxy.md](https://github.com/nextcloud/all-in-one/blob/main/reverse-proxy.md)

### Quels ports doivent être ouvert sur mon pare-feu/routeur ?
Seulement ceux-ci : (Si vous accédez à l'interface du Mastercontainer en interne via le port 8080) :
- `443/TCP` pour le conteneur Apache.
- `443/UDP` si vous voulez activer http3 pour le conteneur Apache
- `3478/TCP` et `3478/UDP` pour le conteneur Talk

### Explication des ports utilisés
- `8080/TCP` : Interface du Mastercontainer avec certificat auto-signé (fonctionne toujours, même si seul l'accès via l'adresse IP est possible, par exemple `https://ip.address.of.this.server:8080/`) ⚠️ **Important:** utilisez toujours une adresse IP si vous accédez à ce port et non un domaine car HSTS pourrait bloquer l'accès à ce port plus tard ! (Il est également prévu que ce port utilise un certificat auto-signé pour des raisons de sécurité que vous devez accepter dans votre navigateur).
- `80/TCP` : redirige vers Nextcloud (est utilisé pour obtenir le certificat via ACME http-challenge pour le Mastercontainer)
- `8443/TCP` : Mastercontainer Interface with valid certificate (ne fonctionne que si les ports 80 et 8443 sont ouverts/transférés dans votre firewall/routeur et que vous pointez un domaine vers votre serveur. Il génère alors automatiquement un certificat valide et l'accès via par exemple `https://public.domain.com:8443/` est possible).
- `443/TCP` : sera utilisé par le conteneur Apache plus tard et doit être ouvert/transféré dans votre pare-feu/routeur.
- `443/UDP` : sera utilisé ultérieurement par le conteneur Apache et doit être ouvert/transféré dans votre pare-feu/routeur si vous voulez activer http3
- `3478/TCP` et `3478/UDP` : sera utilisé par le Turnserver à l'intérieur du conteneur Talk et doit être ouvert/transféré dans votre pare-feu/routeur.

### Notes sur Cloudflare (proxy/tunnel)
Étant donné que Cloudflare Proxy/Tunnel comporte de nombreuses limitations qui sont énumérées ci-dessous, il est plutôt recommandé de passer à [Tailscale](https://github.com/nextcloud/all-in-one/discussions/5439) si possible.
- Cloudflare Proxy et Cloudflare Tunnel requièrent tous deux que Cloudflare effectue la terminaison TLS de leur côté et décrypte ainsi tout le trafic sur leur infrastructure. Il s'agit d'un problème de confidentialité et vous devrez chercher d'autres solutions si cela est inacceptable pour vous.
- L'utilisation de Cloudflare Tunnel peut potentiellement ralentir Nextcloud puisque l'accès local via le domaine configuré n'est pas possible parce que la terminaison TLS est dans ce cas déchargée sur l'infrastructure de Cloudflare. Il n'y a aucun moyen de désactiver ce comportement dans Cloudflare Tunnel.
- Il est connu que la validation du domaine peut ne pas fonctionner correctement derrière Cloudflare car Cloudflare peut bloquer la tentative de validation. Dans ce cas, vous pouvez simplement l'ignorer en suivant les instructions suivantes : https://github.com/nextcloud/all-in-one#how-to-skip-the-domain-validation
- Assurez-vous de [désactiver la fonction Cloudflares Rocket Loader] (https://help.nextcloud.com/t/login-page-not-working-solved/149417/8) car sinon l'invite de connexion de Nextcloud ne s'affichera pas.
- Cloudflare ne prend en charge que le téléchargement de fichiers jusqu'à 100 Mo dans le plan gratuit, si vous essayez de télécharger des fichiers plus gros, vous obtiendrez une erreur (413 - Payload Too Large) si aucun découpage n'est utilisé (par exemple pour les téléchargements publics sur le web, ou si les morceaux sont configurés pour être plus gros que 100 Mo dans les clients ou sur le web). Si vous avez besoin de télécharger des fichiers plus volumineux, vous devez désactiver l'option proxy dans vos paramètres DNS. Notez que cela désactivera la protection DDoS de Cloudflare et le tunnel Cloudflare, car ces services requièrent l'activation de l'option proxy.
- Si vous utilisez le tunnel Cloudflare et le client Nextcloud Desktop [Set Chunking on Nextcloud Desktop Client] (https://github.com/nextcloud/desktop/issues/4271#issuecomment-1159578065)
- Cloudflare n'autorise qu'un délai maximum de 100s pour les requêtes, qui n'est pas configurable. Cela signifie que tout traitement côté serveur, par exemple pour assembler des chunks pour de gros fichiers pendant le téléchargement qui prend plus de 100s, ne fonctionnera tout simplement pas. Voir https://github.com/nextcloud/server/issues/19223. Si vous avez besoin de télécharger de gros fichiers de manière fiable, vous devez désactiver l'option proxy dans vos paramètres DNS. Notez que cela désactivera à la fois la protection DDoS de Cloudflare et le tunnel Cloudflare, car ces services requièrent l'activation de l'option proxy.
- Il est connu que la collaboration incluse dans AIO (Nextcloud Office) ne fonctionne pas d'emblée derrière Cloudflare. Pour le faire fonctionner, vous devez ajouter tous les [Cloudflare IP-ranges] (https://www.cloudflare.com/ips/) à la wopi-allowlist dans `https://yourdomain.com/settings/admin/richdocuments`
- Cloudflare Proxy peut empêcher le Turnserver pour Nextcloud Talk de fonctionner correctement. Vous pouvez donc désactiver Cloudflare Proxy. Voir https://github.com/nextcloud/all-in-one/discussions/2463#discussioncomment-5779981
- Le turn-server intégré de Nextcloud Talk ne fonctionnera pas derrière le tunnel Cloudflare car il a besoin d'un port séparé (par défaut 3478 ou au choix) disponible sur le même domaine. Si vous voulez toujours utiliser cette fonctionnalité, vous devrez installer votre propre serveur de tours ou en utiliser un disponible publiquement et ajuster et tester vos paramètres de stun et de tours dans `https://yourdomain.com/settings/admin/talk`.
- Si vous obtenez une erreur dans l'aperçu de l'administration de Nextcloud indiquant que l'en-tête HSTS n'est pas correctement défini, vous devrez peut-être l'activer manuellement dans Cloudflare.
- Si vous utilisez le Reverse Proxy intégré à AIO et que vous n'utilisez pas votre propre Proxy, il est possible que l'émission de certificats ne fonctionne pas en l'état car Cloudflare pourrait bloquer la tentative. Dans ce cas, vous devez désactiver la fonction Proxy au moins temporairement pour que cela fonctionne. Notez que ce n'est pas une option si vous avez besoin de Cloudflare Tunnel, car la désactivation du proxy désactiverait également Cloudflare Tunnel, ce qui rendrait votre serveur inaccessible pour la vérification. Voir https://github.com/nextcloud/all-in-one/discussions/1101.

### Comment utiliser Nextcloud derrière un tunnel Cloudflare ?
Bien que cela ne semble pas être le cas, du point de vue de l'AIO, un tunnel Cloudflare fonctionne comme un proxy inverse. Dans ce cas, consultez [reverse proxy documentation](./reverse-proxy.md) où est documenté la manière d'utiliser AIO derrière un tunnel Cloudflare. Cependant, consultez d'abord [caveats](https://github.com/nextcloud/all-in-one#notes-on-cloudflare-proxytunnel).

### Comment utiliser Nextcloud via tailscale ?
Pour un exemple de reverse proxy avec tailscale, consultez le guide rédigé par @flll: https://github.com/nextcloud/all-in-one/discussions/5439

### Comment faire fonctionner Nextcloud avec ACME DNS-challenge ?
Vous pouvez installer l'OAA en mode proxy inverse où il est également documenté comment le faire fonctionner en utilisant le défi DNS ACME pour obtenir un certificat valide pour l'OAA. Voir la [documentation sur le proxy inverse](./reverse-proxy.md). (Il s'agit de la section `Caddy with ACME DNS-challenge`). Voir aussi https://github.com/dani-garcia/vaultwarden/wiki/Running-a-private-vaultwarden-instance-with-Let%27s-Encrypt-certs#getting-a-custom-caddy-build pour des documents supplémentaires sur ce sujet.

### Comment faire fonctionner Nextcloud localement ? Vous ne voulez pas de domaine, ou vous voulez un accès intranet dans votre LAN.
Si vous ne voulez pas ouvrir Nextcloud à l'internet public, vous pouvez jeter un coup d'œil à la documentation suivante sur la façon de le configurer localement : [local-instance.md](./local-instance.md), mais gardez à l'esprit que vous devez toujours avoir https qui fonctionne correctement.

### Puis-je utiliser une adresse IP pour Nextcloud au lieu d'un domaine ?
Non et cela ne sera pas ajouté. Si vous voulez seulement l'exécuter localement, vous pouvez jeter un coup d'œil à la documentation suivante : [local-instance.md](./local-instance.md). Il est recommandé d'utiliser [Tailscale](https://github.com/nextcloud/all-in-one/discussions/5439).

### Puis-je exécuter AIO hors ligne ou dans un système airgapped ?
Non. Cela n'est pas possible et ne sera pas ajouté pour de multiples raisons : vérifications des mises à jour, installations d'applications via le store intégré, téléchargement d'images docker supplémentaires à la demande, etc.

### Les certificats auto-signés sont-ils pris en charge par Nextcloud ?
Non et ils ne le seront pas. Si vous voulez l'exécuter localement, sans ouvrir Nextcloud à l'internet public, veuillez consulter la [documentation de l'instance locale](./local-instance.md). Il est recommandé d'utiliser [Tailscale] (https://github.com/nextcloud/all-in-one/discussions/5439).

### Puis-je utiliser AIO avec plusieurs domaines ?
Non et cela ne sera pas ajouté. Cependant, vous pouvez utiliser [cette fonctionnalité](https://github.com/nextcloud/all-in-one/blob/main/multiple-instances.md) afin de créer plusieurs instances AIO, une pour chaque domaine.

### D'autres ports que le 443 par défaut de Nextcloud sont-ils pris en charge ?
Non et ils ne le seront pas. Si le port 443 et/ou 80 est bloqué pour vous, vous pouvez utiliser [Tailscale](https://github.com/nextcloud/all-in-one/discussions/5439) si vous voulez le publier en ligne. Si vous utilisez déjà un autre service sur le port 443, veuillez utiliser un domaine dédié pour Nextcloud et le configurer correctement en suivant la [documentation du proxy inverse](./reverse-proxy.md). Cependant, dans tous les cas, l'interface de Nextcloud vous redirigera vers le port 443.

### Puis-je exécuter Nextcloud dans un sous-répertoire de mon domaine ?
Non et il ne sera pas ajouté. Veuillez utiliser un (sous-)domaine dédié pour Nextcloud et le configurer correctement en suivant la [documentation du proxy inverse](./reverse-proxy.md). Vous pouvez également utiliser [Tailscale] (https://github.com/nextcloud/all-in-one/discussions/5439) si vous souhaitez le publier en ligne.

### Comment puis-je accéder à Nextcloud localement ?
Veuillez noter que l'accès local n'est pas possible si vous exécutez AIO derrière Cloudflare Tunnel puisque le proxy TLS est dans ce cas déchargé sur l'infrastructure de Cloudflares. Vous pouvez résoudre ce problème en mettant en place votre propre proxy inverse qui gère le proxy TLS localement et qui fera fonctionner les étapes ci-dessous.

Veuillez vous assurer que si vous exécutez AIO derrière un proxy inverse, celui-ci est configuré pour utiliser le port 443 sur le serveur qui l'exécute. Dans le cas contraire, les étapes ci-dessous ne fonctionneront pas.

Maintenant que cela est fait, la façon recommandée d'accéder à Nextcloud localement est de mettre en place un serveur DNS local comme un pi-hole et de mettre en place un enregistrement DNS personnalisé pour ce domaine qui pointe vers l'adresse IP interne de votre serveur qui exécute Nextcloud AIO. Voici quelques guides :
- https://www.howtogeek.com/devops/how-to-run-your-own-dns-server-on-your-local-network/
- https://help.nextcloud.com/t/need-help-to-configure-internal-access/156075/6
- https://howchoo.com/pi/pi-hole-setup avec https://web.archive.org/web/20221203223505/https://docs.callitkarma.me/posts/PiHole-Local-DNS/
- https://dockerlabs.collabnix.com/intermediate/networking/Configuring_DNS.html
En outre, il existe maintenant un conteneur communautaire qui peut être ajouté à la pile AIO : https://github.com/nextcloud/all-in-one/tree/main/community-containers/pi-hole

### Comment ignorer la validation du domaine ?
Si vous êtes complètement sûr d'avoir tout configuré correctement et que vous n'êtes pas en mesure de passer la validation de domaine, vous pouvez ignorer la validation de domaine en ajoutant `--env SKIP_DOMAIN_VALIDATION=true` à la commande docker run du mastercontainer (mais avant la dernière ligne `ghcr.io/nextcloud-releases/all-in-one:latest` ! S'il a déjà été démarré, vous devrez arrêter le mastercontainer, le supprimer (aucune donnée ne sera perdue) et le recréer en utilisant la commande docker run que vous avez initialement utilisée).

### Comment résoudre les problèmes de pare-feu avec Fedora Linux, RHEL OS, CentOS, SUSE Linux et d'autres ?
Il est connu que les distros Linux qui utilisent [firewalld](https://firewalld.org) comme démon de pare-feu ont des problèmes avec les réseaux Docker. Dans le cas où les conteneurs ne sont pas capables de communiquer entre eux, vous pouvez changer votre firewalld pour utiliser le backend iptables en exécutant :
``
sudo sed -i 's/FirewallBackend=nftables/FirewallBackend=iptables/g' /etc/firewalld/firewalld.conf
sudo systemctl restart firewalld docker
``
Après cela, cela devrait fonctionner.<br>

Voir https://dev.to/ozorest/fedora-32-how-to-solve-docker-internal-network-issue-22me pour plus de détails à ce sujet. Cette limitation est même mentionnée sur le site officiel de firewalld : https://firewalld.org/#who-is-using-it

### Que puis-je faire pour corriger "Internal error" et "Internal reseved ip-address error" ?
Si vous obtenez une erreur lors de la validation du domaine indiquant que votre adresse IP est une adresse IP interne ou réservée, vous pouvez corriger cela en vous assurant d'abord que votre domaine possède effectivement la bonne adresse IP publique pointant vers le serveur, puis en ajoutant --add-host yourdomain.com:<public-ip-address> à la commande docker run du mastercontainer (mais avant la dernière ligne ghcr.io/nextcloud-releases/all-in-one:latest ! Si le mastercontainer a déjà été démarré, vous devrez l'arrêter, le supprimer (aucune donnée ne sera perdue) et le recréer en utilisant la commande docker run que vous avez initialement utilisée) ce qui permettra à la validation du domaine de fonctionner correctement. Et pour que vous le sachiez : même si l'enregistrement A de votre domaine devait changer au fil du temps, ce n'est pas un problème car le mastercontainer ne tentera pas d'accéder au domaine choisi après la validation initiale du domaine.

## Infrastructure
### Quelles architectures CPU sont supportées ?
Vous pouvez vérifier cela sous Linux en exécutant : uname -m

x86_64/x64/amd64
aarch64/arm64/armv8

### Fournisseurs VPS à éviter
- *Older* Strato VPS utilisant Virtuozzo causait des problèmes. Les version du 3ème trimestre 2023 et plus récentes devraient marcher.
  Si vous avez un VPS avec `/proc/user_beancounters` et une limite `numproc` basse, votre serveur risque de ne par marcher correctement une fois cette limite rencontrée, qui est très vite atteinte par AIO. Consultez [here](https://github.com/nextcloud/all-in-one/discussions/1747#discussioncomment-4716164).
- Les VPS Hostingers semblent être dépourvu d'une fonctionnalité du noyau qui est obligatoire pour que AIO tourne correctement. Consultez [here](https://help.nextcloud.com/t/help-installing-nc-via-aio-on-vps/153956).

### Fournisseurs VPS recommandés
En général nous recommande les VPS qui ne sont pas virtualisés/sous KVM parce que cela permet de rendre Docker stable.

### Note sur les options de stockage
- Les cartes SD ne sont pas recommandées pour AIO car elles brident les performances et ne sont pas concues pour supporters un grande nombre d'opération d'écriture, ce qui est le cas de la base de données et d'autres fonctionnalités.
- Le stockage SSD est grandement recommandé.
- Le stockage HDD marche correctement mais est beaucoup plus lent que le stockage SSD.

### Y a-t-il des problèmes connus avec SELinux ?
Oui. Quand SELinux est activés, vous pourriez avoir besoin d'ajouter `--security-opt label:disable` à la commande docker du mastercontainer afin de l'autoriser à accéder à la socket Docker. (ou, `security_opt: ["label:disable"]` dans le fichier compose.yaml). Consultez https://github.com/nextcloud/all-in-one/discussions/485

## Personnalisation

### Comment changer la localisation par défaut du répertoire de données Nextcloud ?
> [!WARNING]  
> Do not set or adjust this value after the initial Nextcloud installation is done! If you still want to do it afterwards, see [this](https://github.com/nextcloud/all-in-one/discussions/890#discussioncomment-3089903) on how to do it.

You can configure the Nextcloud container to use a specific directory on your host as data directory. You can do so by adding the environmental variable `NEXTCLOUD_DATADIR` to the docker run command of the mastercontainer (but before the last line `ghcr.io/nextcloud-releases/all-in-one:latest`! If it was started already, you will need to stop the mastercontainer, remove it (no data will be lost) and recreate it using the docker run command that you initially used). Allowed values for that variable are strings that start with `/` and are not equal to `/`. The chosen directory or volume will then be mounted to `/mnt/ncdata` inside the container.

- An example for Linux is `--env NEXTCLOUD_DATADIR="/mnt/ncdata"`. ⚠️ Please note: If you should be using an external BTRFS drive that is mounted to `/mnt/ncdata`, make sure to choose a subfolder like e.g. `/mnt/ncdata/nextcloud` as datadir, since the root folder is not suited as datadir in that case. See https://github.com/nextcloud/all-in-one/discussions/2696.
- On macOS it might be `--env NEXTCLOUD_DATADIR="/var/nextcloud-data"`
- For Synology it may be `--env NEXTCLOUD_DATADIR="/volume1/docker/nextcloud/data"`. 
- On Windows it might be `--env NEXTCLOUD_DATADIR="/run/desktop/mnt/host/c/ncdata"`. (This path is equivalent to `C:\ncdata` on your Windows host so you need to translate the path accordingly. Hint: the path that you enter needs to start with `/run/desktop/mnt/host/`. Append to that the exact location on your windows host, e.g. `c/ncdata` which is equivalent to `C:\ncdata`.) ⚠️ **Please note**: This does not work with external drives like USB or network drives and only with internal drives like SATA or NVME drives.
- Another option is to provide a specific volume name here with: `--env NEXTCLOUD_DATADIR="nextcloud_aio_nextcloud_datadir"`. This volume needs to be created beforehand manually by you in order to be able to use it. e.g. on Windows with:
    ```
    docker volume create ^
    --driver local ^
    --name nextcloud_aio_nextcloud_datadir ^
    -o device="/host_mnt/e/your/data/path" ^
    -o type="none" ^
    -o o="bind"
    ```
    In this example, it would mount `E:\your\data\path` into the volume so for a different location you need to adjust `/host_mnt/e/your/data/path` accordingly.

### Comment stocker les fichiers d'installation et les données Nextcloud sur des disques distincts ?
You can move the whole docker library and all its files including all Nextcloud AIO files and folders to a separate drive by first mounting the drive in the host OS (NTFS is not supported and ext4 is recommended as FS) and then following this tutorial: https://www.guguweb.com/2019/02/07/how-to-move-docker-data-directory-to-another-location-on-ubuntu/<br>
(Of course docker needs to be installed first for this to work.)

⚠️ If you encounter errors from richdocuments in your Nextcloud logs, check in your Collabora container if the message "Capabilities are not set for the coolforkit program." appears. If so, follow these steps:

1. Stop all the containers from the AIO Interface.
2. Go to your terminal and delete the Collabora container (`docker rm nextcloud-aio-collabora`) AND the Collabora image (`docker image rm nextcloud/aio-collabora`).
3. You might also want to prune your Docker (`docker system prune`) (no data will be lost).
4. Restart your containers from the AIO Interface.

This should solve the problem.

### Comment aurotiser le conteneur Nextcloud à accéder aux répertoire de l'hôte ?
By default, the Nextcloud container is confined and cannot access directories on the host OS. You might want to change this when you are planning to use local external storage in Nextcloud to store some files outside the data directory and can do so by adding the environmental variable `NEXTCLOUD_MOUNT` to the docker run command of the mastercontainer (but before the last line `ghcr.io/nextcloud-releases/all-in-one:latest`! If it was started already, you will need to stop the mastercontainer, remove it (no data will be lost) and recreate it using the docker run command that you initially used). Allowed values for that variable are strings that start with `/` and are not equal to `/`.

- Two examples for Linux are `--env NEXTCLOUD_MOUNT="/mnt/"` and `--env NEXTCLOUD_MOUNT="/media/"`.
- On macOS it might be `--env NEXTCLOUD_MOUNT="/Volumes/your_drive/"`
- For Synology it may be `--env NEXTCLOUD_MOUNT="/volume1/"`.
- On Windows it might be `--env NEXTCLOUD_MOUNT="/run/desktop/mnt/host/d/your-folder/"`. (This path is equivalent to `D:\your-folder` on your Windows host so you need to translate the path accordingly. Hint: the path that you enter needs to start with `/run/desktop/mnt/host/`. Append to that the exact location on your windows host, e.g. `d/your-folder/` which is equivalent to `D:\your-folder`.) ⚠️ **Please note**: This does not work with external drives like USB or network drives and only with internal drives like SATA or NVME drives.

After using this option, please make sure to apply the correct permissions to the directories that you want to use in Nextcloud. E.g. `sudo chown -R 33:0 /mnt/your-drive-mountpoint` and `sudo chmod -R 750 /mnt/your-drive-mountpoint` should make it work on Linux when you have used `--env NEXTCLOUD_MOUNT="/mnt/"`. On Windows you could do this e.g. with `docker exec -it nextcloud-aio-nextcloud chown -R 33:0 /run/desktop/mnt/host/d/your-folder/` and `docker exec -it nextcloud-aio-nextcloud chmod -R 750 /run/desktop/mnt/host/d/your-folder/`.

You can then navigate to `https://your-nc-domain.com/settings/apps/disabled`, activate the external storage app, navigate to `https://your-nc-domain.com/settings/admin/externalstorages` and add a local external storage directory that will be accessible inside the container at the same place that you've entered. E.g. `/mnt/your-drive-mountpoint` will be mounted to `/mnt/your-drive-mountpoint` inside the container, etc. 

Be aware though that these locations will not be covered by the built-in backup solution - but you can add further Docker volumes and host paths that you want to back up after the initial backup is done.

> [!NOTE]  
> If you can't see the type "local storage" in the external storage admin options, a restart of the containers from the AIO interface may be required.

### Comment modifier le port de la fonctionnalité Talk ?
By default will the talk container use port `3478/UDP` and `3478/TCP` for connections. This should be set to something higher than 1024! You can adjust the port by adding e.g. `--env TALK_PORT=3478` to the docker run command of the mastercontainer (but before the last line `ghcr.io/nextcloud-releases/all-in-one:latest`! If it was started already, you will need to stop the mastercontainer, remove it (no data will be lost) and recreate it using the docker run command that you initially used) and adjusting the port to your desired value. Best is to use a port over 1024, so e.g. 3479 to not run into this: https://github.com/nextcloud/all-in-one/discussions/2517

### COmment modifier la limite d'upload de Nextcloud ? (Taille des fichiers)
By default, public uploads to Nextcloud are limited to a max of 16G (logged in users can upload much bigger files using the webinterface or the mobile/desktop clients, since chunking is used in that case). You can adjust the upload limit by providing `--env NEXTCLOUD_UPLOAD_LIMIT=16G` to the docker run command of the mastercontainer (but before the last line `ghcr.io/nextcloud-releases/all-in-one:latest`! If it was started already, you will need to stop the mastercontainer, remove it (no data will be lost) and recreate it using the docker run command that you initially used) and customize the value to your fitting. It must start with a number and end with `G` e.g. `16G`.

### Comment modifier la durée maximale d'exécution de Nextcloud ?
By default, uploads to Nextcloud are limited to a max of 3600s. You can adjust the upload time limit by providing `--env NEXTCLOUD_MAX_TIME=3600` to the docker run command of the mastercontainer (but before the last line `ghcr.io/nextcloud-releases/all-in-one:latest`! If it was started already, you will need to stop the mastercontainer, remove it (no data will be lost) and recreate it using the docker run command that you initially used) and customize the value to your fitting. It must be a number e.g. `3600`.

### Comment modifier la limite de mémoire PHP de Nextcloud ?
By default, each PHP process in the Nextcloud container is limited to a max of 512 MB. You can adjust the memory limit by providing `--env NEXTCLOUD_MEMORY_LIMIT=512M` to the docker run command of the mastercontainer (but before the last line `ghcr.io/nextcloud-releases/all-in-one:latest`! If it was started already, you will need to stop the mastercontainer, remove it (no data will be lost) and recreate it using the docker run command that you initially used) and customize the value to your fitting. It must start with a number and end with `M` e.g. `1024M`.

### How to change the Nextcloud apps that are installed on the first startup?
You might want to adjust the Nextcloud apps that are installed upon the first startup of the Nextcloud container. You can do so by adding `--env NEXTCLOUD_STARTUP_APPS="deck twofactor_totp tasks calendar contacts notes"` to the docker run command of the mastercontainer (but before the last line `ghcr.io/nextcloud-releases/all-in-one:latest`! If it was started already, you will need to stop the mastercontainer, remove it (no data will be lost) and recreate it using the docker run command that you initially used) and customize the value to your fitting. It must be a string with small letters a-z, 0-9, spaces and hyphens or '_'. You can disable shipped and by default enabled apps by adding a hyphen in front of the appid. E.g. `-contactsinteraction`.

### How to add OS packages permanently to the Nextcloud container?
Some Nextcloud apps require additional external dependencies that must be bundled within Nextcloud container in order to work correctly. As we cannot put each and every dependency for all apps into the container - as this would make the project quickly unmaintainable - there is an official way in which you can add additional dependencies into the Nextcloud container. However note that doing this is disrecommended since we do not test Nextcloud apps that require external dependencies. 

You can do so by adding `--env NEXTCLOUD_ADDITIONAL_APKS="imagemagick dependency2 dependency3"` to the docker run command of the mastercontainer (but before the last line `ghcr.io/nextcloud-releases/all-in-one:latest`! If it was started already, you will need to stop the mastercontainer, remove it (no data will be lost) and recreate it using the docker run command that you initially used) and customize the value to your fitting. It must be a string with small letters a-z, digits 0-9, spaces, dots and hyphens or '_'. You can find available packages here: https://pkgs.alpinelinux.org/packages?branch=v3.21. By default `imagemagick` is added. If you want to keep it, you need to specify it as well.

### How to add PHP extensions permanently to the Nextcloud container?
Some Nextcloud apps require additional php extensions that must be bundled within Nextcloud container in order to work correctly. As we cannot put each and every dependency for all apps into the container - as this would make the project quickly unmaintainable - there is an official way in which you can add additional php extensions into the Nextcloud container. However note that doing this is disrecommended since we do not test Nextcloud apps that require additional php extensions. 

You can do so by adding `--env NEXTCLOUD_ADDITIONAL_PHP_EXTENSIONS="imagick extension1 extension2"` to the docker run command of the mastercontainer (but before the last line `ghcr.io/nextcloud-releases/all-in-one:latest`! If it was started already, you will need to stop the mastercontainer, remove it (no data will be lost) and recreate it using the docker run command that you initially used) and customize the value to your fitting. It must be a string with small letters a-z, digits 0-9, spaces, dots and hyphens or '_'. You can find available extensions here: https://pecl.php.net/packages.php. By default `imagick` is added. If you want to keep it, you need to specify it as well.

### What about the pdlib PHP extension for the facerecognition app?
The [facerecognition app](https://apps.nextcloud.com/apps/facerecognition) requires the pdlib PHP extension to be installed. Unfortunately, it is not available on PECL nor via PHP core, so there is no way to add this into AIO currently. However you can use [this community container](https://github.com/nextcloud/all-in-one/tree/main/community-containers/facerecognition) in order to run facerecognition.

### How to enable hardware acceleration for Nextcloud?
Some container can use GPU acceleration to increase performance like [memories app](https://apps.nextcloud.com/apps/memories) allows to enable hardware transcoding for videos.

#### With open source drivers MESA for AMD, Intel and **new** drivers `Nouveau` for Nvidia

> [!WARNING]  
> This only works if the `/dev/dri` device is present on the host! If it does not exist on your host, don't proceed as otherwise the Nextcloud container will fail to start! If you are unsure about this, better do not proceed with the instructions below. Make sure that your driver is correctly configured on the host.

A list of supported device can be fond in [MESA 3D documentation](https://docs.mesa3d.org/systems.html).

This method use the [Direct Rendering Infrastructure](https://dri.freedesktop.org/wiki/) with the access to the `/dev/dri` device.

In order to use that, you need to add `--env NEXTCLOUD_ENABLE_DRI_DEVICE=true` to the docker run command of the mastercontainer (but before the last line `ghcr.io/nextcloud-releases/all-in-one:latest`! If it was started already, you will need to stop the mastercontainer, remove it (no data will be lost) and recreate it using the docker run command that you initially used) which will mount the `/dev/dri` device into the container.


#### With proprietary drivers for Nvidia :warning: BETA

> [!WARNING]
> This only works if the Nvidia Toolkit is installed on the host and an NVIDIA GPU is enabled! Make sure that it is correctly configured on the host. If it does not exist on your host, don't proceed as otherwise the Nextcloud container will fail to start! If you are unsure about this, better do not proceed with the instructions below.
> 
> This feature is in beta. Since the proprietary, we haven't a lot of user using proprietary drivers, we can't guarantee the stability of this feature. Your feedback is welcome.

This method use the [Nvidia Container Toolkit](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/index.html) with the nvidia runtime.

In order to use that, you need to add `--env NEXTCLOUD_ENABLE_NVIDIA_GPU=true` to the docker run command of the mastercontainer (but before the last line `ghcr.io/nextcloud-releases/all-in-one:latest`! If it was started already, you will need to stop the mastercontainer, remove it (no data will be lost) and recreate it using the docker run command that you initially used) which will enable the nvidia runtime.

If you're using WSL2 and want to use the NVIDIA runtime, please follow the instructions to [install the NVIDIA Container Toolkit meta-version in WSL](https://docs.nvidia.com/cuda/wsl-user-guide/index.html#cuda-support-for-wsl-2).

### How to keep disabled apps?
In certain situations you might want to keep Nextcloud apps that are disabled in the AIO interface and not uninstall them if they should be installed in Nextcloud. You can do so by adding `--env NEXTCLOUD_KEEP_DISABLED_APPS=true` to the docker run command of the mastercontainer (but before the last line `ghcr.io/nextcloud-releases/all-in-one:latest`! If it was started already, you will need to stop the mastercontainer, remove it (no data will be lost) and recreate it using the docker run command that you initially used). 
> [!WARNING]  
> Doing this might cause unintended problems in Nextcloud if an app that requires an external dependency is still installed but the external dependency not for example.

### How to trust user-defined Certification Authorities (CA)?
> [!NOTE]
> Please note, that this feature is only intended to make LDAPS connections with self-signed certificates work. It will not make other interconnectivity between the different containers work, as they expect a valid publicly trusted certificate like one from Let's Encrypt.

For some applications it might be necessary to establish a secure connection to another host/server which is using a certificate issued by a Certification Authority that is not trusted out of the box. An example could be configuring LDAPS against a domain controller (Active Directory or Samba-based) of an organization.

You can make the Nextcloud container trust any Certification Authority by providing the environmental variable `NEXTCLOUD_TRUSTED_CACERTS_DIR` to the docker run command of the mastercontainer (but before the last line `ghcr.io/nextcloud-releases/all-in-one:latest`! If it was started already, you will need to stop the mastercontainer, remove it (no data will be lost) and recreate it using the docker run command that you initially used). The value of the variables should be set to the absolute paths of the directory on the host, which contains one or more Certification Authorities certificates. You should use X.509 certificates, Base64 encoded. (Other formats may work but have not been tested!) All the certificates in the directory will be trusted.

When using `docker run`, the environmental variable can be set with `--env NEXTCLOUD_TRUSTED_CACERTS_DIR=/path/to/my/cacerts`.

In order for the value to be valid, the path should start with `/` and not end with `/` and point to an existing **directory**. Pointing the variable directly to a certificate **file** will not work and may also break things.

### How to disable Collabora's Seccomp feature?
The Collabora container enables Seccomp by default, which is a security feature of the Linux kernel. On systems without this kernel feature enabled, you need to provide `--env COLLABORA_SECCOMP_DISABLED=true` to the initial docker run command in order to make it work. If it was started already, you will need to stop the mastercontainer, remove it (no data will be lost) and recreate it using the docker run command that you initially used. 

### How to adjust the Fulltextsearch Java options?
The Fulltextsearch Java options are by default set to `-Xms512M -Xmx512M` which might not be enough on some systems. You can adjust this by adding e.g. `--env FULLTEXTSEARCH_JAVA_OPTIONS="-Xms1024M -Xmx1024M"` to the initial docker run command. If it was started already, you will need to stop the mastercontainer, remove it (no data will be lost) and recreate it using the docker run command that you initially used.

## Guides

### How to run AIO on macOS?
On macOS, there is only one thing different in comparison to Linux: instead of using `--volume /var/run/docker.sock:/var/run/docker.sock:ro`, you need to use `--volume /var/run/docker.sock.raw:/var/run/docker.sock:ro` to run it after you installed [Docker Desktop](https://www.docker.com/products/docker-desktop/) (and don't forget to [enable ipv6](https://github.com/nextcloud/all-in-one/blob/main/docker-ipv6-support.md) if you should need that). Apart from that it should work and behave the same like on Linux.

Also, you may be interested in adjusting Nextcloud's Datadir to store the files on the host system. See [this documentation](https://github.com/nextcloud/all-in-one#how-to-change-the-default-location-of-nextclouds-datadir) on how to do it.

### How to run AIO on Windows?
On Windows, install [Docker Desktop](https://www.docker.com/products/docker-desktop/) (and don't forget to [enable ipv6](https://github.com/nextcloud/all-in-one/blob/main/docker-ipv6-support.md) if you should need that) and run the following command in the command prompt:

```
docker run ^
--init ^
--sig-proxy=false ^
--name nextcloud-aio-mastercontainer ^
--restart always ^
--publish 80:80 ^
--publish 8080:8080 ^
--publish 8443:8443 ^
--volume nextcloud_aio_mastercontainer:/mnt/docker-aio-config ^
--volume //var/run/docker.sock:/var/run/docker.sock:ro ^
ghcr.io/nextcloud-releases/all-in-one:latest
```

Also, you may be interested in adjusting Nextcloud's Datadir to store the files on the host system. See [this documentation](https://github.com/nextcloud/all-in-one#how-to-change-the-default-location-of-nextclouds-datadir) on how to do it.

> [!NOTE]  
> Almost all commands in this project's documentation use `sudo docker ...`. Since `sudo` is not available on Windows, you simply remove `sudo` from the commands and they should work.  

### How to run AIO on Synology DSM
On Synology, there are two things different in comparison to Linux: instead of using `--volume /var/run/docker.sock:/var/run/docker.sock:ro`, you need to use `--volume /volume1/docker/docker.sock:/var/run/docker.sock:ro` to run it. You also need to add `--env WATCHTOWER_DOCKER_SOCKET_PATH="/volume1/docker/docker.sock"`to the docker run command of the mastercontainer (but before the last line `ghcr.io/nextcloud-releases/all-in-one:latest`). Apart from that it should work and behave the same like on Linux. Obviously the Synology Docker GUI will not work with that so you will need to either use SSH or create a user-defined script task in the task scheduler as the user 'root' in order to run the command.

> [!NOTE]  
> It is possible that the docker socket on your Synology is located in `/var/run/docker.sock` like the default on Linux. Then you can just use the Linux command without having to change anything - you will notice this when you try to start the container and it says that the bind mount failed. E.g. `docker: Error response from daemon: Bind mount failed: '/volume1/docker/docker.sock' does not exists.` 

Also, you may be interested in adjusting Nextcloud's Datadir to store the files on the host system. See [this documentation](https://github.com/nextcloud/all-in-one#how-to-change-the-default-location-of-nextclouds-datadir) on how to do it.

You'll also need to adjust Synology's firewall, see below:

<details>
<summary>Click here to expand</summary>

The Synology DSM is vulnerable to attacks with it's open ports and login interfaces, which is why a firewall setup is always recommended. If a firewall is activated it is necessary to have exceptions for ports 80,443, the subnet of the docker bridge which includes the Nextcloud containers, your public static IP (if you don't use DDNS) and if applicable your NC-Talk ports 3478 TCP+UDP:

![Screenshot 2023-01-19 at 14 13 48](https://user-images.githubusercontent.com/70434961/213677995-71a9f364-e5d2-49e5-831e-4579f217c95c.png)

If you have the NAS setup on your local network (which is most often the case) you will need to setup the Synology DNS to be able to access Nextcloud from your network via its domain. Also don't forget to add the new DNS to your DHCP server and your fixed IP settings:
 
![Screenshot 2023-01-20 at 12 13 44](https://user-images.githubusercontent.com/70434961/213683295-0b39a2bd-7a26-414c-a408-127dd4f07826.png)
</details>

### How to run AIO with Portainer?
The easiest way to run it with Portainer on Linux is to use Portainer's stacks feature and use [this docker-compose file](./compose.yaml) in order to start AIO correctly. 

### Can I run AIO on TrueNAS SCALE?
With the Truenas Scale Release 24.10.0 (which was officially released on October 29th 2024 as a stable release) IX Systems ditched the Kubernetes integration and implemented a fully working docker environment.

For a more complete guide, see this guide by @zybster: https://github.com/nextcloud/all-in-one/discussions/5506

On older TrueNAS SCALE releases with Kubernetes environment, there are two ways to run AIO. The preferred one is to run AIO inside a VM. This is necessary since they do not expose the docker socket for containers on the host, you also cannot use docker-compose on it thus and it is also not possible to run custom helm-charts that are not explicitly written for TrueNAS SCALE.

Another but untested way is to install Portainer on your TrueNAS SCALE from here https://truecharts.org/charts/stable/portainer/installation-notes and add the Helm-chart repository https://nextcloud.github.io/all-in-one/ into Portainer by following https://docs.portainer.io/user/kubernetes/helm. More docs on AIOs Helm Chart are available here: https://github.com/nextcloud/all-in-one/tree/main/nextcloud-aio-helm-chart#nextcloud-aio-helm-chart.

### How to run `occ` commands?
Simply run the following: `sudo docker exec --user www-data -it nextcloud-aio-nextcloud php occ your-command`. Of course `your-command` needs to be exchanged with the command that you want to run.

### How to resolve `Security & setup warnings displays the "missing default phone region" after initial install`?
Simply run the following command: `sudo docker exec --user www-data nextcloud-aio-nextcloud php occ config:system:set default_phone_region --value="yourvalue"`. Of course you need to modify `yourvalue` based on your location. Examples are `DE`, `US` and `GB`. See this list for more codes: https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Officially_assigned_code_elements

### How to run multiple AIO instances on one server?
See [multiple-instances.md](./multiple-instances.md) for some documentation on this.

### Bruteforce protection FAQ
Nextcloud features a built-in bruteforce protection which may get triggered and will block an ip-address or disable a user. You can unblock an ip-address by running `sudo docker exec --user www-data -it nextcloud-aio-nextcloud php occ security:bruteforce:reset <ip-address>` and enable a disabled user by running `sudo docker exec --user www-data -it nextcloud-aio-nextcloud php occ user:enable <name of user>`. See https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/occ_command.html#security for further information.

### How to switch the channel?
You can switch to a different channel like e.g. the beta channel or from the beta channel back to the latest channel by stopping the mastercontainer, removing it (no data will be lost) and recreating the container using the same command that you used initially to create the mastercontainer. You simply need to change the last line `ghcr.io/nextcloud-releases/all-in-one:latest` to `ghcr.io/nextcloud-releases/all-in-one:beta` and vice versa.

### How to update the containers?
If we push new containers to `latest`, you will see in the AIO interface below the `containers` section that new container updates were found. In this case, just press `Stop containers` and `Start and update containers` in order to update the containers. The mastercontainer has its own update procedure though. See below. And don't forget to back up the current state of your instance using the built-in backup solution before starting the containers again! Otherwise you won't be able to restore your instance easily if something should break during the update. 

If a new `mastercontainer` update was found, you'll see a note below the `Stop containers` button that allows to show the changelog. If you click that button and the containers are stopped, you will see a new button that allows to update the mastercontainer. After doing so and after the update is gone through, you will have the  option again to `Start and update containers`. It is recommended to create a backup before clicking the `Start and update containers` button.

Additionally, there is a cronjob that runs once a day that checks for container and mastercontainer updates and sends a notification to all Nextcloud admins if a new update was found.

### How to easily log in to the AIO interface?
If your Nextcloud is running and you are logged in as admin in your Nextcloud, you can easily log in to the AIO interface by opening `https://yourdomain.tld/settings/admin/overview` which will show a button on top that enables you to log in to the AIO interface by just clicking on this button. 

> [!Note]
> You can change the domain/ip-address/port of the button by simply stopping the containers, visiting the AIO interface from the correct and desired domain/ip-address/port and clicking once on `Start containers`.

### How to change the domain?
> [!NOTE]  
> Editing the configuration.json manually and making a mistake may break your instance so please create a backup first!

If you set up a new AIO instance, you need to enter a domain. Currently there is no way to change this domain afterwards from the AIO interface. So in order to change it, you need to edit the configuration.json manually using `sudo docker run -it --rm --volume nextcloud_aio_mastercontainer:/mnt/docker-aio-config:rw alpine sh -c "apk add --no-cache nano && nano /mnt/docker-aio-config/data/configuration.json"`, substitute each occurrence of your old domain with your new domain and save and write out the file. Afterwards restart your containers from the AIO interface and everything should work as expected if the new domain is correctly configured.<br>
If you are running AIO behind a web server or reverse proxy (like Apache, Nginx, Caddy, Cloudflare Tunnel and else), you need to obviously also change the domain in your reverse proxy config.

Additionally, after restarting the containers, you need to open the admin settings and update some values manually that cannot be changed automatically. Here is a list of some known places:
- `https://your-nc-domain.com/settings/admin/talk` for Turn/Stun server and Signaling Server if you enabled Talk via the AIO interface
- `https://your-nc-domain.com/settings/admin/theming` for the theming URL
- `https://your-nc-domain.com/settings/admin/app_api` for the deploy daemon if you enabled the App API via the AIO interface

### How to properly reset the instance?
If something goes unexpected routes during the initial installation, you might want to reset the AIO installation to be able to start from scratch.

> [!NOTE]  
> If you already have it running and have data on your instance, you should not follow these instructions as it will delete all data that is coupled to your AIO instance.

Here is how to reset the AIO instance properly:
1. Stop all containers if they are running from the AIO interface
1. Stop the mastercontainer with `sudo docker stop nextcloud-aio-mastercontainer`
1. If the domaincheck container is still running, stop it with `sudo docker stop nextcloud-aio-domaincheck`
1. Check that no AIO containers are running anymore by running `sudo docker ps --format {{.Names}}`. If no `nextcloud-aio` containers are listed, you can proceed with the steps below. If there should be some, you will need to stop them with `sudo docker stop <container_name>` until no one is listed anymore.
1. Check which containers are stopped: `sudo docker ps --filter "status=exited"`
1. Now remove all these stopped containers with `sudo docker container prune`
1. Delete the docker network with `sudo docker network rm nextcloud-aio`
1. Check which volumes are dangling with `sudo docker volume ls --filter "dangling=true"`
1. Now remove all these dangling volumes: `sudo docker volume prune --filter all=1` (on Windows you might need to remove some volumes afterwards manually with `docker volume rm nextcloud_aio_backupdir`, `docker volume rm nextcloud_aio_nextcloud_datadir`). 
1. If you've configured `NEXTCLOUD_DATADIR` to a path on your host instead of the default volume, you need to clean that up as well. (E.g. by simply deleting the directory).
1. Make sure that no volumes are remaining with `sudo docker volume ls --format {{.Name}}`. If no `nextcloud-aio` volumes are listed, you can proceed with the steps below. If there should be some, you will need to remove them with `sudo docker volume rm <volume_name>` until no one is listed anymore.
1. Optional: You can remove all docker images with `sudo docker image prune -a`.
1. And you are done! Now feel free to start over with the recommended docker run command!

### Can I use a CIFS/SMB share as Nextcloud's datadir?
Sure. Add this to the `/etc/fstab` file on the host system: <br>
`<your-storage-host-and-subpath> <your-mount-dir> cifs rw,mfsymlinks,seal,credentials=<your-credentials-file>,uid=33,gid=0,file_mode=0770,dir_mode=0770 0 0`<br>
(Of course you need to modify `<your-storage-host-and-subpath>`, `<your-mount-dir>` and `<your-credentials-file>` for your specific case.)

One example could look like this:<br>
`//your-storage-host/subpath /mnt/storagebox cifs rw,mfsymlinks,seal,credentials=/etc/storage-credentials,uid=33,gid=0,file_mode=0770,dir_mode=0770 0 0`<br>
and add into `/etc/storage-credentials`:
```
username=<smb/cifs username>
password=<password>
```
(Of course you need to modify `<smb/cifs username>` and `<password>` for your specific case.)

Now you can use `/mnt/storagebox` as Nextcloud's datadir like described in the section above this one.

### Can I run this with Docker swarm?
Yes. For that to work, you need to use and follow the [manual-install documentation](./manual-install/).

### Can I run this with Kubernetes?
Yes. For that to work, you need to use and follow the [helm-chart documentation](./nextcloud-aio-helm-chart/).

### How to run this with Docker rootless?
You can run AIO also with docker rootless. How to do this is documented here: [docker-rootless.md](https://github.com/nextcloud/all-in-one/blob/main/docker-rootless.md)

### Can I run this with Podman instead of Docker?
Since Podman is not 100% compatible with the Docker API, Podman is not supported (since that would add yet another platform where the maintainer would need to test on). However you can use and follow the [manual-install documentation](./manual-install/) to get AIO's containers running with Podman or use Docker rootless, as described in the above section. Also there is this now: https://github.com/nextcloud/all-in-one/discussions/3487

### Access/Edit Nextcloud files/folders manually
The files and folders that you add to Nextcloud are by default stored in the following docker directory: `nextcloud_aio_nextcloud:/mnt/ncdata/` (usually `/var/lib/docker/volumes/nextcloud_aio_nextcloud_data/_data/` on linux host systems). If needed, you can modify/add/delete files/folders there but **ATTENTION**: be very careful when doing so because you might corrupt your AIO installation! Best is to create a backup using the built-in backup solution before editing/changing files/folders in there because you will then be able to restore your instance to the backed up state.

After you are done modifying/adding/deleting files/folders, don't forget to apply the correct permissions by running: `sudo docker exec nextcloud-aio-nextcloud chown -R 33:0 /mnt/ncdata/` and `sudo docker exec nextcloud-aio-nextcloud chmod -R 750 /mnt/ncdata/` and rescan the files with `sudo docker exec --user www-data -it nextcloud-aio-nextcloud php occ files:scan --all`.

### How to edit Nextclouds config.php file with a texteditor?
You can edit Nextclouds config.php file directly from the host with your favorite text editor. E.g. like this: `sudo docker run -it --rm --volume nextcloud_aio_nextcloud:/var/www/html:rw alpine sh -c "apk add --no-cache nano && nano /var/www/html/config/config.php"`. Make sure to not break the file though which might corrupt your Nextcloud instance otherwise. In best case, create a backup using the built-in backup solution before editing the file.

### How to change default files by creating a custom skeleton directory?
All users see a set of [default files and folders](https://docs.nextcloud.com/server/latest/admin_manual/configuration_files/default_files_configuration.html) as dictated by Nextcloud's configuration.  To change these default files and folders a custom skeleton directory must first be created; this can be accomplished by copying your skeleton files `sudo docker cp --follow-link /path/to/nextcloud/skeleton/ nextcloud-aio-nextcloud:/mnt/ncdata/skeleton/`, applying the correct permissions with `sudo docker exec nextcloud-aio-nextcloud chown -R 33:0 /mnt/ncdata/skeleton/` and `sudo docker exec nextcloud-aio-nextcloud chmod -R 750 /mnt/ncdata/skeleton/` and setting the skeleton directory option with `sudo docker exec --user www-data -it nextcloud-aio-nextcloud php occ config:system:set skeletondirectory --value="/mnt/ncdata/skeleton"`.  Further information is available in the Nextcloud documentation on [configuration parameters for the skeleton directory](https://docs.nextcloud.com/server/stable/admin_manual/configuration_server/config_sample_php_parameters.html#skeletondirectory).

### How to adjust the version retention policy and trashbin retention policy?
By default, AIO sets the `versions_retention_obligation` and `trashbin_retention_obligation` both to `auto, 30` which means that versions and items in the trashbin get deleted after 30 days. If you want to change this, see https://docs.nextcloud.com/server/latest/admin_manual/configuration_files/file_versioning.html.

### How to enable automatic updates without creating a backup beforehand?
If you have an external backup solution, you might want to enable automatic updates without creating a backup first. However note that doing this is disrecommended since you will not be able to easily create and restore a backup from the AIO interface anymore and you need to make sure to shut down all the containers properly before creating the backup, e.g. by stopping them from the AIO interface first. 

But anyhow, is here a guide that helps you automate the whole procedure:

<details>
<summary>Click here to expand</summary>

```bash
#!/bin/bash

# Stop the containers
docker exec --env STOP_CONTAINERS=1 nextcloud-aio-mastercontainer /daily-backup.sh

# Below is optional if you run AIO in a VM which will shut down the VM afterwards
# poweroff

```

</details>

You can simply copy and paste the script into a file e.g. named `shutdown-script.sh` e.g. here: `/root/shutdown-script.sh`. 

Afterwards apply the correct permissions with `sudo chown root:root /root/shutdown-script.sh` and `sudo chmod 700 /root/shutdown-script.sh`. Then you can create a cronjob that runs it on a schedule e.g. runs the script at `04:00` each day like this: 
1. Open the cronjob with `sudo crontab -u root -e` (and choose your editor of choice if not already done. I'd recommend nano). 
1. Add the following new line to the crontab if not already present: `0 4 * * * /root/shutdown-script.sh` which will run the script at 04:00 each day. 
1. save and close the crontab (when using nano the shortcuts for this are `Ctrl + o` and then `Enter` to save, and close the editor with `Ctrl + x`).


**After that is in place, you should schedule a backup from your backup solution that creates a backup after AIO is shut down properly. Hint: If your backup runs on the same host, make sure to at least back up all docker volumes and additionally Nextcloud's datadir if it is not stored in a docker volume.**

**Afterwards, you can create a second script that automatically updates the containers:**

<details>
<summary>Click here to expand</summary>

```bash
#!/bin/bash

# Run container update once
if ! docker exec --env AUTOMATIC_UPDATES=1 nextcloud-aio-mastercontainer /daily-backup.sh; then
    while docker ps --format "{{.Names}}" | grep -q "^nextcloud-aio-watchtower$"; do
        echo "Waiting for watchtower to stop"
        sleep 30
    done

    while ! docker ps --format "{{.Names}}" | grep -q "^nextcloud-aio-mastercontainer$"; do
        echo "Waiting for Mastercontainer to start"
        sleep 30
    done

    # Run container update another time to make sure that all containers are updated correctly.
    docker exec --env AUTOMATIC_UPDATES=1 nextcloud-aio-mastercontainer /daily-backup.sh
fi

```

</details>

You can simply copy and paste the script into a file e.g. named `automatic-updates.sh` e.g. here: `/root/automatic-updates.sh`.

Afterwards apply the correct permissions with `sudo chown root:root /root/automatic-updates.sh` and `sudo chmod 700 /root/automatic-updates.sh`. Then you can create a cronjob that runs e.g. at `05:00` each day like this: 
1. Open the cronjob with `sudo crontab -u root -e` (and choose your editor of choice if not already done. I'd recommend nano). 
1. Add the following new line to the crontab if not already present: `0 5 * * * /root/automatic-updates.sh` which will run the script at 05:00 each day. 
1. save and close the crontab (when using nano the shortcuts for this are `Ctrl + o` then `Enter` to save, and close the editor with `Ctrl + x`).

### Securing the AIO interface from unauthorized ACME challenges
[By design](https://github.com/nextcloud/all-in-one/discussions/4882#discussioncomment-9858384), Caddy that runs inside the mastercontainer, which handles automatic TLS certificate generation for the AIO interface on port 8443, is configured to accept traffic on any valid domain in order to make the AIO interface as convenient to use as possible. However due to this, it is vulnerable to receiving DNS challenges for arbitrary hostnames from anyone on the internet. While this does not compromise your server's security, it can result in cluttered logs and rejected certificate renewal attempts due to rate limit abuse. To mitigate this issue, it is recommended to place the AIO interface behind a VPN and/or limit its public exposure.

### How to migrate from an already existing Nextcloud installation to Nextcloud AIO?
Please see the following documentation on this: [migration.md](https://github.com/nextcloud/all-in-one/blob/main/migration.md)

## Backup
Nextcloud AIO provides a backup solution based on [BorgBackup](https://github.com/borgbackup/borg#what-is-borgbackup). These backups act as a restore point in case the installation gets corrupted. By using this tool, backups are incremental, differential, compressed and encrypted – so only the first backup will take a while. Further backups should be fast as only changes are taken into account.

It is recommended to create a backup before any container update. By doing this, you will be safe regarding any possible complication during updates because you will be able to restore the whole instance with basically one click. 

For local backups, the restore process should be pretty fast as rsync is used to restore the chosen backup which only transfers changed files and deletes additional ones. For remote borg backups, the whole backup archive is extracted from the remote, which depending on how clever `borg extract` is, may require downloading the whole archive.

If you connect an external drive to your host, and choose the backup directory to be on that drive, you are also kind of safe against drive failures of the drive where the docker volumes are stored on. 

<details>
<summary>How to do the above step for step</summary>

1. Mount an external/backup HDD to the host OS using the built-in functionality or udev rules or whatever way you prefer. (E.g. follow this video: https://www.youtube.com/watch?v=2lSyX4D3v_s) and mount the drive in best case in `/mnt/backup`.
2. If not already done, fire up the docker container and set up Nextcloud as per the guide.
3. Now open the AIO interface.
4. Under backup section, add your external disk mountpoint as backup directory, e.g. `/mnt/backup`.
5. Click on `Create Backup` which should create the first backup on the external disk.

</details>

If you want to back up directly to a remote borg repository:

<details>
<summary>How to do the above step for step</summary>

1. Create your borg repository at the remote. Note down the repository URL for later.
2. Open the AIO interface
3. Under backup section, leave the local path blank and fill in the url to your borg repository that you noted down earlier.
4. Click on `Create backup`, this will create an ssh key pair and fail because the remote doesn't trust this key yet. Copy the public key shown in AIO and add it to your authorized keys on the remote.
5. Try again to create a backup, this time it should succeed.

</details>

Backups can be created and restored in the AIO interface using the buttons `Create Backup` and `Restore selected backup`. Additionally, a backup check is provided that checks the integrity of your backups but it shouldn't be needed in most situations. 

The backups themselves get encrypted with an encryption key that gets shown to you in the AIO interface. Please save that at a safe place as you will not be able to restore from backup without this key.

Daily backups can get enabled after the initial backup is done. Enabling this also allows to enable an option that allows to automatically update all containers, Nextcloud and its apps.

Be aware that this solution does not back up files and folders that are mounted into Nextcloud using the external storage app - but you can add further Docker volumes and host paths that you want to back up after the initial backup is done.

---

### What is getting backed up by AIO's backup solution?
Backed up will get all important data of your Nextcloud AIO instance required to restore the instance, like the database, your files and configuration files of the mastercontainer and else. Files and folders that are mounted into Nextcloud using the external storage app are not getting backed up. There is currently no way to exclude the data directory because it would require hacks like running files:scan and would make the backup solution much more unreliable (since the database and your files/folders need to stay in sync). If you still don't want your datadirectory to be backed up, see https://github.com/nextcloud/all-in-one#how-to-enable-automatic-updates-without-creating-a-backup-beforehand for options (there is a hint what needs to be backed up in which order).

### How to adjust borgs retention policy?
The built-in borg-based backup solution has by default a retention policy of `--keep-within=7d --keep-weekly=4 --keep-monthly=6`. See https://borgbackup.readthedocs.io/en/stable/usage/prune.html for what these values mean. You can adjust the retention policy by providing `--env BORG_RETENTION_POLICY="--keep-within=7d --keep-weekly=4 --keep-monthly=6"` to the docker run command of the mastercontainer (but before the last line `ghcr.io/nextcloud-releases/all-in-one:latest`! If it was started already, you will need to stop the mastercontainer, remove it (no data will be lost) and recreate it using the docker run command that you initially used) and customize the value to your fitting. ⚠️ Please make sure that this value is valid, otherwise backup pruning will bug out!

### How to migrate from AIO to AIO?
If you have the borg backup feature enabled, you can copy it over to the new host and restore from the backup. This guide assumes the new installation data dir will be on `/mnt/datadir`, you can adjust the steps if it's elsewhere.

1. Set the DNS entry to 60 seconds TTL if applicable
1. On your current installation, use the AIO interface to:
    1. Update AIO and all containers
    1. Stop all containers (from now on, your cloud is down)
    1. Create a current borg backup
    1. Note the path where the backups are stored and the encryption password
1. Navigate to the backup folder
1. Create archive of the backup so it's easier to copy: `tar -czvf borg.tar.gz borg`
1. Copy the archive over to the new host: `scp borg.tar.gz user@new.host:/mnt`. Make sure to replace `user` with your actual user and `new.host` with the IP or domain of the actual host. You can also use another way to copy the archive.
1. Switch to the new host
1. Go to the folder you put the backup archive and extract it with `tar -xf borg.tar.gz`
1. Follow the installation guide to create a new aio instance, but do not start the containers yet (the `docker run` or `docker compose up -d` command)
1. Change the DNS entry to the new host's IP
1. Configure your reverse proxy if you use one
1. Start the AIO container and open the new AIO interface in your browser
1. Make sure to save the newly generated passphrase and enter it in the next step
1. Select the "Restore former AIO instance from backup" option and enter the encryption password from the old backup and the path in which the extracted `borg` folder lies in (without the borg part) and hit `Submit location and password`
1. Choose the latest backup in the dropdown and hit `Restore selected backup`
1. Wait until the backup is restored
1. Start the containers in the AIO interface

### Are remote borg backups supported?
Backing up directly to a remote borg repository is supported. This avoids having to store a local copy of your backups, supports append-only borg keys to counter ransomware and allows using the AIO interface to manage your backups.

Some alternatives, which do not have all the above benefits:

- Mount a network FS like SSHFS, SMB or NFS in the directory that you enter in AIO as backup directory
- Use rsync or rclone for syncing the borg backup archive that AIO creates locally to a remote target (make sure to lock the backup archive correctly before starting the sync; search for "aio-lockfile"; you can find a local example script here: https://github.com/nextcloud/all-in-one#sync-local-backups-regularly-to-another-drive)
- You can find a well written guide that uses rclone and e.g. BorgBase for remote backups here: https://github.com/nextcloud/all-in-one/discussions/2247
- Here is another one that utilizes borgmatic and BorgBase for remote backups: https://github.com/nextcloud/all-in-one/discussions/4391
- create your own backup solution using a script and borg, borgmatic or any other to backup tool for backing up to a remote target (make sure to stop and start the AIO containers correctly following https://github.com/nextcloud/all-in-one#how-to-enable-automatic-updates-without-creating-a-backup-beforehand)

---

### Failure of the backup container in LXC containers
If you are running AIO in a LXC container, you need to make sure that FUSE is enabled in the LXC container settings. Also, if using Alpine Linux as host OS, make sure to add fuse via `apk add fuse`. Otherwise the backup container will not be able to start as FUSE is required for it to work.

---

### How to create the backup volume on Windows?
As stated in the AIO interface, it is possible to use a docker volume as backup target. Before you can use that, you need to create it first. Here is an example how to create one on Windows:
```
docker volume create ^
--driver local ^
--name nextcloud_aio_backupdir ^
-o device="/host_mnt/e/your/backup/path" ^
-o type="none" ^
-o o="bind"
```
In this example, it would mount `E:\your\backup\path` into the volume so for a different location you need to adjust `/host_mnt/e/your/backup/path` accordingly. Afterwards enter `nextcloud_aio_backupdir` in the AIO interface as backup location.

---

### Pro-tip: Backup archives access
You can open the BorgBackup archives on your host by following these steps:<br>
(instructions for Ubuntu Desktop)

Alternatively, there is now a community container that allows to access your backups in a web session: https://github.com/nextcloud/all-in-one/tree/main/community-containers/borgbackup-viewer.

```bash
# Install borgbackup on the host
sudo apt update && sudo apt install borgbackup

# In any shell where you use borg, you must first export this variable
# If you are using the default backup location /mnt/backup/borg
export BORG_REPO='/mnt/backup/borg'
# or if you are using a remote repository
export BORG_REPO='user@host:/path/to/repo'

# Mount the archives to /tmp/borg
sudo mkdir -p /tmp/borg && sudo borg mount "$BORG_REPO" /tmp/borg

# After entering your repository key successfully, you should be able to access all archives in /tmp/borg
# You can now do whatever you want by syncing them to a different place using rsync or doing other things
# E.g. you can open the file manager on that location by running:
xhost +si:localuser:root && sudo nautilus /tmp/borg

# When you are done, simply close the file manager and run the following command to unmount the backup archives:
sudo umount /tmp/borg
```

---

### Delete backup archives manually
You can delete BorgBackup archives on your host manually by following these steps:<br>
(instructions for Debian based OS' like Ubuntu)

Alternatively, there is now a community container that allows to access your backups in a web session: https://github.com/nextcloud/all-in-one/tree/main/community-containers/borgbackup-viewer.

```bash
# Install borgbackup on the host
sudo apt update && sudo apt install borgbackup

# In any shell where you use borg, you must first export this variable
# If you are using the default backup location /mnt/backup/borg
export BORG_REPO='/mnt/backup/borg'
# or if you are using a remote repository
export BORG_REPO='user@host:/path/to/repo'

# List all archives (if you are using the default backup location /mnt/backup/borg)
sudo borg list

# After entering your repository key successfully, you should now see a list of all backup archives
# An example backup archive might be called 20220223_174237-nextcloud-aio
# Then you can simply delete the archive with:
sudo borg delete --stats --progress "::20220223_174237-nextcloud-aio"

# If borg 1.2.0 or higher is installed, you then need to run borg compact in order to clean up the freed space
sudo borg --version
# If version number of the command above is higher than 1.2.0 you need to run the command below:
sudo borg compact

```

After doing so, make sure to update the backup archives list in the AIO interface!<br>
You can do so by clicking on the `Check backup integrity` button or `Create backup` button.

---

### Sync local backups regularly to another drive
For increased backup security, you might consider syncing the local backup repository regularly to another drive.

To do that, first add the drive to `/etc/fstab` so that it is able to get automatically mounted and then create a script that does all the things automatically. Here is an example for such a script:

<details>
<summary>Click here to expand</summary>

```bash
#!/bin/bash

# Please modify all variables below to your needings:
SOURCE_DIRECTORY="/mnt/backup/borg"
DRIVE_MOUNTPOINT="/mnt/backup-drive"
TARGET_DIRECTORY="/mnt/backup-drive/borg"

########################################
# Please do NOT modify anything below! #
########################################

if [ "$EUID" -ne 0 ]; then 
    echo "Please run as root"
    exit 1
fi

if ! [ -d "$SOURCE_DIRECTORY" ]; then
    echo "The source directory does not exist."
    exit 1
fi

if [ -z "$(ls -A "$SOURCE_DIRECTORY/")" ]; then
    echo "The source directory is empty which is not allowed."
    exit 1
fi

if ! [ -d "$DRIVE_MOUNTPOINT" ]; then
    echo "The drive mountpoint must be an existing directory"
    exit 1
fi

if ! grep -q "$DRIVE_MOUNTPOINT" /etc/fstab; then
    echo "Could not find the drive mountpoint in the fstab file. Did you add it there?"
    exit 1
fi

if ! mountpoint -q "$DRIVE_MOUNTPOINT"; then
    mount "$DRIVE_MOUNTPOINT"
    if ! mountpoint -q "$DRIVE_MOUNTPOINT"; then
        echo "Could not mount the drive. Is it connected?"
        exit 1
    fi
fi

if [ -f "$SOURCE_DIRECTORY/lock.roster" ]; then
    echo "Cannot run the script as the backup archive is currently changed. Please try again later."
    exit 1
fi

mkdir -p "$TARGET_DIRECTORY"
if ! [ -d "$TARGET_DIRECTORY" ]; then
    echo "Could not create target directory"
    exit 1
fi

if [ -f "$SOURCE_DIRECTORY/aio-lockfile" ]; then
    echo "Not continuing because aio-lockfile already exists."
    exit 1
fi

touch "$SOURCE_DIRECTORY/aio-lockfile"

if ! rsync --stats --archive --human-readable --delete "$SOURCE_DIRECTORY/" "$TARGET_DIRECTORY"; then
    echo "Failed to sync the backup repository to the target directory."
    exit 1
fi

rm "$SOURCE_DIRECTORY/aio-lockfile"
rm "$TARGET_DIRECTORY/aio-lockfile"

umount "$DRIVE_MOUNTPOINT"

if docker ps --format "{{.Names}}" | grep "^nextcloud-aio-nextcloud$"; then
    docker exec nextcloud-aio-nextcloud bash /notify.sh "Rsync backup successful!" "Synced the backup repository successfully."
else
    echo "Synced the backup repository successfully."
fi

```

</details>

You can simply copy and paste the script into a file e.g. named `backup-script.sh` e.g. here: `/root/backup-script.sh`. Do not forget to modify the variables to your requirements!

Afterwards apply the correct permissions with `sudo chown root:root /root/backup-script.sh` and `sudo chmod 700 /root/backup-script.sh`. Then you can create a cronjob that runs e.g. at `20:00` each week on Sundays like this: 
1. Open the cronjob with `sudo crontab -u root -e` (and choose your editor of choice if not already done. I'd recommend nano). 
1. Add the following new line to the crontab if not already present: `0 20 * * 7 /root/backup-script.sh` which will run the script at 20:00 on Sundays each week. 
1. save and close the crontab (when using nano are the shortcuts for this `Ctrl + o` -> `Enter` and close the editor with `Ctrl + x`).

### How to exclude Nextcloud's data directory or the preview folder from backup?
In order to speed up the backups and to keep the backup archives small, you might want to exclude Nextcloud's data directory or its preview folder from backup. 

> [!WARNING]
> However please note that you will run into problems if the database and the data directory or preview folder get out of sync. **So please only read further, if you have an additional external backup of the data directory!** See [this guide](#how-to-enable-automatic-updates-without-creating-a-backup-beforehand) for example.

> [!TIP]
> A better option is to use the external storage app inside Nextcloud as the data connected via the external storage app is not backed up by AIO's backup solution. See [this documentation](https://docs.nextcloud.com/server/latest/admin_manual/configuration_files/external_storage_configuration_gui.html) on how to configure the app.

If you still want to proceed, you can exclude the data directory by simply creating a `.noaiobackup` file in the root directory of the specified `NEXTCLOUD_DATADIR` target. The same logic is implemented for the preview folder that is located inside the data directory, inside the `appdata_*/preview` folder. So simply create a `.noaiobackup` file in there if you want to exclude the preview folder.

After doing a restore via the AIO interface, you might run into problems due to the data directory and database being out of sync. You might be able to fix this by running `occ files:scan --all` and `occ maintenance:repair` and `occ files:scan-app-data`. See https://github.com/nextcloud/all-in-one#how-to-run-occ-commands. If only the preview folder is excluded, the command `occ files:scan-app-data preview` should be used.

### How to stop/start/update containers or trigger the daily backup from a script externally?
> [!WARNING]  
> The below script will only work after the initial setup of AIO. So you will always need to first visit the AIO interface, type in your domain and start the containers the first time or restore an older AIO instance from its borg backup before you can use the script.

You can do so by running the `/daily-backup.sh` script that is stored in the mastercontainer. It accepts the following environment variables:
- `AUTOMATIC_UPDATES` if set to `1`, it will automatically stop the containers, update them and start them including the mastercontainer. If the mastercontainer gets updated, this script's execution will stop as soon as the mastercontainer gets stopped. You can then wait until it is started again and run the script with this flag again in order to update all containers correctly afterwards.
- `DAILY_BACKUP` if set to `1`, it will automatically stop the containers and create a backup. If you want to start them again afterwards, you may have a look at the `START_CONTAINERS` option.
- `START_CONTAINERS` if set to `1`, it will automatically start the containers without updating them.
- `STOP_CONTAINERS` if set to `1`, it will automatically stop the containers.
- `CHECK_BACKUP` if set to `1`, it will start the backup check. This is not allowed to be enabled at the same time like `DAILY_BACKUP`. Please be aware that this option is non-blocking which means that the backup check is not done when the process is finished since it only start the borgbackup container with the correct configuration.

One example for this would be `sudo docker exec -it --env DAILY_BACKUP=1 nextcloud-aio-mastercontainer /daily-backup.sh`, which you can run via a cronjob or put it in a script.

> [!NOTE]  
> None of the option returns error codes. So you need to check for the correct result yourself.

### How to disable the backup section?
If you already have a backup solution in place, you may want to hide the backup section. You can do so by adding `--env AIO_DISABLE_BACKUP_SECTION=true` to the docker run command of the mastercontainer (but before the last line `ghcr.io/nextcloud-releases/all-in-one:latest`! If it was started already, you will need to stop the mastercontainer, remove it (no data will be lost) and recreate it using the docker run command that you initially used).

## Addons

### Fail2ban
You can configure your server to block certain ip-addresses using fail2ban as bruteforce protection. Here is how to set it up: https://docs.nextcloud.com/server/stable/admin_manual/installation/harden_server.html#setup-fail2ban. The logpath of AIO is by default `/var/lib/docker/volumes/nextcloud_aio_nextcloud/_data/data/nextcloud.log`. Do not forget to add `chain=DOCKER-USER` to your nextcloud jail config (`nextcloud.local`) otherwise the nextcloud service running on docker will still be accessible even if the IP is banned. Also, you may change the blocked ports to cover all AIO ports: by default `80,443,8080,8443,3478` (see [this](https://github.com/nextcloud/all-in-one#explanation-of-used-ports)). Apart from that there is now a community container that can be added to the AIO stack: https://github.com/nextcloud/all-in-one/tree/main/community-containers/fail2ban

### LDAP
It is possible to connect to an existing LDAP server. You need to make sure that the LDAP server is reachable from the Nextcloud container. Then you can enable the LDAP app and configure LDAP in Nextcloud manually. If you don't have a LDAP server yet, recommended is to use this docker container: https://hub.docker.com/r/nitnelave/lldap. Make sure here as well that Nextcloud can talk to the LDAP server. The easiest way is by adding the LDAP docker container to the docker network `nextcloud-aio`. Then you can connect to the LDAP container by its name from the Nextcloud container. There is now a community container which allows to easily add LLDAP to AIO: https://github.com/nextcloud/all-in-one/tree/main/community-containers/lldap

### Netdata
Netdata allows you to monitor your server using a GUI. You can install it by following https://learn.netdata.cloud/docs/agent/packaging/docker#create-a-new-netdata-agent-container. Apart from that there is now a way for the community to add containers: https://github.com/nextcloud/all-in-one/discussions/392#discussioncomment-7133563

### USER_SQL
If you want to use the user_sql app, the easiest way is to create an additional database container and add it to the docker network `nextcloud-aio`. Then the Nextcloud container should be able to talk to the database container using its name.

### phpMyAdmin, Adminer or pgAdmin
It is possible to install any of these to get a GUI for your AIO database. The pgAdmin container is recommended. You can get some docs on it here: https://www.pgadmin.org/docs/pgadmin4/latest/container_deployment.html. For the container to connect to the aio-database, you need to connect the container to the docker network `nextcloud-aio` and use `nextcloud-aio-database` as database host, `oc_nextcloud` as database username and the password that you get when running `sudo docker exec nextcloud-aio-nextcloud grep dbpassword config/config.php` as the password. Apart from that there is now a way for the community to add containers: https://github.com/nextcloud/all-in-one/discussions/3061#discussioncomment-7307045

### Mail server
You can configure one yourself by using either of these four recommended projects: [Docker Mailserver](https://github.com/docker-mailserver/docker-mailserver/#docker-mailserver), [Mailu](https://github.com/Mailu/Mailu), [Maddy Mail Server](https://github.com/foxcpp/maddy#maddy-mail-server), [Mailcow](https://github.com/mailcow/mailcow-dockerized#mailcow-dockerized-------) or [Stalwart](https://stalw.art/). There is now a community container which allows to easily add Stalwart Mail server to AIO: https://github.com/nextcloud/all-in-one/tree/main/community-containers/stalwart

## Miscellaneous

### Requirements for integrating new containers
For integrating new containers, they must pass specific requirements for being considered to get integrated in AIO itself. Even if not considered, we may add some documentation on it. Also there is this now: https://github.com/nextcloud/all-in-one/tree/main/community-containers#community-containers

What are the requirements?
1. New containers must be related to Nextcloud. Related means that there must be a feature in Nextcloud that gets added by adding this container.
2. It must be optionally installable. Disabling and enabling the container from the AIO interface must work and must not produce any unexpected side-effects.
3. The feature that gets added into Nextcloud by adding the container must be maintained by the Nextcloud GmbH. 
4. It must be possible to run the container without big quirks inside docker containers. Big quirks means e.g. needing to change the capabilities or security options. 
5. The container should not mount directories from the host into the container: only docker volumes should be used.
6. The container must be usable by more than 90% of the users (e.g. not too high system requirements and such)
7. No additional setup should be needed after adding the container - it should work completely out of the box.
8. If the container requires being exposed, only subfolders are supported. So the container should not require its own (sub-)domain and must be able to run in a subfolder.

### Update policy
This project values stability over new features. That means that when a new major Nextcloud update gets introduced, we will wait at least until the first patch release, e.g. `24.0.1` is out before upgrading to it. Also we will wait with the upgrade until all important apps are compatible with the new major version. Minor or patch releases for Nextcloud and all dependencies as well as all containers will be updated to new versions as soon as possible but we try to give all updates first a good test round before pushing them. That means that it can take around 2 weeks before new updates reach the `latest` channel. If you want to help testing, you can switch to the `beta` channel by following [this documentation](#how-to-switch-the-channel) which will also give you the updates earlier.

### How often are update notifications sent?
AIO ships its own update notifications implementation. It checks if container updates are available. If so, it sends a notification with the title `Container updates available!` on saturdays to Nextcloud users that are part of the `admin` group. If the Nextcloud container image should be older than 90 days (~3 months) and thus badly outdated, AIO sends a notification to all Nextcloud users with the title `AIO is outdated!`. Thus admins should make sure to update the container images at least once every 3 months in order to make sure that the instance gets all security bugfixes as soon as possible.

### Huge docker logs
If you should run into issues with huge docker logs, you can adjust the log size by following https://docs.docker.com/config/containers/logging/local/#usage. However for the included AIO containers, this should usually not be needed because almost all of them have the log level set to warn so they should not produce many logs.
