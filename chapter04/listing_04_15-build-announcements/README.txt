初始化构建环境
Gradle的核心插件，build-announcements插件提供了一种将通告发送到本地通知系统如Snarl（Windows）或Growl(Mac OS X)的方式。
你可以把这个插件独立的运用到每个项目上，但是为什么不使用Gradle提供的强大机制呢?
初始化脚本会在任何构建脚本执行之前运行，这样编写一个初始化脚本，把插件应用到项目中，不需要人工干预

gradle会执行在init.d下以.gradle为扩展名的所有初始化脚本。因为想在任何构建脚本执行之前使用插件，所以选择最合适的生命周期回调方法，即Gradle#projectsLoaded(Closure)

当project创建好时，执行闭包

请注意，一些生命周期插件只有在适当的位置声明才会发生。比如，如果将闭包Gradle#projectsLoaded(Closure)声明在build.gradle文件中，那么将不会发生这个事件，因为项目创建发生在初始化阶段。


The file build-announcements.gradle needs to be copied to the directory <USER_HOME>/.gradle/init.d
