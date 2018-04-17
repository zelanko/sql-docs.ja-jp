---
title: GetCurrentCertificate メソッド (SInstance クラス) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- GetCurrentCertificate Method (SInstance Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- GetCurrentCertificate method
ms.assetid: 9d2b72df-cb21-414a-abef-917f13d4de62
caps.latest.revision: 14
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 54cd64c269b7e3843af876f80f58400d13f54ea6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getcurrentcertificate-method-sinstance-class"></a>GetCurrentCertificate メソッド (SInstance クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  現在のセキュリティ証明書を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.GetCurrentCertificate(SHA)  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 [のインスタンス上のサーバー設定を表す](../../../relational-databases/wmi-provider-configuration-classes/sinstance-class/sinstance-class.md) SInstance クラス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|Description|  
|---------------|-----------------|  
|*SHA*|メソッドの完了後に現在のセキュリティ証明書を指定する文字列オブジェクトの値 (出力パラメーター)|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 **uint32** 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [サーバー ネットワーク プロトコルとネットワーク ライブラリの構成](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
