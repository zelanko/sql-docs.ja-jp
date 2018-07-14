---
title: セキュリティ拡張機能の実装 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], extensions
- forms-based authentication [Reporting Services]
- custom authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: d2327e7c-0d48-49e3-bcd9-3bba4e67a68b
caps.latest.revision: 39
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 27707a7736c10794aec6c80679728988528665ba
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37216772"
---
# <a name="implementing-a-security-extension"></a>セキュリティ拡張機能の実装
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 認証は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] でレポートのセキュリティを確保するための主要なシステムです。 ただし、企業のカスタム セキュリティに対処するために、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のセキュリティ システムを拡張する必要が生じることもあります。 このような場合には、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] API に備えられた開発プラットフォームを使用します。 ここでは、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のセキュリティ拡張機能の概要について説明します。  
  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] セキュリティ拡張機能の実装、配置、および削除の詳細については、「[SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889)」 (SQL Server Reporting Services 製品サンプル) を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [セキュリティ拡張機能の概要](security-extensions-overview.md)  
 Reporting Services セキュリティ拡張機能の概要です。  
  
 [Reporting Services での認証](authentication-in-reporting-services.md)  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] での認証について説明します。  
  
 [Reporting Services での承認](authorization-in-reporting-services.md)  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] での承認について説明します。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.ReportingServices.Interfaces>   
 [Reporting Services の拡張機能](../reporting-services-extensions.md)   
 [Reporting Services 拡張機能ライブラリ](../reporting-services-extension-library.md)  
  
  
