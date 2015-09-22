# Virtual Router Manager
Wifi Hot Spot for Windows 10, 8, 8.1, 7 and 2008 R2

Copyright (c) 2013 Chris Pietschmann (http://pietschsoft.com)

Licensed under the Microsoft Public License (Ms-PL, https://opensource.org/licenses/MS-PL)

Original source code from: http://virtualrouter.codeplex.com/license

This version of Virtual Router Manager (1.0a) contains some updates to make the tool working with a german, french or spanish Windows 8, 8.1 or 10. It also offers localization of the user interface (partly). The source compiles fine with Microsoft Visual Studio 2010 and requires .Net Framework 3.5 SP1.

The updates are needed because the names of the virtual Wifi adapter may vary in each Windows version depending on the language. You will find these changes in VirtualRouterHost.cs:

```csharp
privateConnectionGuid = (from c in this.icsManager.Connections 
where c.props.DeviceName.ToLowerInvariant().Contains("microsoft virtual wifi miniport adapter") // Windows 7
|| c.props.DeviceName.ToLowerInvariant().Contains("microsoft hosted network virtual adapter") // Windows 8
|| c.props.DeviceName.ToLowerInvariant().Contains("von microsoft gehosteter, virtueller netzwerkadapter") // Windows 8 german
|| c.props.DeviceName.ToLowerInvariant().Contains("Adaptador virtual de red hospedada de Microsoft") // Windows 8 spanish
|| c.props.DeviceName.ToLowerInvariant().Contains("виртуальный адаптер размещенной сети (майкрософт)") //Windows 8 russian
|| c.props.DeviceName.ToLowerInvariant().Contains("Carte virtuelle de réseau hébergé Microsoft") // Windows 8 french
select c.Guid).FirstOrDefault();```
