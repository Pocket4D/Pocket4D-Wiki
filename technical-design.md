# Technical Design

This document describes the architecture of the Pocket4D mini application platform **only**. It does not describe the implementation or design of other similar projects.


## Client Side

![Client Structure](/assets/p4d_client_structure.001.jpeg)

The client side includes `P4D-Core`, and `P4D-Mini-Program`.

### `P4D-Core` 

1. P4D is based on the Flutter application framework, because:
   * Flutter apps can, in principle, run on iOS/Android/Web/Desktop, and has a rich plugin system with the ability to interop with native libs written in C/C++/Rust and low-level OS APIs.
   * Flutter has its own high performance rendering engine called Skia which provides an abstraction over various client-side interfaces.
   * Flutter, via the Dart VM and programming language, has high performance characteristics.
   * The Flutter ecosystem has a large community number of developers. Many large tech companies are deeply invested in Flutter. Its cross-platform features continue to attract more and more developers from the Android/iOS/Web ecosystems to use it as their go-to app development platform.
  
2. We use QuickJS and JavaScriptCore as our JavaScript engine, because:
   * `QuickJS` is a lightweight and high-performance JavaScript engine developed by Fabrice Bellard and Charlie Gordon. Written purely in C, it is easily embedded on most devices, including low-powered `IoT` devices.
   * We use `JavaScriptCore` as it is officially supported on iOS/macOS devices, and is currently most widely used within the Apple ecosystem. While we plan to use `QuickJS` on iOS, at this time, we don't know whether Apple will permit apps running JS engines other than `JavaScriptCore` to be listed on the App Store. This makes QuickJS a risky proposition for the time being.
   * We have made a conscious decision to opt out of Google's famous `V8` engine due to size concerns and the difficulty of maintaing a Dart interface to its extremely large API surface area.
  
3. MethodChannel/PlatformChannel is the primary method used for interop with OS-level Android/iOS APIs. 
   * There are a lot of excellent packages developed by Android/iOS system. We don't intend to reinvent any wheels. By using Flutter's plugin system and MethodChannel/PlatformChannel, can avoid doing so.
   * We can easily augment native APIs, e.g., by providing plugins and libraries for cryptography and other non-standard APIs.

4. Dart:FFI is used for interop with native code written in C/C++/Rust.
   * Unlike MethodChannel/PlatformChannel, Dart:FFI can interop with C/C++/Rust directly. The JSEngine uses Dart:FFI to do so for maximum performance.
   * Many blockchain-specific client SDKs and libraries are written in Rust. We intend to provide Rust-based APIs to these via Dart:FFI.
  
5. Implementation happens in Dart/Flutter
   * We use the Flutter runtime as the core and hub for various plugins/libs, whether written in Dart, JS or native code.
   * Flutter via the Dart:FFI is also responsible for managing the QuickJS JavaScript runtime.
   * To implement a mini program platform, we define components in Flutter that can be described and dynamically rendered via a HTML-like DSL, and expose APIs for JavaScript code to interact with the Flutter core.
   * Other custom APIs can be made available to mini programs via the (WIP) P4D plugin API.


### `P4D-Mini-Program` 

1. Business logic in P4D mini apps are written in standard JavaScript. However, as P4D is new and implements a custom runtime from scratch, many Node and browser APIs may not be provided.
2. P4D provides a simple HTML-like DSL that is used to describe views. It provides directive-based APIs similar to frameworks like Vue.js.
3. P4D mini apps are styled via standard css files, but have some limitations and differences due to being based on Flutter.
4. All these files will be compiled through our `P4D-Cli`, and then uploaded to server or decentralized storage depending on developer needs.
5. The `P4D-Mini-Program` works like other `Mini-Program`, they can be converted to Vue-Like or React-Like systems, so developers who are familiar with those systems can use familiar tools to develop `P4D-Mini-Program`.

## Tooling Side
![Tooling](/assets/p4d_tooling.001.jpeg)

Currently, P4D provides three main tools:
1. `p4d-cli`: which works like a compiler and bundler for mini programs that can be executed by the P4D Flutter core.
2. P4D IDE Plugin: which works like VSCode extension that provides the lint and other programming service for developers.
3. P4D Uploader: developers are free to deploy the `Mini-Program` and host it themselves. Otherwise, they can upload their apps to P4D-provided public decentralized storage.

## Network Side

### Distributed Network

![Client Structure](/assets/p4d_general_design.001.jpeg)

Here we come to the general design of the client loop, 

For public deployment.
* The `P4D-Core` will be distributed through Flutter's ecosystem and embedded by host applications.
* The `P4D-Mini-Program` will be uploaded to decentralized storage, and managed by the community.

For private deployment or develop stage
* The `P4D-Core` will be embedded as usual.
* The `P4D-Mini-Program` will be uploaded to private server and manage by developer him/herself.

### Blockchain specific network and economic model
TBD

