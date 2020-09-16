# 技术层面的设计
该设计只面向Pocket4D本身，并不代表其他的`小程序`方案的实现与设计

## 客户端

![客户端架构](/assets/P4D_client_structure.001.jpeg)
客户端侧包括`P4D-Core`, 以及 `P4D-Mini-Program`

### `P4D-Core` 

1. 我们采用Flutter作为我们的主要开发框架，原因如下::
   
   * Flutter的App可以运行在iOS/Android/网页/桌面客户端，它有自己的插件体系，以及与原生c/c++/rust和终端设备交互的能力
   * Flutter有自己的渲染引擎Skia，这是一个高性能的引擎，运行在客户端表面
   * Flutter有自己的虚拟机，称为dartVM，同时dart语言也是开发语言，这是一门面向对象的开发语言
   * Flutter的生态系统中，有大量的开发者。许多科技巨头都在投入大量的人力物力和新项目在Flutter上。Flutter的跨平台能力吸引了越来越多的开发者，他们当中大部分来自于Android/iOS和Web，他们乐于选择Flutter作为跨平台开发的首选平台
  
2. 我们使用QuickJS和JavascriptCore作为JS引擎，原因如下:
   * `QuickJS`是一个轻量级高性能的javascript引擎，由Fabrice Bellard和Charlie Gordon所研发，引擎使用C语言进行开发，很容易嵌入到设备中，尤其是iOT设备中。
   * `JavascriptCore`是一个iOS/macOS提供的嵌入式框架，在苹果开发者群体中大量使用。我们原本打算在iOS上使用`QuickJS`，可是我们并不清楚苹果是否会拒绝非`JavascriptCore`的框架，因此保险起见，我们将在iOS上使用`JavascriptCore`嵌入
   * 不采用google的v8引擎，是因为其包大小过大，以及难以维护
  
3. MethodChannel/PlatformChannel用以与现有Android/iOS系统进行通信
   * 在现有Android/iOS系统中，有很多优秀的工具包，我们并不打算重新造轮子，因此我们使用MethodChannel/PlatformChannel与它们通信，而在我们的核心代码中采用这些工具。
   * 同时我们将利用Flutter的plugin体系对核心代码进行扩展，比如`Crypto`类

4. Dart:FFI用于与C/C++/Rust进行通信
   * 与MethodChannel/PlatformChannel不同，我们使用Dart:FFI直接与C/C++/rust进行通信，我们的JS引擎使用的就是Dart:FFI
   * 其他的blockchain相关的SDK或者插件，如果使用rust，我们可以直接接入。
  
5. 在Dart/Flutter层做实现
   * 我们使用Flutter组合全部的插件和库
   * 我们使用Flutter去持有和运行Javascript的运行时
   * 对于`小程序`，我们为xml渲染定义P4D组件，以及P4D Apis向javascript提供核心代码的交互能力。
   * 对于`小程序`当中可直接引入的功能组件，我们使用P4D插件对其提供


### `P4D-Mini-Program` 

1. P4D javascript，标准的javascript虚拟机，不过与node或者浏览器所提供的api不一样
2. P4D html, 简单而直接的xml/html标准页面，展示组件的结构，如果你对vue.js熟悉，你会发现有不少相似之处。
3. P4D styles, 标准的css样式，同时进行了扩展
4. 所有的这些文件都将通过`P4D-Cli`进行编译，随后上传到服务器或者去中心化存储中，这由开发者自行决定。
5. `P4D-Mini-Program` 与其他的`小程序`工作方式类似，因此它可以轻易的转化成适应`Vue`或者`React`的系统中，开发者可选择自己熟悉的工具来开发`P4D-Mini-Program`

## 工具侧
![工具侧](/assets/P4D_tooling.001.jpeg)
工具侧主要包含3个方面：
1. P4D Cli，它以一个编译器和模版提供方的方式进行工作，用以编译小程序的源文件为指定的文件格式
2. P4D IDE Plugin，就像VSCode一样工作，提供lint和面向开发者的编码支持
3. P4D Uploader: 如果开发者决定私有化部署，他们可以把编译后的文件上传至自己的服务器，如果选择公开化部署，他们可以上传至去中心化存储系统中

## 网络侧

### 分布式网络

![分布式网络](/assets/P4D_general_design.001.jpeg)
我们看一下客户端在分布式网络的运行方式


对于公开部署
* `P4D-Core` 将会通过Flutter的生态系统进行分发，并被众多App所嵌入
* `P4D-Mini-Program` 将会被上传至去中心化存储中，由社区进行管理

对于私有化部署或开发阶段
* `P4D-Core` 将会被私有的APP所嵌入
* `P4D-Mini-Program` 将会被上传至私有的服务器中，并由开发者自行管理

### Blockchain相关的网络设计和经济模型
TBD

