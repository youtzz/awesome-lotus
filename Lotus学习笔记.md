## Lotus 源码学习

### 项目结构

- api目录

  定义基本的 api interface，采用了代理模式，每个 interface 都有一个 interfaceStruct 作为代理类，实现由 interfaceStruc t的 Internal 负责。

  type ComonApiStruct

  ```go
  type Common interface {
      ...
      Version(conetext.Context) (APIVersion, error)
  }
  
  type CommonStruct sturct {
      Internal struct {
          ...
          Version func(context.Context) (APIVersion, error)
      }
  }
  
  func (c *CommonStruct) Version(ctx context.Context) (APIVersion, error) {
     ...
      return c.Internal.Version(ctx)
  }
  ```

- build 目录

包含build相关的文件，比如 genesis block 的数据。

- cli 目录

lotus 所有的命令行都在这里定义。

- cmd 目录

main 函数在这里定义。