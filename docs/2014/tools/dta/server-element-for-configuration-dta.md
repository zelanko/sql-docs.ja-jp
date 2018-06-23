---
title: Server 要素 (DTA) の構成 |Microsoft ドキュメント
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
- Server element
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 131885c5e9547767dece2240bcbd64c06b5e4a61
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070883"
---
# <a name="server-element-for-configuration-dta"></a>Configuration の Server 要素 (DTA)
  データベース エンジン チューニング アドバイザーを仮定の構成を評価するサーバーの識別情報が含まれています (によって指定された、`Configuration`要素)。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Configuration>  
    <Server>  
...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|1 回ごとに必要な`Configuration`要素。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[構成要素&#40;DTA&#41;](configuration-element-dta.md)|  
|**子要素**|[サーバーの名前を要素&#40;DTA&#41;](name-element-for-server-dta.md)<br /><br /> [Configuration の database 要素&#40;DTA&#41;](database-element-for-configuration-dta.md)|  
  
## <a name="remarks"></a>コメント  
 1 つだけ指定できます`Server`要素を`Configuration`要素。 この要素は、 **データベース エンジン チューニング アドバイザー XML スキーマ** の [ServerTypecomplexType](http://go.microsoft.com/fwlink/?linkid=43100)の名前です。 これを混同しないでください`Server`要素の子である 1 つで、`DTAInput`要素。 詳しくは、「[Server 要素 &#40;DTA&#41;](server-element-dta.md)」を参照してください。  
  
## <a name="example"></a>例  
 使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  