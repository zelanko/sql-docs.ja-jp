---
title: 依存関係プロパティ (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- Dependencies Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Dependencies property
ms.assetid: 92d54b7e-de2f-4978-b601-0196e37cbb41
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: ec643ad360da9d953edf9d88640fc53ed212566c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48170542"
---
# <a name="dependencies-property-sqlservice-class"></a>Dependencies プロパティ (SqlService クラス)
  参照されたサービスに依存するサービスのリストを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.Dependencies [= value]  
```  
  
## <a name="parts"></a>要素  
 *object*  
 サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 参照されたサービスに依存するサービスのリストを格納する string[] 配列。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [開始とサービスの停止](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
