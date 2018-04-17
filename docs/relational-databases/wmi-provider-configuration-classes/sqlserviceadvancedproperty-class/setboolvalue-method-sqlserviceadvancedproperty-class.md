---
title: SetBoolValue メソッド (SqlServiceAdvancedProperty クラス) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
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
- SetBoolValue Method (SqlServiceAdvancedProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetBoolValue method
ms.assetid: 5252b439-fce5-446a-8e57-99e3054bee69
caps.latest.revision: 33
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4d0a27a480a78b0c5da5ab52ca2d0ee1f6d363ad
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="setboolvalue-method-sqlserviceadvancedproperty-class"></a>SetBoolValue メソッド (SqlServiceAdvancedProperty クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  プロパティのブール値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetBoolValue [= value]  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 詳細プロパティを表す [SqlServiceAdvancedProperty クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*BoolValue*|詳細プロパティの値を指定するブール値|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 **uint32** 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
 プロパティをブール値に設定するには、プロパティ値の型がブール型である必要があります。  
  
## <a name="see-also"></a>参照  
 [開始して、サービスの停止](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
