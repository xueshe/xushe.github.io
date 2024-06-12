# [Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh)

## 参考

[mac环境下oh-my-zsh的安装、配置与卸载](https://juejin.cn/post/7089257391740420109)

## 安装

```shell
export REMOTE=https://gitee.com/imirror/ohmyzsh.git
sh -c "$(curl -fsSL https://cdn.jsdelivr.net/gh/ohmyzsh/ohmyzsh/tools/install.sh)"
```

Alternatively, the installer is also mirrored outside GitHub. Using this URL instead may be required if you're in a country like China or India (for certain ISPs), that blocks `raw.githubusercontent.com`:

| Method    | Command                                           |
| --------- | ------------------------------------------------- |
| **curl**  | `sh -c "$(curl -fsSL https://install.ohmyz.sh/)"` |
| **wget**  | `sh -c "$(wget -O- https://install.ohmyz.sh/)"`   |
| **fetch** | `sh -c "$(fetch -o - https://install.ohmyz.sh/)"` |

## 插件

`````
cd ~/.oh-my-zsh/custom/plugins
`````

### 命令自动补全功能：zsh-autosuggestions

```shell
git clone https://github.com/zsh-users/zsh-autosuggestions.git
```



### 语法高亮：zsh-syntax-highlighting

`````
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
`````

### zsh-nvm

```shell
git clone https://github.com/lukechilds/zsh-nvm.git
```

## 卸载

进入到.oh-my-zsh/tools目录

```shell
cd .oh-my-zsh/tools
chmod +x uninstall.sh
./uninstall.sh
```

