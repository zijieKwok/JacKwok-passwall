## passwall软件包自动云编译
#### 自动更新依赖：[![Workflow Status](https://github.com/zijieKwok/JacKwok-passwall/actions/workflows/Auto.update.packages.yml/badge.svg)](https://github.com/zijieKwok/JacKwok-passwall/actions)      自动编译插件及依赖：[![Workflow Status](https://github.com/zijieKwok/JacKwok-passwall/actions/workflows/Auto.compile.ipk.yml/badge.svg)](https://github.com/zijieKwok/JacKwok-passwall/actions)
<summary>预览截图</summary>
<p>

![image](https://raw.githubusercontent.com/zijieKwok/JacKwok-passwall/master/img/openwrt.png)
  
![image](https://raw.githubusercontent.com/zijieKwok/JacKwok-passwall/master/img/passwall.png)

#### 插件及依赖下载:
[![GitHub release (latest by date)](https://img.shields.io/github/v/release/zijieKwok/JacKwok-passwall?style=for-the-badge&label=下载跳转)](https://github.com/zijieKwok/JacKwok-passwall/releases/tag/4.72-2-1)

#### 使用说明
```yaml
此passwall版本获取到ip，显示对应地区旗帜

默认passwall与ssr的插件与依赖整合包

使用方法：将整合包上传到openwrt设备的tmp目录，输入命令： opkg install *.ipk

默认压缩包里包含passwall  passwall2  ssr  bypass  vssr插件

```

##### 单独安装passwall与依赖
`````yaml
rm -rf {*passwall2*,*ssr*,*bypass*,*vssr*}
`````

##### 单独安装passwall2与依赖 
`````yaml
rm -rf {*passwall*,*ssr*,*bypass*,*vssr*}
`````
##### 单独安装ssr与依赖，
`````yaml
rm -rf {*passwall*,*passwall2*,*bypass*,*vssr*}
`````
##### 单独安装bypass与依赖
`````yaml
rm -rf {*passwall*,*passwall2*,*ssr*,*vssr*}
`````
##### 单独安装vssr与依赖
`````yaml
rm -rf {*passwall*,*passwall2*,*ssr*,*bypass*}
`````


#### 线下编译使用
一键命令
```yaml
sed -i '$a src-git JacKwok_passwall https://github.com/zijieKwok/JacKwok-passwall' feeds.conf.default
git pull
./scripts/feeds update -a
./scripts/feeds install -a
make menuconfig
```

#### 注意请检查feeds/packages/lang/golang/Makefile是否1.20以上版本
编译新版Sing-box和hysteria，需golang版本1.20或者以上版本 ，可以使用用以下命令更新
```yaml
rm -rf feeds/packages/lang/golang
git clone https://github.com/sbwml/packages_lang_golang -b 21.x feeds/packages/lang/golang
```

第二种
```yaml
pushd feeds/packages/lang
rm -rf golang && svn co https://github.com/openwrt/packages/branches/openwrt-23.05/lang/golang
popd
```

