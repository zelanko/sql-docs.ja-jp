---
title: Filter プロパティ |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Filter
helpviewer_keywords:
- Filter property
ms.assetid: 80263a7a-5d21-45d1-84fc-34b7a9be4c22
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ff06bc27e765945d1cca74b5f8401e0caadf6b17
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67918635"
---
# <a name="filter-property"></a>Filter プロパティ
[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)内のデータのフィルターを示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値

**バリアント**値を設定または返します。この値には、次のいずれかの項目を含めることができます。  
  
-   **条件文字列:****AND**また**は or**演算子と連結された1つ以上の個別の句で構成される文字列。  
  
-   **ブックマークの配列:** レコード**セット**オブジェクトのレコードを指す一意のブックマーク値の配列。  
  
-   [Filtergroupenum](../../../ado/reference/ado-api/filtergroupenum.md)値。  
  
## <a name="remarks"></a>Remarks

**フィルター**プロパティを使用して、レコード**セット**オブジェクトのレコードを選択的に表示します。 フィルター選択された**レコードセット**が現在のカーソルになります。 現在の**カーソル**に基づいて値を返すその他のプロパティは、 [ABSOLUTEPOSITION property (ado)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)、 [AbsolutePage property (ado)](../../../ado/reference/ado-api/absolutepage-property-ado.md)、 [RecordCount Property (ADO](../../../ado/reference/ado-api/recordcount-property-ado.md))、および[PageCount property (ado)](../../../ado/reference/ado-api/pagecount-property-ado.md)などの影響を受けます。 **Filter**プロパティを特定の新しい値に設定すると、現在のレコードが、新しい値を満たす最初のレコードに移動します。
  
条件文字列は、 *FieldName-Operator-Value*という形式の句で構成されてい`"LastName = 'Smith'"`ます (例:)。 複合句を作成するには、個別の句を**AND** (たとえば`"LastName = 'Smith' AND FirstName = 'John'"`、) また**は or** (など`"LastName = 'Smith' OR LastName = 'Jones'"`) と連結します。 条件文字列の場合は、次のガイドラインに従います。

-   *FieldName*は、**レコードセット**の有効なフィールド名である必要があります。 フィールド名にスペースが含まれている場合は、名前を角かっこで囲む必要があります。  
  
-   演算子は、 \<、>、 \<=、>=、 <>、=、または**LIKE**のいずれかである必要があります。  
  
-   値は、フィールド値の比較に使用する値です (例、' Smith '、#8/24/95 #、12.345、$50.00)。 文字列とシャープ記号 (#) を使用して、単一引用符を使用します。 数値の場合は、小数点、ドル記号、および指数表記を使用できます。 Operator が**LIKE**の場合、値にはワイルドカードを使用できます。 アスタリスク (*) とパーセント記号 (%) のみワイルドカードを使用できます。また、文字列の最後の文字である必要があります。 値を null にすることはできません。  
  
> [!NOTE]
>  フィルター値に単一引用符 (') を含めるには、2つの単一引用符を使用して1つのを表します。 たとえば、O'Malley に対してフィルター処理を行うには、 `"col1 = 'O''Malley'"`条件文字列をにする必要があります。 フィルター値の先頭と末尾の両方に単一引用符を含めるには、文字列をシャープ記号 (#) で囲みます。 たとえば、' 1 ' でフィルター処理するには、条件文字列を`"col1 = #'1'#"`にする必要があります。  
  
-   AND と OR の間には優先順位がありません。 句は、かっこ内でグループ化できます。 ただし、次のコードスニペットのように、OR で結合された句をグループ化してから、とを使用して別の句にグループを結合することはできません。  
 `(LastName = 'Smith' OR LastName = 'Jones') AND FirstName = 'John'`  
  
-   代わりに、次のようにこのフィルターを構築します。  
 `(LastName = 'Smith' AND FirstName = 'John') OR (LastName = 'Jones' AND FirstName = 'John')`  
  
-   **LIKE**句では、パターンの先頭と末尾にワイルドカードを使用できます。 たとえば、`LastName Like '*mit*'` を使用できます。 また、 **LIKE**では、パターンの最後でのみワイルドカードを使用できます。 たとえば、`LastName Like 'Smit*'` のようにします。  
  
 フィルター定数を使用すると、バッチ更新モード中に個々のレコードの競合を解決しやすくなります。たとえば、最後の[UpdateBatch メソッド](../../../ado/reference/ado-api/updatebatch-method.md)メソッド呼び出しの間に影響を受けたレコードだけを表示できます。  
  
**フィルター**プロパティ自体の設定は、基になるデータとの競合によって失敗する可能性があります。 たとえば、このエラーは、レコードが別のユーザーによって既に削除されている場合に発生する可能性があります。 このような場合、プロバイダーは[エラーコレクション (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)コレクションに警告を返しますが、プログラムの実行を停止することはありません。 実行時のエラーは、要求されたすべてのレコードに競合がある場合にのみ発生します。 競合しているレコードを検索するには、 [Status プロパティ (ADO Recordset)](../../../ado/reference/ado-api/status-property-ado-recordset.md)プロパティを使用します。  
  
**Filter**プロパティを長さ0の文字列 ("") に設定すると、 **adfilternone**定数を使用する場合と同じ効果があります。
  
**フィルター**プロパティが設定されている場合、現在のレコードの位置は、レコード**セット**内のフィルター処理されたレコードセット内の最初のレコードに移動します。 同様に、**フィルター**プロパティをクリアすると、現在のレコード位置がレコード**セット**内の最初のレコードに移動します。

たとえば、sql_variant 型など、バリアント型のフィールドに基づいて**レコードセット**がフィルター処理されるとします。 条件文字列で使用されているフィールドとフィルター値のサブタイプが一致しない場合、エラー (DISP_E_TYPEMISMATCH または 80020005) が発生します。 たとえば、次のように想定します。

- **レコードセット**オブジェクト (rs) には、sql_variant 型の列 (C) が含まれています。
- この列のフィールドには、I4 型の値1が割り当てられています。 条件文字列は、フィールドで`rs.Filter = "C='A'"`に設定されます。

この構成では、実行時にエラーが生成されます。 ただし、 `rs.Filter = "C=2"`同じフィールドに適用してもエラーは生成されません。 また、フィールドが現在のレコードセットから除外されます。

[ブックマークの[プロパティ (ADO)](../../../ado/reference/ado-api/bookmark-property-ado.md) ] プロパティを参照してください。ブックマークの値によって、Filter プロパティで使用する配列を作成できます。

条件文字列の形式のフィルターのみが、永続化された**レコードセット**の内容に影響します。 条件文字列の例として`OrderDate > '12/31/1999'`は、があります。 ブックマークの配列を使用して作成されたフィルター、または**Filtergroupenum**の値を使用して作成されたフィルターは、永続化された**レコードセット**の内容には影響しません。 これらのルールは、クライアント側カーソルまたはサーバー側カーソルを使用して作成されたレコードセットに適用されます。
  
> [!NOTE]
>  バッチ更新モードでフィルター処理および変更されたレコード**セット**に adFilterPendingRecords フラグを適用すると、フィルター処理が単一キーテーブルのキーフィールドに基づいており、キーフィールド値に対して変更が行われた場合、結果の**レコードセット**は空になります。 次のいずれかのステートメントが true の場合、結果の**レコードセット**は空になりません。  
  
-   フィルター処理は、単一キーテーブルのキー以外のフィールドに基づいていました。  
  
-   フィルター処理は、複数のキーを持つテーブルのフィールドに基づいていました。  
  
-   1つのキーを持つテーブルのキー以外のフィールドに変更が加えられました。  
  
-   複数のキーを持つテーブルのフィールドに対して変更が行われました。  
  
次の表は、フィルター処理と変更のさまざまな組み合わせにおける**Adfilterpendingrecords**の影響をまとめたものです。 左側の列には、考えられる変更が示されています。 キーを使用しない任意のフィールド、単一キーテーブルのキーフィールド、または複数のキーが設定されたテーブルのいずれかのキーフィールドに対して変更を行うことができます。 一番上の行には、フィルターの条件が表示されます。 フィルター処理は、非キーフィールド、単一キーテーブルのキーフィールド、または複数のキーが設定されたテーブルのいずれかのキーフィールドに基づいて行うことができます。 交差するセルに結果が表示されます。 プラス**+** 記号は、 **Adfilterpendingrecords**を適用すると、空ではない**レコードセット**が生成されることを意味します。 負**-** 符号は空の**レコードセット**を意味します。  
  
||非キー|1つのキー|複数のキー|
|-|--------------|----------------|-------------------|
|**非キー**|+|+|+|
|**1つのキー**|+|-|なし|
|**複数のキー**|+|なし|+|
|||||
  
## <a name="applies-to"></a>適用対象

[Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照

[Filter および recordcount プロパティの例 (VB)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vb.md)
[フィルターと recordcount プロパティの例 (VC + +)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vc.md)
[Clear メソッド (ado)](../../../ado/reference/ado-api/clear-method-ado.md)
[Optimize プロパティ-動的 (ado)](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)
