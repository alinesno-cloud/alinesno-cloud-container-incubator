## 中台容器镜像规划

### 概述

基础容器镜像用于平台快速部署和管理，用于更有优势的部署，同时更统一的环境，
此处容器镜像采用docker，进行统一管理，此处的容器规范的是基础平台业务的

### 研发中台容器架构

#### 容器架构图

- 基础容器(alinesno-container-base) --> CentOS_7.2_x64
- 开发容器(alinesno-container-dev) --> Jenkins/zookeeper/kafka
- 数仓容器(alinesno-container-data) --> Hadoop/Flink
- 物联网容器(alinesno-container-iot) --> 
- 视觉容器(alinesno-container-vision) --> YoloV5/Tensorflow

- 研发中台容器(alinesno-cloud-base) --> YoloV5/Tensorflow
- 业务中台容器(alinesno-cloud-business) --> YoloV5/Tensorflow

- 文档中台容器(alinesno-cloud-document) --> YoloV5/Tensorflow

#### 架构说明

- 基础容器(alinesno-container-base) --> CentOS_7.2_x64
- 开发容器(alinesno-container-dev) --> Jenkins/zookeeper/kafka
- 数仓容器(alinesno-container-data) --> Hadoop/Flink
- 物联网容器(alinesno-container-iot) --> 
- 视觉容器(alinesno-container-vision) --> YoloV5/Tensorflow

- 研发中台容器(alinesno-cloud-base) --> YoloV5/Tensorflow
- 业务中台容器(alinesno-cloud-business) --> YoloV5/Tensorflow
- 文档中台容器(alinesno-cloud-document) --> YoloV5/Tensorflow

### 容器技术版本

| 序号 | 工具         | 技术           | 版本 | 备注 |
|------|--------------|----------------|------|------|
| 5    | 容器         | Docker         |      |      |
| 1    | 容器仓库     | 阿里云/harbor  |      |      |
| 2    | 容器管理     | kubernetes     |      |      |
| 3    | 容器部署     | helm           |      |      |
| 4    | 部署界面管理 | Monocular UI   |      |      |
| 5    | 单机部署     | docker-compose |      |      |
| 6    |              |                |      |      |

### 镜像规划

空间名称为：alinesno-container ，命名规范按 平台+版本，比如:

```
alinesno-vision/x64/Dockerfile
alinesno-vision/arm64/Dockerfile
alinesno-vision/x86/Dockerfile
```

| 序号 | 范围         | 容器名称                           | 最新版本 | 说明            | 之前版本 |
|------|--------------|------------------------------------|----------|-----------------|----------|
| 1    | 基础(base)   | alinesno-container-base-centos     | 1.1.0    | CentOS_7.2 镜像 |          |
| 1    | 基础(base)   | alinesno-container-base-node       | 1.1.0    | nodejs镜像      |          |
| 1    | 基础(base)   | alinesno-container-base-docsify    | 1.1.0    | docsify文件镜像 |          |
|      |              |                                    |          |                 |          |
| 2    | 开发(dev)    | alinesno-container-dev-openjdk     | 11       |                 |          |
| 2    | 开发(dev)    | alinesno-container-dev-ansible     | 11       |                 |          |
| 2    | 开发(dev)    | alinesno-container-dev-jenkins     |          |                 |          |
| 2    | 开发(dev)    | alinesno-container-dev-mysql       |          |                 |          |
| 2    | 开发(dev)    | alinesno-container-dev-redis       |          |                 |          |
| 2    | 开发(dev)    | alinesno-container-dev-mysql       |          |                 |          |
|      |              |                                    |          |                 |          |
| 3    | 数仓(data)   | alinesno-container-data-hadoop     |          |                 |          |
| 3    | 数仓(data)   | alinesno-container-data-flink      |          |                 |          |
| 3    | 数仓(data)   | alinesno-container-data-kafka      |          |                 |          |
| 3    | 数仓(data)   | alinesno-container-data-zookeeper  |          |                 |          |
| 3    | 数仓(data)   | alinesno-container-data-mysql      |          |                 |          |
| 3    | 数仓(data)   | alinesno-container-data-kettle     |          |                 |          |
| 3    | 数仓(data)   | alinesno-container-data-clickhouse |          |                 |          |
|      |              |                                    |          |                 |          |
| 4    | 物联网(iot)  | alinesno-container-iot-centos      |          |                 |          |
|      |              |                                    |          |                 |          |
| 5    | 视觉(vision) | alinesno-container-iot-yolo        | v5       |                 |          |
| 5    | 视觉(vision) |                                    |          |                 |          |

### 部署脚本

> 后期考虑管理工具，比如 helm + Monocular UI 进行k8s-deploy管理

命名规范按 工具_平台 ，如下：

```
deploy/alinesno-container-base-centos_x64/docker-compose-single/
deploy/alinesno-container-base-centos_x64/docker-compose-cluster/
deploy/alinesno-container-base-centos_x64/k8s-single/
deploy/alinesno-container-base-centos_x64/k8s-cluster/

deploy/alinesno-container-base-centos_arm64/docker-compose-single/
deploy/alinesno-container-base-centos_arm64/docker-compose-cluster/
deploy/alinesno-container-base-centos_arm64/k8s-single/
deploy/alinesno-container-base-centos_arm64/k8s-cluster/
```

## 其它

- 无

















