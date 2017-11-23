---
title: "AcceptStop プロパティ (SqlService クラス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: AcceptStop Property (SqlService Class)
apilocation: sqlmgmproviderxpsp2up.mof
helpviewer_keywords: AcceptStop property
ms.assetid: bf8ffe79-4f4c-4a2d-82e5-2ae8f5d466c5
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b23092b3e4e395f0dfc4e391808b295677648029
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="acceptstop-property-sqlservice-class"></a>AcceptStop プロパティ (SqlService クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]このサービスを停止するかどうかを指定するブール型プロパティ値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.AcceptStop [= value]  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 A [SqlService クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md)サービスを表すオブジェクト  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サービスを停止できるかどうかを示すブール値: **true**場合は、サービスを停止することができます、または**false**場合は、サービスを停止できません。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [開始して、サービスの停止](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
