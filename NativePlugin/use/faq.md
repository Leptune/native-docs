## Q：uni-app原生插件使用的条件是什么？
A：**要求HBuilderX1.4.0及以上版本，并且必须是uni-app项目**
老版本HBuilder不支持（请迁移到最新版本的HBuilderX），5+APP及Wap2App项目都不支持调用uni-app原生插件。

## Q：uni-app原生插件如何支持真机运行？
A：HBuilderX中自带的默认真机运行基座不包含任何uni-app原生插件，所以不支持直接调用uni-app原生插件。
**必须使用[自定义基座](https://ask.dcloud.net.cn/article/35115)才能支持真机运行调用uni-app原生插件**

## Q：uni-app原生插件真机运行提示“using unregistered native plugin 'XXX'”？
A：**默认真机运行的基座中不包含任何原生插件，所以不能调用uni原生插件，必须自定义基座**

- 确定配置了[自定义基座](https://ask.dcloud.net.cn/article/35115)，并且勾选了“使用自定义基座”（HBuilderX的菜单"运行"->"运行到手机或模拟器"->"使用自定义基座"）
- 确定手机上运行的是配置uni-app原生插件后提交生成的自定义基座，可以尝试删除手机上的自定义基座应用，重新真机运行

## Q：已上传插件市场的插件如何下架？
A：插件下架会导致已经使用该插件的app无法再打包，这涉及到插件使用者的利益，所以原则上不允许插件下架。如有特殊原因需要下架请使用注册账号邮箱发邮件到service@dcloud.io进行申请，并详细描述下架原因

## Q：如何更新插件
A：插件作者需注意保持好版本质量和向下兼容。一旦提交市场新版插件，旧版插件就不能再使用。已经使用旧版插件的App，此后再次云打包，会直接集成新版插件。也就是插件的更新不当可能造成已经使用插件的开发者无法及时发布新版应用。

## Q：iOS端插件之间依赖库冲突

同时集成多个原生插件时，如果 A 插件和 B 插件依赖同一个三方库就可能会造成冲突导致打包失败，这种情况可以配置其中一个插件中冲突的库不参与编译打包即可解决冲突，示例：比如冲突的库为 xxx.a，我们配置 A 插件中的 xxx.a 不参与打包

**步骤：**在 Uni 项目的 `nativeplugins/插件A/`目录中创建 `ios-exclude.txt`文件（如果使用的是云端插件请手动创建目录），在 ios-exclude.txt 中填写 xxx.a，（每行填写一个文件名）如下图所示：

![](https://img.cdn.aliyun.dcloud.net.cn/nativedocs/nativeplugin/Iosimgs/ios-exclude.png)