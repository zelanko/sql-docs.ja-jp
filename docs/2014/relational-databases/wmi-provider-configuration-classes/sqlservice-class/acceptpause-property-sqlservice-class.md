---
title: AcceptPause プロパティ (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- AcceptPause Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- AcceptPause property
ms.assetid: 4339e903-35ee-4395-b005-ca58b3a24a84
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: a0efdc0cf758bf57ea46932e54ccbd7150713483
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48173132"
---
# <a name="acceptpause-property-sqlservice-class"></a>AcceptPause プロパティ (SqlService クラス)
  サービスを一時停止できるかどうかを指定するブール型のプロパティ値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.AcceptPause [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サービスを一時停止できるかどうかを指定するブール値。 サービスを一時停止できる場合は `true`、サービスを一時停止できない場合は `false` です。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [開始とサービスの停止](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
