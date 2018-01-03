---
title: "Move メソッド (ADO) |Microsoft ドキュメント"
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
apitype: COM
f1_keywords:
- Recordset15::Move
- Recordset15::raw_Move
helpviewer_keywords: Move method [ADO]
ms.assetid: 13fe9381-d00b-4f4a-9162-83c3f21b3837
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 47239335259fc7bee4d01ef01741e4148f1a3ea0
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="move-method-ado"></a>Move メソッド (ADO)
現在のレコードの位置を移動、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
recordset.Move NumRecords, Start  
```  
  
#### <a name="parameters"></a>パラメーター  
 *NumRecords*  
 符号付き**長い**レコードの現在の位置を移動するレコードの数を指定する式。  
  
 *開始*  
 省略可。 A**文字列**値または**バリアント**ブックマークに評価されます。 使用することも、 [BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md)値。  
  
## <a name="remarks"></a>解説  
 **移動**メソッドがすべてでサポートされている**Recordset**オブジェクト。  
  
 場合、 *NumRecords*引数は、0 より大きい値は、現在のレコードの位置を前方に移動 (の終了に向けて、 **Recordset**)。 場合*NumRecords*が現在のレコードの位置は後方に移動、0 より小さい (の先頭に向かって、 **Recordset**)。  
  
 場合、**移動**呼び出しは先頭レコードの前に、のポイントに現在のレコードの位置を移動すると、ADO レコード セット内の最初のレコードの前に位置する現在のレコードの設定 ([BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)は**は True。**). 旧バージョンとされる場合に移動しよう、 **BOF**プロパティが既に**True**でエラーが生成されます。  
  
 場合、**移動**呼び出しは最後のレコードの後のポイントに現在のレコードの位置を移動すると、ADO レコード セットの最後のレコードの後に、現在のレコードを位置に設定する ([EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)は**は True。**). ときに前方に移動しよう、 **EOF**プロパティが既に**True**でエラーが生成されます。  
  
 呼び出す、**移動**メソッドは空の**Recordset**オブジェクト、エラーが発生します。  
  
 渡す場合、*開始*引数は、このブックマーク レコードに対して相対的です。 移動と仮定した場合、**レコード セット**オブジェクトは、ブックマークをサポートしています。 指定しない場合、現在のレコード相対移動パスです。  
  
 使用している場合、 [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)受け渡し、プロバイダーからのレコードをローカルにキャッシュするプロパティ、 *NumRecords*引数キャッシュされているレコードの現在のグループの外側、現在のレコードの位置を移動します。強制的にレコードを送信先レコードからの新しいグループを取得します。 **CacheSize**プロパティは、新たに取得したグループのサイズを決定し、送信先レコードは、最初のレコードを取得します。  
  
 場合、 **Recordset**オブジェクトは順方向専用、ユーザーに渡すことができますが、 *NumRecords* 0 より小さい引数がキャッシュされているレコードの現在のセット内に、変換先を指定します。 場合、**移動**呼び出しは、現在のレコードの位置のレコードに移動最初のキャッシュされたレコードの前に、エラーが発生します。 したがって、前方スクロールのみをサポートするプロバイダーで、完全スクロールをサポートしているレコードのキャッシュを使用できます。 キャッシュされているレコードがメモリに読み込まれ、ために、レコードのために必要な数のキャッシュを回避する必要があります。 順方向専用の場合でも**レコード セット**呼び出すオブジェクトでサポートされる旧バージョンとは、この方法で移動、 [MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)メソッドいずれかを順方向専用**レコード セット**オブジェクトがあります。エラーを生成します。  
  
> [!NOTE]
>  順方向専用の逆行サポート**Recordset**プロバイダーによっては、予測可能ではありません。 現在のレコードは、後の最後のレコードに位置付けられている場合、 **Recordset**、**移動**後方されないことがある現在の位置が正しい。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [メソッドの例 (VB) を移動します。](../../../ado/reference/ado-api/move-method-example-vb.md)   
 [メソッドの例 (VBScript) を移動します。](../../../ado/reference/ado-api/move-method-example-vbscript.md)   
 [メソッドの例 (vc++) に移動します。](../../../ado/reference/ado-api/move-method-example-vc.md)   
 [MoveFirst、MoveLast、MoveNext、および MovePrevious メソッド (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [MoveFirst、MoveLast、MoveNext、および MovePrevious メソッド (RDS)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)   
 [MoveRecord メソッド (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)
