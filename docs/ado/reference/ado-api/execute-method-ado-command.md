---
title: "Execute メソッド (ADO コマンド) |Microsoft ドキュメント"
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
- Command15::Execute
- Command15::raw_Execute
helpviewer_keywords: Execute method [ADO]
ms.assetid: f84a5ff3-0528-4ad7-9bea-9a15103378dd
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: aa39093a0efe75959bfa0e6805ea90b65c6d39a9
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="execute-method-ado-command"></a>Execute メソッド (ADO コマンド)
クエリや、SQL ステートメントで指定されたストアド プロシージャの実行、 [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)または[CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md)のプロパティ、[コマンド オブジェクト](../../../ado/reference/ado-api/command-object-ado.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set recordset = command.Execute( RecordsAffected, Parameters, Options )  
```  
  
## <a name="return-value"></a>戻り値  
 返します、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト参照、ストリーム、または**Nothing**です。  
  
#### <a name="parameters"></a>パラメーター  
 *RecordsAffected*  
 省略可。 A**長い**先変数プロバイダーが返されます、操作の影響を受けるレコードの数。 *RecordsAffected*パラメーターは、アクションのクエリまたはストアド プロシージャに対してのみ適用されます。 *RecordsAffected*結果を返すクエリまたはストアド プロシージャによって返されるレコードの数は返しません。 この情報を取得するには、 [RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)プロパティです。 **Execute**メソッドでは、正しい情報で使用する場合は返されません**adAsyncExecute**、単にコマンドを実行すると非同期的に、ために影響を受けたレコードの数はまだわかりません時に、メソッドを返します。  
  
 *パラメーター*  
 省略可。 A**バリアント**入力文字列またはストリームに指定されたと組み合わせて使用するパラメーター値の配列**CommandText**または**CommandStream**です。 (出力パラメーターは返されませんこの引数で渡されるときに適切な値。)  
  
 *および*  
 省略可。 A**長い**プロバイダーを評価する方法を示す値、 [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)または[CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md)のプロパティ、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト。 指定できる値のビットマスクを使用して確立[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)や[ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md)値。 たとえば、使用する**adCmdText**と**adExecuteNoRecords**組み合わせて ADO の値を評価する場合、 **CommandText**プロパティとして、テキストと示しますのコマンドは、必要がありますを破棄し、コマンド テキストの実行時に生成されるレコードが返されません。  
  
> [!NOTE]
>  使用して、 **ExecuteOptionEnum**値**adExecuteNoRecords**内部処理を最小限に抑えることによってパフォーマンスを向上させるためにします。 場合**adExecuteStream**が指定されているオプション**adAsyncFetch**と**adAsynchFetchNonBlocking**は無視されます。 使用しないでください、 **CommandTypeEnum**値**adCmdFile**または**adCmdTableDirect**で**Execute**です。 これらの値は、オプションとしてのみ使用できます、[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)と[Requery](../../../ado/reference/ado-api/requery-method.md)のメソッド、 **Recordset**です。  
  
## <a name="remarks"></a>解説  
 使用して、 **Execute**メソッドを**コマンド**オブジェクトで指定されたクエリの実行、 **CommandText**プロパティまたは**CommandStream**オブジェクトのプロパティです。  
  
 結果が返される、 **Recordset** (既定) またはバイナリ情報のストリームとして。 バイナリ ストリームを取得する指定**adExecuteStream**で*オプション*を設定してストリームを指定し、 **Command.Properties (「出力ストリーム」)**です。 ADO**ストリーム**結果を受信するオブジェクトを指定するか、IIS 応答オブジェクトなどの別のストリーム オブジェクトを指定することができます。 呼び出しの前にストリームが指定されなかった場合**Execute**で**adExecuteStream**エラーが発生します。 制御が戻るとき、ストリームの位置**Execute**がプロバイダーを特定します。  
  
 プロバイダーが返すかどうか、コマンドはありません (たとえば、SQL UPDATE クエリ) の結果を返す**Nothing**オプションとして長さ**adExecuteNoRecords**が指定されているそれ以外の場合を返しますを実行、。閉じられた**Recordset**です。 いない場合は、この戻り値を無視することは一部のアプリケーション言語**Recordset**が必要です。  
  
 **実行**ユーザーの値を指定する場合、エラーが発生**CommandStream**ときに、 **CommandType**は**adCmdStoredProc**、 **adCmdTable**、または**adCmdTableDirect**です。  
  
 場合は、クエリでは、パラメーターを持ち、現在の値、**コマンド**これらに渡されたパラメーター値をオーバーライドする場合を除き、オブジェクトのパラメーターが使用されます、 **Execute**呼び出します。 呼び出すときに、一部のパラメーターの新しい値を省略することで、パラメーターのサブセットをオーバーライドすることができます、 **Execute**メソッドです。 パラメーターを指定する順序は、メソッドがそれらに渡す同じ順序です。 たとえば、次の 4 つ (以上) のパラメーターがあった場合と 1 番目と 4 番目のパラメーターだけの新しい値を渡すに渡す場合`Array(var1,,,var4)`として、*パラメーター*引数。  
  
> [!NOTE]
>  出力パラメーターに渡されるときに正しい値を返しません、*パラメーター*引数。  
  
 [ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md)この操作の終了時にイベントが発行されます。  
  
> [!NOTE]
>  Url を含むコマンドを発行する際に、http スキームを使用しているユーザーが自動的に呼び出さ、 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)です。 詳細については、次を参照してください。[絶対と相対 Url](../../../ado/guide/data/absolute-and-relative-urls.md)です。  
  
## <a name="applies-to"></a>適用対象  
 [Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [実行、クエリを再実行、およびメソッドの例 (VB) をオフに](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [実行、クエリを再実行、およびメソッドの例 (VBScript) をオフに](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [実行、クエリを再実行、およびメソッドの例 (vc++) をオフに](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [CommandStream プロパティ (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md)   
 [CommandText プロパティ (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)   
 [Execute メソッド (ADO 接続)](../../../ado/reference/ado-api/execute-method-ado-connection.md)   
 [ExecuteComplete イベント (ADO)](../../../ado/reference/ado-api/executecomplete-event-ado.md)
