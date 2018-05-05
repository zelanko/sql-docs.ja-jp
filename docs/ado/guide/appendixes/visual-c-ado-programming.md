---
title: Visual C ADO プログラミング |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO, Visual C++
- Visual C++ [ADO]
ms.assetid: 11233b96-e05c-4221-9aed-5f20944b0f1c
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ce5a300ec2dd17109f888c9023b934c686289504
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="visual-c-ado-programming"></a>Visual C ADO プログラミング
ADO の API リファレンスでは、ADO アプリケーション プログラミング インターフェイス (API)、Microsoft Visual Basic に似た構文を使用するの機能について説明します。 ADO プログラマが Visual Basic、Visual C などのさまざまな言語を使用する対象とするユーザーには、すべてのユーザーが、(とそうでない、 **#import**ディレクティブ)、および Visual j (ADO/WFC クラス パッケージ) にします。  

> [!NOTE]
> Microsoft では、2004 年に Visual j のサポートが終了しました。

 この多様性をそれに合わせて、 [Visual C++ 構文のインデックスの ADO](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md)機能、パラメーター、例外的な動作、および API 内の一般的な説明へのリンクを Visual C の言語に固有の構文を使用します。参照。  
  
 ADO は、COM (コンポーネント オブジェクト モデル) インターフェイスで実装されます。 ただし、他のユーザーよりも特定のプログラミング言語で COM を使用するプログラマにとって簡単です。 たとえば、詳細自体を Visual C プログラマに参加する必要がありますが、Visual Basic プログラマのための COM の使用の詳細をほぼすべては暗黙的に処理されます。  
  
 次のセクションでは、ADO を使用する C および C++ のプログラマのための詳細情報の要約および **#import**ディレクティブです。 COM に固有のデータ型に焦点を当てています (**バリアント**、 **BSTR**、および**SafeArray**)、およびエラー処理 (_com_error)。  
  
## <a name="using-the-import-compiler-directive"></a>#Import コンパイラ ディレクティブを使用します。  
 **#Import** Visual C コンパイラ ディレクティブは、ADO のメソッドとプロパティの使用を簡略化します。 ディレクティブは、ADO dll (Msado15.dll) などのタイプ ライブラリを含むファイルの名前を取得し、typedef 宣言、インターフェイス、および列挙定数のスマート ポインターを含むヘッダー ファイルを生成します。 各インターフェイスがカプセル化され、またはクラスでラップします。  
  
 クラス (メソッドまたはプロパティの呼び出し) 内で各操作がある操作を呼び出す、直接 (つまり、「生の」形式の操作)、宣言と生の操作を呼び出すし、succ を実行する操作が失敗した場合は、COM エラーをスローする宣言essfully です。 操作が、プロパティの場合は、通常は、Visual Basic などの構文のある操作の代替構文を作成するコンパイラ ディレクティブ。  
  
 プロパティの値を取得する操作は、フォームの名前を持つ **取得 * * * プロパティ*です。 プロパティの値を設定する操作は、フォームの名前を持つ **Put * * * プロパティ*です。 ADO オブジェクトにポインターを使用してプロパティの値を設定する操作は、フォームの名前を持つ **PutRef * * * プロパティ*です。  
  
 取得またはこれらの形式の呼び出しを持つプロパティを設定することができます。  
  
```  
variable = objectPtr->GetProperty(); // get property value   
objectPtr->PutProperty(value);       // set property value  
objectPtr->PutRefProperty(&value);   // set property with object pointer  
```  
  
## <a name="using-property-directives"></a>プロパティのディレクティブを使用します。  
 **__Declspec(property...)** コンパイラ ディレクティブは、代替構文を持つとプロパティとして使用される関数を宣言する Microsoft 固有の C 言語拡張機能です。 その結果、設定または Visual Basic に似た方法でプロパティの値を取得できます。 たとえば、設定およびプロパティにこの方法を取得できます。  
  
```  
objectPtr->property = value;        // set property value  
variable = objectPtr->property;     // get property value  
```  
  
 コードにはできませんに注意してください。  
  
```  
objectPtr->PutProperty(value);      // set property value  
variable = objectPtr->GetProperty;  // get property value  
```  
  
 コンパイラは、適切な生成 **Get * * *-*、 **Put**-、または **PutRef * * * プロパティ*代替構文は宣言されており、プロパティは使用するかどうかに基づいて、呼び出し読み取りまたは書き込まれます。  
  
 **__Declspec(property...)** のみコンパイラ ディレクティブを宣言できます**取得**、 **put**、または**取得**と**put**関数の代替構文です。 読み取り専用操作だけが、**取得**宣言; のみが書き込み専用の操作、**配置**宣言以外の操作は両方の読み取りし、書き込み両方を**取得**と**put**宣言します。  
  
 2 つだけ宣言も有効であるこのディレクティブを指定します。ただし、各プロパティがプロパティの 3 つの関数を必要があります: **取得 * * * プロパティ*、**Put * * * プロパティ*、および **PutRef * * * プロパティ*です。 その場合は、プロパティの 2 つの形式では、代替構文があります。  
  
 たとえば、**コマンド**オブジェクト**ActiveConnection**プロパティが、別の構文で宣言された **取得 * * * ActiveConnection*と **PutRef ** * ActiveConnection*です。 **PutRef**の実習では通常設定する、開いているために、構文は、適切な選択**接続**オブジェクト (つまり、**接続**オブジェクト ポインター) このプロパティ。 その一方で、**レコード セット**オブジェクトが**取得**-、 **Put**-、および **PutRef * * * ActiveConnection*操作が代替オプションがないです。構文があります。  
  
## <a name="collections-the-getitem-method-and-the-item-property"></a>コレクション、GetItem メソッド、および項目のプロパティ  
 ADO など、いくつかのコレクションを定義する**フィールド**、**パラメーター**、**プロパティ**、および**エラー**です。 Visual c で、 **GetItem (***インデックス***)** メソッドがコレクションのメンバーを返します。 *インデックス*は、**バリアント**の値は、コレクション内のメンバーの数値インデックスまたはメンバーの名前を含む文字列。  
  
 **__Declspec(property...)** コンパイラ ディレクティブを宣言、**項目**コレクションごとに別の構文としてプロパティの基本的な**37-1getitem ()** メソッドです。 代替構文では、角かっこを使用し、配列参照に似たします。 一般に、2 つの形式は、次のようになります。  
  
```  
  
      collectionPtr->GetItem(index);  
collectionPtr->Item[index];  
```  
  
 などのフィールドに値を割り当てる、 **Recordset**という名前のオブジェクト***rs***から派生した、**作成者**のテーブル、 **pubs**データベース。 使用して、 **Item()** 、3 番目にアクセスするプロパティ**フィールド**の**Recordset**オブジェクト**フィールド**コレクション (コレクションのインデックスはから0;3 番目のフィールドの名前は前提としています。 ***au_fname***)。 まず、 **Value()** メソッドを**フィールド**文字列値を代入するオブジェクト。  
  
 これで表現できる Visual Basic では、次の 4 つの方法 (最後の 2 つのフォームは、Visual Basic に一意です。 他の言語には、対応はありません)。  
  
```  
rs.Fields.Item(2).Value = "value"  
rs.Fields.Item("au_fname").Value = "value"  
rs(2) = "value"  
rs!au_fname = "value"  
```  
  
 Visual C で上記の最初の 2 つのフォームには。  
  
```  
rs->Fields->GetItem(long(2))->PutValue("value");   
rs->Fields->GetItem("au_fname")->PutValue("value");  
```  
  
 - または - (代替構文を**値**もプロパティが表示されます)  
  
```  
rs->Fields->Item[long(2)]->Value = "value";  
rs->Fields->Item["au_fname"]->Value = "value";  
```  
  
 コレクションを反復処理する例については、「ADO 参照」の「ADO コレクション」セクションを参照してください。  
  
## <a name="com-specific-data-types"></a>COM に固有のデータ型  
 一般に、ADO の API リファレンスを検索する任意の Visual Basic データ型は、同等の Visual C がします。 などの標準的なデータ型が含まれます**unsigned char** Visual basic**バイト**、**短い**の**整数**、および**長い**の**長い**です。 構文 Indexesto ファイルの場所では、特定のメソッドまたはプロパティのオペランドは、ために必要なだけを参照してください。  
  
 このルールの例外は COM に固有のデータ型:**バリアント**、 **BSTR**、および**SafeArray**です。  
  
### <a name="variant"></a>Variant  
 A**バリアント**値メンバーおよびデータ型のメンバーを含む構造化されたデータ型です。 A**バリアント**幅広い別バリアント、BSTR、ブール値、IDispatch、または IUnknown ポインター、通貨、日付、およびなどを含む他のデータ型を含めることがあります。 COM では、メソッドを簡単に 1 つのデータ型の変換も用意されています。  
  
 **_Variant_t**クラスは、カプセル化し、管理、**バリアント**データ型。  
  
 ADO の API リファレンス」でメソッドまたはプロパティのオペランドが値を受け取り場合、通常は、値が渡された、 **_variant_t**です。  
  
 このルールは、明示的に true のときに、**パラメーター**オペランドは、ADO の API リファレンスのトピックでは、セクションの質問、**バリアント**です。 1 つの例外は、ドキュメントに明示的に記載されている場合、オペランドがなど、標準のデータ型を受け取る**長い**または**バイト**、または列挙体です。 別の例外は、オペランドを受け取るときに、**文字列**です。  
  
### <a name="bstr"></a>BSTR  
 A **BSTR** (**B**などがあります**STR**ing) 文字の文字列および文字列の長さを格納する構造化データ型です。 COM は、割り当て、操作、および解放するメソッドを提供する**BSTR**です。  
  
 **_Bstr_t**クラスは、カプセル化し、管理、 **BSTR**データ型。  
  
 ADO の API リファレンスが、メソッドやプロパティを表示するときに、**文字列**値、つまり、値の形式で、 **_bstr_t**です。  
  
### <a name="casting-variantt-and-bstrt-classes"></a>キャスト _variant_t および _bstr_t クラス  
 多くの場合、コードでは明示的にする必要はありません、 **_variant_t**または **_bstr_t**で操作に渡す引数。 場合、 **_variant_t**または **_bstr_t**クラスは、引数のデータ型と一致するコンス トラクターを持つ、コンパイラは、適切な生成 **_variant_t**または **_bstr_t**です。  
  
 ただし、引数があいまいな場合は、引数のデータ型が複数のコンス トラクターを一致する、適切な正しいのコンス トラクターを呼び出すデータ型引数をキャストする必要があります。  
  
 宣言など、 **Recordset::Open**メソッドは。  
  
```  
    HRESULT Open (  
        const _variant_t & Source,  
        const _variant_t & ActiveConnection,  
        enum CursorTypeEnum CursorType,  
        enum LockTypeEnum LockType,  
        long Options );  
```  
  
 `ActiveConnection`引数への参照には、 **_variant_t**、接続文字列または開いているへのポインターとしてコードがこれ**接続**オブジェクト。  
  
 正しい **_variant_t**など、文字列を渡す場合は、暗黙的に構築されます"`DSN=pubs;uid=MyUserName;pwd=MyPassword;`"、またはなどのポインター"`(IDispatch *) pConn`"です。  
  
> [!NOTE]
>  Windows 認証をサポートするデータ ソース プロバイダーに接続するかどうかは、する必要がありますを指定する**Trusted_Connection = [はい]** または**Integrated Security = SSPI**ユーザー ID とパスワードの代わりに接続文字列の情報です。  
  
 明示的にコーディングすることがありますか、 **_variant_t**などへのポインターを含む"`_variant_t((IDispatch *) pConn, true)`"です。 キャスト`(IDispatch *)`、IUnknown インターフェイスへのポインターを受け取る別のコンス トラクターを持つあいまいさを解決します。  
  
 頻度の低いファクト、ADO は IDispatch インターフェイスを記載されている場合は、重要です。 として、ADO オブジェクトへのポインターを渡す必要があるたびに、**バリアント**、IDispatch インターフェイスへのポインターとしてそのポインターをキャストする必要があります。  
  
 最後の場合は、コンス トラクターの 2 番目のブール型の引数、省略可能で、既定値に明示的にコーディング`true`です。 この引数により、**バリアント**コンス トラクターを呼び出す、 **AddRef**() メソッドは、自動的に呼び出す ADO の補正、 **_variant_t::Release**() メソッドADO メソッドまたはプロパティの呼び出しが完了したとき。  
  
### <a name="safearray"></a>SafeArray  
 A **SafeArray**は他のデータ型の配列を含む構造化されたデータ型です。 A **SafeArray**が呼び出された*セーフ*のため、各配列の次元の範囲に関する情報を含み、それらの範囲内の配列要素へのアクセスを制限します。  
  
 ときに、ADO API リファレンス」メソッドまたはプロパティが受け取るか、配列を返します、意味メソッドまたはプロパティが受け取るかを返す、 **SafeArray**、ネイティブ C/C++ 配列ではありません。  
  
 たとえば、2 番目のパラメーター、**接続**オブジェクト**OpenSchema**メソッドには、配列が必要です。**バリアント**値。 もの**バリアント**の要素として値を渡す必要があります、 **SafeArray**、および**SafeArray**別の値として設定する必要があります**バリアント**. 他の**バリアント**の 2 番目の引数として渡された**OpenSchema**です。  
  
 例では、さらの最初の引数、**検索**メソッドは、**バリアント**値を持つ 1 次元**SafeArray**; 各省略可能な最初と 2 番目の引数**AddNew**は、1 次元**SafeArray**; と戻り値、 **GetRows**メソッドは、**バリアント**が値は、2 次元**SafeArray**です。  
  
## <a name="missing-and-default-parameters"></a>Missing および既定のパラメーター  
 Visual Basic では、メソッドのパラメーターがありません。 たとえば、 **Recordset**オブジェクト**開く**メソッドには 5 つのパラメーターが、中間のパラメーターをスキップし、後続のパラメーターをオフのままにすることができます。 既定の**BSTR**または**バリアント**が不足しているオペランドのデータの種類によって置換されます。  
  
 C と C++ では、すべてのオペランドを指定する必要があります。 データ型が文字列で不足しているパラメーターを指定する場合、指定、 **_bstr_t** null 文字列を格納します。 データ型が不足しているパラメーターを指定するかどうか、**バリアント**を指定して、 **_variant_t** DISP_E_PARAMNOTFOUND と VT_ERROR の型の値を使用します。 また、該当するショートカットを指定 **_variant_t**定数、 **vtMissing**は、によって提供される、 **#import**ディレクティブです。  
  
 次の 3 つのメソッドは例外の典型的な使用を**vtMissing**です。 これらは、 **Execute**のメソッド、**接続**と**コマンド**オブジェクト、および**NextRecordset**メソッド、の**Recordset**オブジェクト。 それぞれの署名を次に示します。  
  
```  
_RecordsetPtr <A HREF="mdmthcnnexecute.htm">Execute</A>( _bstr_t CommandText, VARIANT * RecordsAffected,   
        long Options );  // Connection  
_RecordsetPtr <A HREF="mdmthcmdexecute.htm">Execute</A>( VARIANT * RecordsAffected, VARIANT * Parameters,   
        long Options );  // Command  
_RecordsetPtr <A HREF="mdmthnextrec.htm">NextRecordset</A>( VARIANT * RecordsAffected );  // Recordset  
```  
  
 パラメーター、 *RecordsAffected*と*パラメーター*へのポインター、**バリアント**です。 *パラメーター*のアドレスを指定する入力パラメーターには、**バリアント**を含む 1 つのパラメーター、または実行中のコマンドを変更するには、パラメーターの配列。 *RecordsAffected*のアドレスを指定する出力パラメーターです、**バリアント**、メソッドによって影響を受ける行の数が返されます。  
  
 **コマンド**オブジェクト**Execute**メソッドを設定して、パラメーターが指定されていないことを示す*パラメーター*いずれかに`&vtMissing`(これは推奨) またはnull ポインター (つまり、 **NULL**またはゼロ (0))。 場合*パラメーター*が設定を null のポインターでは、メソッドは内部的に相当**vtMissing**、し、操作を完了します。  
  
 すべてのメソッドに影響を受けたレコードの数を設定して返されないことを示す*RecordsAffected* null ポインターです。 この場合、null ポインター パラメーターではありませんほど、不足しているメソッドが影響を受けたレコードの数を破棄することを示す値として。  
  
 したがって、これら 3 つのメソッドのようなコーディングに有効なは。  
  
```  
pConnection->Execute("commandText", NULL, adCmdText);   
pCommand->Execute(NULL, NULL, adCmdText);  
pRecordset->NextRecordset(NULL);  
```  
  
## <a name="error-handling"></a>エラー処理  
 COM では、ほとんどの操作は、関数が正常に完了したかどうかを示す HRESULT のリターン コードを返します。 **#Import**ディレクティブは、各「生の」メソッドまたはプロパティの周囲にラッパー コードを生成し、返された HRESULT を確認します。 HRESULT エラーを示している場合、ラッパー コードは、引数として HRESULT のリターン コードの呼び出し元の _com_issue_errorex() によって COM エラーをスローします。 COM エラー オブジェクトをキャッチすることができます、**再試行**-**キャッチ**ブロックします。 (効率性のためへの参照をキャッチ、 **_com_error**オブジェクトです)。  
  
 ただし、これらは、ADO エラー: ADO 操作の失敗に起因します。 基になるプロバイダーから返されたエラーとして表示されます**エラー**内のオブジェクト、**接続**オブジェクト**エラー**コレクション。  
  
 **#Import**ディレクティブがエラーのみを処理ルーチンで、ADO .dll で宣言されたプロパティとメソッドを作成します。 ただし、これと同じエラー マクロまたはインライン関数の確認、独自のエラーを記述して処理機構の利点を実行できます。 トピックを参照して[Visual C 拡張](../../../ado/guide/appendixes/visual-c-extensions-for-ado.md)、または、コード例については次のセクションでします。  
  
## <a name="visual-c-equivalents-of-visual-basic-conventions"></a>Visual Basic の規則の対応する visual C  
 ドキュメントでは、ADO、Visual Basic と Visual C の同等のコード化されたいくつかの規則の概要を次に示します。  
  
### <a name="declaring-an-ado-object"></a>ADO オブジェクトを宣言します。  
 Visual basic で ADO オブジェクト変数 (このためには、**レコード セット**オブジェクト) が次のように宣言されています。  
  
```  
Dim rst As ADODB.Recordset  
```  
  
 句"`ADODB.Recordset`"の ProgID は、**レコード セット**オブジェクト、レジストリで定義されています。 新しいインスタンスを**レコード**オブジェクトが次のように宣言されています。  
  
```  
Dim rst As New ADODB.Recordset  
```  
  
 -または-  
  
```  
Dim rst As ADODB.Recordset  
Set rst = New ADODB.Recordset  
```  
  
 Visual c で、 **#import**ディレクティブには、すべての ADO オブジェクトのスマート ポインター型宣言が生成されます。 指す変数など、 **_Recordset**オブジェクトの型が **_RecordsetPtr**が次のように宣言されているとします。  
  
```  
_RecordsetPtr  rs;  
```  
  
 新しいインスタンスを指す変数、 **_Recordset**オブジェクトが次のように宣言します。  
  
```  
_RecordsetPtr  rs("ADODB.Recordset");  
```  
  
 -または-  
  
```  
_RecordsetPtr  rs;  
rs.CreateInstance("ADODB.Recordset");  
```  
  
 -または-  
  
```  
_RecordsetPtr  rs;  
rs.CreateInstance(__uuidof(_Recordset));  
```  
  
 後に、 **CreateInstance**メソッドが呼び出されると、次のように、変数を使用できます。  
  
```  
rs->Open(...);  
```  
  
 1 つのケースに注意してください、"`.`"操作は、変数がクラスのインスタンスである場合のように、使用 (`rs.CreateInstance`)、および別のケースで、"`->`"場合と同様、変数のインターフェイスへのポインター演算子を使用 (`rs->Open`)。  
  
 2 つの方法で 1 つの変数を使用できます、"`->`"インターフェイスへのポインターのように動作するクラスのインスタンスを許可する演算子をオーバー ロードします。 インスタンスの変数のプライベート クラス メンバーへのポインターを含む、 **_Recordset**インターフェイス;、"`->`"演算子では、そのポインターと、返されたポインターのメンバーにアクセスを返します、 **_Recordset**オブジェクト。  
  
### <a name="coding-a-missing-parameter--string"></a>不足しているパラメーターをコーディング-文字列  
 見つからないをコーディングする必要がある場合**文字列**オペランド Visual basic でするだけでオペランドを省略します。 Visual C のオペランドを指定する必要があります。 コード、 **_bstr_t**値として空の文字列を含むです。  
  
```  
_bstr_t strMissing(L"");  
```  
  
### <a name="coding-a-missing-parameter--variant"></a>不足しているパラメーターをコーディング — バリアント  
 見つからないをコーディングする必要がある場合**バリアント**オペランド Visual Basic の場合にだけを省略するオペランド。 Visual C では、すべてのオペランドを指定する必要があります。 コードが存在しない**バリアント**を持つパラメーター、 **_variant_t**特殊な値、DISP_E_PARAMNOTFOUND、型、VT_ERROR に設定します。 または、指定**vtMissing**、これと同等の定義済みの定数によって提供される、 **#import**ディレクティブです。  
  
```  
_variant_t  vtMissingYours(DISP_E_PARAMNOTFOUND, VT_ERROR);   
```  
  
 またはを使用して、  
  
```  
...vtMissing...;  
```  
  
### <a name="declaring-a-variant"></a>バリアント型を宣言します。  
 Visual Basic では、**バリアント**で宣言された、 **Dim**次のようにステートメント。  
  
```  
Dim VariableName As Variant  
```  
  
 Visual c での型として変数を宣言 **_variant_t**です。 いくつかの概略図 **_variant_t**宣言を以下に示します。  
  
> [!NOTE]
>  これらの宣言は、単なる独自のプログラムでコーディングする新機能の大まかな目安を提供します。 詳細については、以下の例と Visual c ドキュメントを参照してください。  
  
```  
_variant_t  VariableName(value);  
_variant_t  VariableName((data type cast) value);  
_variant_t  VariableName(value, VT_DATATYPE);  
_variant_t  VariableName(interface * value, bool fAddRef = true);  
```  
  
### <a name="using-arrays-of-variants"></a>バリアント型の配列の使用  
 Visual basic での配列**バリアント**でコーディングすることができます、 **Dim**ステートメントでは、またはを使用して、**配列**関数は、次のコード例に示されています。  
  
```  
Public Sub ArrayOfVariants  
Dim cn As ADODB.Connection  
Dim rs As ADODB.Recordset  
Dim fld As ADODB.Field  
  
    cn.Open "DSN=pubs"  
    rs = cn.OpenSchema(adSchemaColumns, _  
        Array(Empty, Empty, "authors", Empty))  
    For Each fld in rs.Fields  
        Debug.Print "Name = "; fld.Name  
    Next fld  
    rs.Close  
    cn.Close  
End Sub  
```  
  
 Visual C の次の例では、使用方法を示します、 **SafeArray**と共に使用する **_variant_t**です。  
  
#### <a name="notes"></a>注  
 次の注意事項は、コード例ではコメント部分に対応します。  
  
1.  もう一度 TESTHR() インライン関数は、既存のエラー処理メカニズムを活用するために定義されます。  
  
2.  必要なだけ 1 次元配列で使用できるように**SafeArrayCreateVector**、一般的な用途ではなく**SAFEARRAYBOUND**宣言と**SafeArrayCreate**関数。 次はそのコードを使用するようになります**SafeArrayCreate**:  
  
    ```  
       SAFEARRAYBOUND   sabound[1];  
       sabound[0].lLbound = 0;  
       sabound[0].cElements = 4;  
       pSa = SafeArrayCreate(VT_VARIANT, 1, sabound);  
    ```  
  
3.  列挙型の定数で識別されるスキーマ**adSchemaColumns**、4 つの制約列に関連付けられて: TABLE_CATALOG、table_schema、TABLE_NAME、COLUMN_NAME、します。 したがって、配列の**バリアント**4 つの要素を持つ値を作成します。 3 番目の列では、TABLE_NAME に対応する制約の値を指定しています。  
  
     **Recordset**返されるのサブセットは、制約列の複数の列で構成されます。 返された各行の制約の列の値は、対応する制約の値と同じである必要があります。  
  
4.  よく知っている**Safearray**可能性がある意外に思いました**SafeArrayDestroy**() は、終了する前に呼び出されません。 実際には、呼び出す**SafeArrayDestroy**() ここでは、例外が発生する、実行時。 その理由は、デストラクターの`vtCriteria`が呼び出す**VariantClear**() ときに、 **_variant_t**を開放するスコープから外れた、 **SafeArray**です。 呼び出す**SafeArrayDestroy**、手動でオフにせず、 **_variant_t**、無効なをオフにしようとするデストラクターを原因となる**SafeArray**ポインター。  
  
     場合**SafeArrayDestroy**が呼び出されると、コードは、次のようなります。  
  
    ```  
          TESTHR(SafeArrayDestroy(pSa));  
       vtCriteria.vt = VT_EMPTY;  
          vtCriteria.parray = NULL;  
    ```  
  
     ただし、はるかに簡単には、 **_variant_t**管理、 **SafeArray**です。  
  
```  
// Visual_CPP_ADO_Prog_1.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
// Note 1  
inline void TESTHR( HRESULT _hr ) {   
   if FAILED(_hr)   
      _com_issue_error(_hr);   
}  
  
int main() {  
   CoInitialize(NULL);  
   try {  
      _RecordsetPtr pRs("ADODB.Recordset");  
      _ConnectionPtr pCn("ADODB.Connection");  
      _variant_t vtTableName("authors"), vtCriteria;  
      long ix[1];  
      SAFEARRAY *pSa = NULL;  
  
      pCn->Provider = "sqloledb";  
      pCn->Open("Data Source='(local)';Initial Catalog='pubs';Integrated Security=SSPI", "", "", adConnectUnspecified);  
      // Note 2, Note 3  
      pSa = SafeArrayCreateVector(VT_VARIANT, 1, 4);  
      if (!pSa)   
         _com_issue_error(E_OUTOFMEMORY);  
  
      // Specify TABLE_NAME in the third array element (index of 2).   
      ix[0] = 2;        
      TESTHR(SafeArrayPutElement(pSa, ix, &vtTableName));  
  
      // There is no Variant constructor for a SafeArray, so manually set the   
      // type (SafeArray of Variant) and value (pointer to a SafeArray).  
  
      vtCriteria.vt = VT_ARRAY | VT_VARIANT;  
      vtCriteria.parray = pSa;  
  
      pRs = pCn->OpenSchema(adSchemaColumns, vtCriteria, vtMissing);  
  
      long limit = pRs->GetFields()->Count;  
      for ( long x = 0 ; x < limit ; x++ )  
         printf( "%d: %s\n", x + 1, ((char*) pRs->GetFields()->Item[x]->Name) );  
      // Note 4  
      pRs->Close();  
      pCn->Close();  
   }  
   catch (_com_error &e) {  
      printf("Error:\n");  
      printf("Code = %08lx\n", e.Error());  
      printf("Code meaning = %s\n", (char*) e.ErrorMessage());  
      printf("Source = %s\n", (char*) e.Source());  
      printf("Description = %s\n", (char*) e.Description());  
   }  
   CoUninitialize();  
}  
```  
  
### <a name="using-property-getputputref"></a>プロパティの Get と Put/PutRef を使用します。  
 Visual basic ではか取得、割り当てられている、または参照の割り当てによって、プロパティの名前は修飾されません。  
  
```  
Public Sub GetPutPutRef  
Dim rs As New ADODB.Recordset  
Dim cn As New ADODB.Connection  
Dim sz as Integer  
cn.Open "Provider=sqloledb;Data Source=yourserver;" & _  
         "Initial Catalog=pubs;Integrated Security=SSPI;"  
rs.PageSize = 10  
sz = rs.PageSize  
rs.ActiveConnection = cn  
rs.Open "authors",,adOpenStatic  
' ...  
rs.Close  
cn.Close  
End Sub  
```  
  
 この Visual C の例を示します、**取得**/**Put**/**PutRef * * * プロパティ*です。  
  
#### <a name="notes"></a>注  
 次の注意事項は、コード例ではコメント部分に対応します。  
  
1.  この例は、不足している文字列引数の 2 つの形式を使用して: 明示的な定数、 **strMissing**、およびコンパイラが、一時パスワードが作成に使用する文字列 **_bstr_t** のスコープに存在します。**開いている**メソッドです。  
  
2.  オペランドをキャストする必要はありません`rs->PutRefActiveConnection(cn)`に`(IDispatch *)`オペランドの型が既に`(IDispatch *)`です。  
  
```  
// Visual_CPP_ado_prog_2.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
int main() {  
   CoInitialize(NULL);  
   try {  
      _ConnectionPtr cn("ADODB.Connection");  
      _RecordsetPtr rs("ADODB.Recordset");  
      _bstr_t strMissing(L"");  
      long oldPgSz = 0, newPgSz = 5;  
  
      // Note 1  
      cn->Provider = "sqloledb";  
      cn->Open("Data Source='(local)';Initial Catalog=pubs;Integrated Security=SSPI;", strMissing, "", adConnectUnspecified);  
  
      oldPgSz = rs->GetPageSize();  
      // -or-  
      // oldPgSz = rs->PageSize;  
  
      rs->PutPageSize(newPgSz);  
      // -or-  
      // rs->PageSize = newPgSz;  
  
      // Note 2  
      rs->PutRefActiveConnection( cn );  
      rs->Open("authors", vtMissing, adOpenStatic, adLockReadOnly, adCmdTable);  
      printf("Original pagesize = %d, new pagesize = %d\n", oldPgSz, rs->GetPageSize());  
      rs->Close();  
      cn->Close();  
  
   }  
   catch (_com_error &e) {  
      printf("Description = %s\n", (char*) e.Description());  
   }  
   ::CoUninitialize();  
}  
```  
  
### <a name="using-getitemx-and-itemx"></a>GetItem(x) および項目の [x] を使用します。  
 この Visual Basic のサンプル構文を示しています、standard、および代替の**項目**()。  
  
```  
Public Sub GetItemItem  
Dim rs As New ADODB.Recordset  
Dim name as String  
rs = rs.Open "authors", "DSN=pubs;", adOpenDynamic, _  
         adLockBatchOptimistic, adTable  
name = rs(0)  
' -or-  
name = rs.Fields.Item(0)  
rs(0) = "Test"  
rs.UpdateBatch  
' Restore name  
rs(0) = name  
rs.UpdateBatch  
rs.Close  
End Sub  
```  
  
 この Visual C の例を示します**項目**です。  
  
> [!NOTE]
>  次のメモがコメント部分のコード例に対応しています: でコレクションにアクセスすると**項目**、インデックス、 **2**にキャストする必要があります**長い**ので、適切なコンス トラクターが呼び出されます。  
  
```  
// Visual_CPP_ado_prog_3.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
void main() {  
   CoInitialize(NULL);  
   try {  
      _ConnectionPtr cn("ADODB.Connection");  
      _RecordsetPtr rs("ADODB.Recordset");  
      _variant_t vtFirstName;  
  
      cn->Provider = "sqloledb";  
      cn->Open("Data Source='(local)';Initial Catalog=pubs;Integrated Security=SSPI;", "", "", adConnectUnspecified);  
  
      rs->PutRefActiveConnection( cn );  
      rs->Open("authors", vtMissing, adOpenStatic, adLockOptimistic, adCmdTable);  
      rs->MoveFirst();  
  
      // Note 1. Get a field.  
      vtFirstName = rs->Fields->GetItem((long)2)->GetValue();  
      // -or-  
      vtFirstName = rs->Fields->Item[(long)2]->Value;  
  
      printf( "First name = '%s'\n", (char*)( (_bstr_t)vtFirstName) );  
  
      rs->Fields->GetItem((long)2)->Value = L"TEST";  
      rs->Update(vtMissing, vtMissing);  
  
      // Restore name  
      rs->Fields->GetItem((long)2)->PutValue(vtFirstName);  
      // -or-  
      rs->Fields->GetItem((long)2)->Value = vtFirstName;  
      rs->Update(vtMissing, vtMissing);  
      rs->Close();  
   }  
   catch (_com_error &e) {  
      printf("Description = '%s'\n", (char*) e.Description());  
   }  
   ::CoUninitialize();  
}  
```  
  
### <a name="casting-ado-object-pointers-with-idispatch-"></a>ADO オブジェクトのポインターにキャスト (IDispatch *)  
 Visual C の次の例では、使用方法を示します (IDispatch *) ADO オブジェクトのポインターをキャストします。  
  
#### <a name="notes"></a>注  
 次の注意事項は、コード例ではコメント部分に対応します。  
  
1.  開いているを指定**接続**で明示的にコード化されたオブジェクト**バリアント**です。 キャスト (IDispatch \*) 正しいコンス トラクターが呼び出されるようにします。 また、2 つ目を明示的に設定 **_variant_t**パラメーターの既定値を**true**ので、オブジェクトの参照カウントされるが正しい場合、 **Recordset::Open**操作を終了します。  
  
2.  式、 `(_bstr_t)`、キャストではありませんが、 **_variant_t**抽出演算子、 **_bstr_t**から文字列、**バリアント**によって返される**値**.  
  
 式、 `(char*)`、キャストではありませんが、 **_bstr_t**でカプセル化された文字列へのポインターを抽出する演算子、 **_bstr_t**オブジェクト。  
  
 コードのこのセクションでは、に使用できる動作の一部を示しています **_variant_t**と **_bstr_t**演算子。  
  
```  
// Visual_CPP_ado_prog_4.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
int main() {  
   CoInitialize(NULL);  
   try {  
      _ConnectionPtr pConn("ADODB.Connection");  
      _RecordsetPtr pRst("ADODB.Recordset");  
  
      pConn->Provider = "sqloledb";  
      pConn->Open("Data Source='(local)';Initial Catalog='pubs';Integrated Security=SSPI", "", "", adConnectUnspecified);  
  
      // Note 1.  
      pRst->Open("authors", _variant_t((IDispatch *) pConn, true), adOpenStatic, adLockReadOnly, adCmdTable);  
      pRst->MoveLast();  
  
      // Note 2.  
      printf("Last name is '%s %s'\n",   
         (char*) ((_bstr_t) pRst->GetFields()->GetItem("au_fname")->GetValue()),  
         (char*) ((_bstr_t) pRst->Fields->Item["au_lname"]->Value));  
  
      pRst->Close();  
      pConn->Close();  
   }  
   catch (_com_error &e) {  
      printf("Description = '%s'\n", (char*) e.Description());  
   }     
   ::CoUninitialize();  
}  
```
