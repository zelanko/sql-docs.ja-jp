---
title: Microsoft.VisualBasic.dll | で許可されていない型とメンバーMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: 45f55646-4bf1-4493-9f72-d1363c9a9ac6
author: rothja
ms.author: jroth
ms.openlocfilehash: 9756c67e3cdfe1ff9e30127b3f8b5bf6ddcda436
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84954392"
---
# <a name="disallowed-types-and-members-in-microsoftvisualbasicdll"></a>Microsoft.VisualBasic.dll の許可されない型およびメンバー
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]共通言語統合 (CLR) プログラミングでは、、、、、、 `HostProtectionAttribute` `System.Security.Permissions.HostProtectionResource` `ExternalProcessMgmt` `ExternalThreading` `MayLeakOnAbort` `SecurityInfrastructure` `SelfAffectingProcessMgmnt` `SelfAffectingThreading` 、 **sharedstate**、 `Synchronization` 、または `UI` の値を持つ列挙体を指定するを持つ型またはメンバーの使用は禁止されています。 次の表は、ホスト保護属性 (HPA) 値が許可されない `Microsoft.VisualBasic.dll` アセンブリのメンバーおよび型を示しています。  
  
> [!NOTE]  
>  この一覧は、サポートされているアセンブリから作成されたものです。 詳細については、「[サポートされている .NET Framework ライブラリ](../clr-integration/database-objects/supported-net-framework-libraries.md)」を参照してください。  
  
|**型またはメンバー**|**HPA 値**|  
|------------------------|------------------------|  
|Microsoft.VisualBasic.ApplicationServices.ApplicationBase|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeCulture()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.ApplicationBase.get_Info()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.AssemblyInfo|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.BuiltInRoleConverter|SharedState|  
|Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.User|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.WebUser|ExternalProcessMgmt|  
|Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase|ExternalProcessMgmt|  
|Microsoft.VisualBasic.CompilerServices.HostServices|SharedState|  
|Microsoft.VisualBasic.CompilerServices.ProjectData.EndApp()|SelfAffectingProcessMgmt|  
|Microsoft.VisualBasic.CompilerServices.Utils.SetCultureInfo()|SelfAffectingThreading|  
|Microsoft.VisualBasic.DateAndTime.set_DateString()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.DateAndTime.set_TimeOfDay()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.DateAndTime.set_TimeString()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.DateAndTime.set_Today()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Audio|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Clock|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Computer|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.ComputerInfo|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Keyboard|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Mouse|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Network|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.Ports|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Devices.ServerComputer|ExternalProcessMgmt|  
|Microsoft.VisualBasic.FileIO.FileSystem|ExternalProcessMgmt|  
|Microsoft.VisualBasic.FileIO.SpecialDirectories|ExternalProcessMgmt|  
|Microsoft.VisualBasic.FileIO.TextFieldParser..ctor()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.FileSystem|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Interaction.CreateObject()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Interaction.DeleteSetting()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Interaction.GetObject()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Interaction.InputBox()|UI|  
|Microsoft.VisualBasic.Interaction.MsgBox()|UI|  
|Microsoft.VisualBasic.Logging.AspLog|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener..ctor()|ExternalProcessMgmt|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.Close()|同期|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.Dispose()|同期|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.Flush()|同期|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.GetSupportedAttributes()|同期|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.TraceData()|同期|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.TraceEvent()|同期|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.Write()|同期|  
|Microsoft.VisualBasic.Logging.FileLogTraceListener.WriteLine()|同期|  
|Microsoft.VisualBasic.Logging.Log|ExternalProcessMgmt|  
|Microsoft.VisualBasic.MyServices.ClipboardProxy|ExternalProcessMgmt|  
|Microsoft.VisualBasic.MyServices.FileSystemProxy|ExternalProcessMgmt|  
|Microsoft.VisualBasic.MyServices.RegistryProxy|ExternalProcessMgmt|  
|Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy|ExternalProcessMgmt|  
  
## <a name="see-also"></a>参照  
 [ホスト保護属性と CLR 統合プログラミング](host-protection-attributes-and-clr-integration-programming.md)   
 [mscorlib.dllで許可されていない型とメンバー](disallowed-types-and-members-in-mscorlib-dll.md)   
 [System.dllで許可されていない型とメンバー](disallowed-types-and-members-in-system-dll.md)   
 [System.Data.dllで許可されていない型とメンバー](disallowed-types-and-members-in-system-data-dll.md)   
 [System.Core.dll の許可されない型およびメンバー](disallowed-types-and-members-in-system-core-dll.md)  
  
  
