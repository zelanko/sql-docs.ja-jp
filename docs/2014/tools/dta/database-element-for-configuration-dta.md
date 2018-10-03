---
title: 要素をデータベースの構成 (DTA) |Microsoft Docs
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
- Database element
ms.assetid: e91ba243-6cc9-457a-8f5a-134f3c71ae69
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1a3547d10f325e047174f7106267b480084e88df
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48062042"
---
# <a name="database-element-for-configuration-dta"></a>Configuration の Database 要素 (DTA)
  仮定の構成を評価するデータベース エンジン チューニング アドバイザーを対象のデータベースを指定します (で指定された、`Configuration`要素)。  
  
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
|**個数**|1 回の 1 つまたは複数必要な`Server`要素。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[Configuration の server 要素&#40;DTA&#41;](server-element-for-configuration-dta.md)|  
|**子要素**|[データベースの名前を要素&#40;DTA&#41;](name-element-for-database-dta.md)<br /><br /> [Database の schema 要素&#40;DTA&#41;](schema-element-for-database-dta.md)<br /><br /> [Recommendation 要素&#40;DTA&#41;](recommendation-element-dta.md)|  
  
## <a name="remarks"></a>Remarks  
 この要素は、データベース エンジン チューニング アドバイザー XML スキーマの **DatabaseTypecomplexType** の名前です。 この `Database` 要素を、ルートの親要素が `Server` 要素である (XML 入力ファイルの最上位に記述する) 同じ名前の要素と混同しないでください。 詳細については、「[Server の Database 要素 &#40;DTA&#41;](database-element-for-server-dta.md)」を参照してください。  
  
## <a name="example"></a>例  
 この使用例については`Database`要素を参照してください、[ユーザー指定の構成の XML 入力ファイルのサンプル&#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)します。  
  
## <a name="see-also"></a>関連項目  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
