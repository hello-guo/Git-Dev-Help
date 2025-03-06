# 团队项目开发流程（GitHub 托管）

## 介绍
本项目托管在 GitHub 上，团队成员将通过 Git 和 GitHub 协作开发。以下是整个开发流程的概述，确保每个团队成员都能高效地协作，减少冲突，确保代码的质量。

## 1. 初始化项目

1. 创建 GitHub 仓库：由团队负责人或指定成员创建 GitHub 仓库。
2. 克隆仓库：每个团队成员在本地机器上克隆仓库，以便开始开发。

   ```bash
   git clone https://github.com/hello-guo/Git-Dev-Help.git
   ```

3. 创建分支

    **主分支(main)**：这是默认的分支，所有的稳定版本代码都应该推送到主分支。

    **功能分支(feature branches)**：每个成员根据自己的任务创建一个新分支进行开发(或者由管理员统一安排分配)。分支命名应具有描述性，例如 feature/login-page 或 bugfix/fix-header-issue。
    ```bash
    git checkout -b feature/your-feature-name
    ```

4. 开发与提交

    **开发功能**：在自己创建的分支上进行开发。

    **提交更改**：开发完成后，先将本地更改暂存，并写明有意义的提交信息。

    ```bash
    git add .
    git commit -m  #"描述本次提交的功能或修复内容"
    git push origin feature/your-feature-name  #"将本地分支推送到 GitHub 对应分支上"
    ```

5. 拉取请求（Pull Request）

    **创建 Pull Request**：当功能开发完成并推送到 GitHub 后，创建一个 **Pull Request（PR）**将该功能分支合并到主分支。

    **代码审查**：管理员对 **PR** 进行代码审查，确保代码符合项目规范，没有问题。

    **代码测试**：管理员对更新的代码进行测测试，标准算例测试，确保跟新前后算例测试无误。

    **通过审查后合并**：一旦所有审查通过，可以将 **PR** 合并到主分支。

6. 更新与同步

    **保持同步**：在团队开发过程中，主分支会被其他成员更新。因此，在每次开始新的开发前，请确保将主分支的最新更改拉取到本地并合并。

    ```bash
    git checkout main
    git pull origin main
    ```

7. 解决冲突

    如果在合并时出现冲突，团队成员需要手动解决冲突。解决冲突后，再次提交和推送更改。

8. 继续开发

    主分支被其他成员更新后，需要在此时的主分支上继续进行开发，需要把主分支合并到功能分支

    **更新本地主分支**：确保本地的 **main** 分支是最新的。如果本地的 **main** 分支已经落后于远程的 **main** 分支，需要拉取最新的更改。

    ```bash
    git checkout main
    git pull origin main
    ```

    **合并最新的分支**: 将最新的 **main** 分支合并到功能分支，以确保开发是在最新版本的基础上进行。

    ```bash
    git checkout feature/your-feature-name
    git merge main
    ```

    **继续开发并提交更改**：在合并 **main** 分支之后，继续开发工作。完成开发后，提交并推送更改。

    ```bash
    git add .
    git commit -m #"描述更新的功能和更改"
    git push origin feature/your-feature-name

## 2. 发布版本
1. **创建一个 Git 标签**

    在发布版本之前，您需要为该版本创建一个 Git 标签。标签是 Git 中的一个重要概念，通常用于标记特定的提交（例如发布版本）。

    创建标签并推送到 GitHub：切换到 main 分支：确保您当前在最新的 main 分支上。

    ```bash
    git checkout main                       #拉取最新的代码：确保您的 main 分支是最新的
    git pull origin main
    git tag -a v1.0.0 -m "发布版本 v1.0.0"  #其中，v1.0.0 是版本号，-m 后跟的是对版本的描述信息。
    git push origin v1.0.0                 #推送标签到远程 GitHub 仓库

2. **在 GitHub 上创建发布（Release）**

    (1) 点击 "Create a new release" 按钮。
    
    (2) 在页面上选择您要发布的标签（比如 v1.0.0）。

    (3) 填写版本的标题和描述（可以写一些关于本次版本的说明、修复内容等）。

    (4) 点击 "Publish release" 发布版本。

3. **发布成功**

    完成上述步骤后，您就成功地在 GitHub 上创建了一个版本发布（Release）。其他团队成员或者用户可以通过这个版本下载源代码或者查看发布日志。

    发布后的版本会在 GitHub 仓库的 Releases 页面上展示，供大家查看。
