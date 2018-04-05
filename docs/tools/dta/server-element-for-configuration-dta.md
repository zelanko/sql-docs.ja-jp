---
title: Server 要素 (DTA) の構成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: dta
ms.reviewer: ''
ms.suite: sql
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
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4df65dc3db8f8c23aa0fd012ee834020839d1ce9
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="server-element-for-configuration-dta"></a>Configuration の Server 要素 (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]データベース エンジン チューニング アドバイザーを仮定の構成を評価するサーバーの識別情報が含まれています (によって指定された、**構成**要素)。  
  
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
|**個数**|必須。 **Configuration** 要素につき 1 個。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[Configuration 要素 &#40;DTA&#41;](../../tools/dta/configuration-element-dta.md)|  
|**子要素**|[サーバー &#40;DTA&#41; の name 要素](../../tools/dta/name-element-for-server-dta.md)<br /><br /> [構成 &#40;DTA&#41; の database 要素](../../tools/dta/database-element-for-configuration-dta.md)|  
  
## <a name="remarks"></a>解説  
 **Server** 要素は、 **Configuration** 要素に 1 個だけ指定できます。 この要素は、 **データベース エンジン チューニング アドバイザー XML スキーマ** の [ServerTypecomplexType](http://go.microsoft.com/fwlink/?linkid=43100)の名前です。 この **Server** 要素を **DTAInput** 要素の子要素と混同しないでください。 詳しくは、「[Server 要素 &#40;DTA&#41;](../../tools/dta/server-element-dta.md)」を参照してください。  
  
## <a name="example"></a>例  
 使用例については、「[ユーザー指定の構成を指定した XML 入力ファイルのサンプル &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
