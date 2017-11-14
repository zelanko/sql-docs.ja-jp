---
title: "Execute21 メソッド (RDS) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- Execute21 method [RDS]
ms.assetid: 9f131c8d-1497-416d-8209-abb481c38f7b
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b3a985a6bb9d9e50a3a6d6741a8f379abafc26af
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="execute21-method-rds"></a>Execute21 メソッド (RDS)
要求を実行し、ADO 2.1 で使用する ADO レコード セットを作成します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.Execute21(ConnectionString As String, HandlerString As String, QueryString As String, lMarshalOptions As Long, Properties, TableId, lExecuteOptions As Long, pParameters)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ConnectionString*  
 実行のため、要求を送信する先の OLE DB プロバイダーへの接続に使用する文字列。 使用して、ハンドラーが指定されている場合*HandlerString*、編集、接続文字列を置換します。  
  
 *HandlerString*  
 文字列は、この実行で使用するハンドラーを識別します。 文字列には、2 つの部分が含まれています。 最初の部分には、使用するハンドラーの名前 (ProgID) が含まれています。 文字列の 2 番目の部分には、ハンドラーに渡される引数が含まれています。 特定のハンドラーには、引数文字列を解釈する方法です。 (ただし、引数文字列には、追加のコンマを含めることができます)、2 つの部分は、コンマ、文字列内の最初のインスタンスで区切られます。 引数は省略できます。  
  
 *クエリ文字列*  
 接続文字列で識別される OLE DB プロバイダーによってサポートされるコマンド言語でのコマンド。 SQL ベースのプロバイダーでは、含まれる、[!INCLUDE[tsql](../../../includes/tsql_md.md)]ステートメントでは、コマンドしますが、非 SQL プロバイダー (たとえば、MSDataShape) とは限りません、[!INCLUDE[tsql](../../../includes/tsql_md.md)]ステートメントのクエリを実行します。  
  
 ハンドラーが使用されている (ハンドラーを使用することを強くお勧め) 場合、ハンドラーを変更したり、ここで指定した値を置換できます。 たとえば、ハンドラーは、通常に置き換えられます*QueryString* .ini ファイルからクエリ文字列を使用します。 既定では、Msdfmap.ini ファイルが使用されます。  
  
 *lMarshalOptions*  
 返される行セットまたはレコード セットでのマーシャ リング オプションを設定するために使用します。  
  
 *TableID*  
 バリアントは、VT_EMPTY または VT_BSTR のいずれかを入力します。 この値が VT_EMPTY 型の場合は無視されます。 使用して、レコード セットが作成された VT_BSTR 型の場合、 **adCmdTableDirect**ここで指定された値を使用して、 *QueryString*パラメーターは無視されます。  
  
 *lExecuteOptions*  
 実行オプションのビットマスクを指定します。  
  
 1 =*ReadOnly*を使用して、レコード セットを開いた、 **adLockReadOnly**です。  
  
 2 =*NoBatch*を使用して、レコード セットを開いた、 **adLockOptimistic**です。  
  
 4 =*AllParamInfoSupplied* 、呼び出し元のすべてのパラメーターのパラメーター情報を提供することを保証*pParameters*です。  
  
 8 =*GetInfo*クエリのパラメーター情報が、OLE DB プロバイダーから取得しで返される、 *pParameters*パラメーター。 クエリが実行されないと、レコード セットは返されません。  
  
 16 = を使用して、レコード セットを開いた、GetHiddenColumns **adLockBatchOptimistic**と非表示の列は、レコード セットに含まれます。  
  
 *ReadOnly*、 *NoBatch*と*GetHiddenColumns*相互排他的なオプションは、1 つ以上を設定すると、エラーではありません。 複数のオプションが設定されている場合*GetHiddenColumns*後に、その他のすべてのオプションよりも優先*ReadOnly*です。 使用して、レコード セットを開いたオプションが指定されていない場合、既定では、 **adLockBatchOptimistic**非表示の列は、レコード セットには含まれません。  
  
 *pParameters*  
 パラメーターの定義のセーフ配列を含むバリアント型。 場合、 *GetInfo*オプションに指定されました*lExecuteOptions*、このパラメーターは、OLE DB プロバイダーから取得したパラメーターの定義を返すに使用します。 それ以外の場合、このパラメーターを空にすることがあります。  
  
## <a name="remarks"></a>解説  
 *HandlerString*パラメーターを null にすることがあります。 この場合の処理は、RDS サーバーを構成する方法によって異なります。 "MSDFMAP.handler"のハンドラーの文字列では、Microsoft から提供されたハンドラー (Msdfmap.dll) を使用することを示します。 "MASDFMAP.handler,sample.ini"のハンドラー文字列は、Msdfmap.dll ハンドラーを使用することと、"sample.ini"の引数をハンドラーに渡される必要があることを示します。 MSDFMAP.dll は、方向、sample.ini を使用して、接続およびクエリ文字列を確認すると、引数を解釈します。  
  
> [!NOTE]
>  **Execute21**メソッドは、バージョンのでは、[メソッド (RDS) を実行する](../../../ado/reference/rds-api/execute-method-rds.md)です。 使用する必要があります、 **Execute** 2.1 では、ADO と通信するメソッド、 **Execute21**メソッドを代わりに呼び出すことができます。 機能、 **Execute** ADO 2.5 以降のメソッドは、ADO 2.1 では、同じメソッドを提供する機能のスーパー セットです。  
  
## <a name="applies-to"></a>適用対象  
 [DataFactory オブジェクト (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)



