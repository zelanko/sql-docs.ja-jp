---
title: "レコード セットの境界 |Microsoft ドキュメント"
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
- EOF property [ADO], boundaries of a Recordset
- Recordset object [ADO], boundaries of a Recordset
- BOF property [ADO], boundaries of a Recordset
ms.assetid: c0dd4a0f-478d-4c5e-b5d5-7535f211d064
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 66dec387cc91a2d0bd4d3aded73a6b4301aff593
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="boundaries-of-a-recordset"></a>レコード セットの境界
**レコード セット**をサポートしている、 **BOF**と**EOF**に含めること示す先頭と末尾、それぞれ、データセットのプロパティです。 考えることができます**BOF**と**EOF**の先頭と末尾の位置「ファントム」のレコードとして、 **Recordset**です。 カウント**BOF**と**EOF**、サンプル**Recordset**は、次のようになります。  
  
|ProductID|ProductName|UnitPrice|  
|---------------|-----------------|---------------|  
|BOF|||  
|7|伯父さん Bob の有機乾燥なし|30.0000|  
|14|階層|23.2500|  
|28|Rssle ザワークラウト|45.6000|  
|51|りんご|53.0000|  
|74|Longlife 階層|10.0000|  
|EOF|||  
  
 過去の最後のレコードでは、カーソルを動かしたときに**EOF**に設定されている**True**以外の場合、その値は**False**です。 カーソルが最初のレコードの前に移動すると同様に、 **BOF**に設定されている**True**以外の場合、その値は**False**です。 これらのプロパティは、次の JScript コード フラグメントに示すように通常、データセットのレコードの列挙に使用されます。  
  
```  
while (objRecordset.EOF != true)   
{  
   // Work on the current record.  
   ...  
   // Advance the cursor forward to the next record.  
   objRecordset.MoveNext();  
}  
or  
while (objRecordset.BOF != true)   
{  
   // Work on the current record.  
   ...  
   // Move the cursor to the previous record.  
   objRecordset.MovePrevious();  
}  
```  
  
 両方**BOF**と**EOF**は**True**、**レコード セット**オブジェクトが空です。 両方のプロパティになります**False**新しく開かれた空でないため**Recordset**オブジェクト。 使用することができます、 **BOF**と**EOF**プロパティかどうかをまとめて、**レコード セット**オブジェクトが空か、次の JScript コード フラグメントで示すように、します。  
  
```  
if (objRecordset.EOF == true && objRecordset.BOF == true)  
{  
   WScript.Echo("we got an empty dataset.");  
}  
else  
{  
   WScript.Echo("we got a full dataset.");  
}  
```  
  
 このスキームでは、すべての種類のカーソル動作し、は、基になるプロバイダーに依存しません。 空かを決定しようとする場合、 **Recordset**オブジェクトを確認する場合、 **RecordCount**プロパティの値がゼロ (0) か、適切なカーソルとプロバイダーを使用する予防措置を行う必要がありますを結果内のレコードの数を返すをサポートします。  
  
 最後の残りのレコードを削除する場合、 **Recordset**オブジェクト、カーソルは、不定状態のままにします。 **BOF**と**EOF**プロパティが残る可能性がある**False**まで、現在のレコードの位置を変更しようとすると、プロバイダーによって異なります。 詳細については、次を参照してください。 [Delete メソッドを使用してレコードを削除すると、](../../../ado/guide/data/deleting-records-using-the-delete-method.md)です。
