---
title: "Cellset オブジェクト (ADO MD) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Cellset
helpviewer_keywords:
- Cellset object [ADO MD]
ms.assetid: 5e2452c0-cac0-49b2-8099-836c35794d50
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f53e9ec68a4375a9c8d07dc3937750c2e7ba3d46
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="cellset-object-ado-md"></a>Cellset オブジェクト (ADO MD)
多次元クエリの結果を表します。 これは、キューブまたはその他のセルセットから選択したセルのコレクションです。  
  
## <a name="remarks"></a>解説  
 内のデータ、**セルセット**、直接の配列に似たアクセスを使用して取得されます。 ドリル ダウンできます。 特定のメンバーで、そのメンバーに関するデータを取得します。 たとえば、次のコードを返します最初のメンバーのキャプション最初の位置で名前付きセル セットの最初の軸で`cst`:  
  
```  
cst.Axes(0).Positions(0).Members(0).Caption  
```  
  
## <a name="remarks"></a>解説  
 セル セット内の現在のセルの概念はありません。 代わりに、[項目](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)プロパティは、固有の仕様を取得[セル](../../../ado/reference/ado-md-api/cell-object-ado-md.md)セルセットからのオブジェクト。 引数、**項目**プロパティを決定するセルを取得します。 セルの序数に基づく一意の値を指定することができます。 セルセットの各軸の位置番号を使用してセルを取得することもできます。 セルの取得の詳細については、次を参照してください。、[項目](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)プロパティです。  
  
 コレクション、メソッド、およびプロパティの使用、**セルセット**オブジェクトを次を行うことができます。  
  
-   開いている接続に関連付ける、**セルセット**オブジェクトを設定してその[ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md)プロパティです。  
  
-   実行しを持つ多次元クエリの結果を取得、[開く](../../../ado/reference/ado-md-api/open-method-ado-md.md)メソッドです。  
  
-   取得、**セル**から、**セルセット**で、[項目](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)プロパティです。  
  
-   返す、[軸](../../../ado/reference/ado-md-api/axis-object-ado-md.md)を定義するオブジェクト、**セルセット**で、[軸](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)コレクション。  
  
-   内のデータをフィルター処理に使用されるディメンションに関する情報を取得、**セルセット**で、 [FilterAxis](../../../ado/reference/ado-md-api/filteraxis-property-ado-md.md)プロパティです。  
  
-   返すかを定義するためのクエリを指定、**セルセット**で、[ソース](../../../ado/reference/ado-md-api/source-property-ado-md.md)プロパティです。  
  
-   現在の状態を返す、**セルセット**(オープン、クローズを実行する、または接続する) で、[状態](../../../ado/reference/ado-md-api/state-property-ado-md.md)プロパティです。  
  
-   閉じる、開く**セルセット**で、[閉じる](../../../ado/reference/ado-md-api/close-method-ado-md.md)メソッドです。  
  
-   プロバイダー固有の情報を取得、**セルセット**標準 ado[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクション。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [プロパティ、メソッド、およびイベント](../../../ado/reference/ado-md-api/cellset-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [セル セットの例 (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Axes コレクション (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)   
 [セルのオブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [プロパティのコレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)

