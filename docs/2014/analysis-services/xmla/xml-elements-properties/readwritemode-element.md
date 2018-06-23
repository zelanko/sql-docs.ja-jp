---
title: ReadWriteMode 要素 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ReadWriteMode command
ms.assetid: 379bcaca-bb7e-4934-a9e7-21f8ede2fdc7
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 88ebc7e23fc3ec4aad0d8273464636354958217a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179185"
---
# <a name="readwritemode-element"></a>ReadWriteMode 要素
  `ReadWriteMode` データベース プロパティは、データベースが `ReadWrite` モードと `ReadOnly` モードのどちらであるかを指定します。 このプロパティの使用可能な値は 2 つだけです。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Database>  
...  
   <ddlns_100_0:ReadWriteMode>...</ddlns_100_0:ReadWriteMode>  
...  
</Database>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|ReadWrite|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[データベース]](database-element-xmla.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 データベースは `ReadWrite` モードのみで作成されます。 `ReadOnly` モードでは作成できません。  
  
 `ReadWriteMode` 要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*ReadOnly*|変更または更新をデータベースに適用できません。|  
|*読み取り/書き込み*|変更または更新をデータベースに適用できます。|  
  
## <a name="see-also"></a>参照  
 [Attach 要素](../xml-elements-commands/attach-element.md)   
 [アタッチし、Analysis Services データベースのデタッチ](../../multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Analysis Services データベースを移動します。](../../multidimensional-models/move-an-analysis-services-database.md)   
 [データベースの Readwritemode](../../multidimensional-models/database-readwritemodes.md)   
 [Analysis Services データベースの ReadOnly モードと ReadWrite モードの切り替え](../../multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  