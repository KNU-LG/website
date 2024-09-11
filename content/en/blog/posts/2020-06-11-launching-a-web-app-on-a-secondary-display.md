---
title: Launching a web app on a secondary display
date: 2020-06-11
slug: launching-a-web-app-on-a-secondary-display
posttype: article
toc: true
thumbnail: th-web-app-on-secondary-displays.jpg
---

**Author: NERGI**

Since version 2.0.0, webOS OSE has been supporting a dual display feature. Thanks to that feature, a user can select an output display of a webOS OSE app.

For those who want to try out the feature on webOS OSE, this guide introduces a sample app which can select the output display.

## How to Install the App

To install the app, first you have to clone the repository.

``` bash
$ git clone https://github.com/Heeam-Shin/web-app-controller-sample.git
$ cd web-app-controller-sample
```

The installation procedure is the same as that of a web app. Type the following commands:

``` bash
$ ares-package .
$ ares-install ./com.dual.webapp.sample_1.0.0_all.ipk -d [your-target-device]
```

{{< note >}}
For more details on the above procedure, refer to [Developing Downloadable Web Apps]({{< relref "developing-downloadable-web-apps" >}}).
{{< /note >}}

If the installation succeed, the app card of the installed sample appears in Home Launcher.

{{< figure src="/images/blog/articles/dual-display-sample-app-card.jpg" alt="Sample app in Home Launcher" caption="" >}}

Then click the app card to launch the sample app. You can launch/close the built-in YouTube app by clicking the **Launch / Close** buttons, respectively.

{{< figure src="/images/blog/articles/dual-display-web-app-sample.jpg" alt="Launched sample app" caption="" >}}

## Source Codes

This section explains the codes which are directly related to usage of LS2 API rather than explaining the whole codes.

### appinfo.json

``` json {linenos=table}
{
  "id": "com.dual.webapp.sample",
  "version": "1.0.0",
  "vendor": "LG Electronics",
  "type": "web",
  "main": "index.html",
  "title": "Secondary display sample",
  "icon": "./images/NERGI.png",
  "requiredPermissions": ["configurator.callbacks","applications","all","applications.launch","applications.internal"]
}
```

A brief explanation of the above file:

- Line(9) : Set ACG (Access Control Groups) information. Every method of LS2 APIs needs ACG information to get security permissions. For more details on how to get the ACG information, see [Identify the ACG Group of the Methods]({{< relref "using-ls2-api-in-web-apps#identify-the-acg-group-of-the-methods" >}}).

### index.html

``` html {linenos=table}
<body>
    <div class="middle-center-align">
        <h1 class="burning-shadow">Launch/Close YouTube App!</h1>
        <h2>(on your secondary display)</h2>
        <div class="center-align">
            <button class="button" onclick="openApp();">Launch</button>
            <button class="button" onclick="closeApp();">Close</button>
        </div>
    </div>
</body>
```

It's a pretty basic HTML code. A brief explanation of the above file:

- Line(6~7) : Call JavaScript functions using the `onclick` event.

### webapp-test.js

In this file, `openApp()` function calls the `launch` method and `closeApp()` calls the `close` method using the [WebOSServiceBridge API]({{< relref "webosservicebridge-api-reference" >}}). Both `openApp()` and `closeApp()` use the WebOSServiceBridge API in a similar way. So I'll only explain how `openApp()` makes use of the API only.

{{< note >}}
For more details on `launch` and `close`, see the [com.webos.service.applicationmanager API]({{< relref "com-webos-service-applicationmanager" >}}).
{{< /note >}}

``` js {linenos=table}
function openApp(){
    var bridge = new WebOSServiceBridge();

    var url = 'luna://com.webos.service.applicationmanager/launch';
    var params = '{"id":"com.webos.app.test.youtube", "params": {"displayAffinity": 1}}';

    bridge.call(url, params);
}
```

A brief explanation of the above file:

- Line(2) : Create a `WebOSServiceBridge` object.
- Line(4~5) : Define parameters for the call method.
- Line(7) : Call a LS2 API with predefined parameters (`url`, `params`). You can use various LS2 APIs by changing parameters of the `call` method.

{{< note >}}
For more information about other LS2 APIs, see [LS2 API Index]({{< relref "ls2-api-index" >}}).
{{< /note >}}