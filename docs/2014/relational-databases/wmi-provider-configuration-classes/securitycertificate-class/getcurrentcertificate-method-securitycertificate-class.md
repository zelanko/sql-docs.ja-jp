---
title: GetCurrentCertificate メソッド (SecurityCertificate クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- GetCurrentCertificate Method (SecurityCertificate Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- GetCurrentCertificate method
ms.assetid: 987a2671-1801-45c4-93e6-29f883c58720
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4b79e57afac4509401acc69892eb1665ec73bf84
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85060036"
---
# <a name="getcurrentcertificate-method-securitycertificate-class"></a>GetCurrentCertificate メソッド (SecurityCertificate クラス)
  現在のセキュリティ証明書を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.GetCurrentCertificate(  
SHA , SQLInstance  
)  
  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 セキュリティ証明書を表す [SecurityCertificate クラス](securitycertificate-class.md) オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*SHA*|メソッドの完了後に現在のセキュリティ証明書 SHA サムプリントを指定する文字列値 (出力パラメーター)|  
|*SQLInstance*|証明書を必要とするインスタンスを指定する文字列値|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 `uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>参照  
 [サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
