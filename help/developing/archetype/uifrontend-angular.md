---
title: Front-End Build for Angular SPAs
description: A description of the front-end build process for Angular-based SPA projects
feature: Core Components, AEM Project Archetype
role: Architect, Developer, Admin
exl-id: 5726e29d-081c-42bb-bf4e-2852043b21d6
---
# Front-End Build for Angular SPAs {#frontend-angular}

This document explains the details of the project created when using the archetype to create a single page application (SPA) based on the Angular framework. I.e. when you set the `frontendModule` option to `angular`.

## Overview {#overview}

This project was bootstrapped with the [Angular CLI](https://github.com/angular/angular-cli).

This application is built to consume the AEM model of a site. It will automatically generate the layout using the helper components from the [@adobe/cq-angular-editable-components](https://www.npmjs.com/package/@adobe/cq-angular-editable-components) package.

## Scripts {#scripts}

In the project directory, you can run the following commands.

### npm start {#npm-start}

```
npm start
```

This command runs the app in development mode by proxying the JSON model from a local AEM instance running at http://localhost:4502. This assumes that the entire project has been deployed to AEM at least once (`mvn clean install -PautoInstallPackage` in the project root).

After running npm start in the ui.frontend directory, your app will be automatically opened in your browser (at path http://localhost:4200/content/${appId}/${country}/${language}/home.html). If you make edits, the page will reload.

If you are getting errors related to CORS, you might want to configure AEM as follows:

1. Navigate to the Configuration Manager (http://localhost:4502/system/console/configMgr)
1. Open the configuration for "Adobe Granite Cross-Origin Resource Sharing Policy"
1. Create a new configuration with the following additional values:
   * Allowed Origins: http://localhost:4200
   * Supported Headers: Authorization
   * Allowed Methods: OPTIONS

### npm test {#npm-test}

```shell
npm test
```

This command launches the Karma test runner. See the [Angular documentation about running tests](https://angular.io/guide/testing) for more information.

### npm run test:debug {#npm-run-test-debug}

```shell
npm run test:debug
```

This command launches the Karma test runner in interactive watch mode.

### npm run build {#npm-run-build}

```shell
npm run build
```

This command builds the app for production to the build folder. It bundles Angular in production mode and optimizes the build for the best performance. See the [Angular documentation about deployment](https://angular.io/guide/deployment) for more information.

Furthermore, an AEM ClientLib is generated from the app using the [aem-clientlib-generator](https://github.com/wcm-io-frontend/aem-clientlib-generator) package.

See the general [ui.frontend module documentation](uifrontend.md#clientlibs) for further information about how AEM ClientLibs are used by the project archetype.

## Browser Support {#browser-support}

By default, this project uses [Browserslist](https://github.com/browserslist/browserslist)'s defaults option to identify target browsers. Additionally, it includes polyfills for modern language features to support older browsers (e.g. Internet Explorer 11). If supporting such browsers isn't a requirement, the polyfill dependencies and imports can be removed.
