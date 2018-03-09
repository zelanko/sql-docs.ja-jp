---
title: "Recommendation 要素 (DTA) |Microsoft ドキュメント"
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
helpviewer_keywords: Recommendation element
ms.assetid: 679ea535-865a-4633-a4d3-5b3090515158
caps.latest.revision: "13"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: affac3964b25761341c5ac39e3987a107636fae1
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="recommendation-element-dta"></a>Recommendation 要素 (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]ユーザー指定の構成の一部である仮想インデックスについて説明します。  
  
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
|**個数**|省略可。 **Table** 要素につき 1 回使用できます。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[スキーマ &#40; DTA &#41; の table 要素](../../tools/dta/table-element-for-schema-dta.md)|  
|**子要素**|[Create 要素 &#40;DTA&#41;](../../tools/dta/create-element-dta.md)<br /><br /> **Drop** 要素。 詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](http://go.microsoft.com/fwlink/?linkid=43100)を参照してください。|  
  
## <a name="remarks"></a>解説  
 この要素は、データベース エンジン チューニング アドバイザー XML スキーマの **RecommendationTypecomplexType** の名前です。 仮想的な構成でのインデックスを指定するために使用します。 この **Recommendation** 要素を、パーティション分割を指定するための**RecommendationPType**や、ビューを指定するための**RecommendationViewType**という他の種類の要素と混同しないでください。 このような他の種類の **Recommendation** 要素の詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](http://go.microsoft.com/fwlink/?linkid=43100)を参照してください。  
  
## <a name="example"></a>例  
 この要素の使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
