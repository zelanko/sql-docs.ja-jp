---
title: プロパティをフィルター処理 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Filter
helpviewer_keywords:
- Filter property
ms.assetid: 80263a7a-5d21-45d1-84fc-34b7a9be4c22
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9dc176d7c64d1845ddb863cd58fd41313967ccce
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="filter-property"></a>プロパティをフィルター処理します。
内のデータにフィルターを示します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。  
  
## <a name="settings-and-return-values"></a>設定と戻り値

取得または設定、**バリアント**値で、次の項目のいずれかを含めることができます。  
  
-   **条件の文字列:** と連結された 1 つまたは複数の個別句から成る文字列**AND**または**OR**演算子。  
  
-   **ブックマークの配列。**一意のブックマークの配列値内のレコードを指す、**レコード セット**オブジェクト。  
  
-   A [FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md)値。  
  
## <a name="remarks"></a>解説

使用して、**フィルター**プロパティ内のレコードを選択して画面を**Recordset**オブジェクト。 フィルター選択された**Recordset**現在のカーソルになります。 その他のプロパティ値を返すことが、現在に基づく**カーソル**は、影響を受けるよう[AbsolutePosition プロパティ (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)、[と、AbsolutePage プロパティ (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)、 [RecordCount プロパティ (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)、および[PageCount プロパティ (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)です。 設定、**フィルター**プロパティに特定の新しい値を新しい値を満たす最初のレコードに現在のレコードに移動します。
  
フォーム内の句の条件の文字列から成る*FieldName 演算子値*(たとえば、 `"LastName = 'Smith'"`)。 個々 の句を連結して複合句を作成することができます**AND** (たとえば、 `"LastName = 'Smith' AND FirstName = 'John'"`) または**OR** (たとえば、 `"LastName = 'Smith' OR LastName = 'Jones'"`)。 条件の文字列の次のガイドラインに従います。

-   *FieldName*から有効なフィールド名にする必要があります、 **Recordset**です。 フィールド名にスペースが含まれている場合は、角かっこで囲んで、名前を囲む必要があります。  
  
-   演算子は、次のいずれかを指定する必要があります: \<、>、 \<=、> =、<>、=、または**など**です。  
  
-   値は、これには、フィールドの値を比較し、値 (たとえば、"smith"から、8/24/95 # 12.345、または 50.00 ドル)。 単一引用符を使用して、文字列と日付にはシャープ記号 (#) を使用します。 数値の場合は、小数点、ドル記号、および科学的表記法を使用できます。 演算子は場合**など**値は、ワイルドカードを使用できます。 アスタリスク (*) とパーセント記号 (%) のワイルドカードのみを使用すると、および文字列の最後の文字であることが必要です。 値を NULL にすることはできません。  
  
> [!NOTE]
>  フィルター値で単一引用符 (') を含めるには、2 つの単一引用符を使用して、1 つを表します。 たとえば、O'Malley でフィルター処理、条件の文字列があります`"col1 = 'O''Malley'"`です。 先頭と末尾のフィルター値の両方に単一引用符を含めるにシャープ記号文字列を囲みます (#)。 たとえば、'1' でフィルター処理、条件の文字列があります`"col1 = #'1'#"`です。  
  
-   間の優先順位がない AND したりします。 句は、かっこで囲まれてグループ化することができます。 ただし、OR で結合句をグループ化と、次のコード スニペットのように、AND で別の句をグループに参加することはできません。  
 `(LastName = 'Smith' OR LastName = 'Jones') AND FirstName = 'John'`  
  
-   このフィルターを作成する代わりに、  
 `(LastName = 'Smith' AND FirstName = 'John') OR (LastName = 'Jones' AND FirstName = 'John')`  
  
-   **など**句、先頭とパターンの末尾にワイルドカードを使用することができます。 たとえば、使用することができます`LastName Like '*mit*'`です。 または**など**パターンの末尾でのみ、ワイルドカードを使用することができます。 たとえば、 `LastName Like 'Smit*'`のようにします。  
  
 フィルター定数しやすく、最後の中に影響を受けたレコードを専用などを表示することにより、バッチ更新モード中に個々 のレコード競合を解決するのには[UpdateBatch メソッド](../../../ado/reference/ado-api/updatebatch-method.md)メソッドの呼び出しです。  
  
設定、**フィルター**プロパティ自体は、基になるデータと競合するため失敗する可能性があります。 たとえば、レコードは既に別のユーザーによって削除されたときに、このエラーが発生することができます。 このような場合は、プロバイダーは警告を返します、[エラー コレクション (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)コレクションが、プログラムの実行は停止しません。 要求されたすべてのレコードの競合がある場合にのみ、実行時にエラーが発生します。 使用して、 [Status プロパティ (ADO レコード セット)](../../../ado/reference/ado-api/status-property-ado-recordset.md)競合しているレコードを検索するプロパティです。  
  
設定、**フィルター**プロパティを長さ 0 の文字列 ("") を使用する場合と同じ効果、 **adFilterNone**定数。
  
ときに、**フィルター**プロパティを設定すると、現在のレコードの位置に移動内のレコードのフィルター処理されたサブセットの最初のレコード、 **Recordset**です。 同様に、ときに、**フィルター**プロパティをオフにすると、現在のレコードの位置に移動の最初のレコード、 **Recordset**です。

仮定します、 **Recordset** sql_variant 型など、いくつかのバリアント型のフィールドの基にフィルターされます。 エラー (DISP_E_TYPEMISMATCH 80020005 または) 条件の文字列で使用するフィールドとフィルター値のサブタイプが一致しない場合に発生します。 たとえばとします。

- A **Recordset**オブジェクト (rs) には、sql_variant 型の列 (C) が含まれています。
- および I4 の種類が 1 個の値がこの列のフィールドに割り当てられています。 条件の文字列に設定されている`rs.Filter = "C='A'"`フィールドにします。

この構成では、実行時にエラーが生成されます。 ただし、`rs.Filter = "C=2"`同じに適用されるフィールドでは、エラーは生成されません。 フィールドは、現在のレコード セットからフィルターで除外します。

参照してください、[ブックマーク プロパティ (ADO)](../../../ado/reference/ado-api/bookmark-property-ado.md)については、フィルター プロパティを使用する配列をビルドすることができますブックマーク値のプロパティです。

フィルター条件文字列の形式で保存されるの内容には影響のみ**Recordset**です。 条件の文字列の例は`OrderDate > '12/31/1999'`します。 ブックマークをまたはから値を使用しての配列が作成されたフィルター、 **FilterGroupEnum**、永続化の内容には影響しません**Recordset**です。 これらの規則は、クライアント側またはサーバー側のカーソルで作成されたレコード セットに適用されます。
  
> [!NOTE]
>  フィルター選択された行と列のフラグを適用すると変更と**レコード セット**バッチ更新モードが、結果として得られる**レコード セット**のキー フィールドに基づく、フィルター選択された場合は空には単一キー テーブルと、変更は、キー フィールドの値で行われました。 結果**Recordset** -空でない場合は、次のステートメントのいずれかが true になります。  
  
-   フィルターは、単一キー テーブルの非キー フィールドに基づいていました。  
  
-   フィルターは、複数キー テーブル内のフィールドに基づいていました。  
  
-   単一キーのテーブル内の非キー フィールドに変更されました。  
  
-   複数キー テーブル内のフィールドで変更されました。  
  
次の表の効果**行と列が**フィルター処理と変更のさまざまな組み合わせでします。 左側の列は、変更を表示します。 任意の非キー フィールド、または単一キーのテーブル内のキー フィールドに複数キー テーブルのキー フィールドのいずれかで変更できます。 最上位の行は、フィルター選択条件を示します。 フィルター処理できますに基づいて任意の非キー フィールドで、単一キーのテーブルでは、または複数キー テーブルのキー フィールドのいずれかのキー フィールド。 交差するセルは、結果を表示します。 A **+** プラス記号は、適用されることを意味**行と列が**結果、空でない、 **Recordset**です。 A **-** マイナス記号は、空**Recordset**です。  
  
||非キー|1 つのキー|複数のキー|
|-|--------------|----------------|-------------------|
|**非キー**|+|+|+|
|**1 つのキー**|+|-|なし|
|**複数のキー**|+|なし|+|
|||||
  
## <a name="applies-to"></a>適用対象

[Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照

[フィルターおよび RecordCount のプロパティの例 (VB)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vb.md)
[フィルターと RecordCount のプロパティの例 (vc++)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vc.md)
[Clear メソッド (ADO)](../../../ado/reference/ado-api/clear-method-ado.md) 
[(ADO) のプロパティ-動的な最適化](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)
