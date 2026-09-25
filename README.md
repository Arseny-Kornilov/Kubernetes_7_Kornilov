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
