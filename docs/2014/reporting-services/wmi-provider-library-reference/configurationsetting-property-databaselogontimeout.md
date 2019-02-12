---
title: DatabaseLogonTimeout プロパティ (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonTimeout Property
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonTimeout property
ms.assetid: 4a65162c-33de-485e-8fd3-2bd6bff8bf8d
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: ef5793aa278d9d1a1b9a10f45a68dd5a97442f69
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56019133"
---
# <a name="databaselogontimeout-property-wmi-msreportserverconfigurationsetting"></a>DatabaseLogonTimeout プロパティ (WMI MSReportServer_ConfigurationSetting)
  レポート サーバー データベースへのログインを失敗と判断するまでの待機時間を秒数で指定します。 値 **0** は、待ち時間が無限であることを示します。 読み取り専用。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Dim DatabaseLogonTimeout As Int32  
```  
  
```csharp  
public Int32 DatabaseLogonTimeout;  
```  
  
## <a name="property-values"></a>プロパティ値  
 秒数を表す 32 ビット符号付き整数オブジェクト。  
  
## <a name="example-code"></a>コード例  
 [MSReportServer_ConfigurationSetting クラス](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  
