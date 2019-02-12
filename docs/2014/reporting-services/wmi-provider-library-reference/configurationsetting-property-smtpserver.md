---
title: SMTPServer プロパティ (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- SMTPServer
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SMTPServer property
ms.assetid: 8bcceeba-e1a0-44ef-bda1-600c6925e1db
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 1e2309050495316946693adc84a97315f0b597a7
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56034793"
---
# <a name="smtpserver-property-wmi-msreportserverconfigurationsetting"></a>SMTPServer プロパティ (WMI MSReportServer_ConfigurationSetting)
  レポート サーバー構成ファイルから SMTP サーバー プロパティを取得します。 読み取り専用です。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Dim SMTPServer As String  
```  
  
```csharp  
public string SMTPServer;  
```  
  
## <a name="property-values"></a>プロパティ値  
 RSReportServer.config ファイルから取得した `String` プロパティ値を含む、読み取り専用の `SMTPServer` オブジェクト。  
  
## <a name="example-code"></a>コード例  
 [MSReportServer_ConfigurationSetting クラス](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  
