# ASP.NET Core | App Configuration

App configuration in ASP.NET Core is done through **configuration providers**. 
Configuration providers read key:value pairs from various sources.

`IConfiguration` service:
- primary means of resolving/reading configuration values from some source
- `Microsoft.Extensions.Configuration` namespace

The following inits a new instance of the `WebApplicationBuilder` class. It has
some default configuration (app-level).
```cs
var builder = WebApplication.CreateBuilder(args);
```

Configuration Load Order (highest -> lowest priority)
1. Command Line Arugments 
2. Environment variables not prefixed with `ASPNETCORE_` or `DOTNET_`
3. User secrets (dev only)
4. `appsettings.{Environment}.json` files
5. `appsettings.json` general file
6. Fallback host configuration file
