---
title: RemoveCertificate メソッド (ServerSettings クラス) |Microsoft ドキュメント
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
- RemoveCertificate Method (ServerSettings Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- RemoveCertificate method
ms.assetid: 9ffdbc39-93f5-48fb-859a-86a3ad545827
caps.latest.revision: 14
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c30982add92c19f7a213d0da76578d068344c61d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="removecertificate-method-serversettings-class"></a>RemoveCertificate メソッド (ServerSettings クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンスから現在のセキュリティ証明書を削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.RemoveCertificate()  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 [のインスタンス上のサーバー設定を表す](../../../relational-databases/wmi-provider-configuration-classes/serversettings-class/serversettings-class.md) ServerSettings クラス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 u**int32** 値。サービスが正常に変更された場合は 0、要求がサポートされない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [サーバー ネットワーク プロトコルとネットワーク ライブラリの構成](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
