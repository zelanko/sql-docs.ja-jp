---
title: テーブル (DTA) の要素の名前を付けます |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Name element
ms.assetid: 422a755f-ee52-4863-b1aa-f4ef1b8fd0bb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 513a3751baa41293c6a8dd84ab03af5f3d5a3103
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48206322"
---
# <a name="name-element-for-table-dta"></a>Table の Name 要素 (DTA)
  チューニングのためのテーブル名を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Schema>  
    <Table>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|`string`、1 ～ 255 文字。|  
|**既定値**|[なし] :|  
|**個数**|必須。 ごとに 1 回`Table`要素。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[テーブル スキーマの要素&#40;DTA&#41;](table-element-for-schema-dta.md)|  
|**子要素**|[なし] :|  
  
## <a name="example"></a>例  
 使用例については、「[Server 要素 &#40;DTA&#41;](server-element-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
