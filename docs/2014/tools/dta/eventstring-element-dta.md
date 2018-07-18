---
title: EventString 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- EventString element
ms.assetid: f76c37b4-2f6e-4274-8ee2-87e89d98e8a2
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: db55d1d2451ab8febf984deb9e5bcb6d4718353f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37291698"
---
# <a name="eventstring-element-dta"></a>EventString 要素 (DTA)
  [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ワークロードを XML 入力ファイルで直接指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Workload>  
    <EventString Weight="...">  
    ...code removed here...  
    </EventString>  
</Workload>  
```  
  
## <a name="element-attributes"></a>要素の属性  
  
|属性|説明|  
|---------------|-----------------|  
|`Weight`|任意。 対象のイベントに関するクエリの重み係数 (重要度の係数) を指定します。 使用して、`float`重みを指定するデータ型。 たとえば、`Weight`="100.01" のようにします。 `Weight` に指定できる最小値は「0」です。|  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|`string`、長さは制限されます。|  
|**既定値**|[なし] :|  
|**個数**|他の種類のワークロードが指定されていない場合は、1 回の出現が必要です。 指定する必要があります、 `EventString`、 `File`、または`Database`の子要素、`Workload`親が 1 つだけの型を使用できます。 たとえば、ワークロードを指定する場合、`EventString`要素を使用してワークロードは指定できません、`File`同じ XML 入力ファイル内の要素。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[Workload 要素&#40;DTA&#41;](workload-element-dta.md)|  
|**子要素**|[なし] :|  
  
## <a name="example"></a>例  
 この要素の使用例については、「[インライン ワークロードを使用した XML 入力ファイルのサンプル &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
