## Transition to Linux

* Make a Windows 64bit CLI application <!-- .element: class="fragment" -->
* Enable Linux64 <!-- .element: class="fragment" -->
  - https://docwiki.embarcadero.com/RADStudio/Alexandria/en/Linux_Application_Development <!-- .element: class="fragment" -->
  - You only need remote access once to determine the OS version and SDK <!-- .element: class="fragment" -->
* Make sure you have rebuilt needed 3rd party components for Linux64 (Aurelius, Spring) <!-- .element: class="fragment" -->
  - Make sure to output (package output + unit output) to separate .\\$(Platform)\\$(Config) directory <!-- .element: class="fragment" -->
  - And update the Linux64 Library paths <!-- .element: class="fragment" -->

---

## Local testing options

* Windows build <!-- .element: class="fragment" -->
  - Quick iteration possible <!-- .element: class="fragment" -->
  - But can't test everything <!-- .element: class="fragment" -->
* Linux build + use PAServer to upload to remote machine <!-- .element: class="fragment" -->
  - https://docwiki.embarcadero.com/RADStudio/Athens/en/PAServer,_the_Platform_Assistant_Server_Application <!-- .element: class="fragment" -->
* Linux build + use PAServer debugging in WSL <!-- .element: class="fragment" -->
  - Uploading costs time <!-- .element: class="fragment" -->
* Linux build + Docker build <!-- .element: class="fragment" -->
  - After 1st time build it should be pretty quick <!-- .element: class="fragment" -->
  - PAServer debugging possible <!-- .element: class="fragment" -->
