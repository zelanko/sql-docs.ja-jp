---
title: ReencryptSecureInformation メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- ReencryptSecureInformation (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- ReencryptSecureInformation method
ms.assetid: 8a487497-c207-45b2-8c92-87c58cc68716
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: faf998f4d9d3cbd3c45de4c1a0b214ba1de2152e
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2019
ms.locfileid: "59941168"
---
# <a name="reencryptsecureinformation-method-wmi-msreportserverconfigurationsetting"></a>ReencryptSecureInformation メソッド (WMI MSReportServer_ConfigurationSetting)
  新しい暗号化キーを生成し、この新しいキーを使用してカタログ内のセキュリティで保護されたすべての情報を再度暗号化します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub ReencryptSecureInformation(ByRef HRESULT as Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void ReencryptSecureInformation (out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>パラメーター  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
 *ExtendedErrors[]*  
 [out] 呼び出しによって返されたその他のエラーを含む文字列の配列。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="remarks"></a>コメント  
 ReencryptSecureInformation メソッドを使用することによって、管理者は既存の暗号化キーを新しいキーと置き換えることができます。  
  
 このメソッドを呼び出すと、レポート サーバーが新しい暗号化キーを生成し、新しい暗号化キーを使用してすべての暗号化されたコンテンツを反復処理して再度暗号化します。  
  
 配信拡張機能は、セキュリティで保護された情報を配信設定構造に格納できます。 ReencryptSecureInformation を呼び出すと、レポート サーバーが各サブスクリプションと対応する拡張機能を読み込み、関連付けられた設定に格納された情報を再度暗号化します。  
  
 スケールアウト配置のコンピューターでこのメソッドを実行する場合は、スケールアウト配置の各コンピューターを再度初期化する必要があります。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](msreportserver-configurationsetting-members.md)  
  
  
