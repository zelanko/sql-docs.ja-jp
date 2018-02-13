---
title: "SetCurrentCertificate メソッド (SecurityCertificate クラス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- SetCurrentCertificate Method (SecurityCertificate Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetCurrentCertificate method
ms.assetid: 04b1a76a-932d-4824-8506-e346afe7554e
caps.latest.revision: 
author: JennieHubbard
ms.author: jhubbard
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ec64ddeccafc4135a40dc2256451212e90799b92
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="setcurrentcertificate-method-securitycertificate-class"></a>SetCurrentCertificate メソッド (SecurityCertificate クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
現在のセキュリティ証明書を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetCurrentCertificate(SHA , SQLInstance)  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 セキュリティ証明書を表す [SecurityCertificate クラス](../../../relational-databases/wmi-provider-configuration-classes/securitycertificate-class/securitycertificate-class.md) オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|Description|  
|---------------|-----------------|  
|*SHA*|必要なセキュリティ証明書に対応する SHA (secure hash algorithm) サムプリントを指定する文字列値。|  
|*SQLInstance*|証明書を必要とするインスタンスを指定する文字列値|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 uint32 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [サーバー ネットワーク プロトコルとネットワーク ライブラリの構成](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
