---
title: "Clone メソッド (ADO) |Microsoft ドキュメント"
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
- Recordset20::Clone
- Recordset20::raw_Clone
helpviewer_keywords: Clone method [ADO]
ms.assetid: ad49265f-1c05-4271-9bbf-7c00010ac18c
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b0fa4429b66b8a43bf2eecccca1fbc94597f07a5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="clone-method-ado"></a>Clone メソッド (ADO)
複製を作成[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) 、既存のオブジェクト**Recordset**オブジェクト。 必要に応じて、複製が読み取り専用であることを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set rstDuplicate = rstOriginal.Clone (LockType)  
```  
  
## <a name="return-value"></a>戻り値  
 返します、 **Recordset**オブジェクト参照。  
  
#### <a name="parameters"></a>パラメーター  
 *rstDuplicate*  
 重複を識別するオブジェクト変数**Recordset**オブジェクトを作成します。  
  
 *rstOriginal*  
 オブジェクト変数を識別する、 **Recordset**は重複するオブジェクト。  
  
 *ロック。*  
 省略可。 A [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) 、元のいずれか、ロックの種類を指定する値**Recordset**、または読み取り専用**Recordset**です。 有効な値は**adLockUnspecified**または**adLockReadOnly**です。  
  
## <a name="remarks"></a>解説  
 使用して、**クローン**を複数作成するメソッドが重複して**Recordset**オブジェクトを指定したレコード セットの 1 つ以上の現在のレコードを維持する場合に特にです。 使用して、**クローン**メソッドが作成して、新しいよりも効率的**Recordset**元として、同じ定義を使用するオブジェクト。  
  
 [フィルター](../../../ado/reference/ado-api/filter-property.md) 、元のプロパティ**Recordset**、いずれか、複製には適用されない場合、します。 設定、**フィルター**新しいプロパティ**Recordset**結果をフィルター処理します。 既存のすべてをコピーする最も簡単な方法**フィルター**値は、次のように、直接割り当てることができます。  
  
```  
rsNew.Filter = rsOriginal.Filter  
```  
  
 新しく作成された複製の現在のレコードは、最初のレコードに設定されます。  
  
 いずれかに加えた**Recordset**オブジェクトがすべてのカーソルの種類に関係なく複製で表示されます。 ただしを実行する前後[Requery](../../../ado/reference/ado-api/requery-method.md)元の**Recordset**クローンは、元に同期できなくします。  
  
 元の終了**レコード セット**は、そのコピーを閉じませんも閉じるコピーの終了では、元または他のコピーのいずれか。  
  
 複製することしか、 **Recordset**ブックマークをサポートするオブジェクト。 ブックマークの値は同義です。いずれかからのブックマーク参照は、 **Recordset**オブジェクトの複製のいずれかで同じレコードを参照します。  
  
 いくつか**Recordset**も、トリガーされるイベントがすべて発生**レコード セット**のクローンを作成します。 ただし、現在のレコードが異なるために複製**レコード セット**イベントは、複製の有効でない可能性があります。 たとえば、フィールドの値を変更する場合、 [WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md) 、変更後のイベントが発生する**レコード セット**とすべてのクローンでします。 *フィールド*のパラメーター、 **WillChangeField**のクローン イベント**Recordset** (ここで、変更が加えられません) では、複製の現在のレコードのフィールドを参照元の現在のレコードよりも別のレコードである**レコード セット**変更が発生しました。  
  
 次の表に、すべての完全一覧**Recordset**イベント。 有効でを使用して生成されたすべてのレコード セットの複製のトリガーされたかどうかを示します、**クローン**メソッドです。  
  
|イベント|クローンで発生しますか。|  
|-----------|--------------------------|  
|[EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|不可|  
|[FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|不可|  
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md)|不可|  
|[FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|可|  
|[MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|不可|  
|[RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|可|  
|[RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|不可|  
|[WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|可|  
|[WillChangeRecord](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|可|  
|[WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|不可|  
|[WillMove](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|不可|  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [メソッドの例 (VB) の複製します。](../../../ado/reference/ado-api/clone-method-example-vb.md)   
 [メソッドの例 (VBScript) の複製します。](../../../ado/reference/ado-api/clone-method-example-vbscript.md)   
 [Clone メソッドの例 (VC++)](../../../ado/reference/ado-api/clone-method-example-vc.md)   
