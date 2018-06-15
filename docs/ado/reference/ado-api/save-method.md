---
title: Save メソッド |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Recordset::Save
- _Recordset::raw_Save
helpviewer_keywords:
- Save method [ADO]
ms.assetid: ed3d9678-5c28-4e61-8bb3-7dfb66d99cf5
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a92e053443dbb32aae83756a98facdc53fa74725
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35281441"
---
# <a name="save-method"></a>Save メソッド
保存、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)ファイルまたは[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
recordset.Save Destination, PersistFormat  
```  
  
#### <a name="parameters"></a>パラメーター  
 *変換先*  
 任意。 A**バリアント**ファイルの完全なパス名を表す場所、 **Recordset**を保存するまたはへの参照、**ストリーム**オブジェクト。  
  
 *PersistFormat*  
 任意。 A [PersistFormatEnum](../../../ado/reference/ado-api/persistformatenum.md)する形式を指定する値、 **Recordset** (XML または adtg 形式) に保存します。 既定値は**adPersistADTG**です。  
  
## <a name="remarks"></a>コメント  
 [Save メソッド](../../../ado/reference/ado-api/save-method.md)メソッドは、開いているでのみ呼び出すこと**Recordset**です。 使用して、 [Open メソッド (ADO レコード セット)](../../../ado/reference/ado-api/open-method-ado-recordset.md)後で復元する方法、**レコード セット**から*先*です。  
  
 場合、[フィルター プロパティ](../../../ado/reference/ado-api/filter-property.md)プロパティは、有効で、 **Recordset**フィルターでアクセス可能な行のみを保存し、します。 場合、**レコード セット**は階層構造、現在の子では、**レコード セット**とその子を保存する親を含む**レコード セット**です。 場合、子の Save メソッド**レコード セット**が呼び出されると、子とその子をすべて保存されますが、親はありません。  
  
 最初に保存するとき、**レコード セット**を指定する省略可能である*先*です。 省略した場合*先*の Source プロパティの値に設定の名前を持つ新しいファイルが作成する、**レコード セット**です。  
  
 省略*先*関数を呼び出すと**保存**後の最初の保存または実行時エラーが発生します。 後で呼び出す場合は、**保存**を新しい*先*、**レコード セット**は新しい場所に保存します。 ただし、新しい移行先と元の送信先が両方開いています。  
  
 **保存**閉じません、**レコード セット**または*先*で作業を続行できるように、**レコード セット**し、最新の変更を保存します。 *移行先*まで開いたまま、 **Recordset**が閉じられます。  
  
 セキュリティ上の理由から、**保存**メソッドは、Microsoft Internet Explorer によって実行されるスクリプトからの低、カスタムのセキュリティ設定の使用のみを許可します。  
  
 場合、**保存**中に、非同期メソッドが呼び出された**レコード セット**フェッチ、実行、または更新操作が進行状況をし**保存**非同期操作まで待機完了しました。  
  
 最初の行で始まるレコードが保存された、 **Recordset**です。 ときに、**保存**メソッドが完了すると、現在の行位置はの最初の行に移動、 **Recordset**です。  
  
 最良の結果を次のように設定します。、 [CursorLocation プロパティ (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティを**adUseClient**で**保存**です。 かどうか、プロバイダーがサポートしないすべての機能を保存するために必要な**レコード セット**オブジェクト、カーソル サービスはその機能を提供します。  
  
 ときに、 **Recordset**に保存されて、 **CursorLocation**プロパティに設定**adUseServer**の更新機能、 **Recordset**は制限されます。 通常、のみ 1 つのテーブルの更新、挿入、および削除が (プロバイダーの機能に依存する) を使用できます。 [メソッドの再同期](../../../ado/reference/ado-api/resync-method.md)メソッドもこの構成では使用できません。  
  
> [!NOTE]
>  保存、 **Recordset**で**フィールド**型の**adVariant**、**追加**、または**しようとする**はADO によってサポートされず、予期しない結果が生じることができます。  
  
 のみをフィルター処理条件文字列の形式で (例: OrderDate > ' 12/31/1999 ') の保存される内容に影響を与える**レコード セット**です。 配列が作成されたフィルター**ブックマーク**から値を使用するか、 [FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md) 、永続化の内容は変わりません**Recordset**です。 これらの規則を適用する**Recordset**クライアント側またはサーバー側のカーソルで作成されました。  
  
 *先*パラメーターは OLE DB IStream インターフェイスをサポートする任意のオブジェクトに使用できる、保存することができます、**レコード セット**ASP 応答オブジェクトに直接できます。 詳細についてを参照してください、 **XML レコード セットを永続化シナリオ**です。  
  
 保存することも、 **Recordset** MSXML の DOM オブジェクトのインスタンスを XML 形式で、次の Visual Basic コードに示すようとしては。  
  
```  
Dim xDOM As New MSXML.DOMDocument  
Dim rsXML As New ADODB.Recordset  
Dim sSQL As String, sConn As String  
  
sSQL = "SELECT customerid, companyname, contactname FROM customers"  
sConn="Provider=Microsoft.Jet.OLEDB.4.0;Data Source=Northwind.mdb"  
rsXML.Open sSQL, sConn  
rsXML.Save xDOM, adPersistXML   'Save Recordset directly into a DOM tree.  
...  
```  
  
> [!NOTE]
>  階層のレコード セット (データ図形) を XML 形式で保存するときに、2 つの制限が適用されます。 場合は、XML に保存することはできません、階層**レコード セット**保留中の更新を含むパラメーター化されたを保存することはできませんと階層**レコード セット**です。  
  
 A **Recordset**保存で XML 形式が保存 utf-8 形式を使用します。 ADO ストリームにこのようなファイルが読み込まれると、ストリーム オブジェクトを開こうとしていない、 **Recordset**ストリームからストリームの文字セット プロパティを適切な utf-8 形式の値に設定しない限り、します。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Stream オブジェクト (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|  
  
## <a name="see-also"></a>参照  
 [保存して開く方法の例 (VB)](../../../ado/reference/ado-api/save-and-open-methods-example-vb.md)   
 [保存して開く方法の例 (vc++)](../../../ado/reference/ado-api/save-and-open-methods-example-vc.md)   
 [Open メソッド (ADO レコード セット)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open メソッド (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [SaveToFile メソッド](../../../ado/reference/ado-api/savetofile-method.md)
