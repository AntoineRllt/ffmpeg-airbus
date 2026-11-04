# README ffmpeg-airbus
This repository contains the modified files of the ffmpeg source code by the Airbus team

Trois patchs appliqués à la version ffmpeg-7.1.1 (03/03/2025)
 
 *** ffmpeg-fixdts.patch :
 Quand un paquet de données arrive sans DTS (Decoding Timestamp)/PTS (presentation Timestamp), le patch lui réutilise le DTS du dernier paquet vidéo. 
 Cela évite les erreurs de timestamp et permet au pipeline de traitement de continuer. 
 Si aucun paquet vidéo n'a encore été vu, le paquet data est simplement ignoré.   
 
 ** ffmpeg-fixrtpjitter.patch :
 Le patch améliore la gestion du jitter RTP (variation de latence réseau). 
 Quand des paquets RTP arrivent avec du retard ou dans le désordre, le démultiplexeur RTP peut les perdre  ou produire des artefacts. 
 Ce patch permet au tampon d'attente de s'adapter automatiquement aux variations de latence réseau.
 la file d'attente s'élargit automatiquement pour absorber les retards. 
 L'option jitter_delay permet de contrôler le seuil initial (100ms par défaut).
  
 ** ffmpeg-airbus-version.patch : 
 Ajout de la signature Airbus dans le output de la commande ffmpeg -version :
 =================== Patched by Airbus team ===================
