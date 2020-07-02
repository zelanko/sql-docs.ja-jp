---
title: IsReadOnly プロパティ (Sqlserviceadvanced プロパティ)
ms.custom: seo-lt-2019
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
ms.openlocfilehash: 8f3423eafc722de30642e3c96ebb6e8a7ddb9476
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750033"
---
# <a name="isreadonly-property-sqlserviceadvancedproperty-class"></a>IsReadOnly プロパティ (SqlServiceAdvancedProperty クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  詳細プロパティが読み取り専用かどうかを指定するブール型のプロパティを取得または設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.IsReadOnly [= value]  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 詳細プロパティを表す [SqlServiceAdvancedProperty クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 詳細プロパティが読み取り専用かどうかを指定するブール値。詳細プロパティが読み取り専用の場合は **true** 、詳細プロパティが変更可能な場合は **false** です。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
