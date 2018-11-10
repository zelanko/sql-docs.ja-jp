---
title: SetBoolValue メソッド (SqlServiceAdvancedProperty クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetBoolValue Method (SqlServiceAdvancedProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetBoolValue method
ms.assetid: 5252b439-fce5-446a-8e57-99e3054bee69
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 99a456da7b3f452c94ab01bd3fc08215152ee2f5
ms.sourcegitcommit: 6c9d35d03c1c349bc82b9ed0878041d976b703c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2018
ms.locfileid: "51216830"
---
# <a name="setboolvalue-method-sqlserviceadvancedproperty-class"></a>SetBoolValue メソッド (SqlServiceAdvancedProperty クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  プロパティのブール値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetBoolValue [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 詳細プロパティを表す [SqlServiceAdvancedProperty クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*BoolValue*|詳細プロパティの値を指定するブール値|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 **uint32** 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>コメント  
 プロパティをブール値に設定するには、プロパティ値の型がブール型である必要があります。  
  
## <a name="see-also"></a>参照  
 [開始とサービスの停止](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
