---
title: AcceptPause プロパティ (SqlService クラス) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
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
- AcceptPause Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
helpviewer_keywords:
- AcceptPause property
ms.assetid: 4339e903-35ee-4395-b005-ca58b3a24a84
caps.latest.revision: 34
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1acbeb71fadc423f9c34057ae50d759c25d6eb60
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="acceptpause-property-sqlservice-class"></a>AcceptPause プロパティ (SqlService クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  サービスを一時停止できるかどうかを指定するブール型のプロパティ値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.AcceptPause [= value]  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 サービスを表す [SqlService クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サービスを一時停止できるかどうかを指定するブール値。 サービスを一時停止できる場合は**true** 、サービスを一時停止できない場合は **false** です。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [開始して、サービスの停止](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
