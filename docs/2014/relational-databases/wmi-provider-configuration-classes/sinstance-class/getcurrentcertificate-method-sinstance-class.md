---
title: GetCurrentCertificate メソッド (SInstance クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- GetCurrentCertificate Method (SInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- GetCurrentCertificate method
ms.assetid: 9d2b72df-cb21-414a-abef-917f13d4de62
caps.latest.revision: 14
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 75b383d6e983f035b22a6b6949d0c640b17007fd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37270348"
---
# <a name="getcurrentcertificate-method-sinstance-class"></a>GetCurrentCertificate メソッド (SInstance クラス)
  現在のセキュリティ証明書を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.GetCurrentCertificate(  
SHA  
)  
  
```  
  
## <a name="parts"></a>要素  
 *object*  
 [のインスタンス上のサーバー設定を表す](sinstance-class.md) SInstance クラス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*SHA*|メソッドの完了後に現在のセキュリティ証明書を指定する文字列オブジェクトの値 (出力パラメーター)|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 `uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [サーバー ネットワーク プロトコルとネットワーク ライブラリの構成](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
