# 获取源代码
## download repo tool
```
mkdir ~/bin
PATH=~/bin:$PATH
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
```
## 使用每月更新的初始化包
> 	由于首次同步需要下载 24GB 数据，过程中任何网络故障都可能造成同步失败，我们强烈建议您使用初始化包进行初始化。
	下载 https://mirrors.tuna.tsinghua.edu.cn/aosp-monthly/aosp-latest.tar，下载完成后记得根据 checksum.txt 的内容校验一下。
	由于所有代码都是从隐藏的 .repo 目录中 checkout 出来的，所以我们只保留了 .repo 目录，下载后解压 再 repo sync 一遍即可得
	到完整的目录。
	使用方法如下:
```
wget https://mirrors.tuna.tsinghua.edu.cn/aosp-monthly/aosp-latest.tar # 下载初始化包
tar xf aosp-latest.tar 
cd AOSP   # 解压得到的 AOSP 工程目录
# 这时 ls 的话什么也看不到，因为只有一个隐藏的 .repo 目录
repo sync # 正常同步一遍即可得到完整目录
# 或 repo sync -l 仅checkout代码
```
> 此后，每次只需运行 repo sync 即可保持同步。 我们强烈建议您保持每天同步，并尽量选择凌晨等低峰时间


## checkout branch 
> repo help init
```
repo init -b xxxversion
repo sync
```
[android版本列表](https://source.android.com/source/build-numbers.html#source-code-tags-and-builds) 
