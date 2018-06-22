---
title: 構成 (DTA) の database 要素 |Microsoft ドキュメント
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
ms.assetid: e91ba243-6cc9-457a-8f5a-134f3c71ae69
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 6afd8b418cd00c2ec89430e4c82613ea1af285d6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073358"
---
# <a name="database-element-for-configuration-dta"></a>Configuration の Database 要素 (DTA)
  仮定の構成を評価する、データベース エンジン チューニング アドバイザーの対象となるデータベースを指定します (によって指定された、`Configuration`要素)。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|につき 1 つまたは複数回の出現が必要な`Server`要素。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[Configuration の server 要素&#40;DTA&#41;](server-element-for-configuration-dta.md)|  
|**子要素**|[データベースの要素の名前を付けます&#40;DTA&#41;](name-element-for-database-dta.md)<br /><br /> [Database の schema 要素&#40;DTA&#41;](schema-element-for-database-dta.md)<br /><br /> [Recommendation 要素&#40;DTA&#41;](recommendation-element-dta.md)|  
  
## <a name="remarks"></a>コメント  
 この要素は、データベース エンジン チューニング アドバイザー XML スキーマの **DatabaseTypecomplexType** の名前です。 この `Database` 要素を、ルートの親要素が `Server` 要素である (XML 入力ファイルの最上位に記述する) 同じ名前の要素と混同しないでください。 詳細については、「[Server の Database 要素 &#40;DTA&#41;](database-element-for-server-dta.md)」を参照してください。  
  
## <a name="example"></a>例  
 この使用例については`Database`要素を参照してください、[ユーザー指定の構成を XML 入力ファイルのサンプル&#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)です。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  