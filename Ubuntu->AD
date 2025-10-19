<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# rentrer un ubuntu dasn l ad apres install\$µ

Pour intégrer un poste Ubuntu à un domaine Active Directory (AD) après l’installation, il suffit de configurer correctement le DNS, Kerberos et SSSD (System Security Services Daemon). L’outil **realmd** simplifie grandement cette jonction et fonctionne bien sur Ubuntu 20.04, 22.04 ou 24.04.[^1][^2][^3]

### Préparation

1. Mettre à jour le système :

```bash
sudo apt update && sudo apt upgrade -y
```

2. Installer les paquets nécessaires :

```bash
sudo apt install realmd sssd-ad sssd-tools libnss-sss libpam-sss adcli samba-common-bin oddjob oddjob-mkhomedir packagekit -y
```

3. Vérifier la résolution DNS vers le domaine AD. Le DNS de la machine Ubuntu doit pointer sur le contrôleur de domaine :

```bash
sudo nano /etc/resolv.conf
```

Ajouter :

```
nameserver <IP_DNS_AD>
search monad.local
```


### Découverte et jonction au domaine

1. Découvrir le domaine :

```bash
realm discover monad.local
```

2. Joindre la machine au domaine :

```bash
sudo realm join --user=Administrateur monad.local
```

Entrer le mot de passe du compte Administrateur AD.
3. Vérifier la jonction :

```bash
realm list
```

4. (Optionnel) Créer automatiquement les répertoires utilisateurs lors de la connexion :

```bash
sudo pam-auth-update --enable mkhomedir
```


### Connexion avec un utilisateur du domaine

Vous pouvez tester la connexion avec :

```bash
su - utilisateur@monad.local
```

Si la jonction est correcte, l’utilisateur AD pourra ouvrir une session et son répertoire personnel sera créé automatiquement.[^4][^2][^3]

Ce processus active une authentification hybride entre Ubuntu et Active Directory, permettant la gestion centralisée des utilisateurs et des politiques, exactement comme sur un poste Windows.
<span style="display:none">[^10][^5][^6][^7][^8][^9]</span>

<div align="center">⁂</div>

[^1]: https://www.datasunrise.com/fr/informations-professionnelles/integration-ubuntu-ad/

[^2]: https://brandonvisca.com/connecter-les-systemes-ubuntu-a-active-directory-en-utilisant-sssd/

[^3]: https://serverspace.io/fr/support/help/linux-machine-into-windows-ad-domain/

[^4]: https://www.youtube.com/watch?v=taMDrdaHg6Y

[^5]: https://neptunet.fr/ubuntu-ad/

[^6]: https://forum.ubuntu-fr.org/viewtopic.php?id=2063150

[^7]: https://le-guide-du-secops.fr/2021/08/10/joindre-une-machine-ubuntu-a-un-domaine-active-directory/

[^8]: http://doc.ubuntu-fr.org/tutoriel/comment_ajouter_machine_ubuntu_dans_domaine_active_directory

[^9]: https://www.reddit.com/r/linuxadmin/comments/zbcmt9/ubuntu_on_a_windows_domain_with_active_directory/

[^10]: https://www.youtube.com/watch?v=XwWSLUuZgjg

