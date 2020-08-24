---
description: Indexes コレクション (ADOX)
title: Indexes コレクション (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Table::Indexes
- Indexes
helpviewer_keywords:
- Indexes collection [ADOX]
ms.assetid: 184cf536-455c-42be-bf1c-a5c25bade961
author: rothja
ms.author: jroth
ms.openlocfilehash: 0075ca8340d869f803a10d296672e03326c5bad6
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88770271"
---
# <a name="indexes-collection-adox"></a>Indexes コレクション (ADOX)
テーブルのすべての [Index](./index-object-adox.md) オブジェクトを格納します。  
  
## <a name="remarks"></a>解説  
 **Indexes**コレクションの[Append](./append-method-adox-indexes.md)メソッドは、ADOX で一意です。 次のようにすることができます。  
  
-   **追加**メソッドを使用して、新しいインデックスをコレクションに追加します。  
  
 その他のプロパティとメソッドは、ADO コレクションの標準です。 次のようにすることができます。  
  
-   [Item](../ado-api/item-property-ado.md)プロパティを使用して、コレクション内のインデックスにアクセスします。  
  
-   [Count](../ado-api/count-property-ado.md)プロパティを使用して、コレクションに格納されているインデックスの数を返します。  
  
-   [Delete](./delete-method-adox-collections.md)メソッドを使用して、コレクションからインデックスを削除します。  
  
-   [更新](../ado-api/refresh-method-ado.md)メソッドを使用して、現在のデータベーススキーマを反映するように、コレクション内のオブジェクトを更新します。  
  
 ここでは、次のトピックについて説明します。  
  
-   [Indexes コレクションのプロパティ、メソッド、およびイベント](./indexes-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Indexes Append メソッドの例 (VB)](./indexes-append-method-example-vb.md)   
 [Index オブジェクト (ADOX)](./index-object-adox.md)