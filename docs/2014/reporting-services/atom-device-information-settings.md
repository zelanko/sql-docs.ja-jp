---
title: ATOM デバイス情報設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fe4a56a4-5552-423c-85c1-895e2e212fee
caps.latest.revision: 7
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c4d0f85da3c3762d32b8a59a34e073e9f14736a9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37321883"
---
# <a name="atom-device-information-settings"></a>ATOM デバイス情報の設定
  ATOM 表示拡張機能のデバイス情報設定では、ATOM フィードの名前および使用する文字エンコードの送信がサポートされています。  
  
 次の表は、データ サービス ドキュメントに表示するためのデバイス情報設定を示しています。  
  
|設定|値|  
|-------------|-----------|  
|`DataFeed`|指定した場合、この設定で指定されたフィード名に対応する ATOM フィードが表示されます。 指定しない場合は、レポートの ATOM サービス ドキュメントが表示されます。 データ フィード固有の自動生成された識別子です。 これは内部で使用される値であり、変更はしないでください。|  
|**[エンコード]**|.NET Framework でサポートされている文字エンコードの Internet Assigned Numbers Authority (IANA) 名。 既定値は `UTF-8` です。 他の値には、ASCII、UTF-7、UTF-16 などがあります。|  
  
## <a name="see-also"></a>参照  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [表示拡張機能にデバイス情報設定を渡す](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [RSReportServer.Config で表示拡張機能パラメーターをカスタマイズする](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [テクニカル リファレンス (SSRS)](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
