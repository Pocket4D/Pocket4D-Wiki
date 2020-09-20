# 技术层面的设计

该设计只面向Pocket4D本身，并不代表其他的`小程序`方案的实现与设计。

## 客户端

![客户端架构](/assets/p4d_client_structure.001.jpeg)
客户端侧包括`P4D-Core`, 以及 `P4D-Mini-Program`。

### `P4D-Core` 

1. 我们采用Flutter作为我们的主要开发框架，原因如下：
   
   * Flutter的App可以运行在iOS/Android/网页/桌面客户端，它有自己的插件体系，以及与原生C/C++/Rust库及终端设备直接交互的能力。
   * Flutter有自己的渲染引擎Skia。这是一个高性能的引擎，可运行在客户端。
   * Flutter有自己的dartVM虚拟机。dart语言是一门面向对象的开发语言，虚拟机正是基于dart语言来开发。
   * Flutter生态系统拥有大量的开发者。许多科技巨头都在投入大量的人力物力将Flutter应用在新项目里。Flutter的跨平台能力吸引了越来越多的开发者，他们之中大部分是Android/iOS及Web开发者。而他们非常乐于选择Flutter作为跨平台开发的首选语言。
  
2. 我们使用QuickJS和JavaScriptCore作为JS引擎，原因如下:
   * `QuickJS`是一个轻量级高性能的JavaScript引擎，由Fabrice Bellard和Charlie Gordon所研发，引擎使用C语言进行开发，很容易嵌入到设备中，尤其是IoT设备中。
   * `JavaScriptCore`是一个iOS/MacOS提供的嵌入式框架，在苹果开发者群体中大量使用。我们原本打算在iOS上使用`QuickJS`，可是我们并不清楚苹果是否会拒绝非`JavaScriptCore`的框架，因此保险起见，我们将在iOS上使用`JavaScriptCore`嵌入。
   * 我们不会采用Google的v8引擎，因为它的包体积太大，而且维护困难。
  
3. MethodChannel/PlatformChannel用于与现有的Android/iOS系统进行通信
   * 在现有Android/iOS系统中，有很多优秀的工具包，我们并不打算重新造轮子，因此我们使用Flutter插件体系以及MethodChannel/PlatformChannel与之通信，使得核心代码能很好地兼容他们。
   * 同时我们将利用Flutter的plugin体系（如`Crypto`类）对核心代码进行扩展。

4. Dart:FFI用于与C/C++/Rust进行通信
   * 与MethodChannel/PlatformChannel不同的是，我们使用Dart:FFI直接与C/C++/rust进行通信，我们的JS引擎使用的就是Dart:FFI。
   * 如果其他的blockchain相关的SDK或者插件使用的是Rust，那么我们可以直接接入。
  
5. 在Dart/Flutter层做实现
   * 我们使用Flutter组合全部的插件及库。
   * 我们使用Flutter去持有和运行JavaScript Runtime。
   * 对于`小程序`，我们为xml渲染定义P4D组件，以及适用于JavaScript的P4D APIs提供核心代码的交互能力。
   * 对于`小程序`当中可直接引入的功能组件，我们使用P4D插件的方式来提供相关能力。


### `P4D-Mini-Program` 

1. P4D JavaScript：标准的JavaScript虚拟机，但可能不提供node或浏览器API。
2. P4D Html：通过简单而直接的xml/html标准页面来展示组件结构。如果你对vue.js熟悉，你会发现有不少相似之处。
3. P4D Styles：标准的css样式，同时进行了扩展。
4. 所有的这些文件都将通过`P4D-Cli`进行编译，然后可由开发者自行决定上传到服务器或去中心化存储中。
5. `P4D-Mini-Program`的运行方式与其他的`小程序`类似，因此它可以轻易的转化成适配`Vue`或者`React`的系统中，开发者可选择自己熟悉的工具来开发`P4D-Mini-Program`。

## 工具侧
![工具侧](/assets/p4d_tooling.001.jpeg)
工具侧主要包含3个方面：
1. P4D Cli，它以一个编译器和模版提供方的方式进行工作，用以编译小程序的源文件为指定的文件格式。
2. P4D IDE Plugin，就像VSCode一样工作，提供lint和面向开发者的编码支持。
3. P4D Uploader: 如果开发者决定私有化部署，他们可以把编译后的文件上传至自己的服务器；如果选择公开化部署，他们可以上传至去中心化存储系统中。

## 网络侧

### 分布式网络

![分布式网络](/assets/p4d_general_design.001.jpeg)
我们看一下客户端在分布式网络的运行方式：


对于公开部署
* `P4D-Core` 将会通过Flutter的生态系统进行分发，并被众多App所嵌入。
* `P4D-Mini-Program` 将会被上传至去中心化存储中，由社区进行管理。

对于私有化部署或开发阶段
* `P4D-Core` 将会嵌入进私有的APP里。
* `P4D-Mini-Program` 将会被上传至私有的服务器中，并由开发者自行管理。

### Blockchain相关的网络设计和经济模型
TBD

