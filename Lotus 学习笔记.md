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

lotus 的命令行 main 函数在这里定义。

- chain

  实现与chain的交互功能。主要包含以下子目录：

  - types: 定义Filecoin中的各种数据结构

  - store: 公链存储相关，处理所有的本地链状态，包括链头、消息和状态等

  - state:处理Filecoin的状态树，内部包装了HAMT

  - actors: Filecoin网络内建的各种**actor**定义

  - vm:Filecoin虚拟机，这里实现了调用Filecoin内**actor**的方法的工具

- extern

- miner

  定义产出区块逻辑，与全节点通过api交互

- node

