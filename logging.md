## Sawing Logs

* What should we actually log? <!-- .element: class="fragment" -->
  - Not too much, not too little <!-- .element: class="fragment" -->
  - If REST API, log the calls <!-- .element: class="fragment" -->
* Default Docker logging is not the best <!-- .element: class="fragment" -->
  - Need to be logged into cloud provider <!-- .element: class="fragment" -->
  - Indivualised per instance <!-- .element: class="fragment" -->
  - Gone as soon as instance terminates <!-- .element: class="fragment" -->
* Choose between the millions of logging providers <!-- .element: class="fragment" -->
  - Best bet is to use Syslog <!-- .element: class="fragment" -->

Note:
* Difficult to determine what beforehand
