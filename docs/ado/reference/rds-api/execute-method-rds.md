---
title: Execute メソッド (RDS) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Execute method [ADO]
ms.assetid: 2d9c30e9-ab5b-4920-91b8-48454c2fb5d8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d1a5fa5c9002d4a27490dfc98fb79f482539f042
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67964318"
---
# <a name="execute-method-rds"></a>Execute メソッド (RDS)
要求を実行し、ado 2.5 以降で使用する ADO レコードセットを作成します。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および[Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416)」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.Execute(ConnectionString As String, HandlerString As String, QueryString As String, lFetchOptions As Long, Properties, TableId, lExecuteOptions As Long, pParameters, [lcid As Long], [pInformation])  
```  
  
#### <a name="parameters"></a>パラメーター  
 *文字列*  
 要求が実行のために送信される OLE DB プロバイダーに接続するために使用される文字列。 ハンドラーが*ハンドラ文字列*を使用して指定されている場合は、接続文字列を編集または置換できます。  
  
 *ハンドラ文字列*  
 この実行で使用されるハンドラーを識別する2つの部分から構成される文字列。 文字列には2つの部分が含まれています。 最初の部分には、使用するハンドラーの名前 (ProgID) が含まれています。 2番目の部分には、ハンドラーに渡される引数が含まれています。 引数文字列の解釈方法の詳細は、各ハンドラーに固有です。 2つの部分は、文字列内のコンマの最初のインスタンスによって区切られます。 Arguments 文字列には、追加のコンマを含めることができます。 引数は省略可能です。  
  
 *クエリ*  
 接続文字列で指定された OLE DB プロバイダーによってサポートされるコマンド言語のコマンドです。 SQL ベースのプロバイダーの場合** 、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]クエリ文字列に transact-sql コマンドステートメントが含まれている可能性がありますが、非 SQL プロバイダー (たとえば、MSDataShape) の場合、これはクエリステートメントではない可能性があります。  
  
 ハンドラーが使用されている場合、ハンドラーはここで指定された値を変更または置換できます。 たとえば、ハンドラーは通常、 *QueryString*を .ini ファイルのクエリ文字列に置き換えます。 既定では、Msdfmap .ini ファイルが使用されます。  
  
 *lFetchOptions*  
 非同期フェッチの種類を示します。  
  
 詳細については、「 [Fetchoptions プロパティ (RDS)](../../../ado/reference/rds-api/fetchoptions-property-rds.md)」を参照してください。  
  
 *TableID*  
 VT_EMPTY または VT_BSTR 型の**バリアント**。 この値が VT_EMPTY 型の場合、この値は無視されます。 VT_BSTR 型の場合、レコードセットは**Adcmdtabledirect**を使用して作成され、ここで指定された値と*QueryString*パラメーターは無視されます。  
  
 *lExecuteOptions*  
 実行オプションのビットマスク。  
  
 1 =*読み取り専用*: **adlockreadonly**を使用してレコードセットを開きます。  
  
 2 =*Nobatch*レコードセットは、 **adlockoptimistic**を使用して開かれます。  
  
 4 =*Allparaminfosupplied*元は、すべてのパラメーターのパラメーター情報が*pparameters*に指定されていることを保証します。  
  
 8 = クエリの*GetInfo*パラメーター情報は OLE DB プロバイダーから取得され、 *pparameters*パラメーターに返されます。 クエリは実行されず、レコードセットは返されません。  
  
 16 =*GetHiddenColumns*レコードセットは**Adlockbatchoptimistic**を使用して開かれ、すべての非表示の列がレコードセットに含まれます。  
  
 *ReadOnly*、 *nobatch* 、および*GetHiddenColumns*は、相互に排他的なオプションです。ただし、複数の値を設定するエラーは発生しません。 複数のオプションが設定されている場合、 *GetHiddenColumns*は他のオプションよりも優先され、その後に*ReadOnly*が適用されます。 オプションが指定されていない場合、既定では、レコードセットは**Adlockbatchoptimistic**を使用して開かれ、非表示の列はレコードセットに含まれません。  
  
 *pParameters*  
 パラメーター定義のセーフ配列を含む**バリアント**。 [ *GetInfo* ] オプションが*lexecuteoptions*で指定されている場合、このパラメーターを使用して、OLE DB プロバイダーから取得したパラメーター定義が返されます。 それ以外の場合、このパラメーターは空にすることができます。  
  
 *lcid*  
 *Pinformation*で返されたエラーを構築するために使用される LCID。  
  
 *pInformation*  
 Execute によって返された情報エラーへのポインター。 NULL の場合、エラー情報は返されません。  
  
## <a name="remarks"></a>解説  
 *ハンドラー文字列*パラメーターは null にすることができます。 この場合の動作は、RDS サーバーがどのように構成されているかによって異なります。 "MSDFMAP. handler" というハンドラー文字列は、Microsoft 提供のハンドラー (Msdfmap .dll) を使用する必要があることを示します。 "" のハンドラー文字列 "は、" "のハンドラー文字列" は、Msdfmap .dll ハンドラーを使用する必要があり、引数 "sample .ini" をハンドラーに渡す必要があることを示します。 MSDFMAP .dll は、この引数を、サンプルの .ini を使用して接続とクエリ文字列を確認するための方向として解釈します。  
  
## <a name="applies-to"></a>適用対象  
 [DataFactory オブジェクト (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


