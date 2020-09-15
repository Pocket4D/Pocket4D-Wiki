# Pocket4D
It's an open-source embbed App/Dapp container, which runs `mini-program` inside existing iOS/Android/Desktop app.

1. [Pocket4D](#pocket4d)
   1. [Background](#background)
      1. [Mini-Programs](#mini-programs)
      2. [Pain-points of current Web2.0 systems](#pain-points-of-current-web20-systems)
      3. [Pain-points of current Web3.0 ecosystem](#pain-points-of-current-web30-ecosystem)
   2. [The general solutions](#the-general-solutions)
   3. [The Technical Design](#the-technical-design)
   4. [Roadmaps](#roadmaps)

## Background
### Mini-Programs
In late 2016, Allen Zhang, who is the one of the creator of Wechat starts the idea of `Mini-Program`. The `Mini-program` runs inside Wechat, which has over 1 billion users around the world. He thought the `Mini-Program` should be `Get when wanted, Leave when finished`("唾手可得，用完即走"). When the idea is shipped into wechat, and the growth is almost unstoppable. Very soon, Baidu, ByteDance, and Alibaba followed Wechat's step, developed their own `Mini-Program` stacks. By the end of June of 2020, the total users of `Mini-Program` has grown to 400 millions user, and over 600,000 `Mini-Program`s are running online.

The `Mini-Program` combines the native apps and javascript apps together. The javascript side can be very easy for most front-end coders to develope, and the native side provide rendering engine and powerful api that web browsers cannot provide. In the meantime, smart-phone users today are more rely on their phone and apps to interact with the internet service those companies provides, so the `Mini-Program` is light enough for companies are willing to extend their service rather than upgrading their existing Native Apps, and submit to AppStore of Apple and Google Play of Google.

However, these giants who made the `Mini-Program` are not intended to open-source their software, because it's hard to separate their bussiness from the service. But they did actually attract many companies and individuals to join their eco-systems.

### Pain-points of current Web2.0 systems
The web2.0 systems are full of pain-points. 
1. One of them is the Big Brothers. As commonly knowns to developers, AppStore of App and GooglePlay of google rejects many apps due to many reasons, some are content-based, some are bussiness based. Developers have not much choise because mobile os are controlled by these giant companies. Recently, a famous mobile gaming app is rejected by AppStore and GooglePlay because the company wanted to use their payment method of their own. Apps and services are watched and regulated by these big brothers, when they think that you are violating their policies, you are rejected without talking about fair.
2. Making a website or a native app is not easy. Developers have to buy a domain, rent an AWS server and provides https certificate and running cloud functions, and promote their apps to market. One have to spend more money before they can benifit little revenue from advertising system. 


### Pain-points of current Web3.0 ecosystem
We hope Web3.0 ecosystem to be strong and everyone can be benefit from it. However, there are serveral pain-points for now.

1. Most Web3.0 project are `backend` projects, they need `client` side to connect to them. However, most `client` side apps are rejected by AppStore or GooglePlay, or they are really hard to use. So there are mobile wallet apps exist.
2. Most Web3.0 `frontend` projects are browser-based. Users have to use their desktop PC or mobile web browser to use these apps. However these apps are mostly rely on browser extensions to interact with, so they are hard to get to mobile users.
3. So there are mobile wallet apps providing the webview and `web3` interface to them. Sadly, the webpages are not very good at rendering and the compatibilities are bad, and when the mobile wallet is rejected by AppStore of Apple or Google Play, the users will have to find other solutions.
4. The web is domain-based, it's hard to be decentralized. Aside from `backend` part, the `client` needs a http/https domain to resolve their frontend assets, even it uses aws or google cloud storage. So there is a level of risk when the domain and the assets are lost, they may become unreachable. 
   
## The general solutions
Here we come to a solution to these pain-points, we think about the possibilities to bring the `mini-program` idea to `decentrailized` system. It may become the last piece of current stage of Web3.0 progress to expand the user scale.

1. Be a container.
   The Pocket4D is tend to be a container, not app itself. This container works like what Wechat did for its `Mini-program` ecosystems. It should provide standard rendering protocols like `xml`, and provide most commonly used api for javascript to interact with, like `navigator`,`deviceInfo`. Also, it should provide most commonly used `Web3` interface for end-users.

   It should be using standard rendering methods to ensure the quality of the service, and should be easy to integrate to the host apps.

2. Be public, be decentralized, be reachable, be privacy protected
   It's important that the Pocket4D is publicly decentralized, that the protocols is opened to Web3.0 eco-systems.
   1. Not using domain system to host the `client` assests. Use IPFS or decentralized storage instead.
   2. Be embedded by apps, not one app. Easily to integrate, just like webview does.
   3. Be searchable, the meta data of `Mini-Apps` can be searched by search engine. 
   4. Privacy is important, that the Pocket4D should be using `privacy-protected` that Web3.0 eco-system provides.
   
3. Bussiness and public potentials
   1. The potential of `mini-program` is the bussiness, especially to the host and the `mini-program` itself. The host can extend their service by integrating the `mini-program` provides, the settlement between them can be done through FIAT system or Crypto system (like Smart-contract).
   2. And the public service can be a `mini-program`, like `COVID-19` information or public voting systems.
   3. Maybe there are many companies and apps are rejected by Apple or Google Play, they might try developing a `mini-apps` to reform their service online to mobile app users.

## The Technical Design
The Technical Design is unique to Pocket4D, please refer to [Technical Design](technical-design.md) 

## Roadmaps
The Pocket4D is a very long-term project, please refer to [Road maps](roadmaps.md)













