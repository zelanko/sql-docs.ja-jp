---
title: ATOM デバイス情報設定 | Microsoft Docs
description: ATOM フィードの名前の送信をサポートする ATOM 表示拡張機能のデバイス情報設定と、使用する文字エンコードについて説明します。
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: fe4a56a4-5552-423c-85c1-895e2e212fee
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 274815c98aa15aead103e33de761b8b496212242
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242502"
---
# <a name="atom-device-information-settings"></a>ATOM デバイス情報の設定
  ATOM 表示拡張機能のデバイス情報設定では、ATOM フィードの名前および使用する文字エンコードの送信がサポートされています。  
  
 次の表は、データ サービス ドキュメントに表示するためのデバイス情報設定を示しています。  
  
|設定|値|  
|-------------|-----------|  
|**DataFeed**|指定した場合、この設定で指定されたフィード名に対応する ATOM フィードが表示されます。 指定しない場合は、レポートの ATOM サービス ドキュメントが表示されます。 データ フィード固有の自動生成された識別子です。 これは内部で使用される値であり、変更はしないでください。|  
|**[エンコード]**|.NET Framework でサポートされている文字エンコードの Internet Assigned Numbers Authority (IANA) 名。 既定値は **UTF-8**です。 他の値には、ASCII、UTF-7、UTF-16 などがあります。|  
  
## <a name="see-also"></a>参照  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [表示拡張機能にデバイス情報設定を渡す](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [RSReportServer.Config で表示拡張機能パラメーターをカスタマイズする](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [テクニカル リファレンス (SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  
