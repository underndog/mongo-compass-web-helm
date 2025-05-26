# mongo-compass-web-helm
Easy MongoDB UI to control your K8s cluster.


helm package ./mongo-compass --destination .
helm repo index ./ --url  https://underndog.github.io/mongo-compass-web-helm