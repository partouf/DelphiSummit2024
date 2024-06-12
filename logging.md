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

---

## Logging for API frameworks

Add Middleware

```pascal
  MyLogging := TMyLogging.Create;

  var LoggingMiddleware := TLoggingMiddleware.Create(MyLogging);

  LoggingMiddleware.LogExceptions := True;
  LoggingMiddleware.LogLevel := TLogLevel.Trace;
  XDataModule.AddMiddleware(LoggingMiddleware);

  XDataModule.Events.OnModuleException.Subscribe(
    procedure(Args: TModuleExceptionArgs)
    begin
      LoggingMiddleware.Logger.Error(
        Format('Exception %s: %s', [Args.Exception.ClassName, Args.Exception.Message])
      );
    end);
```

---

## Logging for API frameworks

Use `x-forwarded-for`

```pascal
function GetOrigin: string;
var
  RemoteIp: string;
begin
  try
    if not TXDataOperationContext.current.Request.Headers.GetIfExists('x-forwarded-for', RemoteIp) then
      RemoteIp := TXDataOperationContext.Current.Request.RemoteIp;

    Result := RemoteIp + ' ' + TXDataOperationContext.Current.Current.Request.Uri.Path;
  except
    // lost request context, but still need to return something
    Result := 'unknown';
  end;
end;
```

Note:
* Don't use if you don't need it, but can be helpful who's doing what
* https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Forwarded-For

---

## Sawing Logs

![Layout with logging](/images/network-3.png)
