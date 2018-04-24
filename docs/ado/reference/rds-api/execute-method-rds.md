---
title: Execute メソッド (RDS) |Microsoft ドキュメント
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
helpviewer_keywords:
- Execute method [ADO]
ms.assetid: 2d9c30e9-ab5b-4920-91b8-48454c2fb5d8
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: db01dfef8e751808431b1796ee022060e30a7d17
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="execute-method-rds"></a>Execute メソッド (RDS)
要求を実行し、2.5 以降、ADO で使用する ADO レコード セットを作成します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.Execute(ConnectionString As String, HandlerString As String, QueryString As String, lFetchOptions As Long, Properties, TableId, lExecuteOptions As Long, pParameters, [lcid As Long], [pInformation])  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ConnectionString*  
 実行のため、要求を送信する先の OLE DB プロバイダーへの接続に使用する文字列。 使用して、ハンドラーが指定されている場合*HandlerString*編集したり、接続文字列を置換します。  
  
 *HandlerString*  
 この実行で使用するハンドラーを識別する 2 つの部分文字列。 文字列には、2 つの部分が含まれています。 最初の部分には、使用するハンドラーの名前 (ProgID) が含まれています。 2 番目の部分には、ハンドラーに渡される引数が含まれています。 引数文字列を解釈する方法の詳細については、各ハンドラーに固有です。 2 つの部分は、最初のインスタンスの文字列で、コンマで区切られます。 引数の文字列には、追加のコンマを含めることができます。 引数は省略できます。  
  
 *QueryString*  
 接続文字列で識別される OLE DB プロバイダーによってサポートされるコマンド言語でのコマンド。 SQL ベースのプロバイダーでは、 *QueryString* TRANSACT-SQL コマンドのステートメントが含まれますが、非 SQL プロバイダー (たとえば、MSDataShape) とは限りません、[!INCLUDE[tsql](../../../includes/tsql_md.md)]ステートメントのクエリを実行します。  
  
 ハンドラーが使用されている場合、ハンドラーが alter またはここで指定した値を置換できます。 たとえば、ハンドラーは、通常に置き換えられます*QueryString* .ini ファイルからクエリ文字列を使用します。 既定では、Msdfmap.ini ファイルが使用されます。  
  
 *lFetchOptions*  
 非同期フェッチの型を示します。  
  
 詳細については、次を参照してください。 [FetchOptions プロパティ (RDS)](../../../ado/reference/rds-api/fetchoptions-property-rds.md)です。  
  
 *TableID*  
 A**バリアント**型の VT_EMPTY または VT_BSTR のいずれか。 この値が VT_EMPTY 型の場合は無視されます。 使用して、レコード セットが作成された VT_BSTR 型の場合、 **adCmdTableDirect**とここで指定した値と*QueryString*パラメーターは無視されます。  
  
 *lExecuteOptions*  
 実行オプションのビット マスク:  
  
 1 =*ReadOnly*を使用して、レコード セットを開いた、 **adLockReadOnly**です。  
  
 2 =*NoBatch*を使用して、レコード セットを開いた、 **adLockOptimistic**です。  
  
 4 =*AllParamInfoSupplied* 、呼び出し元のすべてのパラメーターのパラメーター情報を提供することを保証*pParameters*です。  
  
 8 =*GetInfo*クエリのパラメーター情報が、OLE DB プロバイダーから取得しで返される、 *pParameters*パラメーター。 クエリが実行されないと、レコード セットは返されません。  
  
 16 =*GetHiddenColumns*を使用して、レコード セットを開いた、 **adLockBatchOptimistic**と非表示の列は、レコード セットに含まれます。  
  
 *読み取り専用*、 *NoBatch*と*GetHiddenColumns*相互排他的なオプションです。 ただし、これはエラーが発生しない 1 つ以上を設定します。 複数のオプションが設定されている場合*GetHiddenColumns*他のすべて、続けてよりも優先*ReadOnly*です。 使用して、レコード セットを開いたオプションが指定されていない場合、既定では、 **adLockBatchOptimistic**と非表示の列は、レコード セットに含まれません。  
  
 *pParameters*  
 A**バリアント**パラメーター定義のセーフ配列を格納しています。 場合、 *GetInfo*オプションに指定されました*lExecuteOptions*、このパラメーターは、OLE DB プロバイダーから取得したパラメーターの定義を返すに使用します。 それ以外の場合、このパラメーターを空にすることができます。  
  
 *lcid*  
 返されるエラーをビルドするために使用 LCID *pInformation*です。  
  
 *pInformation*  
 実行によって返される情報エラーへのポインター。 NULL の場合、エラー情報は返されません。  
  
## <a name="remarks"></a>解説  
 *HandlerString*パラメーターを null にすることがあります。 この場合の動作は、RDS サーバーを構成する方法によって異なります。 "MSDFMAP.handler"のハンドラーの文字列では、Microsoft から提供されたハンドラー (Msdfmap.dll) を使用することを示します。 "MASDFMAP.handler,sample.ini"のハンドラー文字列は、Msdfmap.dll ハンドラーを使用することと、"sample.ini"の引数をハンドラーに渡される必要があることを示します。 MSDFMAP.dll は、方向、sample.ini を使用して、接続およびクエリ文字列を確認すると、引数を解釈します。  
  
## <a name="applies-to"></a>適用対象  
 [DataFactory オブジェクト (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


