⛔ DEPRECATED. This project was moved to a new repository. Visit [dashboard-extensions](https://github.com/DevExpress/dashboard-extensions) to find an updated version. 

The current repository does not support the [modular approach](https://docs.devexpress.com/Dashboard/119108/) for HTML JS Dashboard and will not be updated in the future.

------

A custom **FunnelD3** item renders a funnel chart using the [D3Funnel](https://github.com/jakezatecky/d3-funnel/blob/master/README.md) JS library.

This dashboard item supports the following capabilities:

- [Master-Filtering](https://documentation.devexpress.com/#Dashboard/CustomDocument117060)
- [Drill-Down](https://documentation.devexpress.com/#Dashboard/CustomDocument117061)
- [Exporting](https://documentation.devexpress.com/#Dashboard/CustomDocument116694)
- Appearance Customization

> Note that the custom export functionality implemented in the Funnel D3 item is not supported for the Internet Explorer browser due to the problem with HTML canvas drawing. If you use IE 11 or earlier versions, the export buttons will be hidden. Refer to the following Microsoft issue to learn more: https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/1015651/.


## Installation

To add a custom Funnel3D item extension to the Web Dashboard, follow the steps below.

1. Download the latest version of scripts [here](https://github.com/DevExpress/dashboard-extension-funnel-d3-item/releases).

2. Add the *dist* folder in your project.

3. Attach the download script to the project inside the `<body>` section before the end tag onto the page containing Web Dashboard.
```xml
<body>
    <!-- ... -->
    <script src="/dist/funnel.min.js"></script>
</body>
```

4. Attach both the D3.js v4.x and D3Funnel scripts to the project. You can find these libraries here: [D3](https://github.com/d3/d3) and [D3Funnel](https://github.com/jakezatecky/d3-funnel).

```xml
<head>
    <script src="/path/to/d3.v4.js"></script>
    <script src="/path/to/dist/d3-funnel.js"></script>
    <!-- ... -->
</head>
```

5. Handle the Web Dashboard's [BeforeRender](https://documentation.devexpress.com/#Dashboard/DevExpressDashboardWebScriptsASPxClientDashboard_BeforeRendertopic) event to perform client-side customization of the Web Dashboard control before the control and its elements have been rendered.
```xml
<!-- For ASP.NET Web Forms -->
<dx:ASPxDashboard ID="ASPxDashboard1" runat="server" DashboardStorageFolder="~/App_Data/Dashboards">
  <ClientSideEvents BeforeRender="onBeforeRender" />
</dx:ASPxDashboard>
```
```C#
@* For ASP.NET MVC *@
@Html.DevExpress().Dashboard(settings => {
    settings.Name = "Dashboard";
    settings.ClientSideEvents.BeforeRender = "onBeforeRender";
}).GetHtml()
```

6. Register the custom item extension to add the FunnelD3 to the Web Dashboard.

```javascript
function onBeforeRender(sender) {
  var dashboardControl = sender.GetDashboardControl();
  dashboardControl.registerExtension(funnelD3ItemExtension(dashboardControl));
}
```

## Settings
The **FunnelD3** dashboard item supports the following settings that you can configure in the Web Dashboard UI:

![image](https://cloud.githubusercontent.com/assets/17986517/25003741/907a39e0-2059-11e7-8540-312534ec2bad.png)

* **Fill Type** - Specifies the funnel chart's *solid* or *gradient* fill type.
* **Curved** - Specifies whether the funnel is curved.
* **Dynamic Height** - Specifies whether the height of blocks are proportional to their weight.
* **Pinch Count** - Specifies how many blocks to pinch at the bottom to create a funnel "neck".

## Development 

You can use this extension code as a base for your own [dashboard item extension](https://documentation.devexpress.com/#Dashboard/CustomDocument117546) development. 

Before you start, we advise you to [fork](https://help.github.com/articles/fork-a-repo/) this repository and work with your own copy.

1. Clone this extension to get a local copy of the repository.
```Batchfile
git clone https://github.com/DevExpress/dashboard-extension-funnel-d3-item.git
cd dashboard-extension-funnel-d3-item
```

2. In this extension we use the [Node.js](https://nodejs.org/en/about/) toolset. Use the command below to install all modules listed as dependencies in the extension's **package.json** file.
```Batchfile
npm install
```

3. Then install [Gulp](http://gulpjs.com) to build the solution. You can install it globally...
```Batchfile
npm install -g gulp
gulp build
```

... or use a local Gulp version.
```Batchfile
.\node_modules\.bin\gulp build
```

You can find the resulting files at ```...\dashboard-extension-funnel-d3-item\dist```:
**funnel.js** and **funnel.min.js**.

## License

This extension is distributed under the **MIT** license (free and open-source), but can only be used with a commercial DevExpress Dashboard software product. You can [review the license terms](https://www.devexpress.com/Support/EULAs/NetComponents.xml) or [download a free trial version](https://go.devexpress.com/DevExpressDownload_UniversalTrial.aspx) of the Dashboard suite at [DevExpress.com](https://www.devexpress.com).

## Support & Feedback

* Refer to [this section](https://documentation.devexpress.com/#Dashboard/CustomDocument117232) for general information about client-side extensions.
* To learn how to create a custom item, see the following [KB article](https://www.devexpress.com/Support/Center/Question/Details/T491984).
* To address questions regarding the Web Dashboard and JavaScript API, use [DevExpress Support Center](https://www.devexpress.com/Support/Center).
