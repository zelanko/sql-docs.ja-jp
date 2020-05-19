---
title: View オブジェクト (ADOX) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- View
helpviewer_keywords:
- View object [ADOX]
ms.assetid: 653421ce-7b94-43d0-9bc6-4900f8f2af45
author: rothja
ms.author: jroth
ms.openlocfilehash: b468ccc3edc4cc5453b4f08371cd2b4b962f0c72
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82753191"
---
# <a name="view-object-adox"></a>View オブジェクト (ADOX)
フィルター処理されたレコードセットまたは仮想テーブルを表します。 ADO[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトと組み合わせて使用すると、ビュー**オブジェクトを使用して**、ビューの追加、削除、または変更を行うことができます。  
  
## <a name="remarks"></a>解説  
 ビューは、他のデータベーステーブルまたはビューから作成された仮想テーブルです。 **ビュー**オブジェクトを使用すると、プロバイダーの "create View" 構文を知らない場合や使用しなくても、ビューを作成できます。  
  
 **View**オブジェクトのプロパティを使用すると、次のことができます。  
  
-   [Name](../../../ado/reference/adox-api/name-property-adox.md)プロパティを使用してビューを識別します。  
  
-   [コマンド](../../../ado/reference/adox-api/command-property-adox.md)プロパティを使用してビューを追加、削除、または変更するために使用できる ADO**コマンド**オブジェクトを指定します。  
  
-   [DateCreated](../../../ado/reference/adox-api/datecreated-property-adox.md)プロパティと[DateModified](../../../ado/reference/adox-api/datemodified-property-adox.md)プロパティを使用して日付情報を返します。  
  
 ここでは、次のトピックについて説明します。  
  
-   [View オブジェクトのプロパティ、メソッド、およびイベント](../../../ado/reference/adox-api/view-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [Views および Fields コレクションの例 (VB)](../../../ado/reference/adox-api/views-and-fields-collections-example-vb.md)   
 [Views Append メソッドの例 (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Views Collection、CommandText プロパティの例 (VB)](../../../ado/reference/adox-api/views-collection-commandtext-property-example-vb.md)   
 [Views Delete メソッドの例 (VB)](../../../ado/reference/adox-api/views-delete-method-example-vb.md)   
 [Views コレクション (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
