# Technical Design

This design is for Pocket4D only, not representing other implementations or designs of so-called `Mini-Program`.


## Client Side

![Client Structure](/assets/p4d_client_structure.001.jpeg)

The client side includes `p4d-core`, and `p4d-mini-program`.

### `P4D-Core` 

1. We uses Flutter as our main framework, because:
   * Flutter app can run on iOS/Android/Web/Desktop, it has its own plugins system and can interop with native lib like c/c++/rust and communicate with native devices.
   * Flutter has its own rendering engine called Skia, which is a high performance engine, runs on the client side surface.
   * Flutter has its own vm called dartVM, also uses dart as its programming language, which is an OOP language.
   * Flutter has a great number of developers inside its eco-systems. Many tech-giants are investing a lot effort to use flutter as their fresh project. Flutter's cross-platform abilities attract more and more developers, who are coming from Android/iOS/Web to use Flutter as their first-choice app developing platform.
  
2. We use QuickJS and JavascriptCore as our JSEngine, because:
   * `QuickJS` is a lightweight and high-performance javascript engine developed by Fabrice Bellard and Charlie Gordon, it is written in C, can be easily embedded to most devices, iOT devices included.
   * `JavascriptCore` is an embedded framework by iOS/macOS, which is used widely by majority of Apple's developers. We planned to make `QuickJS` as JSEngine of iOS package, however, we don't know whether if Apple rejects js framework other than `JavascriptCore`, so to be safe, we just make `JavascriptCore` embedded.
   * Not using google's v8 engine, because it's bundle size is too big and hard to maintain.
  
3. MethodChannel/PlatformChannel is used to communicate with existing Android/iOS system. 
   * There are a lot of excellent packages developed by Android/iOS system, and we don't need to remake them. By using Flutter's plugin system and MethodChannel/PlatformChannel, we can adopt those good ones to our core.
   * Also we can extend the core by integrating more plugins such as `Crypto` plugin.

4. Dart:FFI is used to interop with C/C++/Rust.
   * Unlike MethodChannel/PlatformChannel, Dart:FFI can interop with C/C++/rust directly, our JSEngine use Dart:FFI.
   * Other blockchain specific client SDK or some plugin is developed by rust, we can use rust to interact with them.
  
5. Implementation happens in Dart/Flutter
   * We use Flutter to combine all the plugin/libs.
   * We use Flutter to hold and run the Javascript Runtime
   * For the `Mini-Program`, we define the P4D Components for xml rendering, and use P4D Apis for javascript to interact with the core.
   * Other features that can be imported by `Mini-Program` , we use p4d plugin to provide those abilities.


### `P4D-Mini-Program` 

1. p4d javascript, standard javascript vm however node and browser apis may not be provided.
2. p4d html, simple xml/html page that present the component structures, if you know vue.js well, you may find them similar.
3. p4d styles, standard css file but have extended style-sheets
4. All these files will be compiled through our `P4d-Cli`, and then upload to server or decentralized storage, which is decided by developers.
5. The `p4d-mini-program` works like other `Mini-Program`, they can be converted to Vue-Like or React-Like systems, so developers who are familiar with those systems can use familiar tools to develop `p4d-mini-program`.

## Tooling Side
![Tooling](/assets/p4d_tooling.001.jpeg)

Tooling has 3 major parts:
1. P4D Cli: which works like a compiler and template provider to compile the `mini-program` source file to specific format.
2. P4D IDE Plugin: which works like VSCode extension that provide the lint and other programming service for developers.
3. P4D Uploader: If developer choose to deploy the `mini-program` and run its own service, they can upload to their server. Otherwise, they can upload to our public decentralized storage.

## Network Side

### Distributed Network

![Client Structure](/assets/p4d_general_design.001.jpeg)

Here we come to the general design of the client loop, 

for public deployment.
* The `P4D-Core` will be distributed through flutter's ecosystem and embedded by many apps.
* The `P4D-Mini-Program` will be uploaded to decentralized storage, and manage by community

For private deployment or develop stage
* The `P4D-Core` will be embedded by private app
* The `P4D-Mini-Program` will be uploaded to private server and manage by developer him/herself.

### Blockchain specific network and economic model
TBD

