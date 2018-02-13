---
title: "ErrorControl プロパティ (SqlService クラス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
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
- ErrorControl Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ErrorControl property
ms.assetid: cbb1e0fa-5bfc-4b1b-a6ed-f7d5cfad4d73
caps.latest.revision: 
author: JennieHubbard
ms.author: jhubbard
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2e0ad1c02cf0444431c583f3f7d06016fd9502c8
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="errorcontrol-property-sqlservice-class"></a>ErrorControl プロパティ (SqlService クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
起動時にサービスを開始できなかった場合のエラーの重大度を取得または設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.ErrorControl [= value]  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 サービスを表す [SqlService クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 起動時にサービスが失敗した場合にレポートされるエラーの重大度を指定する文字列値。 次の表は、使用可能な値を示します。  
  
 Ignore  
 ユーザーへの通知が行われません。  
  
 標準  
 ユーザーへの通知が行われます。  
  
 Severe  
 システムは最後の正しい構成で再起動されます。  
  
 重大  
 正しい構成でシステムの再起動が試行されます。  
  
 Unknown  
 重大度が不明です。  
  
## <a name="remarks"></a>解説  
 値は、失敗が発生した場合に、起動プログラムによって行われるアクションを示しています。 すべてのエラーは、コンピューター システムによって記録されます。  
  
## <a name="see-also"></a>参照  
 [開始して、サービスの停止](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
