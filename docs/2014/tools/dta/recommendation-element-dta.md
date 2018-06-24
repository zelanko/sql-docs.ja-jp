---
title: Recommendation 要素 (DTA) |Microsoft ドキュメント
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
- Recommendation element
ms.assetid: 679ea535-865a-4633-a4d3-5b3090515158
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 58535397a152ff1198cbb4cf713a6d0ec04a7eed
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074980"
---
# <a name="recommendation-element-dta"></a>Recommendation 要素 (DTA)
  ユーザー指定の構成の一部である仮想インデックスについての情報が含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Configuration>  
    ...code removed here...  
    <Table>  
      <Name>...</Name>  
      <Recommendation>  
      ...code removed here...  
      </Recommendation>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|任意。 ごとに 1 回使用できます`Table`要素。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[スキーマの要素をテーブル&#40;DTA&#41;](table-element-for-schema-dta.md)|  
|**子要素**|[要素を作成する&#40;DTA&#41;](create-element-dta.md)<br /><br /> `Drop` 要素。 詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](http://go.microsoft.com/fwlink/?linkid=43100)を参照してください。|  
  
## <a name="remarks"></a>コメント  
 この要素は、データベース エンジン チューニング アドバイザー XML スキーマの **RecommendationTypecomplexType** の名前です。 仮想的な構成でのインデックスを指定するために使用します。 これを混同しないでください`Recommendation`パーティション分割を指定するために使用する他の種類を持つ要素 (`RecommendationPType`) またはビュー (`RecommendationViewType`)。 これら他の方法について`Recommendation`要素型を参照してください、[データベース エンジン チューニング アドバイザーの XML スキーマ](http://go.microsoft.com/fwlink/?linkid=43100)です。  
  
## <a name="example"></a>例  
 この要素の使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  