## Service from a GUI app

* You have an application with a GUI<!-- .element: class="fragment" -->
  - From 20+ years ago<!-- .element: class="fragment" -->
  - Uses files instead of a Database<!-- .element: class="fragment" -->
  - QuickReport<!-- .element: class="fragment" -->
* Customer wants REST API for website<!-- .element: class="fragment" -->
  - By sending JSON or File<!-- .element: class="fragment" -->
  - And getting a JSON result<!-- .element: class="fragment" -->
  - Or a PDF report<!-- .element: class="fragment" -->


---


## Windows service

* Made Windows services before<!-- .element: class="fragment" -->
* Access to QuickReport<!-- .element: class="fragment" -->
* No complicated changes needed<!-- .element: class="fragment" -->
* Just a lot of refactoring<!-- .element: class="fragment" -->


---


## Refactoring for Service

* Separate the UI from the code that you need<!-- .element: class="fragment" -->
  - Prefer to move code to a new unit<!-- .element: class="fragment" -->
  - Change UI errors to exceptions or use a parameter for errors<!-- .element: class="fragment" -->
```pascal
function CalculateSomething: float;
begin
  Result := 0;
  if not Someglobal.IsValid then
  begin
    ShowMessage('Not valid');
    Exit;
  end;
  // ... etc
end;
```
<!-- .element: class="fragment" -->
* Try to keep Windows specific calls in separate functions or (interfaced) classes<!-- .element: class="fragment" -->
  - `{$ifdef API}`<!-- .element: class="fragment" -->
* But don't ifdef your dpr uses, Delphi will make a mess of things<!-- .element: class="fragment" -->


---


## Setting up a REST API

* Choose your poison <!-- .element: class="fragment" -->
  - [TMS Aurelius XData](https://www.tmssoftware.com/site/xdata.asp) <!-- .element: class="fragment" -->
  - [MARS](https://github.com/andrea-magni/MARS) <!-- .element: class="fragment" -->
  - [DMVCFramework](https://github.com/danieleteti/delphimvcframework) <!-- .element: class="fragment" -->
  - [RAD Server](https://www.embarcadero.com/products/rad-server) <!-- .element: class="fragment" -->


Note:

* Test
