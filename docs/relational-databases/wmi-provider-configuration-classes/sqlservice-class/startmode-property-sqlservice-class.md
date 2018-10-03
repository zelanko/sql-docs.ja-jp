---
title: StartMode プロパティ (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- StartMode Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- StartMode property
ms.assetid: c0c2c7f8-d4ae-44f2-ad8e-aecfcb7c2878
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 6e8e6fd01db9c390588bbd1d521411c1467a46ee
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47809220"
---
# <a name="startmode-property-sqlservice-class"></a>StartMode プロパティ (SqlService クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  サービスの開始モードを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.StartMode [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 サービスを表す [SqlService クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サービスのモードを指定する uint32 値。  
  
 値は、次のいずれかを指定できます。  
  
 Boot  
 値 = 0。 オペレーティング システム ローダーによって開始されるサービスです。 このオプションは、ドライバー サービスにのみ有効です。  
  
 システム  
 値 = 1 サービスを開始して、 **IoInitSystem**メソッド。 このオプションは、ドライバー サービスにのみ有効です。  
  
 自動  
 値 = 2。 システムの起動時にサービス コントロール マネージャーによって自動的に開始されるサービスです。  
  
 手動  
 値 = 3 プロセスを呼び出すとき、コンピューター マネージャーによって開始されるサービス、 **StartService**メソッド。  
  
 Disabled  
 値 = 4 サービスを開始できません。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [開始とサービスの停止](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
