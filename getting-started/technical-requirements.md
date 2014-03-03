---
title: Technical Requirements
meta_title: Technical Requirements for using Kendo UI JavaScript framework
meta_description: Check browser and platform support and prerequisites for best performance when working with Kendo UI.
slug: gs-technical-requirements
publish: true
---

<style scoped>
    .stripes
    {
        border: 1px solid #E15613;
        border-collapse: collapse;
    }
    .stripes th
    {
        background: #E15613;
        color: #fff;
    }
    .stripes tr:nth-child(2n+1) td
    {
        background: #fed;
    }
    .stripes td:nth-child(n+2)
    {
        text-align: center;
    }
    .stripes th,
    .stripes td
    {
        padding: 3px 5px;
    }
</style>

# Technical Requirements for using Kendo UI

Below are the system requirements for the Kendo UI Framework.

### Supported Desktop Browsers
<table class="devices-platforms stripes" style="margin-top: 1.2em;">
   <tbody>
        <tr>
            <th style="width: 120px"></th>
            <th style="width: 100px">Kendo UI Web</th>
            <th style="width: 115px">Kendo UI DataViz</th>
            <th style="width: 110px">Kendo UI Mobile</th>
        </tr>
        <tr style="align: center">
           <td><span class="ie"></span>Internet Explorer</td>
           <td>7+</td>
           <td>7+</td>
           <td>10+</td>
        </tr>
        <tr style="align: center">
            <td><span class="firefox"></span>Firefox</td>
            <td><a href="http://www.mozilla.org/en-US/firefox/organizations/">ESR</a> +</td>
            <td><a href="http://www.mozilla.org/en-US/firefox/organizations/">ESR</a> +</td>
            <td>-</td>
        </tr>
        <tr style="align: center">
            <td><span class="chrome"></span>Chrome</td>
            <td>Yes</td>
            <td>Yes</td>
            <td>Yes</td>
        </tr>
        <tr style="align: center">
            <td><span class="opera"></span>Opera</td>
            <td>15.0 +</td>
            <td>15.0 +</td>
            <td>15.0 +</td>
        </tr>
        <tr style="align: center">
            <td><span class="safari"></span>Safari 5+ (OS X)</td>
            <td>Yes</td>
            <td>Yes</td>
            <td>Yes</td>
        </tr>
    </tbody>
</table>

**NOTES:**

* Browsers in beta stage are not supported.
* [Quirks mode](http://www.quirksmode.org/css/quirksmode.html) is not supported. Always specify a [DOCTYPE](http://reference.sitepoint.com/html/doctypes)! Supported DOCTYPES include `HTML5`, `XHTML 1.1`, `XHTML 1.0` (`Transitional` or `Strict`) and `HTML4 Strict`.
Note that `HTML4 Transitional` triggers quirks mode.
* Internet Explorer compatibility modes are not supported. These modes can exhibit different behavior and rendering bugs, compared to the browser versions they emulate.
It is highly recommended to use IE's [Edge mode](http://blogs.msdn.com/b/ie/archive/2010/06/16/ie-s-compatibility-features-for-site-developers.aspx) via META tag or HTTP header.
        
        <meta http-equiv="X-UA-Compatible" content="IE=edge" />
        
* Kendo UI uses progressive enhancement for its CSS styling. As a result, old and obsolete browsers may ignore CSS3 styles, such as rounded corners and linear gradients.

### Kendo UI Platform support

<table class="devices-platforms stripes" style="margin-top: 1.2em;">
    <tr>
        <th class="platform">Platform</th>
        <th class="platform-version">Version</th>
    </tr>
    <tr>
        <td style="width: 150px;"><span class="windows"></span>Windows</td>
        <td>XP +, Server 2003 +</td>
    </tr>
    <tr>
        <td><span class="mac"></span> Mac OS</td>
        <td>OS X +</td>
    </tr>
    <tr>
        <td><span class="android"></span> Android</td>
        <td>2.3 +</td>
    </tr>
    <tr>
        <td><span class="ios"></span> iOS</td>
        <td>6.0 +</td>
    </tr>
    <tr>
        <td><span class="blackberry"></span>BlackBerry</td>
        <td>10.0+</td>
    </tr>
    <tr>
        <td><span class="winphone"></span>Windows Phone</td>
        <td>8.0+</td>
    </tr>
     <tr>
        <td><span class="chrome"></span>Chrome for Android</td>
        <td>Yes</td>
    </tr>
</table>

**NOTES:**

* Kendo UI DataViz is not supported on Android 2.x.
* Hybrid mouse and touch devices are supported (for instance IE10, Chrome and Firefox on Windows 8).

<<<<<<< HEAD
<<<<<<< HEAD
=======
=======
>>>>>>> 650dfb9... Included Chrome for Android in platform list

>>>>>>> 650dfb9... Included Chrome for Android in platform list
## Prerequisites:

* JavaScript must be enabled on all browsers

For best performance:

* 'Disable script debugging' in the browser's config options must be checked
* Caching on Internet Explorer must be activated
