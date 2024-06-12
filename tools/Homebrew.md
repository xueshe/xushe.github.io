# [Homebrew](https://brew.sh/)

## 安装

```
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"
```
## 卸载

```
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/HomebrewUninstall.sh)"
```

## 更换镜像
[清华大学开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/help/homebrew/)

## 更换仓库源

```
## 第一步
cd "$(brew --repo)"
git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git

## 第二步
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git

## 第三步
cd "$(brew --repo)"/Library/Taps/homebrew/homebrew-cask
git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-cask.git

## 第四步
brew update
```
## 更换bottles镜像

```
echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles' >> ~/.bash_profile
source ~/.bash_profile
```
## 复原仓库上游

```
# 第一步：更改brew 程序本身
unset HOMEBREW_BREW_GIT_REMOTE
git -C "$(brew --repo)" remote set-url origin https://github.com/Homebrew/brew

# 第二步：更改系统上的 Homebrew
unset HOMEBREW_CORE_GIT_REMOTE
BREW_TAPS="$(BREW_TAPS="$(brew tap 2>/dev/null)"; echo -n "${BREW_TAPS//$'\n'/:}")"
for tap in core cask{,-fonts,-drivers,-versions} command-not-found; do
    if [[ ":${BREW_TAPS}:" == *":homebrew/${tap}:"* ]]; then  ## 只复原已安装的 Tap
        brew tap --custom-remote "homebrew/${tap}" "https://github.com/Homebrew/homebrew-${tap}"
    fi
done

# 第三步：重新拉取远程
brew update
```
## Homebrew常用的命令

```
1. brew install [package]						# 安装
2. brew uninstall [package]						# 卸载
3. brew update （更新 Homebrew，使之后下载升级有效）	# 更新
4. brew upgrade （升级list中所有）				# 升级
	brew pin [package] 							# 固定软件
	brew unpin [package] 						# 解除固定
	brew upgrade [package] 						# 升级某一软件：
	brew update && brew upgrade && brew cleanup # 更新+升级+清理
5. brew outdated 								# 待升级：列出已安装中待升级
6. brew cleanup 								# 清理：清理不需要的版本极其安装包缓存
7. brew list									# 列出已装软件列表
8. brew search [package]						# 搜索特定软件
9. brew deps [package] 							# 查看依赖包：可以查看该软件的依赖包
10.brew info [package] 							# 查询：主要看具体的信息，比如目前的版本，依赖，安装后注意事项等）
11.brew doctor 									# 检查：

# brew services 管理服务
1. brew services list  							# 查看使用brew安装的服务列表
2. brew services run formula|--all  			# 启动服务（仅启动不注册）
3. brew services start formula|--all  			# 启动服务，并注册
4. brew services stop formula|--all   			# 停止服务，并取消注册
5. brew services restart formula|--all  		# 重启服务，并注册
6. brew services cleanup  						# 清除已卸载应用的无用的配置

# 删除软件及其所有依赖
# 安装rmtree：
brew tap beeftornado/rmtree && brew install brew-rmtree		
brew rmtree <package>							# 删除软件及其所有依赖

# 查看详细命令的操作：
brew commands     								# 查看所有命令 
brew help [COMMAND]								# 查看某一命令详细解释
man brew										# 详细手册
https://docs.brew.sh

# brew commands所有的命令：
-------------------------------------------------------------------------------
Built-in commands
--cache         commands        install         readall         uninstall
--cellar        config          leaves          reinstall       unlink
--env           deps            link            search          unpack
--prefix        desc            list            sh              unpin
--repository    diy             log             shellenv        untap
--version       doctor          migrate         style           update
analytics       fetch           missing         switch          update-report
cask            gist-logs       options         tap             update-reset
cat             help            outdated        tap-info        upgrade
cleanup         home            pin             tap-pin         uses
command         info            postinstall     tap-unpin       vendor-install
Built-in developer commands
audit               extract             prof                tests
bottle              formula             pull                update-test
bump-formula-pr     irb                 release-notes       vendor-gems
bump-revision       linkage             ruby
create              man                 tap-new
edit                mirror              test
External commands
aspell-dictionaries                      services
postgresql-upgrade-database
```
## 可完全卸载

使用以下命令可完全卸载，并且不会影响到其他软件

```
brew rmtree xxx
```

需要安装以下工具

```
brew tap beeftornado/rmtree
brew install brew-rmtree
```

————————————————

                            版权声明：本文为博主原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接和本声明。

原文链接：https://blog.csdn.net/fox372/article/details/129434393