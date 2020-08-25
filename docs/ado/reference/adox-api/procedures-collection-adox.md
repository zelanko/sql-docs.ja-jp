---
description: Procedures コレクション (ADOX)
title: Procedures コレクション (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Procedures
- Catalog::Procedures
helpviewer_keywords:
- Procedures collection [ADOX]
ms.assetid: dc7a38e1-93b9-4034-9af2-ff419e8fb2a3
author: rothja
ms.author: jroth
ms.openlocfilehash: 97421c9020750627dcd27f6188ae5cda72a2d90c
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2020
ms.locfileid: "88769631"
---
# <a name="procedures-collection-adox"></a>Procedures コレクション (ADOX)
カタログのすべての [プロシージャ](./procedure-object-adox.md) オブジェクトを格納します。  
  
## <a name="remarks"></a>解説  
 **Procedures**コレクションの[Append](./append-method-adox-procedures.md)メソッドは、ADOX で一意です。 次のようにすることができます。  
  
-   **追加**メソッドを使用して、新しいプロシージャをコレクションに追加します。  
  
 その他のプロパティとメソッドは、ADO コレクションの標準です。 次のようにすることができます。  
  
-   [項目](../ado-api/item-property-ado.md)プロパティを使用して、コレクション内のプロシージャにアクセスします。  
  
-   [Count](../ado-api/count-property-ado.md)プロパティを使用して、コレクションに含まれているプロシージャの数を返します。  
  
-   [Delete](./delete-method-adox-collections.md)メソッドを使用して、コレクションからプロシージャを削除します。  
  
-   [更新](../ado-api/refresh-method-ado.md)メソッドを使用して、現在のデータベーススキーマを反映するように、コレクション内のオブジェクトを更新します。  
  
 ここでは、次のトピックについて説明します。  
  
-   [Indexes コレクションのプロパティ、メソッド、およびイベント](./indexes-collection-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Command プロパティと CommandText プロパティの例 (VB)](./command-and-commandtext-properties-example-vb.md)   
 [Parameters コレクション、Command プロパティの例 (VB)](./parameters-collection-command-property-example-vb.md)   
 [Procedures Append メソッドの例 (VB)](./procedures-append-method-example-vb.md)   
 [Procedures Delete メソッドの例 (VB)](./procedures-delete-method-example-vb.md)   
 [Procedures Refresh メソッドの例 (VB)](./procedures-refresh-method-example-vb.md)   
 [Procedures コレクションのプロパティ、メソッド、およびイベント](./procedures-collection-properties-methods-and-events.md)   
 [Catalog オブジェクト (ADOX)](./catalog-object-adox.md)   
 [Procedure オブジェクト (ADOX)](./procedure-object-adox.md)