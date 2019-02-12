---
title: DatabaseQueryTimeout プロパティ (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseQueryTimeout Property
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseQueryTimeout property
ms.assetid: 96faed97-9799-4bbf-a66f-fdd532d3eace
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: cf21ba6211a016676ea7d1f2547bf4d96b1e6fb4
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56023764"
---
# <a name="databasequerytimeout-property-wmi-msreportserverconfigurationsetting"></a>DatabaseQueryTimeout プロパティ (WMI MSReportServer_ConfigurationSetting)
  レポート サーバーで、コマンドが失敗した、または処理時間が長すぎると見なされるまでの、経過秒数を指定します。 レポート サーバーは、レポートのデータ ソースではなく、SQL カタログに対するクエリの時間を計測しています。 読み取りと書き込みが可能です。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Dim DatabaseQueryTimeout As UInt32  
```  
  
```csharp  
public UInt32 DatabaseQueryTimeout;  
```  
  
## <a name="property-values"></a>プロパティ値  
 クエリを実行することが許されている秒数を表す 32 ビットの符号なし `integer` オブジェクト。  
  
## <a name="example-code"></a>コード例  
 [MSReportServer_ConfigurationSetting クラス](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  
