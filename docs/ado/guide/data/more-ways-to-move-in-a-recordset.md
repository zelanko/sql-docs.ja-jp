---
title: レコード セット内を移動する方法 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MoveNext method [ADO]
- MoveLast method [ADO]
- MoveFirst method [ADO]
- Recordset object [ADO], moving
- MovePrevious method [ADO]
ms.assetid: 9f8cf1b2-3def-453f-a0ff-4646c5f15262
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 894ab6b4daba13d6d57dda178f45bf07fc8a8f8d
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272131"
---
# <a name="more-ways-to-move-in-a-recordset"></a>レコード セット内を移動する方法
次の 4 つの方法は、移動またはスクロールするのに使用、 **Recordset**: [MoveFirst、MoveLast、MoveNext、および MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)です。 (これらのメソッドの一部は順方向専用カーソルで使用できます)  
  
 **MoveFirst**の最初のレコードを現在のレコードの位置を変更、 **Recordset**です。 **MoveLast**に現在のレコードが最後の位置の変更を記録、 **Recordset**です。 使用する**MoveFirst**または**MoveLast**、 **Recordset**オブジェクトには、ブックマークまたは旧バージョンとカーソルの移動をサポートする必要があります。 それ以外の場合、メソッドの呼び出しでエラーが発生します。  
  
 **MoveNext**現在のレコードが 1 つの場所をフォワード位置に移動します。 最後にある場合は、呼び出すときを記録**MoveNext**、 **EOF**に設定されます**True**です。 **MovePrevious**現在のレコードをひとまとめに旧バージョンとの位置に移動します。 呼び出すと、最初のレコードではかどうか**MovePrevious**、 **BOF**に設定されます**True**です。 確認することをお勧め、 **EOF**と**BOF**これらのメソッドを使用する場合のプロパティのいずれかの端を移動する場合、レコードの現在の有効な位置にカーソルを移動して、 **Recordset**、次のようにします。  
  
```  
. . .  
oRs.MoveNext  
If oRs.EOF Then oRs.MoveLast  
. . .   
```  
  
 またはの場合、 **MovePrevious**メソッド。  
  
```  
. . .   
oRs.MovePrevious  
If oRs.BOF Then oRs.MoveFirst  
. . .  
```  
  
 場合で、**レコード セット**フィルター処理または並べ替えされて現在のレコードのデータが変更されると、位置が変更される場合もします。 このような場合、 **MoveNext**メソッドは通常、動作しますが、位置は 1 であり古い位置ではなく、新しい位置から転送を記録します。 レコードは、並べ替えられたの末尾に移動するよう、現在のレコード内のデータを変更する**レコード セット**、その呼び出し元は、 **MoveNext**現在のレコードを設定する ado の結果、後の最後のレコードの位置、 **Recordset** (**EOF** = **True**)。  
  
 さまざまな移動メソッドの動作、 **Recordset**内のデータのある程度のオブジェクトが依存して、 **Recordset**です。 新しいレコードを追加する、 **Recordset**特定の順序では、データ ソースで定義され、暗黙的に依存している可能性があります、または新しいレコードのデータに明示的に最初に追加します。 たとえば場合、並べ替えまたは結合操作は実行を設定するクエリ、**レコード セット**、内の適切な場所に新しいレコードが挿入されます、**レコード セット**です。 順序指定しない場合は明示的に作成するときに、 **Recordset**、データ ソースの実装で変更の返される行の順序を誤って変更する可能性があります。 追加、並べ替え、フィルター処理、および編集の機能で、**レコード セット**順序に影響を与えることができ、場合によっては、レコード セット内の行が表示されます。  
  
 したがって、 **MoveNext**、 **MovePrevious**、 **MoveFirst**、 **MoveLast**、および**移動**すべて他の操作に依存したが、同じ実行**Recordset**です。 ADO は、明示的に移動することが、場合によっては、介在する変更、後続の移動の効果を理解するが困難になるまで、現在の位置を維持するために常に試みます。 呼び出す場合など、 **MoveFirst** 、並べ替えの最初の行の位置に**レコード セット**降順に昇順の並べ替えを変更して、同じ行のままでは、最後の行であるようになりましたが、**Recordset**です。 **MoveFirst**別の行 (新しい最初の行) になります。  
  
 中に特定の行を配置した場合、別の例として、**レコード セット**を呼び出す**削除**し**MoveNext**、表示されているようになりましたレコード削除されたレコードの直後です。 呼び出し元が**MovePrevious** 、削除したレコードがアクティブなメンバーシップの数えられる不要になったために、現在のレコードを削除する 1 つを前のレコード、**レコード セット**です。  
  
 現在のレコードに対して相対的に移動するメソッドのすべてのプロバイダーで一貫性のある移動セマンティクスを定義することは困難である — **MovePrevious**、 **MoveNext**、および**を移動** : 現在のレコード内のデータを変更した場合。 たとえば、並べ替えられたで作業している場合がフィルター処理**Recordset**と、他のすべてのレコードより前にそのように現在のレコード内のデータを変更するが、変更したデータも不要になったフィルターに一致する、where をはっきりしない場合は、**MoveNext**操作を実行する必要があります。 最も安全な結論は内でその相対移動、**レコード セット**絶対移動するより危険は、(を使用してなど**MoveFirst**または**MoveLast**)、データをする場合変更レコードの編集中に追加、または削除します。 並べ替えとフィルター処理は、この種類の値が変わらないようにするために、プライマリ キーまたは ID に基づく必要があります。
