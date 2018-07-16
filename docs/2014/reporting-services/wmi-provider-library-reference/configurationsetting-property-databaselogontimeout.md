---
title: DatabaseLogonTimeout プロパティ (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
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
caps.latest.revision: 37
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: b93c42c786707f11144b06e1da55569b05701fae
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37257898"
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
  
## <a name="requirements"></a>要件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  
