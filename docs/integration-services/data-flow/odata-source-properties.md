---
title: "OData ソースのプロパティ | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fde5bb0-6d78-4ec4-8f0b-67f91c53fe99
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0ff5a45fff7cc967f8fbec8d07926fe0c9fe3a83
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="odata-source-properties"></a>OData ソースのプロパティ
データ フローで **[OData ソース]** を右クリックし、**[プロパティ]** をクリックすると、 **[プロパティ]** ウィンドウに **[OData ソース]** コンポーネントのプロパティが表示されます。  

## <a name="properties"></a>[プロパティ] 
|プロパティ|Description|  
|-|-|  
|CollectionName|OData サービスから取得するコレクションの名前。 **[CollectionName]** プロパティは、 **UseResourcePath** が FALSE の場合に使用されます。<br /><br /> このプロパティは式にすることができ、実行時に値を設定することができます。 ただし、コレクションのメタデータが、デザイン時に存在したメタデータと一致しない場合は、検証エラーが発生し、データ フローの実行が失敗します。|  
|DefaultStringLength|この値は、最大の長さが設定されていない文字列の列に対して、既定の長さを指定します。<br /><br /> **既定値:** 4000|  
|Query|OData のクエリ パラメーター。 このプロパティは式にすることができ、実行時に設定することができます。|  
|ResourcePath|コレクション名のみを選択する代わりに、完全なリソース パスを指定する必要がある場合は、このプロパティを使用します。 このプロパティが使用されるのは、 **UseResourcePath** が True の場合のみです。|  
|UseResourcePath|True に設定されている場合は、OData のフィードの場所を決定するために、ベース URL に対して **ResourcePath** の値が追加されます。 FALSE に設定すると、 **CollectionName** の値が使用されます。<br /><br /> **既定値:** False|  
  
## <a name="see-also"></a>参照
[OData ソース](odata-source.md)
