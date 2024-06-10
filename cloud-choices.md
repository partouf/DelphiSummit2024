## Cloud choice

* Roll your own Docker server <!-- .element: class="fragment" -->

Note:
* Let's see what that looks like...

---

## DiY Docker

* Install Linux <!-- .element: class="fragment" -->
* Install Docker <!-- .element: class="fragment" -->
  - snap install docker? Nope! <!-- .element: class="fragment" -->
* Deploy mechanism <!-- .element: class="fragment" -->
  - Manual SCP + SSH <!-- .element: class="fragment" -->
  - Jenkins <!-- .element: class="fragment" -->
* Health Checks <!-- .element: class="fragment" -->
  - Cronjob "crontab -e" <!-- .element: class="fragment" -->
  - https://crontab.guru/ <!-- .element: class="fragment" -->
  - And restart... no, re-deploy <!-- .element: class="fragment" -->
  - https://github.com/GDKsoftware/docker-jenkins-recovery-example <!-- .element: class="fragment" -->
* Maintenance <!-- .element: class="fragment" -->
  - Diskspace and inodes <!-- .element: class="fragment" -->
  - Purging unused data <!-- .element: class="fragment" -->
  - Restart of host takes longer and longer <!-- .element: class="fragment" -->

---

## Cloud choice

* Roll your own Docker server
* Cloud Docker container <!-- .element: class="fragment" -->
  - No need to maintain the underlying hardware, OS or docker itself <!-- .element: class="fragment" -->
* Bare Instances <!-- .element: class="fragment" -->
