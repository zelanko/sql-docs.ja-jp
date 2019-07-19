---
title: State プロパティ (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- State Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- State property
ms.assetid: 9e09f419-947c-4d4b-9a49-2d3396c847cd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 06193b774484afd6e6f7f47f286498c0698ab7c9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68094732"
---
# <a name="state-property-sqlservice-class"></a>State プロパティ (SqlService クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  サービスの現在の状態を取得または設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.State [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 サービスを表す [SqlService クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 サービスの状態を指定する uint32 値。  
  
 値は、次のいずれかを指定できます。  
  
 1  
 停止中。 サービスが停止します。  
  
 2  
 開始保留中。 サービスは開始を待機しています。  
  
 3  
 停止保留中。 サービスは停止を待機しています。  
  
 4  
 実行中です。 サービスは実行中です。  
  
 5  
 継続保留中。 サービスは継続を待機しています。  
  
 6  
 一時停止保留中。 サービスは一時停止を待機しています。  
  
 7  
 一時停止。 サービスは一時停止しています。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>関連項目  
 [開始とサービスの停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
