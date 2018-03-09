---
title: "テーブル要素のスキーマ (DTA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: dta
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: Table element [DTA]
ms.assetid: a59e8319-05d1-47f3-af39-7d970ab8e7dc
caps.latest.revision: "13"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2fa7311680006fa5fc6ce51058dce05e6ed1f675
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="table-element-for-schema-dta"></a>Schema の Table 要素 (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]チューニングの対象テーブルを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Schema>  
...code removed here...  
    <Table>...</Table>  
```  
  
## <a name="element-attributes"></a>要素の属性  
  
|属性|Description|  
|---------------|-----------------|  
|**NumberOfRows**|省略可。 さまざまなサイズのテーブルのシミュレーションを行うための整数です。|  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|**string**、1 ～ 255 文字。|  
|**既定値**|[なし] :|  
|**個数**|省略可。 ワークロードに応じて任意の数のテーブルを指定できます。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[データベース &#40;DTA&#41; の schema 要素](../../tools/dta/schema-element-for-database-dta.md)|  
|**子要素**|[テーブル &#40;DTA&#41; の name 要素](../../tools/dta/name-element-for-table-dta.md)|  
  
## <a name="remarks"></a>解説  
 **Table** 要素を指定しない場合、データベース エンジン チューニング アドバイザーでは、指定されているデータベースのすべてのテーブルがチューニング対象と見なされます。  
  
## <a name="example"></a>例  
 使用例については、「[Server 要素 &#40;DTA&#41;](../../tools/dta/server-element-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
