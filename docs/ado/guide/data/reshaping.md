---
title: リシェイプ |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- reshaping previously shaped Recordset [ADO]
- data shaping [ADO], reshaping
ms.assetid: b1c965b7-3dad-4de6-9e0e-502ca8785be3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 324801cbfc97db4e2a1137fa04df0c74dc1897a1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47714530"
---
# <a name="reshaping"></a>リシェイプ
A **Recordset**作成図形の句でのコマンドを割り当てることができます、*エイリアス*名 (通常の AS キーワード)。 形状のエイリアス**Recordset**完全に別のコマンドで参照できます。 つまり、再利用できる、または*変形*、以前成型された**レコード セット**新しい図形コマンドでします。 この機能をサポートする ADO は、プロパティを提供します[Reshape Name](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md)します。  
  
 2 つの主な機能が形状を変更します。 最初に関連付ける既存**レコード セット**新しい親に**レコード セット**します。  
  
## <a name="example"></a>例  
  
```  
rs1.Open "SHAPE {select * from Customers} " & _  
         "APPEND ({select * from Orders} AS chapOrders " & _  
         "RELATE CustomerID to CustomerID)", cn  
  
rs2.Open "SHAPE {select * from Employees} " & _  
         "APPEND (chapOrders RELATE EmployeeID to EmployeeID)", cn  
```  
  
 2 番目の関数は、既存の子への非チャプターのアクセスを有効にするのには**レコード セット**オブジェクトの場合、構文を使用して"図形\<レコード セット名を変形 >"。  
  
> [!NOTE]
>  既存の列を追加することはできません**レコード セット**、パラメーター化された再整形**レコード セット**または**レコード セット**オブジェクト、介在する COMPUTE 句、またはを実行いずれかの操作を集計**レコード セット**から子孫、**レコード セット**形状を変更します。 **Recordset**コマンド形状を変更して、新しい図形を両方使用する必要あります同じ[接続](../../../ado/reference/ado-api/connection-object-ado.md)します。  
  
## <a name="see-also"></a>参照  
 [データ シェイプの例](../../../ado/guide/data/data-shaping-example.md)
