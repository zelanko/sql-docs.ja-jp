---
title: Schema の Table 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Table element [DTA]
ms.assetid: a59e8319-05d1-47f3-af39-7d970ab8e7dc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 622b5a02f0b13e9cbf6a78977a07daea93a3f520
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85007580"
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
  
|属性|[説明]|  
|---------------|-----------------|  
|`NumberOfRows`|任意。 さまざまなサイズのテーブルのシミュレーションを行うための整数です。|  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特徴|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|**string**、1 ～ 255 文字。|  
|**既定値**|[なし] :|  
|**個数**|省略可能。 ワークロードに応じて任意の数のテーブルを指定できます。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[Database の Schema 要素 &#40;DTA&#41;](schema-element-for-database-dta.md)|  
|**子要素**|[Table の Name 要素 (DTA) &#40;DTA&#41;](name-element-for-table-dta.md)|  
  
## <a name="remarks"></a>解説  
 `Table` 要素を指定しない場合、データベース エンジン チューニング アドバイザーでは、指定されているデータベースのすべてのテーブルがチューニング対象と見なされます。  
  
## <a name="example"></a>例  
 使用例については、「[Server 要素 &#40;DTA&#41;](server-element-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
