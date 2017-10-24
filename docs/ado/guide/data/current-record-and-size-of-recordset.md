---
title: "現在のレコードとレコード セットのサイズ |Microsoft ドキュメント"
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
- record location [ADO]
- current record [ADO]
ms.assetid: e63ff331-8655-4be7-82c6-e6cd6cc9d16d
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fb50826230e46cc71106a2b17d01914eae024f47
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="current-record-and-size-of-recordset"></a>現在のレコードとレコード セットのサイズ
このセクションでは、サンプルでは、カーソルの現在位置を検索する方法を説明**レコード セット**で[JScript コード例をレコード セットを返す](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md)です。  
  
## <a name="current-record"></a>現在のレコード  
 データセット内の現在のレコードに対応のカーソルの位置を指すこと、 **Recordset**オブジェクト。 ときに、 **Recordset**呼び出しの結果として、データ ソースから返されるオブジェクト**Recordset.Open**、 **Command.Execute**、または**Connection.Execute** (含む**Connection.NamedCommand**と**Connection.StoredProcedure**)、最初のレコードの位置にカーソルが設定されています。 サンプル データセットで初期の現在のレコードは「伯父さん Bob の有機ドライなし」の項目。  
  
## <a name="size-of-recordset"></a>レコード セットのサイズ  
 サイズを調べるには**Recordset**オブジェクトの値を取得、 **Recordset.RecordCount**プロパティです。 この値は内のレコードの数を示す long 整数、 **Recordset**です。 データセットは、Microsoft SQL Server の ole DB プロバイダーから返される、この値は返される行の数を示します。 読み取り、 **RecordCount**プロパティに、閉じられた**Recordset**エラーが発生します。  
  
 レコードの数を特定できない場合、プロパティの値は – 1 にします。  
  
 値、 **RecordCount**プロパティは、プロバイダーと使用するカーソルの種類の機能にも依存します。 順方向専用カーソルの場合は、値は-1 です。 静的カーソルまたはキーセット カーソルを値は実際に返されるレコード数、 **Recordset**オブジェクト。 動的カーソルの場合、値は-1 またはデータ ソースによっては、レコードの実際の数です。  
  
 サポートするカーソル**Recordcount**必要があります作業困難ですが、および必要計算能力を増強、カーソルはサポートしていませんより**Recordcount**です。 レコードの数を知る必要がない場合異なるカーソルの種類を使用してに役立つアプリケーションのパフォーマンスを向上させる場合に特に大きなデータ セットを処理する必要があります。  
  
 場合によっては、プロバイダーまたはカーソルがな決定できる、 **RecordCount**値の後に、データ ソースからすべてのレコードをフェッチします。 正確なカウントを呼び出して、 **Recordset**.**MoveLast**メソッドを呼び出す前に**Recordset.RecordCount**です。  
  
 サンプル**Recordset**オブジェクトを使用して取得、 [JScript コード例](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md)呼び出すので、順方向専用カーソルを使用して**RecordCount**このオブジェクトに、常に行わ – 1。 呼び出すコード行を変更する場合、 **Recordset**.**開いている**メソッドの次の例に示すように、 **RecordCount**プロパティがフェッチされたレコードの実際の数を返します。  
  
```  
oRs.Open sSQL, sCnStr, adOpenStatic, adLockOptimistic, adCmdText   
```  
  
 これは静的カーソルを[Microsoft OLE DB Provider for SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)サポート**RecordCount**です。 この例では、5 つのレコードであるため**RecordCount** 5 の値を生成する必要があります。  
  
 このセクションには、次のトピックが含まれています。  
  
 [レコード セットの境界](../../../ado/guide/data/boundaries-of-a-recordset.md)

