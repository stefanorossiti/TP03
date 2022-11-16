# Données et Stockage

Dans ce TP, nous allons créer un service web permettant de stocker et récupérer des images, en utilisant les services d'Azure

Le But de ce TP est d'expérimenter avec le stockage Blob d'Azure, de comprendre ses paramètres et les interactions possibles entre différents services d'un Cloud Provider

## Etude du cas d'utilisation
Imaginons que vous vouliez créer un site web qui, pour une raison ou une autre, doit permettre de stocker, télécharger des images et en dériver des vignettes. 

Vous allez devoir caractériser les données (les images dans ce cas) pour votre service, décider quel est le service de stockage d'Azure correspondant le mieux à votre cas, mais implémenter une solution avec Azure Blob Storage.

Il vous faudra aussi réfléchir à l'évolutivité du stockage pour votre service, et la présenter de façon cohérente. 

## Suivez le tutoriel de Microsoft

Vous êtes libres d'utiliser Powershell ou Azure CLI pour les commandes et .NET ou JS pour l'application.
(Azure CLI est disponible sur le container "dockerbase")

Partie 1:
https://learn.microsoft.com/en-us/azure/event-grid/storage-upload-process-images?tabs=javascript%2Cazure-cli
Partie 2
https://learn.microsoft.com/en-us/azure/event-grid/resize-images-on-storage-blob-upload-event?tabs=nodejsv10%2Cazure-cli
Aucun code n'est demandé pour ce TP, mais des justifications pour les paramètres choisis.

### Exemple: étape de création du "Storage Account":

```
blobStorageAccount="<blob_storage_account>"

az storage account create --name group0 --location switzerlandnorth \
  --resource-group fr-isc-infracloud-tp3-rg --sku Standard_LRS --kind StorageV2 --access-tier hot
```

switzerlandnorth: le service sera principalement utilisé en Suisse, et Switzerland North est plus mature que West. 
SKU Standard_GRS: Les performances ne sont pas de la plus grande importance, mais la durabilité des données étant importante pour notre cas, nous souhaitons une redondance géographique. 

## Questions, critères du tp

1) Un cas d'utilisation ayant besoin de stockage d'image est présenté /1
2) Les données sont caractérisées de façon cohérente pour le cas d'utilisation /3
3) Les paramètres choisis pour le Blob Storage sont justifiés et cohérents avec le cas d'utilisation /3
4) Quel service d'Azure correspond le mieux à votre cas? (pas nécessairement Blob Storage) /1
5) Vous présentez un plan d'évolution de votre service, et le coût en stockage attendu /2
6) Votre service d'image est accessible, avec au moins une image stockée sur Azure Blob Storage /3