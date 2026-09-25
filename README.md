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
prepare.yaml - подготовка Ubuntu, swap, sysctl, containerd, kubelet, kubeadm, kubectl;
control-plane.yaml - kubeadm init на rmq01 и создание локального etcd;
test.yaml - проверка готовности кластера
