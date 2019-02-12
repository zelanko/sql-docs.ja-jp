---
title: Reporting Services のプロパティ | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- report servers [Reporting Services], properties
- properties [Reporting Services], about properties
- reports [Reporting Services], properties
- Report Server Web service, properties
- report properties [Reporting Services]
- XML Web service [Reporting Services], properties
- Web service [Reporting Services], properties
- properties [Reporting Services]
ms.assetid: 8c855194-4c20-4ecc-a328-5137d54b560c
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: b2bd9ad5f828072985817b6ee3eb78897bab0b97
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56014971"
---
# <a name="reporting-services-properties"></a>Reporting Services のプロパティ
  レポート サーバーは、レポート サーバーにグローバルなシステム プロパティのセット、およびレポート サーバー データベースに格納された個別のアイテムに関連付けられているアイテム プロパティのセットを定義します。 レポート サーバーによって定義されたプロパティは削除できず、場合によっては読み取り専用です。 アプリケーションでシステム プロパティとアイテム プロパティを拡張するには、ユーザー定義プロパティをシステム プロパティとアイテム プロパティに追加します。  
  
 次の Web サービス メソッドは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のプロパティを取得および設定します。  
  
|方法|操作|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GetProperties%2A>|レポート サーバー データベースのアイテムに関する 1 つ以上のプロパティ値を返します。|  
|<xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>|1 つ以上のシステム プロパティを返します。|  
|<xref:ReportService2010.ReportingService2010.SetProperties%2A>|レポート サーバー データベースのアイテムの 1 つ以上のプロパティを設定します。|  
|<xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>|1 つ以上のシステム プロパティを設定します。|  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[レポート サーバー アイテムのプロパティ](reporting-services-properties-report-server-item-properties.md)|[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のアイテム固有のプロパティについて説明します。|  
|[レポート サーバーのシステム プロパティ](reporting-services-properties-report-server-system-properties.md)|[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のシステム固有のプロパティについて説明します。|  
  
## <a name="see-also"></a>参照  
 [Web サービスと .NET Framework を使用してのアプリケーションの構築](building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー Web サービス](../report-server-web-service.md)   
 [テクニカル リファレンス (SSRS)](../../technical-reference-ssrs.md)  
  
  
