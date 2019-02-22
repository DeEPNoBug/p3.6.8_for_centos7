# Centos7 下安装Pyhton3.6.8

## 1. 查看系统现在的Python所在地址

```shell
which python  # 通常在 /usr/bin 下
cd /usr/bin
ll python*
```

## 2. 安装相关依赖

```shell
sudo yum upgrade
yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gcc make 
```

## 3. 如果当前系统没有安装pip

```shell
# 运行这个命令添加epel扩展源
yum -y install epel-release

# 安装pip
yum install python-pip
```

## 4. 使用 pip 安装 wget

```shell
pip install wget
```

## 5. 使用wget下载Python3源码包

```shell
wget https://www.python.org/ftp/python/3.6.8/Python-3.6.8.tar.xz
```

## 6. 解压编译python3源码包

```shell
# 解压
xz -d Python-3.6.8.tar.xz
tar -xf Python-3.6.8.tar

# 通常新系统并未安装gcc
sudo yum install gcc

# 进入解压后的目录，依次执行下面命令进行手动编译
./configure prefix=/usr/local/python3
make && make install
```

## 7. 添加软连接

```shell
# 添加Python3的软连接
ln -s /usr/local/python3/bin/python3.6 /usr/bin/python3
ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3
# 测试是否成功
python3 --version
```

