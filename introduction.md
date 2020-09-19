# Pocket4D
It's an embedded open-source App/Dapp container, which runs `Mini-Program` inside existing iOS/Android/Desktop applications.

1. [Pocket4D](#pocket4d)
   1. [Background](#background)
      1. [Mini-Programs](#mini-programs)
      2. [Pain points of current Web2.0 systems](#pain-points-of-current-web20-systems)
      3. [Pain points of current Web3.0 system](#pain-points-of-current-web30-ecosystem)
   2. [The General Solutions](#the-general-solutions)
   3. [The Technical Design](#the-technical-design)
   4. [Roadmaps](#roadmaps)

## Background
### Mini-Programs
In late 2016, Allen Zhang, one of the founders of Wechat, initiated the idea of `Mini-Program`. At that time, WeChat already had more than 1 billion users around the world, and the `Mini-Program` were only allowed to run in WeChat. He believed that the `Mini-Program` should be `Get when wanted, Leave when finished`("唾手可得，用完即走"). When the idea landed in WeChat, its development was unstoppable. Very soon, Baidu, ByteDance, and Alibaba followed Wechat's lead and developed their own `Mini-Program` system. As of June 2020, the total number of users of `Mini-Program` has exceeded 400 million, while more than 600,000 `Mini-program` have been running online.

The `Mini-Program` combines Javascript, which is very close to what front-end developers are used to, and native apps, which provide a high-performance rendering engine and a powerful API that web browsers don't. Smartphone users, meanwhile, rely more on the convenience of mobile phones and app-based internet services. App developers prefer to be able to enhance their native apps independently, rather than having to upgrade their app versions and be censored by the App Store or Google Play every time. Thus, the `Mini-Program` becomes the lightweight optimal solution for these companies.

However, these giant companies that develop `Mini-Program` are reluctant to open source their software, as it is difficult to completely separate it from the services they offer in actual business. But the strategies of these companies have indeed attracted many other companies and individual developers to join their ecosystem.

### Pain points of current Web2.0 system
There are a series of pain points in Web 2.0.

1. One is "Big Brothers". As developers are well-known, the App Store and Google Play will remove or reject many apps. Some are due to content violations, and some are for commercial reasons. Since the mobile operating system is under the control of these giant companies, developers have no choice. Recently, a well-known mobile game was removed from the App Store and Google Play simply because its developer wanted to use their own payment method. The "Big Brothers" have been rigorously censoring and supervising the content and services of the applications, so when they believe that the content or the service violates the their policy and regulations, the App will be rejected and there is no room for bargaining.
2. Making a website or a native app is not easy. Developers need to buy domain names, rent servers, provide Https authentication, run cloud programs, and finally spend money to promote apps in the market. Development costs are high, and they may only make a small profit in the advertising business.


### Pain points of current Web3.0 system
We hope that the Web 3.0 ecosystem becomes strong and everyone can benefit from it. However, there are still many pain points.

1. The vast majority of Web 3.0 projects are `back-end` projects that need to redevelop the `client-side` to interface with them. However, many `client-side` apps are rejected by the App Store and Google Play, or the experience of the `client-side` projects is so poor that they have to rely on wallet apps to be of value.
2. The vast majority of Web 3.0 `front-end` projects are browser-based. Therefore, users have to open a desktop or mobile browser to run these web applications. However, these web applications rely to some extent on browser extensions, which makes them very difficult to reach mobile users.
3. Current wallet apps provide interfaces for web applications through Webview and `Web3`. However, the qualities of web applications is uneven, which is prone to slow loading and compatibility issues, resulting in poor user experience. Once the Wallet App is rejected by the App Store and Google Play, users can only look for other alternatives.
4. The web today is domain-based and it's hard to completely decentralize it. Apart from the back-end part, even if AWS cloud storage or Google cloud is used, the client still needs an http/https domain name to resolve the front-end resources. So this creates some operational risk that the app service may be inaccessible due to server-side issues.
   
## The general solutions
Here, we propose a solution to the above pain point: in considering the application of the `Mini-Program` to a decentralized system, we found that it has the potential to become an important piece of the puzzle in scaling users in the current Web 3.0 phase.

1. Be a container.
   Pocket4D will act as a container, not just an app. this container, like WeChat hosting the `Mini-program` ecosystem, will provide the Javascript side with standard rendering protocols (e.g. `xml`), and common APIs (e.g. `navigation`, `deviceInfo`, etc.). It should also provide interfaces such as `Web3` objects to end users. Pocket4D will have a standard rendering engine to provide quality-assured service capabilities, and can be easily integrated into the host app.

2. Open, decentralized, accessible, privacy protected
   An important aspect of Pocket4D is that it is openly decentralized and its protocols will be open to the Web 3.0 ecosystem.
   1. Instead of using the Domain Name System to store or preserve client resources, use IPFS or other decentralized storage solutions instead.
   2. Can be integrated and embedded in most host apps, not just for one app. Low barrier to entry, just like embedding a webview.
   3. Meta information of the `Mini-program` can be crawled by search engines.
   4. Privacy is extremely important, so Pocket4D will use the privacy protection scheme provided in the Web 3.0 ecosystem by default.
   
3. Bussiness and public service potentials
   1. For both the host and the `Mini-program` itself, the `Mini-program` has commercial potential. Hosts can extend their service capabilities by integrating `Mini-program`, and settlements with `Mini-program` service providers can be done in fiat currency or Cryto (such as smart contracts).
   2. Public services can be turned into `Mini-program`, such as information about `COVID-19`, or a voting system for the public.
   3. There are a large number of companies and apps that will be rejected by the App Store or Google Play, so they can try to develop `Mini-program` to get the opportunity to re-target mobile users.

## The Technical Design
The technical design of Pocket4D is unique, please check out [Technical Design](technical-design.md) .

## Roadmaps
The Pocket4D is a very long-term project, please check out [Roadmaps](roadmaps.md).
