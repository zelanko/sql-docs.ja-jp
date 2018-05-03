---
title: ブックマークの使用 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- bookmarks [ADO]
- Recordset object [ADO]
ms.assetid: cca244e6-84f8-4394-bca9-f7a819b8f4df
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e0b6c3f4918d26a801247fbeaf8e3eeeee5619ab
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-bookmarks"></a>ブックマークの使用
移動した後、特定のレコードに直接取得すると便利です、 **Recordset**すべてのレコードをスクロールし、値を比較する必要はありません。 たとえばを使用してレコードを検索しようとする場合、**検索**メソッドが、検索、レコードが返されない、いずれかの端に自動的に、**レコード セット**です。 位置をマークを使用する前にブックマークを使用できる、プロバイダーは、それらをサポートする場合、**検索**メソッドの場所に戻れるようにします。 ブックマークは、**バリアント**内のレコードを一意に識別する値を入力、 **Recordset**オブジェクト。  
  
 ブックマークの variant の配列を使用することも、**レコード セットのフィルター**を選択したレコードのセットをフィルター処理するメソッド。 この手法についての詳細については、「」で結果をフィルター選択[レコード セットを操作](../../../ado/guide/data/working-with-recordsets.md)、このセクションで後述します。  
  
 使用することができます、**ブックマーク**のレコード、ブックマークを取得またはで現在のレコードを設定するプロパティ、**レコード セット**レコードの有効なブックマークによって識別されるオブジェクト。 次のコードでは、**ブックマーク**プロパティをブックマークを設定し、その他のレコードに移動した後、ブックマークが設定されたレコードに戻ります。 かどうかを**Recordset**ブックマーク、使用をサポートする、**をサポートしている**メソッドです。  
  
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
  
 場合を除き、複製された**レコード セット**、ブックマークに固有の**レコード セット**で作成された、同じコマンドを使用する場合でもです。 つまり、使用できません、**ブックマーク**いずれかから取得した**レコード セット**同じレコードが 1 秒あたりに移動する**レコード セット**同じコマンドを使用して開いたです。
