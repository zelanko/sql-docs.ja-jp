---
title: StartMode プロパティ (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- StartMode Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- StartMode property
ms.assetid: c0c2c7f8-d4ae-44f2-ad8e-aecfcb7c2878
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1986e21af8d9c6334d8ff9b5a374d46d6c25dda5
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85013680"
---
# <a name="startmode-property-sqlservice-class"></a>StartMode プロパティ (SqlService クラス)
  サービスの開始モードを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.StartMode [= value]  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サービスのモードを指定する uint32 値。  
  
 値には、次のいずれかを指定できます。  
  
 ブート  
 値 = 0。 オペレーティング システム ローダーによって開始されるサービスです。 このオプションは、ドライバー サービスにのみ有効です。  
  
 システム  
 値 = 1。 `IoInitSystem` メソッドによって開始されるサービスです。 このオプションは、ドライバー サービスにのみ有効です。  
  
 自動  
 値 = 2。 システムの起動時にサービス コントロール マネージャーによって自動的に開始されるサービスです。  
  
 マニュアル  
 値 = 3。 プロセスが `StartService` メソッドを呼び出すとコンピューター マネージャーによって開始されるサービスです。  
  
 無効  
 値 = 4。 サービスを開始できません。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>参照  
 [サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
