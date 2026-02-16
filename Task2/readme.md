**Перечень команд для запуска**

minikube start --addons=metrics-server
minikube image load scaletestapp:1.0 #загрузка образа в миникуб, без этого не может найти образ

kubectl apply -f  deployment.yaml #деплой
kubectl apply -f service.yaml #сервис
kubectl apply -f hpa.yaml #скейлер

minikube tunnel # старт тунеля миникуба для доступа к поду с хоста

minikube dashboard #запуск панели

**Нагрузочное тестирование**

Скейлинг приложения под нагрузкой (745.2 RPS, 73162 общее число запросов) на [скриншоте](Scale.png)

Приложение использует мало памяти, поэтому скейлинг по памяти ограничен. Мне кажется, адекватней было бы масштабировать по метрике числа запросов, при чем снимать эту метрику на уровне LoadBalancer.

