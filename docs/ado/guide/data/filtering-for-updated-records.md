---
title: "レコードが更新のフィルタ リング |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: filtering for updated records [ADO]
ms.assetid: 4a798921-d7bb-47c9-a252-550fd9463ec9
caps.latest.revision: "4"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 37ad79ea1018a2e272cb9071bde61176ddf6348e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="filtering-for-updated-records"></a>更新されたレコードにフィルター処理
UpdateBatch を呼び出す前に、レコード セットが開かれてから変更されているレコードだけを表示するレコード セットのフィルター プロパティまたは UpdateBatch の最後の呼び出しを使用できます。 これを行うには、等しい、次のセクションのコード例に示すように、レコードの数が更新されますを決定するには、行と列にフィルターを設定します。  
  
## <a name="remarks"></a>解説  
 この例は、UpdateBatch を呼び出す前にのみ、レコード セットをフィルター処理、ユーザー レコードは変更を示し、彼女 (CancelBatch メソッドを使用して) の更新をキャンセルできるようにして、前の UpdateBatch 例を拡張します。  
  
```  
'BeginFilterPend  
    '...  
    objRs1.Open strSQL, strConn, adOpenStatic, adLockBatchOptimistic, adCmdText  
  
    ' Change value of Phone field for first record in Recordset, saving value  
    ' for later restoration.  
    intId = objRs1("ShipperId")  
    sPhone = objRs1("Phone")  
  
    objRs1("Phone") = "(111) 555-1111"  
  
    'Add two new records  
    For i = 0 To 1  
        objRs1.AddNew  
        objRs1(1) = "New Shipper #" & CStr((i + 1))  
        objRs1(2) = "(nnn) 555-" & i & i & i & i  
    Next i  
  
    objRs1.Filter = adFilterPendingRecords  
  
    MsgBox "There are " & objRs1.RecordCount & " records pending.", _  
            , "Filter Pending"  
  
    ' Cancel the updates  
    objRs1.CancelBatch  
'EndFilterPend  
```  
  
## <a name="see-also"></a>参照  
 [バッチ モード](../../../ado/guide/data/batch-mode.md)
