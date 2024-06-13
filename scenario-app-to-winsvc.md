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
* And appropriate locking<!-- .element: class="fragment" -->

---

## Setting up a REST API

* Choose your poison
  - [TMS Aurelius XData](https://www.tmssoftware.com/site/xdata.asp))
  - [MARS](https://github.com/andrea-magni/MARS)
  - [DMVCFramework](https://github.com/danieleteti/delphimvcframework)
  - [RAD Server](https://www.embarcadero.com/products/rad-server)
  - Many more

---

## It's alive!

* It worked... mostly <!-- .element: class="fragment" -->
* Awkward installation when updating <!-- .element: class="fragment" -->
* Mostly useless Desktop <!-- .element: class="fragment" -->
* No scaling possible <!-- .element: class="fragment" -->
* But worst of all: random Printer errors <!-- .element: class="fragment" -->
  - "Printer out of range" <!-- .element: class="fragment" -->
  - To fix: restart service <!-- .element: class="fragment" -->

Note:
* Scaling possible but not trivial <!-- .element: class="fragment" -->
* Also multiple Windows servers, but seems wasteful <!-- .element: class="fragment" -->
