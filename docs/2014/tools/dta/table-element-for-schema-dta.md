---
title: テーブル要素をスキーマ (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Table element [DTA]
ms.assetid: a59e8319-05d1-47f3-af39-7d970ab8e7dc
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f58288d90c1a3158f4757856b51b7374ee07f167
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187759"
---
# <a name="table-element-for-schema-dta"></a>Schema の Table 要素 (DTA)
  チューニングの対象にするテーブルを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Schema>  
...code removed here...  
    <Table>...</Table>  
```  
  
## <a name="element-attributes"></a>要素の属性  
  
|属性|説明|  
|---------------|-----------------|  
|`NumberOfRows`|任意。 さまざまなサイズのテーブルのシミュレーションを行うための整数です。|  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|**string**、1 ～ 255 文字。|  
|**既定値**|[なし] :|  
|**個数**|任意。 ワークロードに応じて任意の数のテーブルを指定できます。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[Database の schema 要素&#40;DTA&#41;](schema-element-for-database-dta.md)|  
|**子要素**|[テーブルの名前を要素&#40;DTA&#41;](name-element-for-table-dta.md)|  
  
## <a name="remarks"></a>コメント  
 `Table` 要素を指定しない場合、データベース エンジン チューニング アドバイザーでは、指定されているデータベースのすべてのテーブルがチューニング対象と見なされます。  
  
## <a name="example"></a>例  
 使用例については、「[Server 要素 &#40;DTA&#41;](server-element-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
