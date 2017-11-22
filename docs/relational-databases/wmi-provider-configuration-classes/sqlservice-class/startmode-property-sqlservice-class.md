---
title: "StartMode プロパティ (SqlService クラス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: StartMode Property (SqlService Class)
apilocation: sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords: StartMode property
ms.assetid: c0c2c7f8-d4ae-44f2-ad8e-aecfcb7c2878
caps.latest.revision: "36"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f2c999c38e41ccb370a1edfa182f987a90935709
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="startmode-property-sqlservice-class"></a>StartMode プロパティ (SqlService クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]サービスの開始モードを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.StartMode [= value]  
```  
  
## <a name="parts"></a>要素  
 *オブジェクト*  
 サービスを表す [SqlService クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サービスのモードを指定する uint32 値。  
  
 値は、次のいずれかを指定できます。  
  
 Boot  
 値 = 0。 オペレーティング システム ローダーによって開始されるサービスです。 このオプションは、ドライバー サービスにのみ有効です。  
  
 システム  
 値 = 1 サービスによって開始、 **IoInitSystem**メソッドです。 このオプションは、ドライバー サービスにのみ有効です。  
  
 自動  
 値 = 2。 システムの起動時にサービス コントロール マネージャーによって自動的に開始されるサービスです。  
  
 手動  
 値 = 3 サービス プロセスを呼び出すときに、コンピューター マネージャーによってが開始されて、 **StartService**メソッドです。  
  
 Disabled  
 値 = 4 サービスを開始できません。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [開始して、サービスの停止](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
