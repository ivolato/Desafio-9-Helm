# Helm ---> kubernetes
En este trabajo pasamos el desafío 5 a kubernetes con la aplicación Kompose.
Recordemos que en el desafío 5 a partir de una aplicación (Nestjs) se construye la imagen con Docker y el manifiesto docker-compose.yaml que despliega los contenedores NestJS y la base MongoDB para poder desplegarla con contenedores.
Kompose traduce el manifiesto docker-compose.yaml a varios manifiestos de Kubernetes, deployment, replicaset, pvc y servicios para poder desplegar todo el entorno.

## Clonar el repositorio.
```
git clone https://github.com/ivolato/Desafio-9-Helm.git
cd Desafio-9-Helm
```

## Instalar Helm
```
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
helm version --short
```

## Creamos un Helm Chart
```
helm create mychart
```

## Instalamos el Chart
```
helm upgrade --install Desafio-9 ./mychart
```
