---
title: "プロパティをフィルター処理 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset15::Filter
helpviewer_keywords:
- Filter property
ms.assetid: 80263a7a-5d21-45d1-84fc-34b7a9be4c22
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6aa8e2349bfd564d0cc72d8d17169c6a5ada5f07
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="filter-property"></a>プロパティをフィルター処理します。
内のデータにフィルターを示します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 取得または設定、**バリアント**値で、次のいずれかを含めることができます。  
  
-   **条件の文字列**ビルダー 文字列と連結された 1 つまたは複数の個別句から成る**AND**または**OR**演算子。  
  
-   **ブックマークの配列**ビルダー 一意のブックマークの配列値内のレコードを指す、 **Recordset**オブジェクト。  
  
-   A [FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md)値。  
  
## <a name="remarks"></a>解説  
 使用して、**フィルター**プロパティ内のレコードを選択して画面を**Recordset**オブジェクト。 フィルター選択された**Recordset**現在のカーソルになります。 その他のプロパティ値を返すことが、現在に基づく**カーソル**は、影響を受けるよう[AbsolutePosition プロパティ (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)、[と、AbsolutePage プロパティ (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)、 [RecordCount プロパティ (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)、および[PageCount プロパティ (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)です。 これは、設定するため、**フィルター**プロパティを特定の値には、新しい値を満たす最初のレコードを現在のレコードを移動します。  
  
 フォーム内の句の条件の文字列から成る*FieldName 演算子値*(たとえば、 `"LastName = 'Smith'"`)。 個々 の句を連結して複合句を作成することができます**AND** (たとえば、 `"LastName = 'Smith' AND FirstName = 'John'"`) または**OR** (たとえば、 `"LastName = 'Smith' OR LastName = 'Jones'"`)。 条件の文字列の次のガイドラインを使用します。  
  
-   *FieldName*から有効なフィールド名にする必要があります、 **Recordset**です。 フィールド名にスペースが含まれている場合は、角かっこで囲んで、名前を囲む必要があります。  
  
-   演算子は、次のいずれかを指定する必要があります: \<、>、 \<=、> =、<>、=、または**など**です。  
  
-   値は、これには、フィールドの値を比較し、値 (たとえば、"smith"から、8/24/&#95; 12.345、または 50.00 ドル)。 単一引用符を使用して、文字列と日付にはシャープ記号 (#) を使用します。 数値の場合は、小数点、ドル記号、および科学的表記法を使用できます。 演算子は場合**など**値は、ワイルドカードを使用できます。 アスタリスク (*) とパーセント記号 (%) のワイルドカードのみを使用すると、および文字列の最後の文字であることが必要です。 値を NULL にすることはできません。  
  
> [!NOTE]
>  フィルター値で単一引用符 (') を含めるには、2 つの単一引用符を使用して、1 つを表します。 たとえば、O'Malley でフィルター処理、条件の文字列があります"col1 = 'O' Malley'"です。 先頭と末尾のフィルター値の両方に単一引用符を含めるにシャープ記号文字列を囲みます (#)。 たとえば、'1' でフィルター処理、条件の文字列があります"col&#1;' 1' を = #"です。  
  
-   間の優先順位がない AND したりします。 句は、かっこで囲まれてグループ化することができます。 ただし、OR で結合句をグループ化と、次のように、AND で別の句をグループに参加することはできません。`(LastName = 'Smith' OR LastName = 'Jones') AND FirstName = 'John'`  
  
-   このフィルターを作成する代わりに、`(LastName = 'Smith' AND FirstName = 'John') OR (LastName = 'Jones' AND FirstName = 'John')`  
  
-   **と同様に**句、先頭とパターンの末尾にワイルドカードを使用することができます (LastName のような例では、' * mit\*')、またはパターンの末尾でのみ (LastName のような例では、' Smit\*')。  
  
 フィルター定数しやすく、最後の中に影響を受けたレコードを専用などを表示することにより、バッチ更新モード中に個々 のレコード競合を解決するのには[UpdateBatch メソッド](../../../ado/reference/ado-api/updatebatch-method.md)メソッドの呼び出しです。  
  
 基になるデータとの競合に失敗する可能性、フィルター プロパティ自体の設定 (たとえば、レコードが既に削除されて別のユーザーによって)。 このような場合は、プロバイダーは警告を返します、[エラー コレクション (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)コレクションがいないプログラムの実行を停止します。 要求されたすべてのレコードの競合がある場合にのみ、実行時エラーが発生します。 使用して、 [Status プロパティ (ADO レコード セット)](../../../ado/reference/ado-api/status-property-ado-recordset.md)競合しているレコードを検索するプロパティです。  
  
 設定、**フィルター**プロパティを長さ 0 の文字列 ("") を使用する場合と同じ効果、 **adFilterNone**定数。  
  
 ときに、**フィルター**プロパティを設定すると、現在のレコードの位置に移動内のレコードのフィルター処理されたサブセットの最初のレコード、 **Recordset**です。 同様に、ときに、**フィルター**プロパティをオフにすると、現在のレコードの位置に移動の最初のレコード、 **Recordset**です。  
  
 ときに、 **Recordset**はフィルタ リング バリアント型 (sql_variant など)、エラーのフィールド条件の文字列で使用するフィールドとフィルター値のサブタイプが一致しない場合 (DISP_E_TYPEMISMATCH または 80020005) が発生します。 たとえば場合、**レコード セット**オブジェクト (rs) には sql_variant 型の列 (C) が含まれ、この列のフィールドに rs の条件の文字列を設定、I4 型の 1 の値が割り当てられています。フィルター ="C = 'A'"フィールドにエラーが生成されます、実行時にします。 ただし、rs です。フィルター =「C = 2」に適用されるフィールドは、現在のレコード セットから除外されますがフィールドは、エラーも返りません。  
  
 参照してください、[ブックマーク プロパティ (ADO)](../../../ado/reference/ado-api/bookmark-property-ado.md)については、フィルター プロパティを使用する配列をビルドすることができますブックマーク値のプロパティです。  
  
 のみをフィルター処理条件文字列の形式で (例: OrderDate > ' 12/31/1999 ') の保存される内容に影響を与える**レコード セット**です。 配列のブックマークを使用したフィルターを作成または、永続化の内容を与えません、FilterGroupEnum から値を使用して**Recordset**です。 これらの規則は、クライアント側またはサーバー側のカーソルで作成されたレコード セットに適用されます。  
  
> [!NOTE]
>  フィルター選択された行と列のフラグを適用すると変更と**レコード セット**バッチ更新モードが、結果として得られる**レコード セット**のキー フィールドに基づく、フィルター選択された場合は空には単一キー テーブルと、変更は、キー フィールドの値で行われました。 結果**Recordset** -空でない場合は、次のいずれかが true になります。  
  
-   フィルターは、単一キー テーブルの非キー フィールドに基づいていました。  
  
-   フィルターは、複数キー テーブル内のフィールドに基づいていました。  
  
-   単一キーのテーブル内の非キー フィールドに変更されました。  
  
-   複数キー テーブル内のフィールドで変更されました。  
  
 次の表の効果**行と列が**フィルター処理と変更のさまざまな組み合わせでします。 左側の列の表示可能な変更です。任意の非キー フィールド、または単一キーのテーブル内のキー フィールドに複数キー テーブルのキー フィールドのいずれかで変更できます。 一番上の行は、フィルター条件を示しています。フィルター処理できますに基づいて任意の非キー フィールドで、単一キーのテーブルでは、または複数キー テーブルのキー フィールドのいずれかのキー フィールド。 交差するセルが結果を表示: 適用されることを意味 +**行と列が**空でない結果**レコード セット**; - 空のことを意味**レコード セット**。  
  
||非キー|1 つのキー|複数のキー|  
|-|--------------|----------------|-------------------|  
|**非キー**|+|+|+|  
|**1 つのキー**|+|-|なし|  
|**複数のキー**|+|なし|+|  
  
## <a name="applies-to"></a>適用対象  
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [フィルターおよび RecordCount のプロパティの例 (VB)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vb.md)   
 [フィルターおよび RecordCount のプロパティの例 (vc++)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vc.md)   
 [Clear メソッド (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [動的プロパティ (ADO) を最適化します。](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)

