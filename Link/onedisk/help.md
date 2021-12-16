# 使用帮助

##### 此页面还没写完，有空催一下楊遠徵。😁

---


## NGINX 伪静态配置
```
 if (!-f $request_filename){
set $rule_0 1$rule_0;
}
if (!-d $request_filename){
set $rule_0 2$rule_0;
}
if ($rule_0 = "21"){
rewrite ^/(.*)$ /index.php?/$1 last;
}
```

## 计划任务
[可选]**推荐配置**，非必需。后台定时刷新缓存，可增加前台访问的速度。
### 每小时刷新一次token
```
0 * * * * /具体路径/php /程序具体路径/one.php token:refresh
```

### 每十分钟后台刷新一遍缓存
```
*/10 * * * * /具体路径/php /程序具体路径/one.php cache:refresh
```

## 特殊文件实现功能
` README.md `、`HEAD.md` 、 `.password`、`.tips`、`index.html` 特殊文件使用

**在文件夹底部添加说明:**
> 在 OneDrive 的文件夹中添加` README.md `文件，使用 Markdown 语法。

**在文件夹头部添加说明:**
> 在 OneDrive 的文件夹中添加`HEAD.md` 文件，使用 Markdown 语法。

**加密文件夹:**
> 在 OneDrive 的文件夹中添加`.password`文件，填入密码，密码不能为空。

**加密文件夹提示:**
> 在 OneDrive 的文件夹中添加`.tips`文件，填入文本，会在密码输入界面提示。

**直接输出网页:**
> 在 OneDrive 的文件夹中添加`index.html` 文件，程序会直接输出网页而不列目录。
> 配合 文件展示设置-直接输出 效果更佳。

## 命令行功能
仅能在 PHP CLI 模式下运行

**清除缓存:**
```
php one.php cache:clear
```

**刷新缓存:**
```
php one.php cache:refresh
```

**刷新令牌:**
```
php one.php token:refresh
```

**上传文件:**  
```
php one.php upload:file 本地文件 [OneDrive文件]
```

**上传文件夹:**
```
php one.php upload:folder 本地文件夹 [OneDrive文件夹]
```

例如：
```
//上传demo.zip 到OneDrive 根目录
php one.php upload:file demo.zip

//上传demo.zip 到OneDrive /test/目录
php one.php upload:file demo.zip /test/

//上传demo.zip 到OneDrive /test/目录并将其命名为 d.zip
php one.php upload:file demo.zip /test/d.zip

//上传up/ 到OneDrive /test/ 目录
php one.php upload:file up/ /test/
```

## 图片上传
https://xxx.xxx.xxx/?/images

## 图片上传 API
