## Adding Sparkle to your life

```pascal
interface

uses
  XData.Server.Module, XData.Service.Common, System.SysUtils,
  {$ifdef Linux64}
  Sparkle.Indy.Server
  {$else}
  Sparkle.HttpSys.Server
  {$endif};

type
  TServer = class
  private
    FXDataModule : TXDataServerModule;
    {$ifdef Linux64}
    FSparkleServer: TIndySparkleHTTPServer;
    {$else}
    FSparkleServer: THttpSysServer;
    {$endif}
  public
    procedure StartServer;
  end;
```

---

## Need More Info

```pascal
implementation

procedure TServer.StartServer;
begin
  FXDataModule := TXDataServerModule.Create(GSettings.GetBaseURI);
  {$ifdef Linux64}
  FSparkleServer := TIndySparkleHTTPServer.Create(nil);
  FSparkleServer.DefaultPort := GSettings.GetDefaultPort;
  FSparkleServer.Dispatcher.AddModule(FXDataModule);
  FSparkleServer.Active := True;
  {$else}
  FSparkleServer := THttpSysServer.Create;
  FSparkleServer.AddModule(FXDataModule);
  FSparkleServer.Start;
  {$endif}
  // ... etc
end;
```
