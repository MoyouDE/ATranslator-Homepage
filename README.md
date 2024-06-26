# ATranslator
 [点此下载最新版本启动器](https://github.com/MoyouDE/ATranslator-Homepage/releases/download/1.1.0/ATranslator_Launcher.zip)

## 介绍
这是一款专为游戏文本翻译设计的 ``免费Ai辅助CAT工具`` ，你也可以将其用于任意形式的文本翻译  

此工具 ``集成多种翻译api`` 以及 ``直观的编辑界面`` ，即使外语小白也能轻松做到细致的翻译  

同时工具 ``内嵌本地翻译模型`` ，不需要额外配置环境， ``全自动部署``，本地模型轻松使用。  

此外支持 ``一键自动模型训练``，您可以通过将已校对的翻译文本喂给模型来训练自己的 ``个性化翻译器``，实现劳动力的自我解放  

>欢迎各位 游戏开发 / 汉化 团体与个人 使用。  
>本软件目前处于测试阶段，如有任何 __Bug反馈__ 或 __建议__ 请提交于此仓库[Issues](https://github.com/MoyouDE/ATranslator-Homepage/issues)页面 :smile:

## 使用教程

## 1. 如何安装/更新
- 你可以在此页面顶部找到最新版启动器的下载连接，直接点击下载  
> 或者前往本仓库的 [Release](https://github.com/MoyouDE/ATranslator-Homepage/releases) 界面 下载最新版本启动器的压缩包

- 下载完毕后解压即可得到翻译器的启动器 ATranslator_Launcher.exe
> **提示：** 为了避免路径过长导致的意外错误，请不要将启动器 放置在过深目录下

- 双击启动 ATranslator_Launcher.exe ，启动器会自动检查并下载安装最新版本的翻译器至当前目录下  
  
- 安装完毕后启动器将自动开启
> **提示：** 之后使用也请通过  ATranslator_Launcher.exe 打开  
> 后续需要更新时，应用会自动提示，点击确认即可进入自动更新流程  
> 也可在 顶部工具栏 -> `Help` -> `版本检测` 进行版本更新

## 2. 快速上手
- 于顶部菜单栏 `File` -> `打开项目` 选择要作为翻译工程的 __文件夹__, 选择后翻译器将自动在该文件夹下完成工程初始化 并 加载文件列表
> 翻译器会在文件夹下生成 __.AT__ 隐藏文件夹 作为存储目录 ，所有 __工程相关配置__ 以及 __翻译数据__ 都将存储于此  
> 翻译器设计上 __不会__ 改写你的文件 ，不用担心意外造成的原文件损坏

---

###  为了快速上手，接下来的说明将配合例子进行，你可以在这个仓库里下载到示例中所用工程  
> 该示例中所用数据来源于游戏《潜渊症》（仅供学习使用，有问题可联系我进行删除）

- #### 1 双击打开我们想要翻译的文件，文件初始状态如图，假定我们的目标是翻译.txt 文件中的所有输出语句（不包括注释）

![初始状态](https://github.com/MoyouDE/ATranslator-Homepage/assets/44468640/15fa6380-3584-4537-9570-0d95414322f1)


- #### 2 打开顶部工具栏 -> `Settings` -> `项目设置` ，在项目设置界面中设定我们的匹配规则
  + 请依次在`匹配规则设置`中添加如下规则组：
   
       | 文件名规则 | 文本匹配规则      | 常用的正则表达式解释|
       | ---- | --------- |----|
       | txt    | ^Print\\((.*?)\\)$     | `^`匹配行首 ，  `$`匹配行尾 ， `\(`匹配`(` ， 
       | txt    | (?<!;)Log\\((.*?)\\)      | (?<!;) 表示 其后部分的表达式之前不能是`;`
       | txt    | <title>(.*?)<\\title>      |`(.*?)`代表捕获中间所有字符，其中的`?`代表懒惰匹配，即在规则成立的前提下选择尽可能短的文本进行捕获，加上此符号可避免出现跨行匹配的情况

   > 同样的匹配效果可以有多种写法，表达式相关知识可参阅[此处](https://learn.microsoft.com/zh-cn/dotnet/standard/base-types/regular-expressions)，你也可以在[正则模拟网站](https://regex101.com/)来快速验证表达式的效果
  + 如果你不想在文件列表中看到无关文件，可以勾选 `仅显示文件名规则匹配类型文件` 选项
    
    <details>
     <summary><em> 设置界面示例 </em></summary>
  
    ![项目设置](https://github.com/MoyouDE/ATranslator-Homepage/assets/44468640/5b2c5314-09d4-4006-9bf4-bec90ac2c793)
  
    </details>
  
  + 保存后即可看到设置效果
    
     <details>
     <summary><em> 设置成功后的效果图 </em></summary>
  
    ![效果图](https://github.com/MoyouDE/ATranslator-Homepage/assets/44468640/1641a730-70bc-4ba5-b3ad-62a82b289eac)
  
    </details>
    
     \_<strong>下_划_线_加_粗</strong>\_  部分即为规则设定的需要翻译部分，机器翻译可将此部分 单独提取翻译 后 回填，避免破坏其他文本结构
    
     > 由于 匹配规则变动 生成了新的文本解析数据 ，此时该文件处于 `*待保存状态` ，可点击 `保存` 按钮，或使用 `ctrl + s` 进行保存
     
- #### 3 在 右侧输入框 键入对应 完整翻译文本 以 完成翻译
  当确认 匹配规则 效果正确后 ，如果你具有良好的外语知识就可以直接进入正式的翻译流程了 ，只需在右侧输入翻译文本然后保存即可
  
  ##### 你也可以利用翻译器进行 机器翻译，应用目前内置以下几种翻译引擎：
  
     | 引擎类型 |   详情 |
     | --- | --- |
     | 外部引擎 | 目前包括 `有道` 、`百度` 、`彩云小译` 、 `Chatgpt` |
     | 本地引擎 | 通过切换模型得到不同的翻译效果 ，自带一个初始模型 |

  > 你可以在 顶部工具栏 -> `Settings` -> `翻译引擎设置` -> `通用` -> `默认翻译引擎` 处设置使用何种翻译引擎
  > <details>
  >   <summary><em> 关于外部引擎 </em></summary>  
  > 要使用外部引擎需要进行对应的配置，各 外部引擎 所需配置信息 可在对应配置页的 `如何获取？` 处获得
  >
  > 以 `有道翻译` 为例，你需要在 `Settings` -> `翻译引擎设置` -> `外部引擎` -> `有道翻译` 处填入该引擎所需的 `应用ID` 和 `应用密钥`  
  >
  >  ![外部引擎](https://github.com/MoyouDE/ATranslator-Homepage/assets/44468640/d416d778-7390-446a-bb1b-33251cc7d188)
  >
  >  </details>
  > 
  > <details>
  >   <summary><em> 关于本地引擎 </em></summary> 
  > 本地引擎依托于翻译模型来运行，模型将在翻译器启动时自动部署，你可以通过点击主界面右下角 提示灯 来查看模型状态
  >
  >  ![模型就绪](https://github.com/MoyouDE/ATranslator-Homepage/assets/44468640/b3875826-c3cf-48ea-86b6-66401e180207)
  > 
  > 在 `本地引擎` 页可 切换/删除 翻译模型 以及 检测模型状态
  >
  > ![本地引擎](https://github.com/MoyouDE/ATranslator-Homepage/assets/44468640/48750c4d-1d5d-4646-bd65-44688c8eeb57)
  >
  > 初始时只有一个 `原始模型` ，可以在 [模型训练](https://github.com/MoyouDE/ATranslator-Homepage/tree/main?tab=readme-ov-file#4-%E5%85%B3%E4%BA%8E-%E6%A8%A1%E5%9E%8B%E8%AE%AD%E7%BB%83-%E7%9A%84%E8%AF%B4%E6%98%8E) 处 通过训练得到 新的 `微调模型`
  >
  >  </details> 
  
  ##### 完成配置后可回到编辑界面调用机器翻译
  
    ![进行翻译](https://github.com/MoyouDE/ATranslator-Homepage/assets/44468640/a1f6b971-07c2-406a-97a2-5ebd5d7f15cc)
  
    经过机器翻译的文本块 会被标记为`已翻译状态(黄色)`，以提示你需要进行二次确认，你可以通过 手动编辑译文 ，或者点击文本块右侧的 确认按钮 将其标记为 `确认状态(绿色)`
    > 批量翻译按钮只会对 `未修改状态(灰色)` 状态的文本进行翻译，不必担心覆盖已修正的文本内容  
    > 什么是[文本状态](https://github.com/MoyouDE/ATranslator-Homepage/tree/main?tab=readme-ov-file#3-%E5%85%B3%E4%BA%8E-%E6%96%87%E6%9C%AC%E7%8A%B6%E6%80%81-%E7%9A%84%E8%AF%B4%E6%98%8E)
  
- #### 4 完成翻译工作后可通过 导出 功能获得翻译版本的文件
  导出功能位于 顶部工具栏 -> `File` -> `导出` -> `导出功能` -> `导出工程`
  可在此选择需要导出的文件，以及导出路径
  > 导出功能将在你指定路径下创建原工程的翻译副本，如果将原工程上一级目录作为导出路径导出文件将覆盖原工程
  > 因此为了避免破坏原文件，原工程父文件夹，原工程及其子文件夹不可做为导出目录
  >  
  > 上一级文件夹(不可选择)/  
  >      │  
  >      ├── 原工程文件夹(不可选择)/  
  >      │   ├── 原文件.py  
  >      │   ├── 原文件.py  
  >      │   └── config/  
  >      │       └── 原文件.py  
  >      │  
  >      └── 原工程同级的其他文件夹(可选择作为导出路径)/  

## 3 关于 `文本状态` 的说明
可翻译文本文本具有以下四种状态：

   | 状态 | 说明 |
   | ---  | --- |
   | 未编辑状态 | 初始不包含任何翻译信息时的状态，以灰色表示 |  
   | 机翻状态   | 通过机器翻译得到了翻译文本的状态，以黄色表示  |
   | 推测状态 | 由 词典 或是 编辑记录 自动填入了翻译文本的状态，以橙色表示 |
   | 确认状态 | 经过 手动编辑 或是 手动确认 后的文本状态 ，以绿色表示|

  > 提示：直接删除文本并不能将文本转为 未编辑状态 ,需要通过文本块最右侧的 取消按钮 来将文本重置为 未编辑状态  
  > 提示：批量翻译不会将 确认状态 和 推测状态 文本再次翻译

  如果按照译文的可靠性进行排序，由高到低为：确认状态 > 推测状态 > 翻译状态 > 未编辑状态
   
  通常情况下，应以将文本转化为 确认状态 为目标  
  
  处于 确认状态 的文本将自动添加至 词典 以供 [智能更新](https://github.com/MoyouDE/ATranslator-Homepage/blob/main/README.md#5-%E5%85%B3%E4%BA%8E-%E8%AF%8D%E5%85%B8%E7%B3%BB%E7%BB%9F%E4%B8%8E%E6%99%BA%E8%83%BD%E6%9B%B4%E6%96%B0-%E7%9A%84%E8%AF%B4%E6%98%8E) 功能使用  
  
  同时只有 确认状态 文本能够成为模型的训练材料
  
  可在 编辑界面左上角 查看各状态文本的统计情况       
  ![文本状态](https://github.com/MoyouDE/ATranslator-Homepage/assets/44468640/918e2abf-5098-4f78-806f-944e4c7ea11e)

## 4 关于 `模型训练` 的说明

## 5 关于 `词典系统与智能更新` 的说明

待补完

tip： 低于 `1.0.3` 版本的请通过此仓库下载新版启动器重新安装翻译器进行更新

## 未来开发计划（以下排序不代表优先级）  
补完使用说明    
文字大小/界面风格切换  
本地翻译模型  

## 查看历史版本
[点此前往包体仓库](https://github.com/MoyouDE/ATranslator-Release/releases)
此工具会在您想要翻译的工程文件夹下生成一个 .AT 文文件 所有翻译相关数据都存储此文件夹下，不会破坏或修改您的原本文件内容
  



