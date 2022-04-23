# linux配置

```shell
注意使用虚拟机工具设置共享文件夹
sudo  rm /var/lib/dpkg/lock-frontend
sudo rm /var/lib/dpkg/lock
apt-get install vim
sudo vim /etc/profile
sudo dpkg-reconfigure dash
# 然后选择 no 或者 否 ，并确认。
```





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
# 安装前退出conda环境，可以先尝试conda deactivate
sudo apt-get install qt-sdk
sudo apt-get install openssl
sudo apt-get install libssl-dev
每次编译安装都出错，还是下载编译好的吧
wget https://cmake.org/files/v3.11/cmake-3.11.0-rc1-Linux-x86_64.tar.gz
tar -zxv -f cmake-3.11.0-rc1-Linux-x86_64.tar.gz
gedit ~/.bashrc
export PATH=/home/yanyu/cmake-3.11.0-rc1-Linux-x86_64/bin:$PATH
# 然后source ~/.bashrc
cmake --version
```

### 3、安装cuda

下载runfile([cuda-toolkit-archive](https://developer.nvidia.com/cuda-toolkit-archive))

```shell
wget https://developer.download.nvidia.com/compute/cuda/11.3.1/local_installers/cuda_11.3.1_465.19.01_linux.run
sudo sh cuda_11.3.1_465.19.01_linux.run
# 因为是虚拟机，所以注意不要勾选显卡驱动：Driver
gedit  ~/.bashrc

export PATH=/usr/local/cuda/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
source ~/.bashrc
```





## 二、python环境

### 1、 安装miniconda

```shell
source ~/.bashrc
export PATH=/home/yanyu/miniconda3/bin:$PATH
source ~/.bashrc
# 看是否成功
conda info

# 创建虚拟环境
conda create -n exp_yyag_1 python=3.6
# 或者激活虚拟环境
conda activate exp_yyag_1
```


### 2、安装包

````shell
conda install pytorch torchvision torchaudio cudatoolkit=11.3 -c pytorch

````

