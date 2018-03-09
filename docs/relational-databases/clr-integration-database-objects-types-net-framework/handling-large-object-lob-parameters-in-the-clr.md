---
title: "CLR でラージ オブジェクト (LOB) パラメーターの処理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- large data, CLR integration
- LOB data [SQL Server], CLR integration
- SqlBytes data type
- SqlChars data type
ms.assetid: d07956f6-9543-4476-9426-536f95991150
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4c9692632501eec31e517fb1bade2b3810c18c2b
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="handling-large-object-lob-parameters-in-the-clr"></a>CLR での LOB (ラージ オブジェクト) パラメーターの処理
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
使用して**SqlBytes**と**SqlChars**ラージ オブジェクト (LOB) のバイナリ型を渡したり (**varbinary (max)**) と LOB 文字型 (**nvarchar (max)**)パラメーターでは、それぞれします。 これらの型を使用すると、マネージ領域に LOB 値全体をコピーするのではなく、データベースから CLR (共通言語ランタイム) ルーチンに LOB 値をストリーミングできます。 **SqlBinary**と**SqlString**小さなバイナリおよび文字列の値のみ使用する必要があります。  
  
## <a name="see-also"></a>参照  
 [.NET Framework での SQL Server データ型](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
