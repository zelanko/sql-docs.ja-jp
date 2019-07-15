---
title: テーブル要素をスキーマ (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Table element [DTA]
ms.assetid: a59e8319-05d1-47f3-af39-7d970ab8e7dc
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 12bcab75d2c208dd53bb4f4c77bc5a882f3b32b1
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733448"
---
# <a name="table-element-for-schema-dta"></a>Schema の Table 要素 (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
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
|**NumberOfRows**|省略可。 さまざまなサイズのテーブルのシミュレーションを行うための整数です。|  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|[説明]|  
|--------------------|-----------------|  
|**データ型と長さ**|**string**、1 ～ 255 文字。|  
|**既定値**|[なし] :|  
|**個数**|省略可。 ワークロードに応じて任意の数のテーブルを指定できます。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[Database の Schema 要素 &#40;DTA&#41;](../../tools/dta/schema-element-for-database-dta.md)|  
|**子要素**|[Table の Name 要素 (DTA) &#40;DTA&#41;](../../tools/dta/name-element-for-table-dta.md)|  
  
## <a name="remarks"></a>Remarks  
 **Table** 要素を指定しない場合、データベース エンジン チューニング アドバイザーでは、指定されているデータベースのすべてのテーブルがチューニング対象と見なされます。  
  
## <a name="example"></a>例  
 使用例については、「[Server 要素 &#40;DTA&#41;](../../tools/dta/server-element-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
