# COMPILATION OF TUTORIALS AND TIPS

## ANGULAR
* <details>
  <summary>Use custom elements</summary>
  <br>  
  
  Do the following in every module that uses custom elements:
  ```
  import { CUSTOM_ELEMENTS_SCHEMA } from '@angular/core';
  
  @NgModule({
  schemas: [CUSTOM_ELEMENTS_SCHEMA],
  ...
  })
  ```
</details>

* [Use Stencil webcomponent in Angular](https://stenciljs.com/docs/angular)

## DELPHI
* [Console STDIN example](delphi/console_stdin.md)

## IONIC
* [Push notifications between Ionic 2/3 apps using Firebase Cloud Messaging](ionic/push_notifications_firebase_cloud_messaging.md)
* [Extensive Firebase Cloud Messaging payload guide](https://github.com/phonegap/phonegap-plugin-push/blob/master/docs/PAYLOAD.md)

## NPM
* [Update all packages](/npm/update_all_packages.md)

## STENCIL
* [Using ngModel in stencil webcomponents](https://github.com/kensodemann/blogs/blob/master/stencil/Using%20ngModel%20with%20Stencil%20Components.md)

## HTML/CSS
* <details>
  <summary>Force background-color printing</summary>
  <br>
  
  ```
  * { 
      color-adjust: exact; 
      -webkit-print-color-adjust: exact; 
      print-color-adjust: exact; 
    }
  ```

## WINDOWS OS
* [Renaming domain name on Windows Server 2008](https://www.techieshelp.com/how-to-rename-a-server-2008-domain/)
