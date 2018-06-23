---
title: Server 要素 (DTA) |Microsoft ドキュメント
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
ms.assetid: 9fe0bfb4-3aa6-4eb2-a83e-c0d0e7d4e9f6
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 16bfbc4b45f8438ab5a4ab31cdce8183cb473e64
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177441"
---
# <a name="server-element-dta"></a>Server 要素 (DTA)
  チューニングするデータベースが置かれているサーバーの識別情報が含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
  
<DTAInput>  
    <Server>  
    ...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|1 回ごとに必要な`DTAInput`要素。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[DTAInput 要素&#40;DTA&#41;](dtainput-element-dta.md)|  
|**子要素**|[サーバーの名前を要素&#40;DTA&#41;](name-element-for-server-dta.md)<br /><br /> [Server の database 要素&#40;DTA&#41;](database-element-for-server-dta.md)|  
  
## <a name="remarks"></a>コメント  
 1 つだけ指定できます`Server`要素を`DTAInput`要素。 この要素は、DTA XML スキーマの **ServerDetailsTypecomplexType** の名前です。 これを混同しないでください`Server`要素の子である 1 つで、`Configuration`要素。 詳細については、「[Configuration のサーバー要素 &#40;DTA&#41;](server-element-for-configuration-dta.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例は、SERVER001 上の **AdventureWorks** データベースの **Sales.SalesPerson** テーブルを指定する方法を示しています:  
  
```xml  
<Server>  
  <Name>SERVER001</Name>  
  <Database>  
    <Name>AdventureWorks</Name>  
    <Schema>  
      <Name>Sales</Name>  
      <Table>  
        <Name>SalesPerson</Name>  
      </Table>  
    </Schema>  
  </Database>  
</Server  
```  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  