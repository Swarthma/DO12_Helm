# ⎈ DO12_Helm – Управление Kubernetes с помощью Helm и Kustomize

**Проект по изучению Helm и Kustomize для управления манифестами Kubernetes, шаблонизации и развёртывания микросервисного приложения**

[![Helm](https://img.shields.io/badge/Helm-0F1689?logo=helm&logoColor=white)](https://helm.sh/)
[![Kustomize](https://img.shields.io/badge/Kustomize-326CE5?logo=kubernetes&logoColor=white)](https://kustomize.io/)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![k3s](https://img.shields.io/badge/k3s-FFC61A?logo=kubernetes&logoColor=black)](https://k3s.io/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![RabbitMQ](https://img.shields.io/badge/RabbitMQ-FF6600?logo=rabbitmq&logoColor=white)](https://www.rabbitmq.com/)
[![Java](https://img.shields.io/badge/Java-ED8B00?logo=java&logoColor=white)](https://www.java.com/)

## 📋 О проекте

Проект посвящён управлению Kubernetes-манифестами с помощью **Kustomize** и **Helm**. На примере микросервисного приложения бронирования отелей показано:

- Использование Kustomize для базовой конфигурации и overlay-патчей (изменение количества реплик).
- Создание Helm-чарта для параметризованного развёртывания приложения.
- Установка, обновление и откат релизов через Helm.
- Упаковка чарта в архив и работа с репозиторием.

Проект базируется на кластере k3s, развёрнутом через Vagrant.

## 📚 Документация

- [**Описание задания**](docs/README_RUS.md)
- [**Отчёт о выполнении**](src/report.md)

## 🏗️ Структура проекта

```
DO12_Helm/
├── README.md
├── docs/
│ └── README_RUS.md
├── src/
│ ├── report.md
│ ├── screen/ # Скриншоты
│ ├── kustomize/ # Kustomize-конфигурации
│ │ ├── base/ # Базовые манифесты
│ │ └── overlays/production/ # Патчи для production
│ ├── myapp-chart/ # Helm-чарт
│ │ ├── Chart.yaml
│ │ ├── values.yaml
│ │ └── templates/ # Шаблоны манифестов
│ ├── Vagrantfile
│ └── application_tests.postman_collection.json
```

## 🛠️ Выполненные задачи

### ✅ **Part 1. Kustomize**
- Установка Kustomize.
- Создание базового `kustomization.yaml` с манифестами всех сервисов.
- Создание overlay `production` с патчем `replicas-patch.yaml` (увеличение количества реплик).
- Применение конфигурации через `kubectl apply -k`.
- Проверка количества реплик и работоспособности приложения через Postman.

### ✅ **Part 2. Helm**
- Установка Helm.
- Создание Helm-чарта `myapp-chart` на основе существующих манифестов.
- Параметризация `values.yaml` (образы, реплики, переменные ConfigMap и Secret).
- Использование шаблонов (`{{ .Values }}`) для генерации манифестов.
- Установка релиза: `helm install myapp ./myapp-chart`.
- Обновление релиза (`helm upgrade`) с изменением количества реплик.
- Откат релиза (`helm rollback`) к предыдущей версии.
- Упаковка чарта в архив (`helm package`).

## 💡 Приобретённые навыки

- **Kustomize**: базовые и overlay-конфигурации, патчи.
- **Helm**: создание чартов, шаблонизация, управление релизами.
- **Управление конфигурацией** Kubernetes.
- **Версионирование** развёртываний и откат изменений.

## 🚀 Как использовать

### Предварительные требования
- Кластер k3s (развёрнут через Vagrant).
- Установленные `kubectl`, `kustomize`, `helm`.

### Запуск
```
bash
# Kustomize
kubectl apply -k src/kustomize/overlays/production

# Helm
helm install myapp ./src/myapp-chart
helm upgrade myapp ./src/myapp-chart --set replicaCount=3
helm rollback myapp 1
```
### 📊 Результаты
Проект успешно завершен.

- Освоены Kustomize и Helm для управления манифестами.

- Создан параметризованный Helm-чарт для всего приложения.

- Проверены обновление и откат релизов.

- Успешное прохождение Postman-тестов.

### 🔗 Связанные проекты
- [**D01 - Основы администрирования Linux**](https://github.com/Swarthma/D01_Linux)
- [**D02 - Сети в Linux**](https://github.com/Swarthma/D02_LinuxNetwork)
- [**D03 - Мониторинг Linux v1.0**](https://github.com/Swarthma/D03_LinuxMonitoring_v1)
- [**D04 - Мониторинг Linux v2.0**](https://github.com/Swarthma/D04_LinuxMonitoring)
- [**D05 - Основы Docker**](https://github.com/Swarthma/D05_SimpleDocker)
- [**D06 - CI/CD с GitLab**](https://github.com/Swarthma/D06_CICD)
- [**D08 - Инструменты автоматизации**](https://github.com/Swarthma/D08_AutomationTools)

## 👨‍💻 Автор

**Галиуллин Линар** - начинающий DevOps инженер

[![Email](https://img.shields.io/badge/Email-linar.9207@gmail.com-D14836?logo=gmail)](mailto:linar.9207@gmail.com)
[![Telegram](https://img.shields.io/badge/Telegram-@Linar9207-2CA5E0?logo=telegram&logoColor=white)](https://t.me/Linar9207)
[![GitHub](https://img.shields.io/badge/GitHub-Swarthma-181717?logo=github)](https://github.com/Swarthma)
