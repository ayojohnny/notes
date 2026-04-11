# .NET | Dependency Injection

Dependency Injection: programming concept that tries to solve hard-coded dependencies in codebases
- encourages loose coupling (flexible design)

DI uses an interface or base class to abstract a dependency's implementation (i.e. use abstract types instead
of concrete types). This enables switching the underlying implementation without breaking existing code (i.e.
loose coupling).

.NET runtime:
- creates a service container (`IServiceProvider`)
- registers services to the container & manages their lifetimes (appends to `IServiceCollection` at app startup)
    - the framework handles creating an instance of a dependency (object, etc.) and disposing of it when it's not longer needed

Service: object that provides a service to other objects (`IMessageWriter`). Not a "web service".


```cs
// Abstract type used for dependency injection (DI). The "service".
public interface IMessageWriter
{
    void Write(string message);
}

// The concrete "implementation" for the `IMessageWriter` service.
// By making the conrete type implementing the `IMessageWriter` interface,
// this "links" the implementation to the service that should be injected.
public class MessageWriter : IMessageWriter
{
    public void Write(string message)
    {
        Console.WriteLine($"MessgeWriter.Write(message: "\{message}"\");
    }
}

// Using shorthand for constructor injection.
public sealed Worker(IMessageWriter messageWriter)  : BackgroundService
{
    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            messageWriter.Write($"Worker running at: {DateTimeOffset.Now}");
            await Task.Delay(1_000, stoppingToken);
        }
    }
}
```

A full example of DI (from startup to being used) is below.

```cs
using Microsoft.Extensions.Hosting;
using Microsoft.Extensions.DependencyInjection;

HostApplicationBuilder builder = Host.CreateApplicationBuilder(args);

builder.services.AddHostedService<Worker>(); // Add background worker.

// Dependency injection happens here. 
// `AddSingleton<T, I> is saying that everytime, after startup that IMessageWriter,
// service is called - use the same `MessageWriter` concrete implementation (i.e. use the logic
// that this particular class has for the `Write(string message)` function.
//
// AddSingleton means the service is not dispoed until the app shuts down.
builder.services.AddSingleton<IMessageWriter, MessageWriter>(); 

using IHost host = builder.Build();

host.Run();
```

In the above:
- a host app instance is created
- `Worker` registered as a "Hosted Service" - in this case a background worker
- `IMesasgeWriter` is the "service" that uses the implementation (logic) from `MessageWriter` concrete type.
    - this is what is injected in other classes (see how it's injected in the concrete `Worker` class.
- host is built and ran/executed

By using DI pattern, the worker service does not rely on the concrete type of `MessageWriter`. It only
needs to know what `IMessageWriter` service provides/exposes. The advantage of relying on an abstract type is
that underlying "implementations" (i.e. concrete classes w/ different logic) can bee swapped out **without
modifying the `Worker` background service's code**. Important to note is that the `Worker` service itself **does
not create a new instance of the `MessageWriter` object**; instead, the **service container created by the .NET
framework** handles creating this object. This removes the need for saying `new MessageWriter` w/in the `Worker` class
and removes the repsonsibility of tracking that object's lifetime.

