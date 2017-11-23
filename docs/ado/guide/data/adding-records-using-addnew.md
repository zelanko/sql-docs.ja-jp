---
title: "AddNew を使用してレコードを追加する |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AddNew method [ADO]
- ADO, adding data
- editing data [ADO], AddNew method
ms.assetid: cab4adff-f22f-4fb1-9217-f8138c795268
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e3bb2828935872cc4759608b0041db71ce8c24d6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="adding-records-using-addnew-method"></a>AddNew メソッドを使用してレコードを追加します。
これは、基本的な構文、 **AddNew**メソッド。

 *レコード セット*です。AddNew *FieldList*、*値*

 *FieldList*と*値*引数が必要です。 *フィールド リスト*は、単一の名前か名前の配列。 または、新しいレコードにフィールドの序数位置。

 *値*引数 1 つの値か、新しいレコードのフィールドの値の配列です。

 通常、1 つのレコードを追加する場合にを呼び出す、 **AddNew**メソッドを引数なし。 具体的を呼び出す**AddNew**以外の設定、**値**それぞれの新しいレコードのフィールドを呼び出す**更新**または**UpdateBatch**、または両方とも。 できるようにする、**レコード セット**を使用して新しいレコードの追加をサポートしている、**サポート**を持つプロパティ、 **adAddNew**列挙型定数。

 次のコードでは、この手法を使用して、サンプルを新しい配送会社を追加する**Recordset**です。 SQL Server では、運送フィールドの値を自動的に提供します。 したがって、コードは、新しいレコードのフィールド値を指定するは試みません。

```
'BeginAddNew1.1
If objRs.Supports(adAddNew) Then
    With objRs
        .AddNew
        .Fields("CompanyName") = "Sample Shipper"
        .Fields("Phone") = "(931) 555-6334"
        .Update
    End With
End If
'EndAddNew1.1
```

## <a name="remarks"></a>解説
 このコードを使用して、切断されているため**Recordset**バッチ モードでクライアント側カーソルでは、再接続する必要があります、 **Recordset**を新しいデータ ソースに**接続**オブジェクトを呼び出す前に、 **UpdateBatch**データベースへの変更を行うメソッドです。 新しい関数を使用してこれを簡単に行う**GetNewConnection**です。
