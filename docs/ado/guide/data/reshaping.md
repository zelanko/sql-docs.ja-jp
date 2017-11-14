---
title: "作り直して、|Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reshaping previously shaped Recordset [ADO]
- data shaping [ADO], reshaping
ms.assetid: b1c965b7-3dad-4de6-9e0e-502ca8785be3
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d5264de973e4ed36cc24eb5c535576bdfa0a7228
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="reshaping"></a>形状を変更
A **Recordset**作成図形の句でのコマンドを割り当てることができます、*エイリアス*名 (通常の AS キーワード) です。 形状のエイリアス**Recordset**は完全に別のコマンドで参照できます。 つまり、再利用できる、または*変形*、以前形**レコード セット**新しい図形コマンドでします。 この機能をサポートする ADO には、プロパティが用意されて[変形名前](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md)です。  
  
 形状を変更すると、2 つの主な機能があります。 最初に関連付ける既存**Recordset**新しい親に**レコード セット**です。  
  
## <a name="example"></a>例  
  
```  
rs1.Open "SHAPE {select * from Customers} " & _  
         "APPEND ({select * from Orders} AS chapOrders " & _  
         "RELATE CustomerID to CustomerID)", cn  
  
rs2.Open "SHAPE {select * from Employees} " & _  
         "APPEND (chapOrders RELATE EmployeeID to EmployeeID)", cn  
```  
  
 既存の子にチャプター化されていないアクセスを有効には、2 番目の関数は**レコード セット**オブジェクト、構文を使用して"図形\<レコード セットの形状変更名 >"です。  
  
> [!NOTE]
>  既存の列を追加することはできません**レコード セット**、パラメーター化された形状変更**レコード セット**または**レコード セット**の間にある COMPUTE 句内のオブジェクトまたはを実行いずれかの操作を集計**レコード セット**から子孫、**レコード セット**形状を変更します。 **Recordset**形状を変更して、新しい図形コマンドの両方を使わなければなりません同じ[接続](../../../ado/reference/ado-api/connection-object-ado.md)です。  
  
## <a name="see-also"></a>参照  
 [データ シェイプの例](../../../ado/guide/data/data-shaping-example.md)

