Common Logger <-> Serilog
=====

[![NuGet version](https://badge.fury.io/nu/Common.Logging.Serilog.svg)](https://badge.fury.io/nu/Common.Logging.Serilog) [![Build status](https://ci.appveyor.com/api/projects/status/0t8oqa6n5bu2t3qa/branch/master?svg=true)](https://ci.appveyor.com/project/Jaben/common-logging-serilog/branch/master)

Provides a bridge from the old to the new logging systems.

### Usage

### Configure app.config/web.config file of your project:

```xml
<configSections>
	<sectionGroup name="common">
		<section name="logging" type="Common.Logging.ConfigurationSectionHandler, Common.Logging" />
	</sectionGroup>
</configSections>

<common>
	<logging>
  		<factoryAdapter type="Common.Logging.Serilog.SerilogFactoryAdapter, Common.Logging.Serilog" />
	</logging>
</common>
```

You must configure and provide a global logger to use this adapter:

```csharp
var log = new LoggerConfiguration()
    .WriteTo.ColoredConsole()
    .CreateLogger();

// set global instance of Serilog logger which Common.Logger.Serilog requires.
Log.Logger = log;
```

### Links

* [Common Logging](http://netcommon.sourceforge.net/ "Common Infrastructure Libraries for .NET")
* [Serilog Project](http://serilog.net/ "Serilog")
