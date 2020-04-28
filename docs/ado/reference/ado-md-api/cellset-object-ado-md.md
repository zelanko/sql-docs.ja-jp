---
title: Cellset オブジェクト (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cellset
helpviewer_keywords:
- Cellset object [ADO MD]
ms.assetid: 5e2452c0-cac0-49b2-8099-836c35794d50
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9524e9801f284d3dff3125b850cdd1fd32a361a3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67928644"
---
# <a name="cellset-object-ado-md"></a>CellSet オブジェクト (ADO MD)
多次元クエリの結果を表します。 これは、キューブまたは他のセルセットから選択されたセルのコレクションです。  
  
## <a name="remarks"></a>Remarks  
 **セルセット**内のデータは、配列に似た直接アクセスを使用して取得されます。 特定のメンバーにドリルダウンして、そのメンバーに関するデータを取得することができます。 たとえば、次のコードは、という名前`cst`のセルセットの最初の軸の最初の位置にある最初のメンバーのキャプションを返します。  
  
```  
cst.Axes(0).Positions(0).Members(0).Caption  
```  
  
## <a name="remarks"></a>Remarks  
 セルセット内には、現在のセルの概念はありません。 代わりに、 [Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)プロパティは、セルセットから特定の[セル](../../../ado/reference/ado-md-api/cell-object-ado-md.md)オブジェクトを取得します。 **項目**プロパティの引数によって、取得するセルが決まります。 セルの一意の序数値を指定できます。 セルは、セルセットの各軸に沿った位置番号を使用して取得することもできます。 セルの取得の詳細については、 [Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)プロパティを参照してください。  
  
 **Cellset**オブジェクトのコレクション、メソッド、およびプロパティを使用して、次の操作を実行できます。  
  
-   [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md)プロパティを設定して、開いている接続を**セルセット**オブジェクトに関連付けます。  
  
-   [Open](../../../ado/reference/ado-md-api/open-method-ado-md.md)メソッドを使用して多次元クエリの結果を実行および取得します。  
  
-   [アイテム](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md)プロパティを使用して、セル**セット**から**セル**を取得します。  
  
-   [Axes](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)コレクションを使用して**セルセット**を定義する[軸](../../../ado/reference/ado-md-api/axis-object-ado-md.md)オブジェクトを返します。  
  
-   [Filteraxis](../../../ado/reference/ado-md-api/filteraxis-property-ado-md.md)プロパティを使用して、**セルセット**のデータをフィルター処理するために使用されるディメンションに関する情報を取得します。  
  
-   [Source](../../../ado/reference/ado-md-api/source-property-ado-md.md)プロパティを使用して**セルセット**を定義するために使用するクエリを返します。値の設定もできます。  
  
-   [State](../../../ado/reference/ado-md-api/state-property-ado-md.md)プロパティを使用して、**セルセット**(開く、closed、実行中、または接続) の現在の状態を返します。  
  
-   [Close](../../../ado/reference/ado-md-api/close-method-ado-md.md)メソッドを使用して、開いている**セルセット**を閉じます。  
  
-   標準の ADO[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)コレクションを使用して、**セルセット**に関するプロバイダー固有の情報を取得します。  
  
 ここでは、次のトピックについて説明します。  
  
-   [プロパティ、メソッド、およびイベント](../../../ado/reference/ado-md-api/cellset-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>参照  
 [セルセットの例 (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Axes コレクション (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)   
 [Cell オブジェクト (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Properties コレクション (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
