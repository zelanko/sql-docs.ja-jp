---
title: SetCurrentCertificate メソッド (SecurityCertificate クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetCurrentCertificate Method (SecurityCertificate Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetCurrentCertificate method
ms.assetid: 04b1a76a-932d-4824-8506-e346afe7554e
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 32af70857eac43a99257444081c1bcbdc842a2e5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63270640"
---
# <a name="setcurrentcertificate-method-securitycertificate-class"></a>SetCurrentCertificate メソッド (SecurityCertificate クラス)
  現在のセキュリティ証明書を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.SetCurrentCertificate(  
SHA , SQLInstance  
)  
  
```  
  
## <a name="parts"></a>要素  
 *object*  
 セキュリティ証明書を表す [SecurityCertificate Class] securitycertificate-class.md) オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*SHA*|必要なセキュリティ証明書に対応する SHA (secure hash algorithm) サムプリントを指定する文字列値。|  
|*SQLInstance*|証明書を必要とするインスタンスを指定する文字列値|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 uint32 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>参照  
 [サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
