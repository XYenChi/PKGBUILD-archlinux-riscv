### pytorch
ArchLinux 打包[指南](https://github.com/felixonmars/archriscv-packages/wiki/完全新人指南)
其中 asp 已不可用，使用`pkgctl repo clone --protocol=https python-pytorch`获取最新版 ArchLinux 官方 PKGBUILD。根据酸鸽的[riscv64 patch](https://github.com/felixonmars/archriscv-packages/blob/master/python-pytorch/riscv64.patch)进行修改。   
```
export USE_CUDA=0   # 禁用 cuda
export USE_ROCM=0   # 禁用 ROCM
export USE_HIP=0   # 禁用 HIP
export USE_TRITON=0   # 禁用 TRITON
export USE_NCCL=0   # 禁用 NCCL

export USE_DISTRIBUTED=0   # 禁用 DISTRIBUTED
export USE_GLOO=0   # 禁用 GLOO
export USE_TENSORPIPE=0   # 禁用 TENSORPIPE
export USE_MPI=0   # 禁用 MPI

export USE_MKLDNN=0   # 禁用 MKLDNN
export USE_OPENMP=0   # 禁用 OPENMP

export BUILD_CAFFE2=0   # 禁用 CAFFE2
```
### huggingface-hub  
照 PKGBUILD 打包
### regex
照 PKGBUILD 打包
### safetensors

需要使用 `export PYO3_USE_ABI3_FORWARD_COMPATIBILITY=1` 来解决 PYO3 锁 python 3.12 版本问题。   

### tokenizers
需要解决一下 python 3.13 版本和链接问题。   
```
export PYO3_USE_ABI3_FORWARD_COMPATIBILITY=1   # for python 3.13
export RUSTONIG_STATIC_LIBONIG=1   # static link for oniguruma 
export LDFLAGS="${LDFLAGS} -lonig"
```
### tranformers
照 PKGBUILD 打包
