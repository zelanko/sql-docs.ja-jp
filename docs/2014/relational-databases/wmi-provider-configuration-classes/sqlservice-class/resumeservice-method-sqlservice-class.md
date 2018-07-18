---
title: ResumeService メソッド (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ResumeService Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ResumeService method
ms.assetid: 0b0a5f08-b95e-4626-bf81-309da7a0aacd
caps.latest.revision: 34
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 0cf92d7c4342cba1dd601e5e927c93e78aae6784
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37319754"
---
# <a name="resumeservice-method-sqlservice-class"></a>ResumeService メソッド (SqlService クラス)
  サービスを再開状態にする動作を試行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.ResumeService()  
  
```  
  
## <a name="parts"></a>要素  
 *object*  
 サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 uint32 値。`ResumeService` 要求が正常に受け入れられた場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="see-also"></a>参照  
 [開始とサービスの停止](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
