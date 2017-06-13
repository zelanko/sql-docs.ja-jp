---
title: "ReserveURL メソッド (WMI MSReportServer_ConfigurationSetting) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ReservedURL method
ms.assetid: b9008a62-3edd-4f8a-99f2-7598c2133899
caps.latest.revision: 14
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 01bfda1933bc12672c4959eafd7c95ef9a389139
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="configurationsetting-method---reserveurl"></a>ReserveURL ConfigurationSetting メソッド
  指定したアプリケーションの URL 予約を追加します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub ReserveURL(Application as String, _  
    UrlString as String, Lcid as Int32, _   
    ByRef [Error] as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ReserveURL(string Application, string UrlString, int Lcid,   
    out string error, out int HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *アプリケーション*  
 URL の予約対象となるアプリケーションの名前。  
  
 *URLString*  
 予約する URL。  
  
 *lcid*  
 返されるエラー メッセージに使用するロケール。  
  
 *[エラー]*  
 [out] 発生したエラーの説明。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値が 0 の場合はメソッド呼び出しが正常に完了したことを示します。エラー コードの場合は呼び出しが失敗したことを示します。  
  
## <a name="remarks"></a>解説  
 *UrlString* には仮想ディレクトリ名は含まれません。 仮想ディレクトリ名の設定用に、 [SetVirtualDirectory](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setvirtualdirectory.md) メソッドが用意されています。  
  
 現在の Windows サービス アカウントに対して URL 予約が作成されます。 Windows サービス アカウントを変更するには、すべての URL 予約を手動で更新する必要があります。  
  
 このメソッドを実行すると、すべてのアプリケーション ドメインで強制力の高いリサイクル処理が実行されます。 この処理が完了した後に、アプリケーション ドメインが再起動されます。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
