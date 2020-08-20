---
description: Open メソッド (ADO Recordset)
title: Open メソッド (ADO Recordset) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_Open
- Recordset15::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: 3236749c-4b71-4235-89e2-ccdfaaa9319d
author: rothja
ms.author: jroth
ms.openlocfilehash: d8a4514e677b2b50effdadd2eac24c9f195a1f07
ms.sourcegitcommit: 291ae8f6b72fd355f8f24ce5300339306293ea7e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/18/2020
ms.locfileid: "88512258"
---
# <a name="open-method-ado-recordset"></a>Open メソッド (ADO Recordset)
[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトのカーソルを開きます。  
  
## <a name="syntax"></a>構文  
  
```  
  
recordset.Open Source, ActiveConnection, CursorType, LockType, Options  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ソース*  
 任意。 有効な[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト、SQL ステートメント、テーブル名、ストアドプロシージャ呼び出し、URL、または永続的に格納された[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)を含むファイルまたは[ストリーム](../../../ado/reference/ado-api/stream-object-ado.md)オブジェクトの名前に評価される**バリアント**。  
  
 *ActiveConnection*  
 任意。 有効な[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクト変数名に評価される**Variant** 、または[ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)パラメーターを含む**文字列**。  
  
 *CursorType*  
 任意。 **レコードセット**を開くときにプロバイダーが使用する必要があるカーソルの種類を決定する[cursor typeenum](../../../ado/reference/ado-api/cursortypeenum.md)値。 既定値は **adOpenForwardOnly**です。  
  
 *LockType*  
 任意。 **レコードセット**を開くときにプロバイダーが使用するロックの種類 (同時実行) を決定する[locktypeenum](../../../ado/reference/ado-api/locktypeenum.md)値。 既定値は **Adlockreadonly**です。  
  
 *[オプション]*  
 任意。 プロバイダーが**Command**オブジェクト以外の値を表す場合に*ソース*引数を評価する方法、または**レコードセット**を以前に保存したファイルから復元する必要があるかどうかを示す**Long**値。 1つ以上の [Commandtypeenum](../../../ado/reference/ado-api/commandtypeenum.md) 値または [executeoptionenum](../../../ado/reference/ado-api/executeoptionenum.md) 値を指定できます。この値は、ビットごとの or 演算子と組み合わせることができます。  
  
> [!NOTE]
>  永続化された**レコードセット**を含む**ストリーム**から**レコードセット**を開いた場合、 [executeoptionenum](../../../ado/reference/ado-api/executeoptionenum.md)値**adasyncfetchunusing**を使用しても効果はありません。フェッチは同期およびブロックされます。  
  
> [!NOTE]
>  **AdExecuteNoRecords**または**AdExecuteStream**の**executeopenenum**値は、 **Open**では使用できません。  
  
## <a name="remarks"></a>解説  
 ADO **レコードセット** の既定のカーソルは、サーバー上にある順方向専用の読み取り専用カーソルです。  
  
 **Recordset**オブジェクトで**Open**メソッドを使用すると、ベーステーブル、クエリの結果、または以前に保存した**レコードセット**のレコードを表すカーソルが開きます。  
  
 オプションの *source* 引数を使用して、次のいずれかを使用してデータソースを指定します: **コマンド** オブジェクト変数、SQL ステートメント、ストアドプロシージャ、テーブル名、URL、または完全なファイルパス名。 *Source*がファイルパス名の場合は、完全なパス ("c:\dir\file.rst")、相対パス ("..\file.rst ")、または URL ( `https://files/file.rst` )。  
  
 **Open**メソッドの*Source*引数を使用して、レコードを返さないアクションクエリを実行することはお勧めできません。これは、呼び出しが成功したかどうかを判断する簡単な方法がないためです。 このようなクエリによって返された **レコードセット** は閉じられます。 SQL INSERT ステートメントなど、レコードを返さないクエリを実行するには、 **Command**オブジェクトの[execute](../../../ado/reference/ado-api/execute-method-ado-command.md)メソッド、または[接続](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトの[execute](../../../ado/reference/ado-api/execute-method-ado-connection.md)メソッドを呼び出します。  
  
 *ActiveConnection*引数は[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)プロパティに対応し、**レコードセット**オブジェクトを開くための接続を指定します。 この引数に対して接続定義を渡すと、指定されたパラメーターを使用して新しい接続が開かれます。 クライアント側カーソルを使用して **レコードセット** を開いた後、[ [cursor location](../../../ado/reference/ado-api/cursorlocation-property-ado.md) ] プロパティを **adUseClient**に設定して、このプロパティの値を変更して別のプロバイダーに更新を送信することができます。 または、このプロパティを [ **なし** ] (Microsoft Visual Basic の場合) または [NULL] に設定して、プロバイダーから **レコードセット** を切断することもできます。 ただし、サーバー側カーソルの *ActiveConnection* を変更すると、エラーが生成されます。  
  
 **Recordset**オブジェクト (*Source*、 *CursorType*、および*LockType*) のプロパティに直接対応するその他の引数については、プロパティの引数の関係は次のとおりです。  
  
-   **Recordset**オブジェクトを開く前に、プロパティは読み取り/書き込みが可能です。  
  
-   **Open**メソッドを実行するときに、対応する引数を渡さない限り、プロパティの設定が使用されます。 引数を渡すと、対応するプロパティの設定がオーバーライドされ、プロパティの設定が引数の値で更新されます。  
  
-   **レコードセット**オブジェクトを開いた後、これらのプロパティは読み取り専用になります。  
  
> [!NOTE]
>  **ActiveConnection**プロパティは、 **recordset**オブジェクトが開いていない場合でも、 [Source](../../../ado/reference/ado-api/source-property-ado-recordset.md)プロパティが有効な**コマンド**オブジェクトに設定されている**レコードセット**オブジェクトに対しては読み取り専用です。  
  
 *Source*引数に**Command**オブジェクトを渡し、 *ActiveConnection*引数も渡すと、エラーが発生します。 **Command**オブジェクトの**ActiveConnection**プロパティには、有効な**接続**オブジェクトまたは接続文字列が既に設定されている必要があります。  
  
 *Source*引数で**Command**オブジェクト以外のものを渡す場合は、 *Options*引数を使用して、 *source*引数の評価を最適化できます。 *Options*引数が定義されていない場合、ADO はプロバイダーを呼び出して、引数が SQL ステートメント、ストアドプロシージャ、URL、またはテーブル名であるかどうかを判断する必要があるため、パフォーマンスが低下する可能性があります。 使用している *ソース* の種類がわかっている場合は、 *Options* 引数を設定すると、関連するコードに直接ジャンプするよう ADO に指示されます。 *Options*引数が*ソース*の型と一致しない場合、エラーが発生します。  
  
 *Source*引数に**ストリーム**オブジェクトを渡す場合は、他の引数に情報を渡さないでください。 併用した場合、エラーが発生します。 **レコードセット**が**ストリーム**から開かれた場合、 **ActiveConnection**情報は保持されません。  
  
 接続が**レコードセット**に関連付けられていない場合、 *Options*引数の既定値は**adcmdfile**です。 これは、通常、永続的に格納された **レコードセット** オブジェクトの場合に当てはまります。  
  
 データソースからレコードが返されなかった場合、プロバイダーは [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) プロパティと [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) プロパティの両方を **True**に設定し、現在のレコード位置は未定義になります。 カーソルの種類で許可されている場合は、この空の **レコードセット** オブジェクトに新しいデータを追加することもできます。  
  
 開いている **レコードセット** オブジェクトに対して操作を完了したら、 [Close](../../../ado/reference/ado-api/close-method-ado.md) メソッドを使用して、関連付けられているすべてのシステムリソースを解放します。 オブジェクトを閉じると、メモリから削除されません。プロパティの設定を変更し、 **open** メソッドを使用して後で再び開くことができます。 メモリからオブジェクトを完全に削除するには、オブジェクト変数を *Nothing*に設定します。  
  
 **ActiveConnection**プロパティを設定する前に、オペランドなしで**Open**を呼び出して、**レコードセット**[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)コレクションにフィールドを追加することによって作成された**レコードセット**のインスタンスを作成します。  
  
 [ [カーソルの場所](../../../ado/reference/ado-api/cursorlocation-property-ado.md) ] プロパティを **adUseClient**に設定している場合は、次の2つの方法のいずれかで、行を非同期的に取得できます。 *オプション*を**adasyncfetch**に設定する方法をお勧めします。 または、 [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) コレクションで "非同期の行セット処理" 動的プロパティを使用することもできますが、 *Options* パラメーターを **adasyncfetch**に設定しないと、関連する取得したイベントが失われる可能性があります。  
  
> [!NOTE]
>  MS リモートプロバイダーでのバックグラウンドフェッチは、 **Open** メソッドの *Options* パラメーターを使用してのみサポートされています。  
  
> [!NOTE]
>  Http スキームを使用する Url は、 [インターネット公開のために Microsoft OLE DB プロバイダー](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)を自動的に呼び出します。 詳細については、「 [絶対 url と相対 url](../../../ado/guide/data/absolute-and-relative-urls.md)」を参照してください。  
  
 [Commandtypeenum](../../../ado/reference/ado-api/commandtypeenum.md)値と[executeoptionenum](../../../ado/reference/ado-api/executeoptionenum.md)値の特定の組み合わせが無効です。 組み合わせることができないオプションの詳細については、 [Executeoptionenum](../../../ado/reference/ado-api/executeoptionenum.md)および [commandtypeenum](../../../ado/reference/ado-api/commandtypeenum.md)のトピックを参照してください。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>関連項目  
 [Open および Close メソッドの例 (VB)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Open および Close メソッドの例 (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Open および Close メソッドの例 (VC + +)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Save および Open メソッドの例 (VB)](../../../ado/reference/ado-api/save-and-open-methods-example-vb.md)   
 [Open メソッド (ADO Connection)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open メソッド (ADO Record)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open メソッド (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [OpenSchema メソッド](../../../ado/reference/ado-api/openschema-method.md)   
 [Save メソッド](../../../ado/reference/ado-api/save-method.md)
