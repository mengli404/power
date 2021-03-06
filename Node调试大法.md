
## Node应用调试大法

#### vscode开发调试大法：
* 打开要调试的文件，按f5,编辑器会生成一个launch.json
* 修改launch.json相关内容，主要是name和program字段，改成和你项目对应的
* 点击编辑器左侧长得像蜘蛛的那个按钮
* 点击左上角DEBUG后面的按钮，启动调试
* 打断点，尽情调试（只要你会chrome调试，一模一样）

```

 "debug:webpack": "node --inspect-brk=9230 node_modules/.bin/scalpel hot” 与下面launch.json中的配置配套使用
{
  // 使用 IntelliSense 了解相关属性。
  // 悬停以查看现有属性的描述。
  // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
  "version": "0.2.0",
  "configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "Launch via NPM",
      "runtimeExecutable": "npm",
      "runtimeArgs": ["run-script", "debug:webpack"],
      "port": 9230,
      "skipFiles": ["<node_internals>/**"]
    }
  ]
}

```

#### 命令行调试大法：

```
在项目根目录下运行 node --inspect-brk packages/create-react-app/index.js
在chrome地址栏输入 chrome://inspect/#devices 然后就可以看到我们要调试的脚本了

```

create-react-app 是一个全局的命令行工具用来创建一个新的项目;
react-scripts 是一个生成的项目所需要的开发依赖;一般我们开始创建react web应用程序的时候,要自己通过 npm 或者 yarn 安装项目的全部依赖，再写webpack.config.js,一系列复杂的配置,搭建好开发环境后写src源代码。现在 如果你正在搭建react运行环境，使用 create-react-app 去自动构建你的app程序。你的项目所在的文件夹下是没有配置文件。react-scripts 是唯一的 额外的 构建依赖在你的package.json中，你的运行环境将有每一个你需要用来构建一个现代React app应用程序。你需要的依赖，和在配置文件中编写的配置代码，react-scripts 都帮你写了，比如：react-scripts帮你自动下载需要的 webpack-dev-server 依赖，然后react-scripts自己写了一个nodejs服务端的脚本代码 start.js来 实例化 WebpackDevServer ，并且运行启动了一个使用 express 的Http服务器，现在你只需要专心写src源代码就可以了。省去了很多精力，最适合快速上手一个demo了。

Reference：
- [Vscode debugger](https://code.visualstudio.com/docs/editor/debugging#_launch-configurations)
- [video](https://www.youtube.com/watch?v=2oFKNL7vYV8)
- [video2](https://code.visualstudio.com/docs/introvideos/debugging)
