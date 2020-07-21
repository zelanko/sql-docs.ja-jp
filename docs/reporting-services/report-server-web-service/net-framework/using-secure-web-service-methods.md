---
title: セキュリティで保護された Web サービス メソッドの使用 | Microsoft Docs
description: RSReportServer 構成ファイルの SecureConnectionLevel 設定によるレポート サーバー Web サービス メソッドではセキュリティで保護された接続が必要です。
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- SOAP [Reporting Services], secure connections
- Web service [Reporting Services], SOAP
- Report Server Web service, SOAP
- XML Web service [Reporting Services], SOAP
ms.assetid: 87329299-c2ea-4517-9148-d855726768a9
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c29c7d6d1a8fb8be7edff1203073c4c84d2e197c
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487411"
---
# <a name="using-secure-web-service-methods"></a>セキュリティで保護された Web サービス メソッドの使用
  特定のレポート サーバー Web サービスを呼び出す場合に、セキュリティによる接続の保護が必要なことがあります。 セキュリティで保護された接続を必要とするメソッドは、RSReportServer.config ファイルの **SecureConnectionLevel** 設定で決まります。 有効な設定値は 0 以上の整数値です。 次の表では、これらの値を説明します。  
  
|Level|説明|  
|-----------|-----------------|  
|**0**|セキュリティで保護されません。 Reporting Services SOAP API への呼び出しに対して、セキュリティで保護された接続は不要です。|  
|**0** より大きい。|セキュリティで保護されます。 Reporting Services SOAP API へのすべての呼び出しに対して、セキュリティで保護された接続が必要です。|  
  
 Web サービスの <xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> メソッドを使用して、レポート サーバーの現在の構成に基づいて、セキュリティで保護された接続を必要とする Web サービス メソッドの一覧を返すことができます。 TLS を使用する場合は、<xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A> によって返されたメソッドの一覧を評価し、呼び出すメソッドに応じて Web サービス URI のスキーマ名を "https" または "http" に変更します。  
  
## <a name="see-also"></a>参照  
 [Web サービスと .NET Framework を使用してのアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー web サービス](../../../reporting-services/report-server-web-service/report-server-web-service.md)  
  
  
