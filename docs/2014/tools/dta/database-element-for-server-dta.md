---
title: サーバー (DTA) の database 要素 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: 5cd9a87a-af4b-45f3-8c18-f7fd7e7d3064
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 34bd7e9b2437adedd9a65032d16a6093ea01f634
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075407"
---
# <a name="database-element-for-server-dta"></a>Server の Database 要素 (DTA)
  特定のサーバーにあるチューニング対象のデータベースを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[なし] :|  
|既定値|[なし] :|  
|個数|につき 1 つまたは複数回の出現が必要な`Server`要素。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|親要素|[サーバー要素&#40;DTA&#41;](server-element-dta.md)|  
|子要素|[データベースの要素の名前を付けます&#40;DTA&#41;](name-element-for-database-dta.md)<br /><br /> [Database の schema 要素&#40;DTA&#41;](schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a>コメント  
 この要素は、データベース エンジン チューニング アドバイザー XML スキーマの **DatabaseDetailsTypecomplexType** の名前です。 この `Database` 要素を、ルートの親要素が `Configuration` 要素である他の要素と混同しないでください。 詳細については、「[Configuration の Database 要素 &#40;DTA&#41;](database-element-for-configuration-dta.md)」を参照してください。  
  
## <a name="example"></a>例  
 使用例については、`Database`要素を参照してください[サーバー要素&#40;DTA&#41;](server-element-dta.md)です。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  