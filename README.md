# IDCF 社区开源共创项目 boat-house

项目介绍请参考： https://github.com/idcf-boat-house/boat-house

## boat-house 共创项目基础设施(本库)

boathouse 基础设施库，包括vm环境创建脚本，devops相关工具部署脚本

## 端到端配置文档

请参考主文档库： https://github.com/idcf-boat-house/boat-house

## boathouse 现有的环境

### 环境

| 环境  |  说明  | 访问地址 | 登陆方式    | 密码    |
| ------------ | ------------ |  ------------ | ------------ | ------------ |
| azure linux 虚拟机  | Jenkins 服务器  | jenkins.devopshub.cn  | ssh localadmin@jenkins.devopshub.cn | 标准复杂  |
| azure linux 虚拟机  | Jenkins slave   | 13.76.40.69  | ssh localadmin@13.76.40.69 | 标准复杂  |
| azure linux 虚拟机 | 工具服务器，包括：jira、SonarQube、Nexus。流水线开发测试服务器  | tools.devopshub.cn | ssh localadmin@tools.devopshub.cn | 标准复杂 |
| azure linux 虚拟机  | 用于部署 boathouse dev环境   | 138.91.37.88  | ssh localadmin@138.91.37.88 | 标准复杂  |
| k8s集群  | k8s集群，用于部署boathouse生产环境 | k8s.devopshub.cn | ssh -i <ssh_key_file_path> localadmin@k8s.devopshub.cn | SSH key, 位置 \env\k8s\ssh_key\id_rsa |



### 已经部署工具

| 地址  | 说明  | 用户名密码 |
| ------------ | ------------ | ------------ | 
| http://jenkins.devopshub.cn  | Jenkins管理端  |  admin/标准复杂 | 
| http://tools.devopshub.cn:8081 | Nexus  |  admin/标准复杂 |   
| http://tools.devopshub.cn:9000| Sonarqube  |  admin/标准复杂 |   
| http://tools.devopshub.cn  | Jira  |  admin/标准复杂 | 

## 目录结构


 - devops-tools：存放 devops领域相关工具的部署脚本
    - jenkins-server
    暂无脚本，配置请参考[文档](https://github.com/idcf-boat-house/boat-house/blob/master/docs/quick-start/operation/team-env-config.md)
    - sonaqube-server 
    脚本已迁移，参考[文档](https://github.com/idcf-boat-house/boat-house/blob/master/docs/quick-start/guide/sonarqube/Readme.md)
    - nexus-server
    暂无脚本，配置请参考[文档](https://github.com/idcf-boat-house/boat-house/blob/master/docs/quick-start/guide/nexus-deploy/Readme.md)
    - jira-server,待补充
    - azure-devops-server,待补充
    - gitlab-server,待补充
    - github-enterprise-server,待补充
  - environments： 存放程序运行所需的基础环境创建脚本，如虚拟机创建脚本、集群创建脚本等
	- base-vm ：标准虚拟机创建脚本
		- azure-arm-linux
	- boat-house： boat-house 运行所需的环境
		- dev(vm): 		
		- test(k8): boat-house 运行所需的测试环境,部署至K8s，namespace: boathouse-test        
		boathouse 部署至k8s 参考[这个文档](https://github.com/idcf-boat-house/boat-house/blob/master/docs/quick-start/operation/team-k8s-env-config.md)
		- production (k8s)：boat-house 运行所需的k8s环境，部署至K8s，namespace: boathouse-prod     
		boathouse 部署至k8s 参考[这个文档](https://github.com/idcf-boat-house/boat-house/blob/master/docs/quick-start/operation/team-k8s-env-config.md)





