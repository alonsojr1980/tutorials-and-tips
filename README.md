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

## GOOGLE
* [Download file with exceeded quota](google/download_exceeded_cota.md)

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

* <details>
  <summary>Easy align children center</summary>
  <br>
  
  ```
  .place-items-center { 
      display: grid; 
      place-items: center; 
  }
  ```
## VSCODE
* <details>
  <summary>Useful extensions</summary>
  <br>
  
  <ul>
    <li>Bookmarks - <i>Alessandro Fragnani</i></li>  
    <li>Bracket Pair Colorizer - <i>CoenraadS</i></li>  
    <li>Color Picker - <i>anseki</i></li>  
    <li>Debugger for Chrome - <i>Microsoft</i></li>  
    <li>Live Sass Compiler - <i>Ritwick Dey</i></li>  
    <li>Live Server - <i>Ritwick Dey</i></li>  
  </ul>

## AUTOMATIC1111 (STABLE DIFFUSION UI)
* <details>
  <summary>Useful extensions</summary>
  <br>
  
  <ul>
    <li>StyleSelectorXL (https://github.com/ahgsql/StyleSelectorXL)</li>  
    <li>SD_DYNAMIC_PROMPTS (https://github.com/adieyal/sd-dynamic-prompts)</li>
    <li>SD_WEBUI_CONTROLNET (https://github.com/Mikubill/sd-webui-controlnet)</li>
    <li>DWPose (https://github.com/IDEA-Research/DWPose)</li>
  </ul>

  
## WINDOWS OS
* [Renaming domain name on Windows Server 2008](https://www.techieshelp.com/how-to-rename-a-server-2008-domain/)

* <details>
  <summary>Run TRIM on SSD drive (powershell command)</summary>
  <br>
  
  ```  
  Optimize-Volume -DriveLetter YourDriveLetter -ReTrim -Verbose
  ```

