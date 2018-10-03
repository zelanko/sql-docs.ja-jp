---
title: SetStartMode メソッド (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- SetStartMode Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetStartMode method
ms.assetid: f6f198b4-f9a4-468c-8977-76462ef06e61
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d6513b7f6e8ef99d18d407617c998831d1a8024d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47644980"
---
# <a name="setstartmode-method-sqlservice-class"></a>SetStartMode メソッド (SqlService クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  サービス インスタンスの開始モードを変更します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.SetStartMode(StartMode)  
```  
  
## <a name="parts"></a>要素  
 *object*  
 サービスを表す [SqlService クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) オブジェクト。  
  
#### <a name="parameters"></a>パラメーター  
 *StartMode*  
 A **uint32**サービス インスタンスの開始モードを指定する値。  
  
 有効な値は次のとおりです。  
  
 値 = 0。 (Boot)。デバイス ドライバーがオペレーティング システム ローダーによって開始されます。 この値は、ドライバー サービスに対してのみ指定できます。  
  
 値 = 1 システムによって開始されるデバイス ドライバー、 **IoInitSystem**メソッド。 この値は、ドライバー サービスに対してのみ指定できます。  
  
 値 = 2。 (Automatic)。システムの起動時に、サービス コントロール マネージャーによってサービスが自動的に開始されます。  
  
 値 = 3 手動のプロセスを呼び出すとき、コンピューター マネージャーによって開始されるサービス、 **StartService**メソッド。  
  
 値 = 4 (Disabled)。サービスを開始できません。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 A **uint32**値は、サービスが正常に変更された場合は 0 または 1 の場合は、要求はサポートされていません。 それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [開始とサービスの停止](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
