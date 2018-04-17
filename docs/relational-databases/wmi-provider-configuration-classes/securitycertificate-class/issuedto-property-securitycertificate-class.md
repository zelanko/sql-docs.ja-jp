---
title: IssuedTo プロパティ (SecurityCertificate クラス) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
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
- IssuedTo Property (SecurityCertificate Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- IssuedTo property
ms.assetid: 47a4fcc7-6e8c-4ea2-a68a-f2789151c25f
caps.latest.revision: 32
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c0ef41edfc650935320d871609bc9588b108d7bb
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="issuedto-property-securitycertificate-class"></a>IssuedTo プロパティ (SecurityCertificate クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  セキュリティ証明書の発行先のオブジェクトを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.IssuedTo [= value]  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 セキュリティ証明書を表す [SecurityCertificate クラス](../../../relational-databases/wmi-provider-configuration-classes/securitycertificate-class/securitycertificate-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 セキュリティ証明書の発行先のオブジェクトを指定する文字列値。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [サーバー ネットワーク プロトコルとネットワーク ライブラリの構成](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
