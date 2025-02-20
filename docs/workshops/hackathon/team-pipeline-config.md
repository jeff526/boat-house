### Gitee集成Jenkins搭建流水线

#### 前置说明：

**配置Gitee之前，团队需要选定一个Gitee账号跟Jenkins环境集成

##### 添加全局变量

1. 进入Jenkins | 点击 Manage Jenkins | 点击Config System | 找到 Global properties | 选中 Environment variables | 点击 ADD

添加如下环境变量（注意复制环境变量以及值的时候避免多复制了空格）：

| 变量名称 | 值 | 说明  |
| ------------ | --------- | --------- |
| BOATHOUSE_CONTAINER_REGISTRY  | 容器镜像仓库地址 | 支持团队提供的容器镜像仓库地址 |
| CREDS_GITHUB_REGISTRY_USR  | 容器镜像仓库用户名|支持团队提供的容器镜像仓库用户名|
| CREDS_GITHUB_REGISTRY_PSW  | 容器镜像仓库密码| 支持团队提供的容器镜像仓库密码|
| BOATHOUSE_DEV_HOST  | 请使用实际 | Dev环境IP地址  |
| BOATHOUSE_ORG_NAME | idcf-boat-house  | 团队镜像仓库组织名称 |
| DEPLOY_K8S_NAMESPACE_TEST | boathouse-test | k8s命名空间，即boathouse测试环境部署的命名空间 |
| DEPLOY_K8S_NAMESPACE_PROD | boathouse-prod | k8s命名空间，即boathouse生产环境部署的命名空间 |

添加完成后如下图所示：
![image.png](images/jenkins-add-envs.png)

##### Jenkins配置

1. 进入jenkins首页，点击进入左侧菜单栏中 **open blue ocean** 的菜单

![image.png](.attachments/image-36a3e741-2840-4470-a045-2a00503ad262.png)

1. 进入后，根据提示，点击下方的按钮，创建流水线
![image.png](.attachments/image-b33842d4-c08a-49c5-8621-c1560d31492a.png)

1. 仓库类型选择 git,如下图所示：

![image.png](.attachments/jenkins01.png)

2. 获取仓库地址，如下图所示：

![image.png](images/gitee-url.png)

3. 输入boat-house-frontend仓库地址，并点击创建流水线，如下图所示：


![image.png](.attachments/jenkins02.png)

4. 流水线创建中

![image.png](.attachments/jenkins03.png)

5. 进入流水线主页，可以看到基于Repo中Jenkins File成功创建出流水线。

![image.png](.attachments/image-3c7d5ea4-52bf-4c49-9e0c-8375d8c027cc.png)

6. 点击当前流水线进入流水线活动页面
![image.png](images/teamguide-ci-00.png)

7. 点击分支 Tab，点击某个分支后的修改button可以查看流水线的具体设置及任务
![image.png](images/teamguide-ci-01.png)
![image.png](images/teamguide-ci-02.png)

8. 修改jenkinsfile默认地址：

![image.png](.attachments/jenkins04.png)

9. 脚本路径改为：devops/jenkins/jenkinsfile

![image.png](.attachments/jenkins05.png)

10. 按照同样的方式完成boat-house-backend仓库的导入以及配置。
