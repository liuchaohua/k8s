APISERVER:所有服务访问统一入口

ControllerManager：维持副本期望数目

Sheduler:负责介绍人物，选择合适的节点进行分配任务

ETCD:键值对数据库，存储K8S集群所有重要信息（持久化）【数据存储】

Kubelet：直接跟容器引擎交互，实现容器的生命周期管理

Kube-Proxy：负责写入规则至IPTABLES、IPVS实现服务映射访问的



高可用集群副本数目最好是 >=3



其他插件：

CoreDNS:可以为集群中的SVC创建一个域名IP的对应关系解析。

DashBoard： 给K8S集群提供一个B/S的结构访问体系。

Ingress Controller：官方只能实现四层代理，Ingress可以实现七层代理。

Fedration:可以提供一个可以跨级群中心多K8S统一管理功能。

Prometheus：提供一个k8s集群的监控能力。

ELK：提供K8S集群日志统一分析接入平台。

OCI
Open Container Initiative，也就是常说的OCI，是由多家公司共同成立的项目，并由linux基金会进行管理，致力于container runtime的标准的制定和runc的开发等工作。

CNI（Container Networking Interface）
CSI（Container Storage Interface）

像这样使用一种 API 对象（Deployment）管理另一种 API 对象（Pod）的方法，在 Kubernetes 中，叫作“控制器”模式（controller pattern）

“Namespace 做隔离，Cgroups 做限制，rootfs 做文件系统”


apiVersion: batch/v2alpha1
kind: CronJob
...
CronJob就是API对象的资源类型（Resource）
batch就是它的组（Group）
v2alpha1就是它的版本（Version）

CRD 的全称是 Custom Resource Definition。
顾名思义，它指的就是，允许用户在 Kubernetes 中添加一个跟 Pod、Node 
类似的、新的 API 资源类型，即：自定义 API 资源。

Kubernetes 里所有的 Pod 都会以 Volume 的方式自动挂载 Kubernetes 的默认 ServiceAccount。
所以，这个控制器就会直接使用默认 ServiceAccount 数据卷里的授权信息，来访问 APIServer。



HPA  
    Horizontal Pod Autoscaling仅仅适用于Deploment和ReplicaSet，在V1版本在红仅支持根据Pod的CPU利用率扩缩容，在vlalpha版本汇总，支持根据内存和用户自定义的metric扩缩容。

StatefulSet 是为了解决有装填服务的问题。（Deployment和ReplicaSet是为无状态服务而设计。）	场景包括：
