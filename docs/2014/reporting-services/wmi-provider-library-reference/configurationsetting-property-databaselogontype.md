---
title: DatabaseLogonType プロパティ (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonType
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonType property
ms.assetid: 6b592582-4c35-4029-ab86-982fff47d8d6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cfe28e2cf9c47f3eebaddbcaa013ad492d715748
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2019
ms.locfileid: "59941028"
---
# <a name="databaselogontype-property-wmi-msreportserverconfigurationsetting"></a>DatabaseLogonType プロパティ (WMI MSReportServer_ConfigurationSetting)
  レポート サーバーが [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows サービス アカウント、Windows ユーザー アカウント、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのうちどれを使用してレポート サーバー データベースにアクセスするかを指定します。 読み取り専用。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Dim DatabaseLogonType As Integer  
```  
  
```csharp  
public int DatabaseLogonType;  
```  
  
## <a name="property-values"></a>プロパティ値  
 ログインの種類を表す `integer` オブジェクト。  
  
## <a name="example-code"></a>コード例  
 [MSReportServer_ConfigurationSetting クラス](msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>コメント  
 値は次のとおりです。  
  
-   Windows ログインの場合は 0  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインの場合は 1  
  
-   サービスとしてログインする場合は 2  
  
 0 (Windows) を指定する場合は、 [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) プロパティの値を、有効な Windows ユーザー アカウントに設定する必要があります。  
  
 1 (SQL Server) を指定する場合は、 [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) の値が有効な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインであることを確認してください。  
  
 2 (Windows サービス) を指定する場合、レポート サーバーは [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] アカウントと Windows サービス アカウントを使用してレポート サーバー データベースにアクセスします。 DatabaseLogonAccount プロパティは無視されます。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  
