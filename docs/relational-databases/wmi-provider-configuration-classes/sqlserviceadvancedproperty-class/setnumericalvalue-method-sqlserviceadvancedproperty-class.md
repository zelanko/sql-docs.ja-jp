---
title: SetNumericalValue メソッド (Sqlserviceadvanced プロパティ)
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetNumericalValue Method (SqlServiceAdvancedProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetNumericalValue method
ms.assetid: 950ed1e8-0538-4db4-807c-a2c36f43cf6b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ff97153595698a12a3ee95922e31a83a0cf5ee17
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85736572"
---
# <a name="setnumericalvalue-method-sqlserviceadvancedproperty-class"></a>SetNumericalValue メソッド (SqlServiceAdvancedProperty クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  プロパティの数値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetNumericalValue(NumValue)  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 詳細プロパティを表す [SqlServiceAdvancedProperty クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*NumValue*|詳細プロパティの値を指定する **uint32** 値|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 **uint32** 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>Remarks  
 プロパティを数値に設定するには、プロパティ値の型が数値型である必要があります。  
  
## <a name="see-also"></a>関連項目  
 [サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
