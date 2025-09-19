**Создаем пространство имен для Argo CD**

kubectl create namespace argocd


**Деплоим Argo CD из официального репозитория**

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml


**По умолчанию сервер Argo CD доступен по внутреннему IP. Чтобы получить внешний доступ, меняем тип сервиса на NodePort (для Docker Desktop)** 

kubectl patch svc argocd-server -n argocd -p '{"spec":{"type":"NodePort"}}'


**Получаем начальный пароль от пользователя admin в созданном секрете**

argocd-initial-admin-secret


**Устанавливаем ArgoCD CLI***

brew install argocd


**Узнаем какой порт открыт наружу**

kubectl -n argocd get svc argocd-server 


**Логинимся в ArgoCD  CLI**

argocd login localhost:31046 --username admin --password ****** --insecure
