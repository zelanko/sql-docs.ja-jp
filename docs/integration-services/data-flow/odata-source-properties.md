---
title: OData ソースのプロパティ | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4fde5bb0-6d78-4ec4-8f0b-67f91c53fe99
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fe4a3c3d1375095a4766186e1b854ea038b54ac9
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86920794"
---
# <a name="odata-source-properties"></a>OData ソースのプロパティ

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


データ フローで **[OData ソース]** を右クリックし、 **[プロパティ]** をクリックすると、 **[プロパティ]** ウィンドウに **[OData ソース]** コンポーネントのプロパティが表示されます。  

## <a name="properties"></a>Properties 

|プロパティ|説明|  
|-|-|  
|CollectionName|OData サービスから取得するコレクションの名前。 **[CollectionName]** プロパティは、 **UseResourcePath** が FALSE の場合に使用されます。<br /><br /> このプロパティは式にすることができ、実行時に値を設定することができます。 ただし、コレクションのメタデータが、デザイン時に存在したメタデータと一致しない場合は、検証エラーが発生し、データ フローの実行が失敗します。|  
|DefaultStringLength|この値は、最大の長さが設定されていない文字列の列に対して、既定の長さを指定します。<br /><br /> **既定値:** 4000|  
|クエリ|OData のクエリ パラメーター。 このプロパティは式にすることができ、実行時に設定することができます。|  
|ResourcePath|コレクション名のみを選択する代わりに、完全なリソース パスを指定する必要がある場合は、このプロパティを使用します。 このプロパティが使用されるのは、 **UseResourcePath** が True の場合のみです。|  
|UseResourcePath|True に設定されている場合は、OData のフィードの場所を決定するために、ベース URL に対して **ResourcePath** の値が追加されます。 FALSE に設定すると、 **CollectionName** の値が使用されます。<br /><br /> **既定値:** False|  
  
## <a name="see-also"></a>参照
[OData ソース](odata-source.md)
