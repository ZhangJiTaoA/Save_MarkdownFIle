#### centOS 7中配置c++开发环境

1. ```shell
   yum group list   // 查看yum group，也不是很懂，会看到"Development Tools"
   yum group list ids  
   ```

2. ```shell
   yum group install "Development Tools"
   yum groupinstall "Development Tools"  // 如果上面的失效使用该指令
   whereis gcc  // 查看是否成功
   gcc --version
   ```

3. ```shell
   yum install man-pages man-db man  // 在man可以找到c++提供的函数库
   ```