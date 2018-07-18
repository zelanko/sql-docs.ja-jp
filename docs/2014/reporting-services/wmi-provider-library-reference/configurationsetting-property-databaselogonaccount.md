---
title: DatabaseLogonAccount プロパティ (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
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
- DatabaseLogonAccount
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonAccount property
ms.assetid: 55f2863f-1ac1-4519-b512-e7f11c0ea5ea
caps.latest.revision: 24
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6b94a45ed2c528972fffb79d2f8f51ad9bcba56d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185761"
---
# <a name="databaselogonaccount-property-wmi-msreportserverconfigurationsetting"></a>DatabaseLogonAccount プロパティ (WMI MSReportServer_ConfigurationSetting)
  レポート サーバーがレポート サーバー データベースへの接続に使用するログオン アカウントを指定します。 読み取り専用です。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Dim DatabaseLogonAccount As String  
```  
  
```csharp  
public string DatabaseLogonAccount;  
```  
  
## <a name="property-values"></a>プロパティ値  
 ログオン アカウント名を表す `String` オブジェクト。  
  
## <a name="example-code"></a>コード例  
 [MSReportServer_ConfigurationSetting クラス](msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>コメント  
 このプロパティの有効な値の値によって異なります、 [DatabaseLogonType](configurationsetting-property-databaselogontype.md)プロパティ。  
  
 場合、このプロパティは無視されます、 [DatabaseLogonType](configurationsetting-property-databaselogontype.md)プロパティに設定されて`2 (Service)`します。  
  
## <a name="requirements"></a>要件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  
