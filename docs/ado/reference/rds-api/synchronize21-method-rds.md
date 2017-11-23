---
title: "Synchronize21 メソッド (RDS) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords: Synchronize21 method [ADO]
ms.assetid: 6b35f136-9d9a-4bdd-8144-67decfd3c4e9
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 996510799ad3222a40910af3a1d04c9cbb9b30fe
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="synchronize21-method-rds"></a>Synchronize21 メソッド (RDS)
ADO 2.1 で使用する接続文字列で指定されたデータベースと特定のレコード セットを同期します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.Synchronize21(ConnectionString As String, HandlerString As String, lSynchronizeOptions As Long, ppRecordset As Object, pStatusArray)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ConnectionString*  
 要求が送信され、OLE DB プロバイダーへの接続に使用する文字列。 ハンドラーを使用する場合、ハンドラーが編集または接続文字列を置換できます。  
  
 *HandlerString*  
 文字列は、この実行で使用するハンドラーを識別します。 文字列には、2 つの部分が含まれています。 最初の部分には、使用するハンドラーの名前 (ProgID) が含まれています。 文字列の 2 番目の部分には、ハンドラーに渡される引数が含まれています。 特定のハンドラーには、引数文字列を解釈する方法です。 2 つの部分は、最初のインスタンスの文字列で、コンマで区切られます。 引数の文字列には、追加のコンマを含めることができます。 引数は省略できます。  
  
 *lSynchronizeOptions*  
 同期オプションのビット マスクです。  
  
 1 =*UpdateTransact*データベースへの更新がトランザクションにラップされます。 更新プログラムの失敗した場合は、トランザクションが中止されました。  
  
 2 =*RefreshWithUpdate*原因行のどちらの場合に返されるステータス*更新*も*RefreshConflicts*設定されています。  
  
 4 =*更新*レコード セットは、データベースの現在のデータを更新します。 保留中の更新は、データベースにプッシュされません。 このビットが設定されていない場合は、レコード セットは更新されず、保留中の更新プログラムがデータベースにプッシュされます。  
  
 8 =*RefreshConflicts*保留中の変更を含む行が更新に失敗します。 データベースから現在のデータでは、更新に失敗した行が更新されます。  
  
 *ppRecordset*  
 同期するレコード セットへのポインターへのポインター。  
  
 *pStatusArray*  
 影響を受ける行の状態を行のセーフ配列を返すために使用するバリアント型を同期します。 未設定次の同期オプションのいずれも設定されている場合: *RefreshWithUpdate*、*更新*と*RefreshConflicts*です。  
  
## <a name="remarks"></a>解説  
 *HandlerString*パラメーターを null にすることができます。 この場合の動作は、RDS サーバーを構成する方法によって異なります。 "MSDFMAP.handler"のハンドラーの文字列では、Microsoft から提供されたハンドラー (Msdfmap.dll) を使用することを示します。 "MASDFMAP.handler,sample.ini"のハンドラー文字列は、Msdfmap.dll ハンドラーを使用することと、"sample.ini"の引数をハンドラーに渡される必要があることを示します。 Msdfmap.dll は、sample.ini を使用して、接続およびクエリ文字列を確認する方向として、引数を解釈します。  
  
> [!NOTE]
>  **Synchronize21**メソッドは単なるバージョンのでは、[同期メソッド (RDS)](../../../ado/reference/rds-api/synchronize-method-rds.md)です。 使用する必要があります、**同期**2.1 では、ADO と通信するメソッド、 **Synchronize21**メソッドを代わりに呼び出すことができます。 機能、**同期**ADO 2.5 以降のメソッドは、ADO 2.1 では、同じメソッドを提供する機能のスーパー セットです。  
  
## <a name="applies-to"></a>適用対象  
 [DataFactory オブジェクト (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


