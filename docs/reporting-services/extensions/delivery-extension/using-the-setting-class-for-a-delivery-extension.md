---
title: "配信拡張機能に対する Setting クラスの使用 | Microsoft Docs"
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
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- delivery extensions [Reporting Services], settings
- Setting class
ms.assetid: 50746639-da7c-46a5-ac7b-e87dd6b91880
caps.latest.revision: "32"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: e9089816dd7154a6963cb27ac551a89529b01a3c
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="using-the-setting-class-for-a-delivery-extension"></a>配信拡張機能に対する Setting クラスの使用
  <xref:Microsoft.ReportingServices.Interfaces.Setting> クラスは <xref:Microsoft.ReportingServices.Interfaces> 名前空間にあり、配信拡張機能の拡張機能設定に関する情報を表します。 <xref:Microsoft.ReportingServices.Interfaces.Setting> クラスは、配信拡張機能が正しく機能するために必要な設定に関する情報を格納するインフラストラクチャを提供します。 たとえば、レポート サーバーの電子メール配信では、ユーザーは受信者のアドレス、送信者のアドレス、電子メールの件名など、電子メール配信に固有の設定を入力する必要があります。 カスタム配信プロバイダーの場合にも、通知とレポートを配信する配信拡張機能のために、特定の設定を入力するようにユーザーに求めます。  
  
 <xref:Microsoft.ReportingServices.Interfaces.Setting> クラスは、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ExtensionSettings%2A> インターフェイスの <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> プロパティを実装する場合に使用します。 サブスクリプションまたは通知が作成された場合にユーザーが指定した拡張機能設定データを処理するためにも、<xref:Microsoft.ReportingServices.Interfaces.Setting> クラスを使用します。  
  
 <xref:Microsoft.ReportingServices.Interfaces.Setting> クラスの使用例については、「[SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889)」 (SQL Server Reporting Services 製品サンプル) を参照してください。  
  
## <a name="see-also"></a>参照  
 [配信拡張機能の実装](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
