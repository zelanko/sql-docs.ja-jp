---
title: "SQL Server 2016 における SQL Server Reporting Services における重大な変更 |Microsoft ドキュメント"
ms.date: 07/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Me.Value references
- Reporting Services, backward compatibility
- breaking changes [Reporting Services]
ms.assetid: 39c7aafd-dcb9-4317-b8f7-d15828eb4f9a
caps.latest.revision: 121
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: 6348d05b8dbe6c8ab1a682388b4e69ce438e6a12
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---

# <a name="breaking-changes-in-sql-server-reporting-services-in-sql-server-2016"></a>SQL Server 2016 における SQL Server Reporting Services の重大な変更

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2016](../includes/ssrs-appliesto-2016.md)] [!INCLUDE [ssrs-appliesto-not-2017](../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../includes/ssrs-previous-versions.md)]

このトピックでは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]における重大な変更について説明します。 これらの変更によって、以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に基づくアプリケーション、スクリプト、または機能が使用できなくなる場合があります。 この問題は、アップグレードするとき、またはカスタムのスクリプトやレポートで発生することがあります。

## <a name="security-extensions"></a>セキュリティ拡張機能

カスタム セキュリティ拡張機能が新しい [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]で動作するには、いくつかの変更が必要です。 セキュリティ拡張機能は、IAuthenticationExtension2 インターフェイスを使用する必要があります。

## <a name="wmi-provider"></a>WMI プロバイダー

[!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] アプリケーション名は "ReportManager" から "ReportServerWebApp" へと変更されます。

## <a name="next-steps"></a>次の手順

[SQL Server 2016 における SQL Server Reporting Services の動作変更します。](../reporting-services/behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)  
[Reporting Services (SSRS) の新機能](../reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md)   
[SQL Server 2016 における SQL Server Reporting Services の非推奨機能](../reporting-services/deprecated-features-in-sql-server-reporting-services-ssrs.md)    
[SQL Server 2016 で廃止された SQL Server Reporting Services の機能](../reporting-services/discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)  

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)
