---
title: ErrorControl プロパティ (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ErrorControl Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ErrorControl property
ms.assetid: cbb1e0fa-5bfc-4b1b-a6ed-f7d5cfad4d73
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b666426cd7f1d7eb2395ec4a67f0b166564de17d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85733009"
---
# <a name="errorcontrol-property-sqlservice-class"></a>ErrorControl プロパティ (SqlService クラス)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  起動時にサービスを開始できなかった場合のエラーの重大度を取得または設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.ErrorControl [= value]  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 サービスを表す [SqlService クラス](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 起動時にサービスが失敗した場合にレポートされるエラーの重大度を指定する文字列値。 次の表に、それぞれの値を示します。  
  
 無視  
 ユーザーへの通知が行われません。  
  
 標準  
 ユーザーへの通知が行われます。  
  
 Severe  
 システムは最後の正しい構成で再起動されます。  
  
 重要  
 正しい構成でシステムの再起動が試行されます。  
  
 不明  
 重大度が不明です。  
  
## <a name="remarks"></a>Remarks  
 値は、失敗が発生した場合に、起動プログラムによって行われるアクションを示しています。 すべてのエラーは、コンピューター システムによって記録されます。  
  
## <a name="see-also"></a>関連項目  
 [サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
