---
title: "セキュリティで保護された Web サービス メソッドを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- SOAP [Reporting Services], secure connections
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: 87329299-c2ea-4517-9148-d855726768a9
caps.latest.revision: 36
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 802070f070222fba573b52bf1f53b2c6eb8ba8b6
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="using-secure-web-service-methods"></a>セキュリティで保護された Web サービス メソッドの使用
  特定のレポート サーバー Web サービスを呼び出す場合に、セキュリティによる接続の保護が必要なことがあります。 セキュリティで保護された接続を必要とするメソッドはによって決定されます、 **SecureConnectionLevel** RSReportServer.config ファイルに設定します。 有効な設定値は 0 以上の整数値です。 次の表では、これらの値を説明します。  
  
|レベル|Description|  
|-----------|-----------------|  
|**0**|セキュリティで保護されません。 Reporting Services SOAP API への呼び出しに対して、セキュリティで保護された接続は不要です。|  
|大きい**0**|セキュリティで保護されます。 Reporting Services SOAP API へのすべての呼び出しに対して、セキュリティで保護された接続が必要です。|  
  
 Web サービスの <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> メソッドを使用して、レポート サーバーの現在の構成に基づいて、セキュリティで保護された接続を必要とする Web サービス メソッドの一覧を返すことができます。 SSL を使用する場合は、<xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> によって返されたメソッドの一覧を評価し、呼び出すメソッドに応じて Web サービス URI のスキーマ名を "https" または "http" に変更します。  
  
## <a name="see-also"></a>参照  
 [Web サービスと、.NET Framework を使用してアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー Web サービス](../../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
