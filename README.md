#### VR-Demo-1

![image](http://imageup.info/upload/big/2016/07/14/57881762015e8.png)

This is an [Angular 2](https://angular.io/)-based environment for building WebVR apps with Mozilla's [A-frame](https://aframe.io/).

[Live Demo](http://brakmic.com/demos/vrdemo/)

**Notice**: the live demo contains graphics, SVGs and markups taken from the A-Frame homepage. 

*All copyrights regarding these materials belong to Mozilla and/or other companies and groups (MozVR team etc.)*.

#### Installation

```
yarn 
```

or

```
npm install
```

#### Building 
```
npm start build:prod 
```

#### Running with Hot-Reloading 
Type
```
npm run start:hmr 
```
*then open [localhost:3000](http://localhost:3000) in your browser*.

#### Application Structure 

The [main component](https://github.com/brakmic/Angular_VRDemo/blob/master/src/app/components/app.component.ts) loads available vr modules at boot. By using a simple [routing mechanism](https://github.com/brakmic/Angular_VRDemo/blob/master/src/app/components/app.routes.ts) the [Wrapper](https://github.com/brakmic/Angular_VRDemo/blob/master/src/app/components/shared/wrapper/wrapper.component.ts) configures the [VrElement Directive](https://github.com/brakmic/Angular_VRDemo/blob/master/src/app/components/shared/vr-element/vr-element.directive.ts) to activate a selected VR-module.


##### State Management

The application state management is done via [@ngrx](https://github.com/ngrx/ngrx.github.io). 

The currently available VR modules are located in [src/app/components/app.loader.ts](https://github.com/brakmic/Angular_VRDemo/blob/master/src/app/components/app.loader.ts). Every module implements the [IVrModule](https://github.com/brakmic/Angular_VRDemo/blob/master/src/app/interfaces/declarations/IVrModule.ts) interface and must contain a single [markup structure](https://github.com/brakmic/Angular_VRDemo/blob/master/src/app/interfaces/declarations/IVrModule.ts#L7) and several (optional) [scripts](https://github.com/brakmic/Angular_VRDemo/blob/master/src/app/interfaces/declarations/IVrModule.ts#L8). All of the scripts will be [injected](https://github.com/brakmic/Angular_VRDemo/blob/master/src/app/components/shared/vr-element/vr-element.directive.ts) as separate HTML script tags below the markup. The helper function for dynamic creation of components is located in [ComponentFactory](https://github.com/brakmic/Angular_VRDemo/blob/master/src/app/helpers/component-factory/component-factory.ts)

During the application start the [VrModuleService](https://github.com/brakmic/Angular_VRDemo/blob/master/src/app/services/vr-module/vr-module.service.ts) registers all of the available modules by sending dispatch messages to @ngrx [AppStore](https://github.com/brakmic/Angular_VRDemo/blob/master/src/app/stores/app/app.store.ts). 

#### License 

[MIT](https://github.com/brakmic/Angular_VRDemo/blob/master/LICENSE)
