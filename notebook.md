## 国内源

阿里云：

http://mirrors.aliyun.com/pypi/simple

豆瓣：

http://pypi.douban.com/simple

清华大学：

https://pypi.tuna.tsinghua.edu.cn/simple

中国科学技术大学：

https://pypi.mirrors.ustc.edu.cn/simple

### 项目配置

打开项目目录中的pipfile，修改source块下url

```Bash
[[source]]
# url = "https://pypi.org/simple"
url = "https://pypi.tuna.tsinghua.edu.cn/simple"
verify_ssl = true
name = "pypi"[packages]
requests = "*"[dev-packages]

[requires]
python_version = "3.10"
```