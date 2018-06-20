---
title: Visual C の拡張機能の使用 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++ [ADO], using VC++ extensions
- ADO, Visual C++
ms.assetid: ff759185-df41-4507-8d12-0921894ffbd9
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 06e2d13c589d4dc88f3a148122322f483c49d2fb
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35271591"
---
# <a name="visual-c-extensions"></a>Visual C の拡張機能
## <a name="the-iadorecordbinding-interface"></a>IADORecordBinding インターフェイス
 Microsoft Visual C 拡張の ADO 関連付ける、またはバインド、各フィールドに対して、[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) C と C++ の変数にオブジェクト。 ときに、バインドの現在の行**Recordset** 変更されると、バインドされたすべてのフィールドに、**Recordset** C と C++ の変数にコピーされます。 必要に応じて、コピーしたデータは、C と C++ の変数の宣言されたデータ型に変換されます。

 **BindToRecordset** のメソッド、 **IADORecordBinding** インターフェイスは、C と C++ の変数にフィールドをバインドします。 **AddNew** メソッドは、バインドに新しい行を追加 **Recordset** です。 **Update**メソッドは、新しい行のフィールドを設定、**Recordset**、または C と C++ の変数の値を持つ既存の行のフィールドを更新します。

 **IADORecordBinding** インターフェイスは、 **Recordset** オブジェクト。 コーディングしないでください実装では、自分でします。

## <a name="binding-entries"></a>バインドのエントリ
 ADO の Visual C 拡張のフィールドのマッピング、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) C と C++ の変数にオブジェクト。 フィールドと変数間のマッピングの定義が呼び出された、*エントリをバインド*です。 マクロは、数値、固定長および可変長のデータのバインド エントリを提供します。 バインディング エントリおよび C と C++ の変数が、Visual C 拡張クラスから派生したクラスで宣言されている **CADORecordBinding** です。 **CADORecordBinding** クラスは、バインディング エントリ マクロによって内部的に定義されます。

 ADO は内部的には、OLE DB にこれらのマクロでは、パラメーターをマップ **DBBINDING** を構造化され、OLE DB **Accessor** の移動やフィールドと変数のデータの変換を管理するオブジェクト。 OLE DB で構成されるとしてデータを定義する 3 つの部分: *buffer*データを格納すると;、*status* フィールドが、バッファーに正常に格納されているかどうか、またはに変数を復元する方法を示すフィールドです。および *length* データ。 (を参照してください[の取得と設定データ (OLE DB)](http://msdn.microsoft.com/en-us/4369708b-c9fb-4d48-a321-bf949b41a369)詳細については、OLE DB プログラマーズ リファレンスです)。

## <a name="header-file"></a>ヘッダー ファイル
 ADO の Visual C 拡張を使用するために、アプリケーションでは、次のファイルを含めます。

```
#include <icrsint.h>
```

## <a name="binding-recordset-fields"></a>レコード セットのフィールドのバインド

#### <a name="to-bind-recordset-fields-to-cc-variables"></a>レコード セットのフィールドを C と C++ の変数にバインドするには

1.  派生するクラスを作成、 **CADORecordBinding**クラスです。

2.  派生クラスでバインディング エントリおよび対応する C と C++ の変数を指定します。 右山かっこの間のバインド エントリ**BEGIN_ADO_BINDING**と**END_ADO_BINDING**マクロです。 コンマまたはセミコロンでマクロを終了しないでください。 適切な区切り文字は、各マクロによって自動的に指定されます。

     C と C++ の変数にマップするフィールドごとに 1 つのバインド エントリを指定します。 該当するメンバーを使用して、 **ADO_FIXED_LENGTH_ENTRY**、 **ADO_NUMERIC_ENTRY**、または**ADO_VARIABLE_LENGTH_ENTRY**マクロのファミリです。

3.  派生したクラスのインスタンスを作成、アプリケーションで**CADORecordBinding**です。 取得、 **IADORecordBinding**からインターフェイス、 **Recordset**です。 まず、 **BindToRecordset**にバインドするメソッド、**Recordset**C と C++ の変数へのフィールドです。

 詳細については、次を参照してください。、 [C++ の拡張機能の例で Visual](../../../ado/guide/appendixes/visual-c-extensions-example.md)です。

## <a name="interface-methods"></a>インターフェイス メソッド
 **IADORecordBinding**インターフェイスには 3 つの方法: **BindToRecordset**、 **AddNew**、および**Update**です。 各メソッドに唯一の引数から派生したクラスのインスタンスへのポインターは、 **CADORecordBinding**です。 したがって、 **AddNew**と**Update**メソッドは、ADO メソッド namesakes のパラメーターのいずれかを指定できません。

## <a name="syntax"></a>構文
 **BindToRecordset**メソッド関連付けます、 **Recordset** C と C++ の変数にフィールドです。

```
BindToRecordset(CADORecordBinding *binding)
```

 **AddNew**メソッドを呼び出してその設立、ADO [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)に新しい行を追加する、メソッド、 **Recordset**です。

```
AddNew(CADORecordBinding *binding)
```

 **Update**メソッドを呼び出してその設立、ADO[Update](../../../ado/reference/ado-api/update-method.md)を更新するメソッド、 **Recordset**です。

```
Update(CADORecordBinding *binding)
```

## <a name="binding-entry-macros"></a>バインディングのエントリ マクロ
 バインディングのエントリ マクロ定義の関連付け、 **Recordset**フィールドと変数です。 最初と最後のマクロでは、一連のバインド エントリを区切ります。

 などのマクロのファミリを固定長のデータの提供される**adDate**または**adBoolean**以外の場合は数値データなど**adTinyInt**、 **adInteger**、または**adDouble**; と可変長データなど**adChar**、**adVarChar**または**adVarBinary**です。 すべての数値型以外の**adVarNumeric**も、固定長の型。 各ファミリでは、それぞれ異なるパラメーター セットにいるため、関係のないのは、バインド情報を除外することができます。

 詳細については、次を参照してください。[付録 a: データ型](http://msdn.microsoft.com/en-us/e3a0533a-2196-4eb0-a31e-92fe9556ada6)、OLE DB プログラマーズ リファレンスのです。

### <a name="begin-binding-entries"></a>バインディング エントリを開始します。
 **BEGIN_ADO_BINDING**(*クラス*)

### <a name="fixed-length-data"></a>固定長のデータ
 **ADO_FIXED_LENGTH_ENTRY**(*Ordinal, DataType, Buffer, Status, Modify*)

 **ADO_FIXED_LENGTH_ENTRY2**(*Ordinal, DataType, Buffer, Modify*)

### <a name="numeric-data"></a>数値データ
 **ADO_NUMERIC_ENTRY**(*Ordinal, DataType, Buffer, Precision, Scale, Status, Modify*)

 **ADO_NUMERIC_ENTRY2**(*Ordinal, DataType, Buffer, Precision, Scale, Modify*)

### <a name="variable-length-data"></a>可変長のデータ
 **ADO_VARIABLE_LENGTH_ENTRY**(*Ordinal, DataType, Buffer, Size, Status, Length, Modify*)

 **ADO_VARIABLE_LENGTH_ENTRY2**(*Ordinal, DataType, Buffer, Size, Status, Modify*)

 **ADO_VARIABLE_LENGTH_ENTRY3**(*Ordinal, DataType, Buffer, Size, Length, Modify*)

 **ADO_VARIABLE_LENGTH_ENTRY4**(*Ordinal, DataType, Buffer, Size, Modify*)

### <a name="end-binding-entries"></a>バインディング エントリの終了
 **END_ADO_BINDING**()

|パラメーター|説明|
|---------------|-----------------|
|*Class*|バインディング エントリおよび C と C++ の変数が定義されているクラスです。|
|*Ordinal*|序数のいずれかでカウント、 **Recordset** C と C++ の変数に対応するフィールドです。|
|*DataType*|C と C++ の変数の同等の ADO データ型 (を参照してください[格納](../../../ado/reference/ado-api/datatypeenum.md)有効なデータ型の一覧については)。 値、 **Recordset**フィールドは、必要な場合はこのデータ型に変換されます。|
|*Buffer*|C と C++ の変数の名前を**Recordset**フィールドが格納されます。|
|*Size*|最大サイズ (バイト) の*Buffer*です。 場合*Buffer*可変長の文字列には末尾のゼロの領域を確保できるようにします。|
|*Status*|示す変数の名前かどうかの内容*Buffer*が有効でとかどうか、変換するフィールドの*DataType*が成功しました。<br /><br /> この変数の 2 つの最も重要な値は**adFldOK**、つまり、変換が成功したと**adFldNull**、つまり、フィールドの値となる型 VT_ のバリアントだけでなく、空です。<br /><br /> 指定できる値*Status*次の表では、「状態の値です」に。|
|*Modify*|ブール型のフラグです。TRUE の場合は、ADO の対応する、更新が許可されたことを示します**Recordset**フィールドに含まれる値に*Buffer*です。<br /><br /> ブール値を設定*Modify*ADO では、バインドされたフィールドが更新を有効にする場合は TRUE と FALSE の変更ではなく、フィールドを確認する場合のパラメーターです。|
|*Precision*|数値型の変数で表すことができる数字の数。|
|*Scale*|数値型の変数の小数点以下桁数です。|
|*Length*|内のデータの実際の長さを格納する 4 バイトの変数の名前*Buffer*です。|

## <a name="status-values"></a>状態の値
 値、*Status*変数は、フィールドが変数に正常にコピーされたかどうかを示します。

 データを設定するときに*Status*に設定することがあります**adFldNull**を示すために、 **Recordset**フィールドを設定する必要がありますを null にします。

|定数|値|説明|
|--------------|-----------|-----------------|
|**adFldOK**|0|Null 以外のフィールドの値が返されました。|
|**adFldBadAccessor**|1|バインドが無効でした。|
|**adFldCantConvertValue**|2|符号の不一致またはデータ オーバーフロー以外の理由の値を変換できませんでした。|
|**adFldNull**|3|フィールドを取得するときに、null 値が返されたことを示します。<br /><br /> フィールドに設定するときに、フィールドを設定する必要がありますを示します。 **NULL**フィールドがエンコードできない**NULL**自体 (たとえば、文字配列または整数)。|
|**adFldTruncated**|4|可変長のデータまたは数値の桁は切り捨てられました。|
|**adFldSignMismatch**|5|値は署名され、変数のデータ型は符号付きではありません。|
|**adFldDataOverFlow**|6|値は変数のデータ型に格納する可能性がありますよりも大きいです。|
|**adFldCantCreate**|7|不明な列の型とフィールドが既に開かれています。|
|**adFldUnavailable**|8|フィールドの値を特定できませんでした-たとえば、既定値はありません新しい、割り当てられていないフィールドにします。|
|**adFldPermissionDenied**|9|更新する場合、データの書き込みアクセス許可がありません。|
|**adFldIntegrityViolation**|10|更新する場合、フィールドの値列の整合性に違反します。|
|**adFldSchemaViolation**|11|更新する場合、フィールドの値が列のスキーマに違反します。|
|**adFldBadStatus**|12|更新時に、無効な状態のパラメーターです。|
|**adFldDefault**|13|更新する場合、既定値が使用されました。|

## <a name="see-also"></a>参照
 [Visual C 拡張機能の使用例](../../../ado/guide/appendixes/visual-c-extensions-example.md) [Visual C 拡張機能ヘッダー](../../../ado/guide/appendixes/visual-c-extensions-header.md)
