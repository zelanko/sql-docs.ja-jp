---
title: "Reporting Services 拡張機能ライブラリ | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- namespaces [Reporting Services]
- Reporting Services, extending
- extensions [Reporting Services], library
- library [Reporting Services]
ms.assetid: e8eff470-64d6-41c3-b98b-5ec916c121c3
caps.latest.revision: "33"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: f02795f80e696c423df3b6c55397830775bfaa63
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="reporting-services-extension-library"></a>Reporting Services 拡張機能ライブラリ
  Reporting Services 拡張機能ライブラリは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に含まれているクラス、インターフェイス、および値の型のセットです。 このライブラリは、システムの機能にアクセスし、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] アプリケーションを使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントを拡張するための土台となるように設計されています。  
  
## <a name="namespaces"></a>名前空間  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 拡張機能ライブラリには次の名前空間があります。  
  
 <xref:Microsoft.ReportingServices.DataProcessing>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のデータ処理機能を拡張するコンポーネントの構築に使用できるクラスとインターフェイスが含まれています。  
  
 <xref:Microsoft.ReportingServices.Interfaces>  
 カスタム通知を作成し、独自の配信拡張機能を通じてユーザーに送信したり、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のカスタム セキュリティ拡張機能を構築したりすることを可能にする、クラスとインターフェイスが含まれています。  
  
 **Microsoft.ReportingServices.ReportRendering**  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の表示機能を拡張できるクラスとインターフェイスが含まれています。 この名前空間のメンバーを <xref:Microsoft.ReportingServices.Interfaces> 名前空間のメンバーと共に使用することで、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] で使用する独自のカスタム表示拡張機能を作成できます。  
  
## <a name="see-also"></a>参照  
 [Reporting Services の拡張機能](../../reporting-services/extensions/reporting-services-extensions.md)  
  
  
