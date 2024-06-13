## API Testing

* Important, but is not easy to achieve <!-- .element: class="fragment" -->
* So prefer unit tests <!-- .element: class="fragment" -->
* Else; No need to keep to Delphi here<!-- .element: class="fragment" -->

---

## Approvals

* https://github.com/approvals

```python
import requests
import os

from approvaltests.approvals import verify_as_json

api_url = os.environ['PUBLIC_URL']

class TestForSmoke:
    def get_books(self):
        r = requests.get(f"{api_url}/books/")
        return r.json()

    def test_books(self):
        verify_as_json(self.get_books())
```

---

## Restart your engines

* https://github.com/partouf/DS24-Linux-Delphi-Resources/blob/main/.github/workflows/app-build.yml#L90
