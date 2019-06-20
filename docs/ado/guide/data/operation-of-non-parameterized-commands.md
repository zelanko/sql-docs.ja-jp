---
title: パラメーター化されていないコマンドの操作 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- non-parameterized commands [ADO]
- data shaping [ADO], non-parameterized commands
ms.assetid: 9700e50a-9f17-4ba3-8afb-f750741dc6ca
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 40677971cc2bc5b97c62aad1e638e52deb24c67e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66700536"
---
# <a name="operation-of-non-parameterized-commands"></a>非パラメーター化コマンドの操作
プロバイダーのすべてのコマンドを実行するコマンドのパラメーター化されていないため、**レコード セット**コマンドの実行中に作成されます。 コマンドが同期的に実行される場合すべて、**レコード セット**が完全に設定されます。 非同期モードを選択した場合のデータが設定された状態、**レコード セット**作成モードとのサイズによって異なりますが、**レコード セット**。  
  
 たとえば、*親コマンド*返すことができます、**レコード セット**、Customers テーブルから企業のお客様のおよび*子コマンド*を返すことができます**Recordset** Orders テーブルのすべての顧客の注文の。  
  
```  
SHAPE {SELECT * FROM Customers}   
   APPEND ({SELECT * FROM Orders} AS chapOrders   
   RELATE customerID TO customerID)  
```  
  
 パラメーター化されていない、親子のリレーションシップで親と子の各**Recordset**オブジェクトを関連付けるに共通の列があります。 RELATE 句で列の名前は*親列*最初し*子列*します。 列は、それぞれ異なる名前を必要があります**Recordset**オブジェクトが、意味のある関係を指定するには、同じ情報を参照する必要があります。 たとえば、**顧客**と**注文レコード セット**オブジェクト customerID フィールド両方がある可能性があります。 子のメンバーシップ**レコード セット**プロバイダーのコマンドを子が続く**レコード セット**孤立した行を含めることができます。 追加形状を変更せずにこれらの孤立した行にアクセスできません。  
  
 親にチャプター列を追加するデータの整形**Recordset**します。 チャプター列の値は、子の行への参照を**Recordset**RELATE 句を満たしています。 同じの値が、これは、*親列*では、指定された親行の*子列*」の章の子のすべての行のできます。 同じ RELATE 句で複数の TO 句を使用している場合、AND 演算子を使用してそれらを暗黙的に結合されます。 RELATE 句で親列は、親のキーを構成しない場合**Recordset**、1 つの子行が複数の親行を持つことができます。  
  
 チャプター列内の参照にアクセスするときに、ADO は自動的に取得、 **Recordset**参照によって表されます。 非パラメーター化コマンドで注意子全体**レコード セット**されましたが、取得、章のみでは、行のサブセット。  
  
 追加の列がにない場合*章エイリアス*名前をその自動的に生成されます。 A[フィールド](../../../ado/reference/ado-api/field-object.md)オブジェクトに追加される列の**Recordset**オブジェクトの[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)コレクション、およびそのデータ型になります**adChapter**.  
  
 階層構造を移動する方法については**Recordset**を参照してください[階層レコード セットの行にアクセスする](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)します。  
  
## <a name="see-also"></a>参照  
 [データ シェイプの例](../../../ado/guide/data/data-shaping-example.md)   
 [Shape の正式文法](../../../ado/guide/data/formal-shape-grammar.md)   
 [一般的な Shape コマンド](../../../ado/guide/data/shape-commands-in-general.md)
