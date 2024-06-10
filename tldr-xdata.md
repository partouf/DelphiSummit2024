## TLDR XData

```pascal
interface

uses
  System.Generics.Collections, Aurelius.Types.Nullable;

type
  // [Entity] not needed for non-database objects
  TDetail = class
  private
    FDateAndTime: Nullable<TDateTime>;
    FSomething: Nullable<Int64>;
  public
    property DateAndTime: Nullable<TDateTime> read FDateAndTime write FDateAndTime;
    property Something: Nullable<Int64> read FSomething write FSomething;
  end;

  TOverall = class
  private
    FDetails: TList<TDetail>;
    procedure SetDetails(const Value: TList<TDetail>);
  public
    constructor Create;
    property Details: TList<TDetail> read FDetails write SetDetails;
  end;
```

---

## Un-free

```pascal
implementation

constructor TOverall.Create;
begin
  FDetails := TList<TDetail>.Create;
end;

procedure TOverall.SetDetails(const Value: TList<TDetail>);
begin
  FDetails := Value;
end;

// destructor TOverall.Destroy;
// begin
//   FDetails.Free; // don't do this!
// end;
```

---

## Out of control

* You .Create it
* You give it to the XData layer
* Which sends it over HTTP/TCP
* And then frees it after it's been sent
* And if you got it from XData as a parameter
* It also handles freeing

---

## Point to the end

```pascal
uses
  XData.Service.Common,
  MyEntities;

type
  [ServiceContract]
  [Route('/v1/SomeEndpoint')]
  ISomeEndpoint = interface(IInvokable)
    ['{guid}']

    [HttpPost]
    function Calculate(const Input: TSomething): TOverall;
  end;

implementation
initialization
  RegisterServiceType(TypeInfo(ISomeEndpoint));
end.
```

---

## Implement the answer

```pascal
type
  [ServiceImplementation]
  TSomeEndpoint = class(TInterfacedObject, ISomeEndpoint)
  public
    function Calculate(const Input: TSomething): TOverall;
  end;

implementation

function TSomeEndpoint.Calculate(const Input: TSomething): TOverall;
begin
  Result := TOverall.Create;

  var Detail := TDetail.Create;
  Detail.DateAndTime := Date;
  Detail.Something := 42;

  Result.Details.Add(Detail);
end;

initialization
  RegisterServiceType(TSomeEndpoint);
end.
```

---

## Tricks allowed

* Raising exceptions will return errors to API clients
* You can change return content-types
  - `TXDataOperationContext.Current.Response.Headers.SetValue('content-type', 'text/html');`
* You can read custom headers (contextual per call)
  - `TXDataOperationContext.Current.Request.Headers.Get('my-custom-header')`
