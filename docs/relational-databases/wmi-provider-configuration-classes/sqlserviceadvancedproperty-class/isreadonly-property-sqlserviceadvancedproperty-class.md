---
title: IsReadOnly プロパティ (SqlServiceAdvancedProperty クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- IsReadOnly Property (SqlServiceAdvancedProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- IsReadOnly property
ms.assetid: 9672e70f-1d8c-4133-ac73-3b5733a1c4ee
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a916f98db163dfd9ff6a6de54af517f10212251d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68116651"
---
# <a name="isreadonly-property-sqlserviceadvancedproperty-class"></a>IsReadOnly プロパティ (SqlServiceAdvancedProperty クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  詳細プロパティが読み取り専用かどうかを指定するブール型のプロパティを取得または設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.IsReadOnly [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 詳細プロパティを表す [SqlServiceAdvancedProperty クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 詳細プロパティが読み取り専用かどうかを指定するブール値。詳細プロパティが読み取り専用の場合は **true** 、詳細プロパティが変更可能な場合は **false** です。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>関連項目  
 [開始とサービスの停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
