---
description: Views コレクション (ADOX)
title: Views コレクション (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Catalog::Views
- Views
helpviewer_keywords:
- Views collection [ADOX]
ms.assetid: a55d380c-2b7b-4b57-af74-8ba0b3de0db9
author: rothja
ms.author: jroth
ms.openlocfilehash: a024f21e83a25a82a226428835215a8cba9e21e9
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88768921"
---
# <a name="views-collection-adox"></a>Views コレクション (ADOX)
カタログのすべての [ビュー](./view-object-adox.md) オブジェクトが含まれます。  
  
## <a name="remarks"></a>コメント  
 **Views**コレクションの[Append](./append-method-adox-views.md)メソッドは、ADOX で一意です。 次のようにすることができます。  
  
-   新しいビューをコレクションに追加するには、 **Append** メソッドを使用します。  
  
 その他のプロパティとメソッドは、ADO コレクションの標準です。 次のようにすることができます。  
  
-   [項目](../ado-api/item-property-ado.md)プロパティを使用して、コレクション内のビューにアクセスします。  
  
-   [Count](../ado-api/count-property-ado.md)プロパティを使用して、コレクションに含まれているビューの数を返します。  
  
-   [Delete](./delete-method-adox-collections.md)メソッドを使用して、コレクションからビューを削除します。  
  
-   [更新](../ado-api/refresh-method-ado.md)メソッドを使用して、現在のデータベーススキーマを反映するように、コレクション内のオブジェクトを更新します。  
  
 ここでは、次のトピックについて説明します。  
  
-   [Views コレクションのプロパティ、メソッド、およびイベント](./views-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Views および Fields コレクションの例 (VB)](./views-and-fields-collections-example-vb.md)   
 [Views Append メソッドの例 (VB)](./views-append-method-example-vb.md)   
 [Views Collection、CommandText プロパティの例 (VB)](./views-collection-commandtext-property-example-vb.md)   
 [Views Delete メソッドの例 (VB)](./views-delete-method-example-vb.md)   
 [Views Refresh メソッドの例 (VB)](./views-refresh-method-example-vb.md)   
 [Catalog オブジェクト (ADOX)](./catalog-object-adox.md)   
 [View オブジェクト (ADOX)](./view-object-adox.md)