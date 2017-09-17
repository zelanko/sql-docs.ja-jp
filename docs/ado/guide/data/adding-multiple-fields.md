---
title: "複数のフィールドを追加する |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: H1Hack27Feb2017
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AddNew method [ADO]
- ADO, adding data
- editing data [ADO], adding multiple fields
- editing data [ADO], AddNew method
ms.assetid: f3648ef4-9f36-4991-a868-83a617389844
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 61f6d3c21d4260126f67511c31bbcc680a2da6fa
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="adding-multiple-fields-and-values"></a>複数のフィールドと値の追加
フィールドとを対応する値の配列を渡す方が効率的である可能性がある場合によっては、 **AddNew**設定ではなく、メソッド、**値**の新しいフィールドごとに複数回です。 場合*FieldList* 、配列は、*値*配列でなければなりませんも同じメンバーの数、それ以外のエラーが発生します。 フィールド名の順序は、各配列内のフィールド値の順序と一致する必要があります。 次のコードは、フィールドの配列と値の配列を渡します、 **AddNew**メソッドです。

```
'BeginAddNew2
    Dim avarFldNames As Variant
    Dim avarFldValues As Variant

    avarFldNames = Array("CompanyName", "Phone")
    avarFldValues = Array("Sample Shipper 2", "(931) 555-6334")

    If objRs1.Supports(adAddNew) Then
        objRs1.AddNew avarFldNames, avarFldValues
    End If

    'Re-establish a Connection and update
    Set objRs1.ActiveConnection = GetNewConnection
    objRs1.UpdateBatch
'EndAddNew2
```

