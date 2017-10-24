---
title: "非パラメーター化コマンドの操作 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- non-parameterized commands [ADO]
- data shaping [ADO], non-parameterized commands
ms.assetid: 9700e50a-9f17-4ba3-8afb-f750741dc6ca
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0a19b939b0b0eb33d436a3924a04562473b4c06a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="operation-of-non-parameterized-commands"></a>非パラメーター化コマンドの操作
コマンドのパラメーターのないすべてのプロバイダー コマンドが実行されると、**レコード セット**コマンドの実行中に作成されます。 コマンドが同期的に実行される場合すべて、**レコード セット**が完全に設定されます。 非同期モードを選択した場合のデータが設定された状態、**レコード セット**母集団モードとのサイズによって異なりますが、**レコード セット**です。  
  
 たとえば、*親コマンド*を返すことが、**レコード セット**、Customers テーブルから企業のお客様のおよび*子コマンド*を返すことが**Recordset** Orders テーブルのすべての顧客の注文のです。  
  
```  
SHAPE {SELECT * FROM Customers}   
   APPEND ({SELECT * FROM Orders} AS chapOrders   
   RELATE customerID TO customerID)  
```  
  
 パラメーターのない、親子のリレーションシップで親と子の各**Recordset**オブジェクトがそれらを関連付けてに共通する列を持つ必要があります。 列が RELATE 句で指定*親列*最初し*子列*です。 列は、それぞれ異なる名前を付けることがあります**Recordset**オブジェクトが、意味のある関係を指定するために、同じ情報を参照する必要があります。 たとえば、**顧客**と**注文レコード セット**オブジェクト customerID フィールド両方がある可能性があります。 子のメンバーシップ**Recordset**は、プロバイダー コマンドを子プロセスによって決定されます**レコード セット**孤立した行を含めることができます。 その他の形状を変更せずにこれらの孤立した行にアクセスできません。  
  
 親にチャプター列を追加するデータの整形**Recordset**です。 チャプター列の値は、子の行への参照**Recordset**RELATE 句を満たしています。 つまり、同じ値が、*親列*がで指定された親行の*子列*章の子のすべての行。 同じ RELATE 句で複数の TO 句を使用している場合、AND 演算子を使用してそれらを暗黙的に結合されています。 RELATE 句で親列、親のキーを構成しない場合**Recordset**、1 つの子行が複数の親行を持つことができます。  
  
 ADO が自動的に取得、チャプター列内の参照にアクセスするときに、 **Recordset**参照によって表されます。 ですが、非パラメーター化コマンドで、なお子全体**レコード セット**されましたが、取得、章だけでは、行のサブセットです。  
  
 追加の列があるない場合*章エイリアス*名前をに対して自動的に生成されます。 A[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクトに追加される列の**Recordset**オブジェクトの[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)コレクション、およびそのデータ型になります**adChapter**.  
  
 階層を移動する方法について**Recordset**を参照してください[階層レコード セット内の行へのアクセス](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)です。  
  
## <a name="see-also"></a>参照  
 [データ シェイプの例](../../../ado/guide/data/data-shaping-example.md)   
 [図形の正式な文法](../../../ado/guide/data/formal-shape-grammar.md)   
 [一般的な図形コマンド](../../../ado/guide/data/shape-commands-in-general.md)

