---
title: SetNumericalValue メソッド (Sqlserviceadvanced Property クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetNumericalValue Method (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetNumericalValue method
ms.assetid: 950ed1e8-0538-4db4-807c-a2c36f43cf6b
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 07c54d34b3fa7c874142395e5113b90799dcbe6f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62911495"
---
# <a name="setnumericalvalue-method-sqlserviceadvancedproperty-class"></a>SetNumericalValue メソッド (SqlServiceAdvancedProperty クラス)
  プロパティの数値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.SetNumericalValue(  
NumValue  
)  
  
```  
  
## <a name="parts"></a>要素  
 *素材*  
 詳細プロパティを表す [SqlServiceAdvancedProperty クラス](sqlserviceadvancedproperty-class.md) オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|[説明]|  
|---------------|-----------------|  
|*NumValue*|詳細プロパティの値を指定する `uint32` 値|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 
  `uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
 プロパティを数値に設定するには、プロパティ値の型が数値型である必要があります。  
  
## <a name="see-also"></a>参照  
 [サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
