---
title: DatabaseQueryTimeout プロパティ (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- DatabaseQueryTimeout Property
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- DatabaseQueryTimeout property
ms.assetid: 96faed97-9799-4bbf-a66f-fdd532d3eace
author: markingmyname
ms.author: maghan
ms.openlocfilehash: eb1d0b0ee7257b6526b93c672e0891b8dd349b19
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773000"
---
# <a name="configurationsetting-property---databasequerytimeout"></a>ConfigurationSetting プロパティ - DatabaseQueryTimeout
  レポート サーバーで、コマンドが失敗した、または処理時間が長すぎると見なされるまでの、経過秒数を指定します。 レポート サーバーは、レポートのデータ ソースではなく、SQL カタログに対するクエリの時間を計測しています。 読み取りと書き込みが可能です。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Dim DatabaseQueryTimeout As UInt32  
```  
  
```csharp  
public UInt32 DatabaseQueryTimeout;  
```  
  
## <a name="property-values"></a>プロパティ値  
 クエリを実行することが許されている秒数を表す 32 ビットの符号なし **integer** オブジェクト。  
  
## <a name="example-code"></a>コード例  
 [MSReportServer_ConfigurationSetting クラス](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
