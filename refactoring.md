## Refactoring for Service

* Separate the UI from the code that you need<!-- .element: class="fragment" -->
  - Prefer to move code to a new unit<!-- .element: class="fragment" -->
  - Change UI errors to exceptions or use a parameter for errors<!-- .element: class="fragment" -->
```pascal
function CalculateSomething: Currency;
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

---

### Error handling dos

```pascal
function CalculateSomething: Currency;
begin
  Result := 0;
  if not Someglobal.IsValid then
    raise MyException.Create('Not valid');

  // ... etc
end;
```

or 

```pascal
function TryCalculateSomething(var OutResult: Currency; var ErrorTxt: string): Boolean;
begin
  Result := False;
  if not Someglobal.IsValid then
  begin
    ErrorTxt := ErrorTxt + 'Not valid'#10;
    Exit;
  end;

  OutResult := 42;
  Result := True;
end;
```

---

### Error handling donts

* Don't use global-state

```pascal
var
  LastErrorCode: Integer = 0;
  LastErrorText: string = '';

function CalculateSomething: Currency;
begin
  Result := 0;
  if not Someglobal.IsValid then
  begin
    LastErrorCode := 6;
    LastErrorText := 'Not valid';
    Exit;
  end;

  // ... etc
end;
```

---

## Refactoring for Service

* Separate the UI from the code that you need
  - Prefer to move code to a new unit
  - Change UI errors to exceptions or use a parameter for errors
  - Don't use a global error state
* Try to keep Windows specific calls in separate functions or (interfaced) classes<!-- .element: class="fragment" -->
  - `{$ifdef API}`<!-- .element: class="fragment" -->
* But don't ifdef your dpr uses, Delphi will make a mess of things<!-- .element: class="fragment" -->
