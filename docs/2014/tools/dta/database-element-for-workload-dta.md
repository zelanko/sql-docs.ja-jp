---
title: 要素をデータベースのワークロード (DTA) |Microsoft Docs
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
ms.assetid: 112fca2a-37e5-4162-b2e7-b56eb8ab0c6f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f3f5f7d912a41476588662c4543b20c041b02672
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172142"
---
# <a name="database-element-for-workload-dta"></a>Workload の Database 要素 (DTA)
  ワークロード トレース テーブルのあるデータベースを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Workload>  
  <Database>  
   ...code removed here...  
  </Database>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|他の種類のワークロードが指定されていない場合は、1 回の出現が必要です。 指定する必要があります、 `EventString`、 `File`、または`Database`の子要素、`Workload`親が 1 つだけの型を使用できます。 たとえば、ワークロードを `Database` 要素で指定した場合、同じ XML 入力ファイル内でワークロードを `File` 要素で指定することはできません。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[Workload 要素&#40;DTA&#41;](workload-element-dta.md)|  
|**子要素**|[データベースの名前を要素&#40;DTA&#41;](name-element-for-database-dta.md)<br /><br /> [Database の schema 要素&#40;DTA&#41;](schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a>コメント  
 この要素は、データベース エンジン チューニング アドバイザー XML スキーマの **DatabaseDetailsTypecomplexType** の名前です。 この `Database` 要素を、ルートの親要素が `Configuration` 要素である他の要素と混同しないでください。 (「[Configuration の Database 要素 &#40;DTA&#41;](database-element-for-configuration-dta.md)」を参照)。  
  
## <a name="example"></a>例  
 この使用例については`Database`要素のコード例を参照してください。 [Workload 要素&#40;DTA&#41;](workload-element-dta.md)します。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
