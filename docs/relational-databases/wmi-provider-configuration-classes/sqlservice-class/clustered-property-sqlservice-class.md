---
title: Clustered プロパティ (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- Clustered Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
helpviewer_keywords:
- Clustered property
ms.assetid: f714e7f5-c2db-45c6-9536-6ca2cb5b42aa
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5052595dc30d0cb0959728f36f3e96acf96ab97d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67929911"
---
# <a name="clustered-property-sqlservice-class"></a>Clustered プロパティ (SqlService クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  サービスがクラスター化インスタンスの一部であるかどうかを指定するブール型のプロパティ値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.Clustered [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 サービスを表す [SqlService クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サービスがクラスター化インスタンスに参加しているかどうかを指定するブール値です。サービスがクラスター化インスタンスに参加している場合は **true** 、サービスがクラスター化インスタンスに参加していない場合は **false** です。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>関連項目  
 [開始とサービスの停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
