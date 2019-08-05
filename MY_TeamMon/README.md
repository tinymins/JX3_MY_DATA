# 茗伊插件自定义团队监控数据

> 这是《剑网3》茗伊插件自定义团队监控数据项目，通过该项目可在游戏中快速加载自定义团队监控数据项。

## 文件结构

 * 二级目录对应游戏语言如 `zhcn`、`zhtw`。
 * 三级目录则包含一个 `meta.json` 描述文件存储版本号和信息用于客户端缓存，包含一个数据文件用于实际加载。

## 描述文件

> 描述文件 `meta.json` 要求

 * 编码方式必须为 `UTF-8` 否则会出现乱码问题。

> 描述文件 `meta.json` 包含字段

 * `name`： 数据标题，用于在列表中展示。
 * `author`： 作者名称，用于在列表中展示。
 * `version`： 版本号，用于游戏中下载缓存和更新提示。
 * `data_url`： 数据地址，留空则会自动搜索同目录下 `data.jx3dat` 文件，注意文件必须是导出的加密格式并且后缀名为 `.jx3dat` 。
 * `about`： 详细信息地址，用于在游戏中超链接跳转。

## 数据文件

> 数据文件 `data.jx3dat` 要求

 * 数据必须是导出的加密格式，否则可能出现编码混乱问题。
 * 后缀名必须为 `.jx3dat` ，如使用其他后缀名则无法直接加载。

## 游戏使用

依次点击 `头像菜单` - `茗伊插件` - `团队监控` - `系统菜单` - `导入数据（联网获取文件）` - `添加订阅`，然后在弹出输入框中输入描述文件地址即可。

其中，描述文件地址支持短链接，其格式为：

```
{USERNAME}@{PROVIDER}/{PROJECT}?{BRANCH}:{PATH}
```

> 如果你是普通用户，只需要找数据作者索要短链接地址即可使用，如果你是数据作者，欢迎继续往下阅读各项参数的内容。

 * {USERNAME} 为数据作者仓库账号英文名称
 * {PROVIDER} 为数据仓库所在站点，可选值有 [`github`](https://github.com/tinymins/JX3_MY_DATA)、 [`aliyun`](https://code.aliyun.com/tinymins/JX3_MY_DATA)、 [`gitee`](https://gitee.com/tinymins/JX3_MY_DATA)，默认值为 `github`，各位数据作者可根据自身喜好选择站点。
 * {PROJECT} 为数据仓库项目名称，默认值为 `JX3_MY_DATA`，用于作者有多个数据项目或自定义项目名称时使用。
 * {BRANCH} 为数据仓库分支名称，默认值为 `master`，用于作者数据项目有多个开发进度（如测试服数据）时使用。
 * {PATH} 为数据仓库描述文件地址，默认值为 `MY_TeamMon/{游戏语言}/meta.json`，该字段一般不需做特殊修改。

> 示例

```
tinymins
tinymins?master
tinymins/JX3_MY_DATA
tinymins/JX3_MY_DATA?master
tinymins@github
tinymins@github?master
tinymins@github:/MY_TeamMon/zhcn/meta.json
tinymins@github/JX3_MY_DATA
tinymins@github/JX3_MY_DATA:/MY_TeamMon/zhcn/meta.json
tinymins@github/JX3_MY_DATA?master:/MY_TeamMon/zhcn/meta.json
```

在剑网3简体客户端中，输入上述示例短链接，均等价于直接输入如下描述文件地址

```
https://raw.githubusercontent.com/tinymins/JX3_MY_DATA/master/MY_TeamMon/zhcn/meta.json
```

## 自制云数据

> 开始之前，先根据个人喜好选择一个站点作为数据仓库：

 * [`github`](https://github.com/tinymins/JX3_MY_DATA) 默认站点，限制较少，但在国内连接速度不稳，无中文界面。
 * [`aliyun`](https://code.aliyun.com/tinymins/JX3_MY_DATA) 阿里云仓库，国内速度较快，访问仓库要求用户登录，中文界面。
 * [`gitee`](https://gitee.com/tinymins/JX3_MY_DATA) 码云仓库，国内速度较快，访问仓库不要求登录访问，界面有少许广告。

> 开始创建自己的仓库，这里假设你已制作完成一份数据并从游戏中导出完成。

1. 选择上述任何一个仓库点击进入，注册账号并登录。
2. 点击 `Fork` 按钮（阿里云显示为 `派生项目`），生成一个属于你的派生项目，此时该项目地址为 `https://{站点地址}/{你的用户名}/JX3_MY_DATA`。
3. 进入派生项目，点击进入对应语言文件夹，如简体客户端进入 `JX3_MY_DATA/MY_TeamMon/zhcn/` 目录（注：阿里云需先点击左侧 `文件` 标签页，进入目录浏览模式）。
4. （使用非阿里云）点击 `data.jx3dat` 链接进入数据详情，点击删除按钮点击提交移除旧版数据。
5. （使用非阿里云）重复第3步，回到对应语言文件夹，点击 `Upload files` 按钮数据上传界面。
6. （使用阿里云）点击 `data.jx3dat` 链接进入数据详情，点击替换按钮进入数据替换界面。
7. 将你的数据文件重命名为 `data.jx3dat` 并拖拽到上传框完成上传，输入提交日志并提交改动。
8. 重复第3步，回到对应语言文件夹，点击 `meta.json` 进入描述文件，并点击 `Edit`（阿里云显示为 `编辑`） 按钮开始编辑，修改数据名称、作者、版本号等信息后，点击 `Commit`（阿里云显示为 `提交修改`） 按钮保存改动。

至此，你已完成创建并更新了你的自制云数据，游戏中可添加描述地址，其格式为 `{你的用户名}@{你选择的仓库站点}`，如 ①`tinymins@github`、 ②`tinymins@aliyun`。（注：由于 `github` 是默认站点，所以实际上示例①输入 `tinymins` 即可）

> 更新数据

重复上述 3 - 8 步骤即可，注意 `步骤 8` 不可提前，因为游戏内会根据描述文件 `meta.json` 中的版本号做本地数据缓存，如果提前 `步骤 8` 先更新了描述文件，那么部分用户在你还没来及上传数据时，会下载到错误的数据文件。
