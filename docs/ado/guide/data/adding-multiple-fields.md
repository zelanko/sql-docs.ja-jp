---
title: 複数のフィールドの追加 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, adding data
- editing data [ADO], adding multiple fields
- editing data [ADO], AddNew method
ms.assetid: f3648ef4-9f36-4991-a868-83a617389844
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 07a1a3723b4169872c1b8aa872457e67a60d1f71
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926274"
---
# <a name="adding-multiple-fields-and-values"></a>複数のフィールドと値の追加
場合によっては、新しいフィールドごとに**値**を何度も設定するのではなく、フィールドの配列とそれに対応する値を**AddNew**メソッドに渡す方が効率的な場合があります。 *FieldList*が配列の場合、*値*も同じメンバー数の配列である必要があります。それ以外の場合は、エラーが発生します。 フィールド名の順序は、各配列のフィールド値の順序と一致している必要があります。 次のコードは、フィールドの配列と値の配列を**AddNew**メソッドに渡します。

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
