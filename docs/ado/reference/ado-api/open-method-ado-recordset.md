---
title: Open メソッド (ADO レコード セット) |Microsoft ドキュメント
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
apitype: COM
f1_keywords:
- Recordset15::raw_Open
- Recordset15::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: 3236749c-4b71-4235-89e2-ccdfaaa9319d
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Active
ms.openlocfilehash: a86f84251dca3a76d0e7110c781fea26395fc9d9
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="open-method-ado-recordset"></a>Open メソッド (ADO レコード セット)
カーソルをオープン、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
recordset.Open Source, ActiveConnection, CursorType, LockType, Options  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ソース*  
 省略可。 A**バリアント**として評価された、有効な[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト、SQL ステートメント、テーブル名、ストアド プロシージャの呼び出し、URL、またはファイルの名前または[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクトを含む、永続的に格納されている[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。  
  
 *ActiveConnection*  
 省略可。 いずれか、**バリアント**として評価された、有効な[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト変数名、または**文字列**を格納している[ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)パラメーター。  
  
 *CursorType*  
 省略可。 A [CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md)を開くときに、プロバイダーが使用するカーソルの種類を決定する値、 **Recordset**です。 既定値は**adOpenForwardOnly**です。  
  
 *LockType*  
 省略可。 A [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md)ロック (同時実行) の種類を開くときに、プロバイダーを使用する必要がありますを決定する値、 **Recordset**です。 既定値は**adLockReadOnly**です。  
  
 *Options*  
 省略可。 A**長い**プロバイダーを評価する方法を示す値、*ソース*引数を表している場合のもの以外の場合、**コマンド**オブジェクト、または、 **Recordset**以前保存されているファイルから復元する必要があります。 1 つまたは複数指定できます[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)または[ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md)値で、ビットごとの OR 演算子と組み合わせて使用できます。  
  
> [!NOTE]
>  開いた場合、 **Recordset**から、**ストリーム**、永続化を含む**Recordset**を使用して、 [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) の値**adAsyncFetchNonBlocking**効果はありません。 フェッチは同期的およびブロックしています。  
  
> [!NOTE]
>  **ExecuteOpenEnum**値**adExecuteNoRecords**または**adExecuteStream**では使用できません**開く**です。  
  
## <a name="remarks"></a>解説  
 ADO の既定のカーソル**Recordset**サーバー上にある順方向専用、読み取り専用カーソルします。  
  
 使用して、**開く**メソッドを**Recordset**オブジェクトをベース テーブルのクエリ、または以前に保存した結果からレコードを表すカーソルを開き、**レコード セット**です。  
  
 省略可能なを使用して*ソース*、次のいずれかを使用してデータ ソースを指定する引数:**コマンド**オブジェクト変数、SQL ステートメント、ストアド プロシージャ、テーブル名、URL、またはファイルの完全なパス名。 場合*ソース*は、ファイルのパス名では、完全なパス ("c:\dir\file.rst")、相対パスであることができます ("..\file.rst")、または URL ("http://files/file.rst") です。  
  
 使用することはお勧めできません、*ソース*の引数、**開く**レコードを返さない場合、呼び出しが成功したかどうかを決定する簡単な方法がないため操作クエリを実行するメソッド。 **Recordset**などによって返されたクエリは閉じられます。 SQL の INSERT ステートメントなどのレコードを返さないクエリを実行する呼び出し、 [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)のメソッド、**コマンド**オブジェクトまたは[Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md)メソッド、の[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトの代わりにします。  
  
 *ActiveConnection*引数に対応、 [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)プロパティを開くには接続を指定し、 **Recordset**オブジェクト。 この引数に接続の定義を渡すと、ADO は、指定されたパラメーターを使用して新しい接続を開きます。 開いた後、 **Recordset**を設定してクライアント側カーソル、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティを**adUseClient**、送信するには、このプロパティの値を変更することができます別のプロバイダーを更新します。 このプロパティを設定することも**Nothing** (Microsoft Visual Basic で) または切断する場合は NULL、**レコード セット**任意のプロバイダーからです。 変更する*ActiveConnection*のサーバー側カーソル、ただし、エラーが発生します。  
  
 プロパティに直接対応して、その他の引数に対して、 **Recordset**オブジェクト (*ソース*、*カーソル*、および*LockType*)、。プロパティへの引数の関係は次のとおりです。  
  
-   プロパティは読み取り/書き込みの前に、 **Recordset**オブジェクトをオープンします。  
  
-   実行するときに対応する引数を渡す場合を除き、プロパティの設定が使用される、**開く**メソッドです。 引数を渡す場合、対応するプロパティの設定をオーバーライドし、プロパティの設定が、引数の値で更新します。  
  
-   開いた後、 **Recordset**オブジェクト、これらのプロパティは読み取り専用になります。  
  
> [!NOTE]
>  **ActiveConnection**プロパティは読み取り専用です**Recordset**オブジェクト[ソース](../../../ado/reference/ado-api/source-property-ado-recordset.md)プロパティが有効な**コマンド**オブジェクト場合でも、 **Recordset**オブジェクトが開かれていません。  
  
 渡す場合、**コマンド**内のオブジェクト、*ソース*引数とパス、 *ActiveConnection*引数、エラーが発生します。 **ActiveConnection**のプロパティ、**コマンド**有効なオブジェクトを設定する必要があります既に**接続**オブジェクトまたは接続文字列。  
  
 以外の何か成功した場合、**コマンド**内のオブジェクト、*ソース*引数、使用できます、*オプション*引数の評価を最適化するために、*ソース*引数。 場合、*オプション*引数が定義されていない、ADO プロバイダーへの呼び出しをかどうか、引数は、SQL ステートメント、ストアド プロシージャ、URL、またはテーブル名を決定する必要があるためにパフォーマンスの低下が発生する可能性があります。 新機能がわかっている場合*ソース*設定を使用する型、*オプション*引数 ADO では、関連するコードに直接ジャンプするように指示します。 場合、*オプション*引数と一致しません、*ソース*入力、エラーが発生します。  
  
 渡す場合、**ストリーム**内のオブジェクト、*ソース*引数を渡さないでください情報を他の引数にします。 そうと、エラーが生成されます。 **ActiveConnection**情報が保持される場合に、**レコード セット**から開かれた、**ストリーム**です。  
  
 既定値、*オプション*引数は**adCmdFile**に関連付けられている接続がない場合、 **Recordset**です。 これは一般に、ケース永続的に格納されているため**Recordset**オブジェクト。  
  
 プロバイダーが、両方を設定、データ ソースにレコードが返されない場合、 [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)と[EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)プロパティを**True**、現在のレコードの位置が定義されていないとします。 この空に新しいデータを追加することもできます**Recordset**オブジェクトのかどうか、カーソルの種類で許可されています。  
  
 開いている操作が完了すると**レコード セット**オブジェクトを使用して、[閉じる](../../../ado/reference/ado-api/close-method-ado.md)を解放するメソッドには、システム リソースが関連付けられています。 オブジェクトを閉じてから削除されませんがメモリです。プロパティの設定を変更して、使用することができます、**開く**を後でもう一度開くメソッドです。 メモリからオブジェクトを完全になくすためには、オブジェクト変数を設定*Nothing*です。  
  
 前に、 **ActiveConnection**プロパティが設定されて、呼び出す**開く**なしのオペランドのインスタンスを作成すると、**レコード セット**にフィールドを追加することによって作成された、 **レコード セット**[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)コレクション。  
  
 設定した場合、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティを**adUseClient**、2 つの方法のいずれかで非同期的に行を取得することができます。 設定はお勧め*オプション*に**adAsyncFetch**です。 「非同期行セットの処理」動的なプロパティを使用する代わりに、[プロパティ](../../../ado/reference/ado-api/properties-collection-ado.md)、コレクションが取得した関連のイベントが失われる場合が設定されていなくて、*オプション*パラメーター**adAsyncFetch**です。  
  
> [!NOTE]
>  バック グラウンドのフェッチ MS リモート プロバイダーではサポートされてを通してのみ、**開く**メソッドの*オプション*パラメーター。  
  
> [!NOTE]
>  Http スキームを使用する Url が自動的に起動、 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)です。 詳細については、次を参照してください。[絶対と相対 Url](../../../ado/guide/data/absolute-and-relative-urls.md)です。  
  
 特定の組み合わせ[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)と[ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md)の値が無効です。 どのオプションを組み合わせることができませんについては、トピックをご覧ください。、 [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md)、および[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)です。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Open および Close メソッドの例 (VB)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Open および Close メソッドの例 (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Open および Close メソッドの例 (vc++)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [保存して開く方法の例 (VB)](../../../ado/reference/ado-api/save-and-open-methods-example-vb.md)   
 [Open メソッド (ADO 接続)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open メソッド (ADO レコード)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open メソッド (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [OpenSchema メソッド](../../../ado/reference/ado-api/openschema-method.md)   
 [Save メソッド](../../../ado/reference/ado-api/save-method.md)
