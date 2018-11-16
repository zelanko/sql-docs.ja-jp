---
title: AcceptStop プロパティ (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- AcceptStop Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
helpviewer_keywords:
- AcceptStop property
ms.assetid: bf8ffe79-4f4c-4a2d-82e5-2ae8f5d466c5
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 26889228181b16c7ea58560708766d048b939f0d
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51656691"
---
# <a name="acceptstop-property-sqlservice-class"></a>AcceptStop プロパティ (SqlService クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  サービスを停止できるかどうかを指定するブール型のプロパティの値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.AcceptStop [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 A [SqlService クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md)サービスを表すオブジェクト  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サービスを停止できるかどうかを指定するブール値: **true**サービスを停止する場合または**false**場合は、サービスを停止することはできません。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [開始とサービスの停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
