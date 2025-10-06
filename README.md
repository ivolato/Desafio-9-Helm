# Helm ---> Kubernetes
Este desafío es una continuación del [desafío 5](https://github.com/ivolato/desafio_5_docker) y el [desafío 8](https://github.com/ivolato/desafio-8-k8s), desafíos en los cuales dockerizamos la app NestJs creando el Dockerfile y docker-compose, luego en el 8 con estos archivos y con la ayuda de la herramienta Kompose creamos los templates para crear los recursos para NestJs dentro de Kubernetes.
Ahora en este desafío utilizamos esos manifiestos para crear nuestra aplicación dentro de Helm y podes agregar mayor valor, flexibilidad y simpleza al proceso de instalación de la app. Por ejemplo podríamos usar el mismo repo para levantar un entorno de desarrollo con los parámetros que deseamos, o el de producción con sus parámetros, también podemos modificar fácilmente los puertos o la cantidad de réplicas que se utilizaran desde el values.yaml en vez de modificar en cada manifiesto



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

## Creamos el Namespace dev.
```
kubectl create ns dev
kubectl create ns prod
kubens dev
```
## Creamos un Helm Chart
```
helm create Desafio-9
cd Desafio-9
```

## Limpiamos la carpeta Templates
```
rm -rf templates
mkdir templates
rm values.yaml
mv ../valores/values.yaml .
```
## Movemos los manifiestos del repositorio a templates
```
cd ..
mv *yaml ./Desafio-9/templates
```

## Instalamos el Chart
```
helm upgrade --install nestjs ./Desafio-9 -n dev
```

## Verificamos si se aplicaron correctamente los templates
```
kubectl get all -n dev
```
