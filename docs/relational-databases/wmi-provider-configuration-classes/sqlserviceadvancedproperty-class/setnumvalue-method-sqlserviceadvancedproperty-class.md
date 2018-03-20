---
title: "SetNumValue メソッド (SqlServiceAdvancedProperty クラス) |Microsoft ドキュメント"
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
- SetNumValue Method (SqlServiceAdvancedProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetNumValue method
ms.assetid: a5e1056b-0b75-4ad6-99c1-89246010d815
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 504d1ca8ca0c49c188b70bf51cd79ac0c7fb2dfa
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="setnumvalue-method-sqlserviceadvancedproperty-class"></a>SetNumValue メソッド (SqlServiceAdvancedProperty クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  プロパティの数値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetNumValue(NumValue)  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 詳細プロパティを表す [SqlServiceAdvancedProperty クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|Description|  
|---------------|-----------------|  
|*NumValue*|詳細プロパティの値を指定する **uint32** 値|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 **uint32** 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
 プロパティを数値に設定するには、プロパティ値の型が数値型である必要があります。  
  
## <a name="see-also"></a>参照  
 [開始して、サービスの停止](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
