---
title: データの整形を行う例 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data shaping [ADO], about data shaping
ms.assetid: 1bfdcad4-52e1-45bc-ad21-783657ef0a44
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 991ea5c55a99aa8dbe043dd99b9703acd73172e9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="data-shaping-example"></a>データ シェイプの例
次のデータの整形を行うコマンドは、階層構造を構築する方法を示します**レコード セット**から、**顧客**と**Orders** Northwind データベース内のテーブルです。  
  
```  
SHAPE {SELECT CustomerID, ContactName FROM Customers}   
APPEND ({SELECT OrderID, OrderDate, CustomerID FROM Orders} AS chapOrders   
RELATE customerID TO customerID)   
```  
  
 開くにはこのコマンドを使用する場合、 **Recordset**オブジェクト (のように[Visual Basic の例のデータの整形](../../../ado/guide/data/visual-basic-example-of-data-shaping.md))、チャプターが作成されます (**chapOrders**) 返されるレコードごとに**顧客**テーブル。 この章のサブセットから成る、**レコード セット**から返される、 **Orders**テーブル。 **ChapOrders**章には、特定の顧客の注文に関するすべての要求された情報が含まれています。 この例では、チャプターから成る 3 つの列: **OrderID**、 **OrderDate**、および**CustomerID**です。  
  
 結果の形の最初の 2 つのエントリ**Recordset**とおりです。  
  
|CustomerID|[ContactName]|OrderID|OrderDate|CustomerID|  
|----------------|-----------------|-------------|---------------|----------------|  
|ALFKI|Maria Ander|10643<br /><br /> 10692<br /><br /> 10702<br /><br /> 10835<br /><br /> 10952<br /><br /> 11011|1997-08-25<br /><br /> 1997-10-03<br /><br /> 1997-10-13<br /><br /> 1998-01-15<br /><br /> 1998-03-16<br /><br /> 1998-04-09|ALFKI<br /><br /> ALFKI<br /><br /> ALFKI<br /><br /> ALFKI<br /><br /> ALFKI<br /><br /> ALFKI|  
|ANATR|Ana Trujillo|10308<br /><br /> 10625<br /><br /> 10759<br /><br /> 10926|1996-09-18<br /><br /> 1997-08-08<br /><br /> 1997-11-28<br /><br /> 1998-03-04|ANATR<br /><br /> ANATR<br /><br /> ANATR<br /><br /> ANATR|  
  
 SHAPE コマンドの追加は、子の作成に使用**Recordset** 、親に関連付けられた**Recordset** (で既に説明した図形のキーワードの直後に、プロバイダー固有のコマンドから返される以前) RELATE 句でします。 親と子の通常共通がある、少なくとも 1 つの列: 親の行にある列の値は、子のすべての行の列の値と同じです。  
  
 図形のコマンドを使用する 2 番目の方法がある: つまり、親を生成する**Recordset**子から**レコード セット**です。 子のレコード**Recordset**はグループ化が通常 BY 句、および 1 つの行を使用して追加されて、親に**レコード セット**子プロセスの結果として得られるグループごとにします。 BY 句を省略すると、子**レコード セット**1 つのグループと、親フォームは**Recordset**は正確に 1 つの行が含まれます。 これは子全体を「総計」集計を計算するために役立ちます**Recordset**です。  
  
 図形コマンド コンストラクトもすることができます、形状をプログラムで作成**Recordset**です。 コンポーネントにアクセスすることができますし、**レコード セット**プログラムまたは適切なビジュアル コントロール。 Shape コマンドが、その他の ADO コマンド テキストのように発行されます。 詳細については、次を参照してください。[図形が一般にコマンド](../../../ado/guide/data/shape-commands-in-general.md)です。  
  
 どのような方法に関係なく、親**レコード セット**が形式ですが、登録するには子に関連付けるために使用される章列**レコード セット**です。 する場合は、親**Recordset**子の行を集計 (SUM、MIN、MAX、およびなど) を含む列を持つこともできます。 親と子の両方**レコード セット**内の行に式を含む列を持つことができます、**レコード セット**と、新しいと、最初にある列を空にします。  
  
 このセクションでは、次のトピックを続行します。  
  
-   [Visual Basic のデータ シェイプの例](../../../ado/guide/data/visual-basic-example-of-data-shaping.md)
