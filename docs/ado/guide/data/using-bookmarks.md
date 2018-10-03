---
title: ブックマークの使用 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- bookmarks [ADO]
- Recordset object [ADO]
ms.assetid: cca244e6-84f8-4394-bca9-f7a819b8f4df
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a083f9d411474769335fdfae32bd59dfe455a9f8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47660640"
---
# <a name="using-bookmarks"></a>ブックマークを使用する
移動した後、特定のレコードに直接戻ると便利です、 **Recordset**すべてのレコードをスクロールし、値を比較する必要はありません。 たとえばを使用してレコードを検索しようとした場合、**検索**メソッドが、検索、レコードが返されない、いずれかの端に自動的に、**レコード セット**。 使用する前に、お客様の場所をマークするブックマークを使用できる、プロバイダーは、それらをサポートする場合、**検索**メソッドの場所に戻れるようにします。 ブックマークは、**バリアント**内のレコードを一意に識別する値を入力、**レコード セット**オブジェクト。  
  
 ブックマークの variant の配列を使用することも、**レコード セットのフィルター**を選択したレコードのセットをフィルター処理するメソッド。 詳細については、この手法は、このトピックでは、結果をフィルタ リングを参照してください[レコード セットの操作](../../../ado/guide/data/working-with-recordsets.md)、このセクションで後述します。  
  
 使用することができます、**ブックマーク**レコード、ブックマークを取得または現在のレコードを設定するプロパティを**レコード セット**オブジェクトを有効なブックマークで識別されるレコード。 次のコードでは、**ブックマーク**ブックマークを設定し、他のレコードに移動した後、ブックマークが設定されたレコードに、返すプロパティ。 かどうかを**レコード セット**ブックマーク、使用をサポートする、**サポート**メソッド。  
  
```  
'BeginBookmarkEg  
Dim varBookmark As Variant  
Dim blnCanBkmrk As Boolean  
  
objRs.Open strSQL, strConnStr, adOpenStatic, adLockOptimistic, adCmdText  
  
If objRs.RecordCount > 4 Then  
    objRs.Move 4                       ' move to the fifth record  
    blnCanBkmrk = objRs.Supports(adBookmark)  
    If blnCanBkmrk = True Then  
        varBookmark = objRs.Bookmark   ' record the bookmark  
        objRs.MoveLast                 ' move to a different record  
        objRs.Bookmark = varBookmark   ' return to the bookmarked (sixth) record  
    End If  
End If  
'EndBookmarkEg  
```  
  
 [サポート](../../../ado/reference/ado-api/supports-method.md)メソッドは、後で詳しく説明します。  
  
 場合を除き、複製された**レコード セット**、ブックマークに固有の**レコード セット**で作成された、同じコマンドを使用する場合でもです。 これは、使用できないことを意味、**ブックマーク**いずれかから取得した**レコード セット**同じレコードが 1 秒あたりに移動する**レコード セット**同じコマンドを使用して開きます。
