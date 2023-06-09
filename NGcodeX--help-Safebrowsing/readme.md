<div align="center">API pour accéder aux listes de ressources Web non sécurisées dans le cadre de la navigation sécurisée Google.</div>
<img src="https://github.com/NGcodeX/NGcodeX_Server/blob/main/.github/workflows/private/safe-browsing.PNG?raw=true">

### Qu'est-ce que la navigation sécurisée ?

La navigation sécurisée est un service Google qui permet aux applications clientes de vérifier les URL par rapport à des listes de ressources Web non sécurisées qui sont constamment mises à jour par Google. Exemples de ressources Web non sécurisées : sites d'ingénierie sociale (sites d'hameçonnage et sites trompeurs) et sites hébergeant des logiciels malveillants ou indésirables. Découvrez toutes les possibilités.

Avec la navigation sécurisée, vous pouvez:

Comparez les pages à nos listes de navigation sécurisée en fonction de la plate-forme et du type de menace.
Avertissez les utilisateurs avant qu'ils ne cliquent sur des liens de votre site susceptibles de mener à des pages infectées.
Empêchez les utilisateurs de publier des liens vers des pages infectées depuis votre site.
L'API Safe Browsing est réservée à un usage non commercial. Si vous devez utiliser des API pour détecter des URL malveillantes à des fins commerciales (autrement dit, pour vendre ou générer des revenus), veuillez vous reporter à l'API Web Risk.

### Apercu

Que sont les API de navigation sécurisée ?
Les API de navigation sécurisée suivantes sont réservées à un usage non commercial. Si vous devez utiliser des API pour détecter des URL malveillantes à des fins commerciales (autrement dit, pour vendre ou générer des revenus), veuillez consulter [l'API Web Risk](https://cloud.google.com/web-risk?hl=fr).

Les API de navigation sécurisée (v4) permettent à vos applications clientes de vérifier les URL par rapport à des listes de ressources Web non sécurisées mises à jour en permanence par Google. Exemples de ressources Web non sécurisées : sites d'ingénierie sociale (sites d'hameçonnage et sites trompeurs) et sites hébergeant des logiciels malveillants ou indésirables. Toute URL figurant sur une liste de navigation sécurisée est considérée comme non sécurisée.

Pour déterminer si une URL figure sur l'une des listes de navigation sécurisée, les clients peuvent utiliser l'API Lookup (v4) ou [l'API Update (v4)](https://developers.google.com/safe-browsing/v4/update-api?hl=fr).

API Lookup (v4)
L'API Lookup permet à vos applications clientes d'envoyer des URL au serveur de navigation sécurisée Google pour vérifier leur état. Cette API est simple et facile à utiliser, car elle évite les complexités de l'API Update.

Avantages :

Vérifications d'URL simplifiées: vous envoyez une requête HTTP POST avec les URL réelles, et le serveur répond avec l'état des URL (sécurisé ou non).
Inconvénients:

Confidentialité: les URL ne sont pas hachées. Le serveur sait donc quelles URL vous recherchez.
Temps de réponse: chaque requête est traitée par le serveur. Nous ne fournissons aucune garantie de délai de réponse de recherche.
Si la confidentialité des URL interrogées n'est pas trop importante et que vous pouvez tolérer la latence induite par une requête réseau, envisagez d'utiliser l'API Lookup, car elle est assez facile à utiliser.

API Update (v4)
L'API Update permet à vos applications clientes de télécharger des versions chiffrées des listes de navigation sécurisée pour les vérifications locales des URL côté client. Elle est conçue pour les clients qui ont besoin de verdicts à haute fréquence et à faible latence. Plusieurs navigateurs Web et plates-formes logicielles utilisent cette API pour protéger de grands ensembles d'utilisateurs.

Avantages :

Confidentialité: vous n'échangez des données qu'occasionnellement (uniquement après une correspondance de préfixe de hachage local) avec les URL hachées, de sorte que le serveur ne connaisse jamais les URL réelles interrogées par les clients.
Temps de réponse: vous gérez une base de données locale contenant des copies des listes de navigation sécurisée. Elles n'ont pas besoin d'interroger le serveur chaque fois qu'elles souhaitent vérifier une URL.
Inconvénients:

Mise en œuvre: vous devez configurer une base de données locale, puis télécharger et mettre à jour régulièrement les copies locales des listes de navigation sécurisée (stockées sous forme de hachages SHA256 de longueur variable).
Vérifications d'URL complexes: vous devez savoir comment utiliser l'URL canonique, créer des expressions de suffixe/préfixe et calculer des hachages SHA256 (pour comparer les copies locales des listes de navigation sécurisée et de la navigation sécurisée stockées sur le serveur).
Si vous avez des inquiétudes concernant la confidentialité des URL interrogées ou la latence induite par une requête réseau, utilisez l'API Update.
