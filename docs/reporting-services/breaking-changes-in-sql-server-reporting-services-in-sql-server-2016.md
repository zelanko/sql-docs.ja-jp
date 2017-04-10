---
title: "SQL Server 2016 における SQL Server Reporting Services の重大な変更 | Microsoft Docs"
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Me.Value references"
  - "Reporting Services, backward compatibility"
  - "重大な変更 [Reporting Services]"
ms.assetid: 39c7aafd-dcb9-4317-b8f7-d15828eb4f9a
caps.latest.revision: 121
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 116
---
# SQL Server 2016 における SQL Server Reporting Services の重大な変更
  このトピックでは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]における重大な変更について説明します。 これらの変更によって、以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に基づくアプリケーション、スクリプト、または機能が使用できなくなる場合があります。 この問題は、アップグレードするとき、またはカスタムのスクリプトやレポートで発生することがあります。  
  
  ## セキュリティ拡張機能
  
  カスタム セキュリティ拡張機能が新しい [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]で動作するには、いくつかの変更が必要です。 セキュリティ拡張機能は、IAuthenticationExtension2 インターフェイスを使用する必要があります。
  
  ## WMI プロバイダー
  
  [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] アプリケーション名は "ReportManager" から "ReportServerWebApp" へと変更されます。
  
## 参照  
 [SQL Server 2016 における SQL Server Reporting Services の動作変更](http://msdn.microsoft.com/ja-jp/2a767f0f-84f2-4099-8784-1e37790f858e)   
 [Reporting Services &#40;SSRS&#41; の新機能](../Topic/What's%20New%20in%20Reporting%20Services%20\(SSRS\).md)   
 [SQL Server 2016 における SQL Server Reporting Services の非推奨機能](http://msdn.microsoft.com/ja-jp/3876c01e-f81d-4cce-9104-5106a8c369e6)   
 [SQL Server 2016 で廃止された SQL Server Reporting Services の機能](http://msdn.microsoft.com/ja-jp/d529cc96-3483-480b-9bfc-bd28b1d0ef52)  
  
  