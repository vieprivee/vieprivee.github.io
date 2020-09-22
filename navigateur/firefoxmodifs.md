# Modifications à apporter à Firefox

# Extensions

## uBlock Origin

uBlock est une extension qui bloque les publicités et les pisteurs, légère en empreinte mémoire et en utilisation du processeur et qui pourtant, est capable d'utiliser et de traiter des milliers de filtres de plus que la plupart des autres bloqueurs.

[uBlock Origin](https://addons.mozilla.org/fr/firefox/addon/ublock-origin/)

---

## HTTPS Everywhere

HTTPS Everywhere est une extension qui chiffre vos communications avec de nombreux sites web, rendant ainsi votre navigation plus sûre. 

[HTTPS Everywhere](https://www.eff.org/https-everywhere)

---

## ClearURLs

Cette extension supprimera automatiquement les éléments de traçage des adresses URL pour vous aider à protéger votre vie privée lorsque vous naviguez sur Internet.

[ClearURLs](https://addons.mozilla.org/fr/firefox/addon/clearurls/)

# "about:config"

*Les trois extensions citées précédemment font un excellent travail. Pour approfondir le sujet, vous pouvez modifier la configuration de Firefox et appliquer les modifications suivantes comme bon vous semble.*

## Préparation

- Cherchez "about:config" dans la barre d'URL Firefox
- Confirmez que vous acceptez le risque
- Suivez les instructions ci-dessous

---

1. privacy.firstparty.isolate = true
    - Résultat de l'effort [Tor Uplift](https://wiki.mozilla.org/Security/Tor_Uplift), cette préférence isole toutes les sources d'identifiants de votre navigateur (ex: les cookies) de domaine principal, avec comme objectif de prévenir le traçage à travers les différents domaines. (N'utilisez pas cette option si vous utilisez l'extension Firefox "Cookie AutoDelete" avec Firefox v58 our inférieur.)
2. privacy.resistFingerprinting = true
    - Résultat de l'effort [Tor Uplift](https://wiki.mozilla.org/Security/Tor_Uplift), cette préférence rend Firefox plus résistant à la génération d'empreinte de navigateur.
3. privacy.trackingprotection.enabled = true
    - C'est la nouvelle protection contre le traçage intégrée par Mozilla. Elle utilise la liste de filtres de Disconnect.me, ce qui est redondant si vous utilisez déjà la liste de filtres tiers de uBlock Origin, en conséquent vous devriez désactiver ce paramètre si vous utilisez la fonctionnalité de l'extension.
4. browser.cache.offline.enable = false
5. browser.safebrowsing.malware.enabled = false
    - Désactive la vérification de programmes malveillants Google Safe Browsing. Un risque potentiel pour la sécurité mais une confidentialité accrue.
6. browser.safebrowsing.phishing.enabled = false
    - Désactive la protection contre le hameçonnage Google Safe Browsing and phishing protection. Un risque potentiel pour la sécurité mais une confidentialité accrue.
7. browser.send_pings = false
    - L'attribut serait utile pour permettre aux sites de tracer les clics de ses visiteurs.
8. browser.sessionstore.max_tabs_undo = 0
    - Même si Firefox est configuré pour oublier l'historique, vos onglets fermés sont conservés temporairement dans le Menu -> Historique -> Onglets Récemment Fermés.
9. browser.urlbar.speculativeConnect.enabled = false
    - Désactiver le préchargement lors de l'autocomplétion des URLs. Firefox précharge les URLs qui s'autocomplètent quand un utilisateur tape dans la barre d'adresse, ce qui est un problème si l'utilisateur ne veut pas visiter les URLs suggérées.
10. dom.battery.enabled = false
    - Désactive le fait que les propriétaires des sites web peuvent tracer l'état de la batterie de votre périphérique.
11. dom.event.clipboardevents.enabled = false
    - Désactive la possibilité pour les sites web d'être notifié lorsque vous copiez, collez ou coupez quelques chose sur la page, leur indiquant quelle partie de la page a été sélectionnée.
12. geo.enabled = false
    - Désactive la géo-localisation.
13. media.eme.enabled = false
    - Désactive la lecture de contenu HTML5 protégé par CDM, qui, si activé, télécharge automatiquement le module Widevine Content Decryption fourni par Google.
    - Le contenu protégé par CDM nécessitant les extensions NPAPI Adobe Flash ou Microsoft Silverlight continueront d'être lisibles, si elles sont installées et activées dans Firefox.
14. media.gmp-widevinecdm.enabled = false
    - Désactive le module Widevine Content Decryption fourni par Google Inc., utilisé pour la lecture de contenu HTML5 protégé par CDM.
15. media.navigator.enabled = false
    - Les sites internet peuvent tracer le status de la caméra et du microphone de votre appareil.
16. network.cookie.cookieBehavior = 1
    - Désactive les cookies
    - 0 = Accepter tous les cookies par défaut
    - 1 = Accepter seulement ceux qui viennent du site d'origine (bloque les cookies tiers)
    - 2 = Bloquer tous les cookies par défaut
17. network.cookie.lifetimePolicy = 2
    - Les cookies sont supprimés à la fin de la session
    - 0 = Accepte les cookies normalement
    - 1 = Demander pour chaque cookie
    - 2 = Accepte pour la session courante seulement
    - 3 = Accepter pour N jours
18. network.http.referer.trimmingPolicy = 2
    - Envoie seulement le schéma, l'hôte, et le port dans l'en-tête `Referer`
    - 0 = Envoie l'URL complète dans l'en-tête `Referer`
    - 1 = Envoie l'URL sans sa chaîne de requête dans l'en-tête `Referer`
    - 2 = Envoie seulement le schéma, l'hôte, et le port dans l'en-tête `Referer`
19. network.http.referer.XOriginPolicy = 2
    - Envoie seulement l'en-tête `Referer` quand le nom d'hôte complet correspond. (Remarque : si vous observez des pannes importantes, vous pouvez essayer `1` associé au réglage `XOriginTrimmingPolicy` ci-dessous.) [Source — Feeding the Clouds](https://feeding.cloud.geek.nz/posts/tweaking-referrer-for-privacy-in-firefox/)
    - 0 = Envoie le `Referer` dans tous les cas
    - 1 = Envoie le `Referer` aux mêmes sites [eTLD](https://en.wikipedia.org/wiki/Public_Suffix_List)
    - 2 = Envoie le `Referer` seulement quand le nom d'hôte complet correspond
20. network.http.referer.XOriginTrimmingPolicy = 2
    - Quand on envoie un `Referer` interorigines, seulement envoyer le schéma, l'hôte, et le port dans l'en-tête `Referer` de la requête interorigines.
    - 0 = Envoie l'URL complète dans le `Referer`
    - 1 = Envoie l'URL sans la chaîne de la requête dans le `Referer`
    - 2 = Envoie seulement le schéma, l'hôte, et le port dans le `Referer`
21. webgl.disabled = true
    - WebGL est un risque potentiel pour la sécurité.
22. browser.sessionstore.privacy_level = 2
    - Cette préférence contrôle quand enregistrer des informations supplémentaires au sujet de la session: le contenu des formulaires, les positions de la barre de défilement, les cookies et les données POST.
    - 0 = Enregistre les données supplémentaires de session pour tous les sites. (Paramètre par défaut depuis Firefox 4.)
    - 1 = Enregistre les données de session supplémentaires pour les sites non-chiffrés (sans HTTPS) seulement. (Paramètre par défaut avant Firefox 4.)
    - 2 = Ne jamais enregistrer des données de session supplémentaires.
23. network.IDN_show_punycode = true
    - Ne pas afficher les [IDNs](https://fr.wikipedia.org/wiki/Nom_de_domaine_internationalis%C3%A9) puisque leur équivalent Punycode vous expose aux attaques par hameçonage pouvant être très difficiles à repérer.
24. extensions.blocklist.url = https://blocklists.settings.services.mozilla.com/v1/blocklist/3/%20/%20/
    - Limite le montant d'informations identifiables envoyées quand on demande à Mozilla la liste des extensions dangereuses.
    - Optionnellement, la liste de blocage peut être désactivée entièrement en paramétrant `extensions.blocklist.enabled` sur `false` afin d'améliorer la confidentialité au détriment de la sécurité.

    ---
