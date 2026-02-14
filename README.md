# LAB-2-Rooting-Android
Étape 1 : Rooter l'AVD

<img width="1328" height="527" alt="image" src="https://github.com/user-attachments/assets/7df5e118-d7a7-4840-8d99-a3205d5140f0" />
<img width="1324" height="327" alt="image" src="https://github.com/user-attachments/assets/90ca31dc-cdda-4126-be4a-8472116e308b" />
<img width="1035" height="695" alt="image" src="https://github.com/user-attachments/assets/d4c314bb-079f-4922-a1ec-8fd9a283368b" />

 Lire Android Security

La sécurité d’Android repose sur plusieurs couches complémentaires, comme un oignon, afin de limiter les risques.
Le sandboxing des applications isole chaque application pour l’empêcher d’accéder aux données des autres.
Le modèle de permissions contrôle l’accès aux ressources sensibles (caméra, stockage, localisation).
L’intégrité globale du système empêche les modifications non autorisées du système d’exploitation.
Le sandboxing est comme placer chaque application dans sa propre salle de classe fermée.
Les permissions et l’intégrité système reviennent à demander l’autorisation au professeur et à verrouiller le bâtiment entier.

<img width="822" height="103" alt="image" src="https://github.com/user-attachments/assets/99130d2a-d24b-445d-b465-7dbfc326ad23" />
<img width="273" height="446" alt="image" src="https://github.com/user-attachments/assets/f599f570-e71e-4885-a536-407dd4fc0257" />
<img width="1919" height="819" alt="image" src="https://github.com/user-attachments/assets/200f78cc-f5bb-4cf0-9263-dd1ee857cc9f" />

AVB (Android Verified Boot)
AVB est la version moderne de Verified Boot dans Android, ajoutant une vérification d’intégrité cryptographique du système au démarrage.
Il garantit que les partitions système n’ont pas été modifiées ou corrompues avant l’exécution.
AVB intègre aussi une protection anti-rollback, empêchant l’installation d’anciennes versions vulnérables du système.

Commande Fastboot (appareil de laboratoire déverrouillé)
adb reboot bootloader
fastboot getvar avb_boot_state

 Définir le rooting
Le rooting correspond à l’obtention des privilèges super-utilisateur (root) sur un système Android, permettant un contrôle total du système.
Il modifie les mécanismes de protection et le modèle de confiance du système, car l’utilisateur peut accéder et altérer toutes les ressources critiques.
En contexte de laboratoire, le rooting est utile pour observer des comportements internes, tester la sécurité ou analyser des mécanismes normalement protégés.
Cependant, il est risqué en environnement réel, ce qui impose un isolement du système, une traçabilité des actions et un reset complet après expérimentation.


Mesures défensives
Réseau isolé afin d’éviter toute communication non contrôlée avec des services externes.
Données fictives uniquement pour éliminer tout risque de fuite ou d’exposition d’informations réelles.
Device ou AVD dédié exclusivement aux tests de sécurité afin d’éviter toute contamination croisée.
Snapshots ou wipe en fin de séance pour garantir qu’aucune trace persistante ne subsiste après les tests.
Journal de configuration détaillé afin d’assurer la reproductibilité et l’auditabilité des expérimentations.
Aucun compte personnel utilisé pour prévenir tout mélange entre données privées et environnement de test.
Contrôle strict des APK installées pour limiter l’introduction de composants malveillants ou non maîtrisés.

OWASP MASVS (2 exigences)
1. MSTG-STORAGE-1 (Stockage Sécurisé)
La Règle : Ne jamais enregistrer de données sensibles (mots de passe, clés API) en texte clair dans les fichiers du téléphone.
Le Test (Root) : Allez dans le dossier /data/data/[app]/shared_prefs. Si vous ouvrez un fichier XML et que vous pouvez lire le mot de passe, l'exigence est non respectée.
2. MSTG-NETWORK-1 (Communication Sécurisée)
La Règle : L'application doit obligatoirement utiliser TLS (HTTPS) pour toutes ses communications réseau afin d'empêcher l'espionnage.
Le Test (Man-in-the-Middle) : Si vous pouvez intercepter et lire les données qui transitent entre l'app et le serveur (via un proxy), l'exigence est non respectée.

OWASP MASTG (2 idées de tests)
1. Test du Stockage Local (SharedPreferences)
Objectif : Vérifier si des secrets sont stockés sans chiffrement.
Action : Avec les droits Root, inspectez le dossier /data/data/[nom.du.paquet]/shared_prefs/.
Commande : cat *.xml
Faille : Trouver un mot de passe ou une clé API lisible en clair dans le fichier.

2. Test des Logs Système (Logcat)
Objectif : Vérifier si l'application divulgue des infos sensibles pendant l'utilisation.
Action : Surveillez les journaux système pendant que vous vous connectez à l'application.
Commande : adb logcat | grep "mot_de_passe" (ou autre mot clé).
Faille : Voir vos données privées s'afficher dans le terminal du PC.

 Commandes de rooting (rappel synthèse)
<img width="1914" height="528" alt="image" src="https://github.com/user-attachments/assets/ef5453d4-fc39-46a4-ab41-c841107a6c9e" />
<img width="1095" height="515" alt="image" src="https://github.com/user-attachments/assets/a6993e7b-2edb-4a96-ba5e-c3210327d006" />
<img width="1090" height="754" alt="image" src="https://github.com/user-attachments/assets/cac1a7a1-076d-4682-ae54-ce292cc40752" />

Fiche Environnement : Pixel 6 (AVD)

<img width="439" height="783" alt="image" src="https://github.com/user-attachments/assets/5327a607-229b-4f72-a300-af3ab0490588" />
<img width="432" height="776" alt="image" src="https://github.com/user-attachments/assets/4c5acba9-498b-4eab-89a0-1ecbbf3e3a6e" />

