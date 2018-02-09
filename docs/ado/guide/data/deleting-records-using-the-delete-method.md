---
title: "Delete メソッドを使用してレコードを削除する |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ADO, deleting records
- deleting records [ADO]
- editing data [ADO], Delete method
- Delete method [ADO]
ms.assetid: bfed5cfa-7f57-463b-9da2-0c612a079d30
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 23238ea9992931cea607feb3fbd73ddefb9201f3
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="deleting-records-using-the-delete-method"></a>Delete メソッドを使用してレコードを削除します。
使用して、**削除**メソッドは、現在のレコードまたはレコードのグループを示します、 **Recordset**オブジェクトを削除します。 場合、 **Recordset**オブジェクトは、他のレコードの削除を許可しないため、エラーが発生します。 即時更新モードの場合は、削除はすぐに、データベースで発生します。 呼び出し後に、レコードが編集モードのままは場合 (たとえば、データベース整合性違反) のため、レコードが正常に削除できません、**更新します。** つまりを使用して、更新をキャンセルする必要があります[ただし](../../../ado/reference/ado-api/cancelupdate-method-ado.md)現在のレコードから移動する前に (たとえばを使用して[閉じる](../../../ado/reference/ado-api/close-method-ado.md)、[移動](../../../ado/reference/ado-api/move-method-ado.md)、または[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md))。  
  
 バッチ更新モードの場合は、レコードがキャッシュからの削除とマークされてし、実際の削除の動作を呼び出すとき、 **UpdateBatch**メソッドです。 (削除されたレコードを表示するには、次のように設定します、**フィルター**プロパティを**adFilterAffectedRecords**後**削除**と呼びます。)。  
  
 削除されたレコードからフィールド値を取得しようとすると、エラーが生成されます。 現在のレコードを削除すると、削除されたレコードのまま別のレコードに移動するまでです。 移動した後、削除されたレコードからアクセスできなくなります。  
  
 使用して削除されたレコードを回復するには、トランザクションで削除を入れ子にする場合、 **RollbackTrans**メソッドです。 バッチ更新モードでは、取り消すことができます、保留中の削除または保留中の削除のグループを使用して、 **CancelBatch**メソッドです。  
  
 基になるデータとの競合のためのレコードを削除する試行が失敗した場合 (たとえば、レコードが別のユーザーによって既に削除されている場合)、プロバイダーに警告を返し、**エラー**コレクション プログラムは停止されませんが、実行します。 要求されたすべてのレコードの競合がある場合にのみ、実行時エラーが発生します。  
  
 場合、**一意テーブル**動的なプロパティが設定されて、**レコード セット**は、複数のテーブルに対して結合操作の実行結果、**削除**メソッド行のみが削除されます指定したテーブルから、**一意テーブル**プロパティです。  
  
 **削除**メソッドで対象となるレコードを指定する省略可能な引数を取る、**削除**操作します。 この引数の唯一の有効な値は、次の ADO のいずれかの**AffectEnum**列挙定数。  
  
-   **adAffectCurrent**現在のレコードのみに影響します。  
  
-   **adAffectGroup**現在に適合するレコードのみに影響を与える**フィルター**プロパティの設定。 **フィルター**プロパティに設定する必要があります、 **FilterGroupEnum**値または配列の**ブックマーク**このオプションを使用します。  
  
 次のコードを指定する例を示します**adAffectGroup**を呼び出すときに、**削除**メソッドです。 この例では、レコードの一部をサンプルに追加**Recordset**し、データベースを更新します。 フィルターが適用し、**レコード セット**を使用して、 **adFilterAffectedRecords**新しく追加されたレコードだけをそのままの表示フィルター列挙型定数、**レコード セット。** 最後、**削除**メソッドことを指定し、すべてのレコードを現在を満たす**フィルター**プロパティの設定 (新しいレコード) を削除する必要があります。  
  
```  
'BeginDeleteGroup  
    'add some bogus records  
    With objRs  
        For i = 0 To 8  
            .AddNew  
            .Fields("CompanyName") = "Shipper Number " & i + 1  
            .Fields("Phone") = "(425) 555-000" & (i + 1)  
            .Update  
        Next i  
  
        ' update  
        .UpdateBatch  
  
        'filter on newly added records  
        .Filter = adFilterAffectedRecords  
        Debug.Print "Deleting the " & .RecordCount & _  
                    " records you just added."  
  
        'delete the newly added bogus records  
        .Delete adAffectGroup  
        .Filter = adFilterNone  
        Debug.Print .RecordCount & " records remain."  
    End With  
'EndDeleteGroup  
```
