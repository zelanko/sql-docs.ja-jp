---
title: "階層のレコード セット内の行にアクセスする |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: 25f1d2a1-6d5e-4457-aa07-5db5c75dee18
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 829afb6aecaa50b521a86201351f6c071d934b5f
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="accessing-rows-in-a-hierarchical-recordset-example"></a>階層のレコード セット (例) 内の行にアクセスします。
次の例では手順アクセス許可の行に必要な階層[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md):

1.  **レコード セット**オブジェクトから、**作成者**と**titleauthor**作成者 ID で関連するテーブル

2.  外側のループには、各著者の姓と名、状態、および識別情報が表示されます。

3.  追加された**レコード セット**から各の行が取得されたため、[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)コレクションに割り当てられていると*最初*です。

4.  内側のループに追加されたそれぞれの行から 4 つのフィールドが表示されます**Recordset**です。

 [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md)プロパティに設定されている**false**わかりやすくするため、認識できるように、チャプター変更明示的に、外側のループの各反復でします。 割り当てが 1 回だけ実行されるように、コード例をより効率的に行うには、割り当て、手順 2. の最初の行の前に、手順 3. でに移動できます。 設定して、 [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md)プロパティを**true**できるように、*最初*対応のチャプターには暗黙的にあり、自動的に変更されるたびに*rst*新しい行に移動します。

## <a name="example"></a>例

```
Sub datashape()
   Dim cnn As New ADODB.Connection
   Dim rst As New ADODB.Recordset
   Dim rstTitleAuthor As New ADODB.Recordset

   cnn.Provider = "MSDataShape"
   cnn.Open    "Data Provider=MSDASQL;" & _
               "Data Source=SRV;Integrated Security=SSPI;Database=Pubs"
' STEP 1
   rst.StayInSync = FALSE
   rst.Open    "SHAPE  {select * from authors} "  & _
               "APPEND ({select * from titleauthor} " & _
               "RELATE au_id TO au_id) AS chapTitleAuthor", _
               cnn
' STEP 2
   While Not rst.EOF
      Debug.Print    rst("au_fname"), rst("au_lname"), _
                     rst("state"), rst("au_id")
' STEP 3
      Set rstTitleAuthor = rst("chapTitleAuthor").Value
' STEP 4
      While Not rstTitleAuthor.EOF
         Debug.Print rstTitleAuthor(0), rstTitleAuthor(1), _
                     rstTitleAuthor(2), rstTitleAuthor(3)
         rstTitleAuthor.MoveNext
      Wend
      rst.MoveNext
   Wend
End Sub
```

## <a name="see-also"></a>参照
 [データの概要をシェイプ](../../../ado/guide/data/data-shaping-overview.md)[オブジェクトのフィールド](../../../ado/reference/ado-api/field-object.md)[フィールドのコレクション (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md) [図形の正式な文法](../../../ado/guide/data/formal-shape-grammar.md) [Microsoft データ シェイプのサービスOLE DB (ADO サービス プロバイダー)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [データ シェイプに必要なプロバイダー](../../../ado/guide/data/required-providers-for-data-shaping.md) [図形の APPEND 句](../../../ado/guide/data/shape-append-clause.md) [図形が一般にコマンド](../../../ado/guide/data/shape-commands-in-general.md) [Shape COMPUTE 句](../../../ado/guide/data/shape-compute-clause.md) [Visual Basic アプリケーション関数](../../../ado/guide/data/visual-basic-for-applications-functions.md)
