## Lotus 需要的依赖

安装 Lotus 时需要的依赖有：

```shell
mesa-opencl-icd ocl-icd-opencl-dev gcc git bzr jq pkg-config curl clang build-essential hwloc libhwloc-dev wget
```

- mesa-opencl-icd、ocl-icd-opencl-dev

  opencl的free实现

- gcc：编译rust

  用于编译rust

- git、bzr

  版本管理

- jq

  用于解析json

- pkg-config

  用于gcc编译时的辅助工具

- curl、wget

  网络请求工具

- clang

  gcc编译前端

- build-essential

  包含一系列用于编译的元包

- hwloc、libhwloc-dev

  提供hierarchical map of key computing elements的工具