---
title: "OData ソースのプロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fde5bb0-6d78-4ec4-8f0b-67f91c53fe99
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b4f3283de9e26ce05849a34c8906a3095c229680
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="odata-source-properties"></a>OData ソースのプロパティ
  データ フローで **[OData ソース]** を右クリックし、 **[プロパティ]**をクリックすると、 **[プロパティ]** ウィンドウに **[OData ソース]** コンポーネントに対応するプロパティが表示されます。  
  
|||  
|-|-|  
|プロパティ|Description|  
|CollectionName|OData サービスから取得するコレクションの名前。 **[CollectionName]** プロパティは、 **UseResourcePath** が FALSE の場合に使用されます。<br /><br /> このプロパティは式にすることができ、その結果、実行時に値を設定することができます。 ただし、コレクションのメタデータが、デザイン時に使用したメタデータと一致しない場合は、検証エラーが発生し、データ フローの実行が失敗します。|  
|DefaultStringLength|この値は、最大の長さが設定されていない文字列の列に対して、既定の長さを指定します。<br /><br /> **既定値:** 4000|  
|Query|OData のクエリ パラメーター。 このプロパティは式にすることができ、その結果、実行時に設定することができます。|  
|ResourcePath|コレクション名のみを選択する代わりに、完全なリソース パスを指定する必要がある場合は、このプロパティを使用します。 このプロパティが使用されるのは、 **UseResourcePath** が True の場合のみです。|  
|UseResourcePath|True に設定されている場合は、OData のフィードの場所を決定するために、ベース URL に対して **ResourcePath** の値が追加されます。 FALSE に設定すると、 **CollectionName** の値が使用されます。<br /><br /> **既定値:** False|  
  
  
