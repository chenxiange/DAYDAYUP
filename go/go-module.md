一. 配置代理
    方法1: https://goproxy.io/zh/docs/getting-started.html 只在终端生效。
    方法2: 长久生效
  **mac/linux**
  
    ```
    # 如果终端是bash
    echo "export GOPROXY=https://goproxy.io,direct" >> ~/.profile && source ~/.profile
    
    # 如果终端是zsh
    echo "export GOPROXY=https://goproxy.io,direct" >> ~/.zshrc && source ~/.zshrc
    ```
    
  **Windows**
  
   我的电脑 -> 属性 -> 高级系统设置 -> 环境变量 -> 新增：变量名: GOPROXY , 变量值：https://goproxy.io,direct
   
二. goland配置代理
    `settings -> Go modules(vgo) -> Proxy: https://goproxy.io,direct`
    
三. mod基本概念
   1. go.mod 文件：项目启动的核心文件，描述了当前项目的依赖包信息。
     - module：用于定义当前项目的模块路径
     - go：用于设置预期的Go版本
     - require：用于需求一个特定的模块版本
     - exclude：用于从使用中排除一个特定的模块版本
     - replace：用于将一个模块版本替换为另一个模块版本
   2. go.sum 文件：类似于Gopkg.lock的一类文件，罗列了当前项目直接或间接依赖的所有模块版本。
   
四. go mod 常用命令
    ```
    用 go help module-get 和 go help gopath-get 分别去了解 Go modules 启用和未启用两种状态下的 go get 的行为
    用 go get 拉取新的依赖
      go get golang.org/x/text@latest # 拉取最新的版本（优先择取 tag）
      go get golang.org/x/text@master # 拉取 master 分支的最新 commit
      go get golang.org/x/text@v0.3.2 # 拉取 tag 为 v0.3.2 的 commit
      go get golang.org/x/text@342b2e1 # 拉取 hash 为 342b231 的 commit，最终会被转换为 v0.3.2
    用 go get -u   # 更新现有的依赖
    用 go mod download 下载 go.mod 文件中指明的所有依赖
    用 go mod tidy 整理现有的依赖
    用 go mod graph 查看现有的依赖 结构
    用 go mod init 生成 go.mod 文件（Go 1.13 中唯一一个可以生成 go.mod 文件的子命令）
    用 go mod edit 编辑 go.mod 文件
    用 go mod vendor 导出现有的所有依赖（事实上 Go modules 正在淡化 Vendor 的概念）
    用 go mod verify 校验一个模块是否被篡改过
    ```
五. 新建项目
    1. 设置代理
    windows
    ```
    go env -w GO111MODULE=on
    go env -w GOPROXY=https://goproxy.cn,direct
    ```
    mac/linux
    ```
    export GO111MODULE=on
    export GOPROXY=https://goproxy.cn
    ```
    2. 创建hello目录
    3. 初始化项目
    ```
    go mod init hello
    ```
    go.mod 提供了go、module, require、replace和exclude 五个命令
    - module：用于定义当前项目的模块路径
    - go：用于设置预期的Go版本
    - require：用于需求一个特定的模块版本
    - exclude：用于从使用中排除一个特定的模块版本
    - replace：用于将一个模块版本替换为另一个模块版本
    
    > 配置git ssl：git config --global http.sslVerify "false"
    
    
    
