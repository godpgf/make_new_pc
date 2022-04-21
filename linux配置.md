# linux配置

## 一、C++环境

### 1、更新gcc

```shell
sudo apt-get purge libappstream3
sudo apt-get update
sudo apt-get install build-essential software-properties-common -y
sudo apt-get install --reinstall ca-certificates
sudo -E add-apt-repository --update ppa:ubuntu-toolchain-r/test
sudo apt-get update
sudo apt-get install gcc-snapshot -y
sudo apt-get update
sudo apt-get install gcc-9 g++-9 -y
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 60 --slave /usr/bin/g++ g++ /usr/bin/g++-9
```

### 2、安装cmake

```shell
wget https://cmake.org/files/v3.9/cmake-3.9.2.tar.gz
tar -zxv -f cmake-3.9.2.tar.gz
cd cmake-3.9.2
./bootstrap
sudo make && make install
https://blog.csdn.net/yuanzhoulvpi/article/details/122938078
```

### 3、安装cuda

下载runfile([cuda-toolkit-archive](https://developer.nvidia.com/cuda-toolkit-archive))

```shell
wget https://developer.download.nvidia.com/compute/cuda/11.6.2/local_installers/cuda_11.6.2_510.47.03_linux.run
sudo sh cuda_11.6.2_510.47.03_linux.run
https://blog.csdn.net/CC977/article/details/122789394
```





## 二、python环境

安装miniconda

```text
export PATH=/home/liu/miniconda3/bin:$PATH
source ~/.bashrc
# 看是否成功
conda info

# 创建虚拟环境
conda create -n exp_yyag_1 python=3.6
# 或者激活虚拟环境
conda activate exp_yyag_1
```

