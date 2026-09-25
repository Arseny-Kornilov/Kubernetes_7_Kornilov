# Домашнее задание к занятию «Установка Kubernetes»
## Задание 1. Установить кластер Kubernetes с 1 master node
 - подготовить кластер из 5 нод: 1 master/control-plane и 4 worker-ноды;
 - использовать containerd в качестве CRI;
 - запускать etcd на master-ноде;
 - способ установки выбрать самостоятельно.

## Решение
### На control plane (rmq01) запускаются:

kube-apiserver;
kube-controller-manager;
kube-scheduler;
локальный etcd;
kubelet;
containerd.

### На worker-нодах запускаются:

kubelet;
containerd;
kube-proxy;
компоненты Calico;
пользовательские Pod.

### Настройка 
 - prepare.yaml - подготовка Ubuntu, swap, sysctl, containerd, kubelet, kubeadm, kubectl;
 - control-plane.yaml - kubeadm init на rmq01 и создание локального etcd;
 - Calico.yaml - установка Calico;
 - workers.yaml - подключение четырёх worker-нод;
 - test.yaml - проверка готовности кластера
   
### Запуск
#### Работа плейбука
<img width="1143" height="974" alt="image" src="https://github.com/user-attachments/assets/0999da34-ba4f-4b60-b38f-bfa544d9e90d" />

#### Успешное завевршение плейбука
<img width="527" height="409" alt="image" src="https://github.com/user-attachments/assets/fbe765d6-a4bc-49f6-bab9-8c054efa8a86" />

#### Проверка
<img width="566" height="456" alt="image" src="https://github.com/user-attachments/assets/abc26fbf-bfde-41b5-9009-623e0de643de" />

#### Демонстрация системных Pod и Calico:
<img width="719" height="303" alt="image" src="https://github.com/user-attachments/assets/a248a78f-d931-491b-bbb7-b8202e55e5c0" />

#### Запуск тестового приложения
<img width="1169" height="117" alt="image" src="https://github.com/user-attachments/assets/4b1432fa-468c-4b87-bfd9-ce6d4d63a160" />

#### Проверка CRI - containerd
<img width="933" height="151" alt="image" src="https://github.com/user-attachments/assets/6437baf6-d06b-4974-8ac3-7fb2d31f20c5" />

#### Проверка доступности через curl к worker-1 и worker-2
<img width="671" height="442" alt="image" src="https://github.com/user-attachments/assets/64dba48b-a5f4-4efd-b6e8-0c7be3dd5f49" />
