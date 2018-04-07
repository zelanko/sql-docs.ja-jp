---
title: ローカル トランザクションのサポート |Microsoft ドキュメント
description: SQL Server の OLE DB Driver でローカル トランザクション
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-transactions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- OLE DB Driver for SQL Server, transactions
- local transactions [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5076c62a7c6553c0474585960da74af2f392b019
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="supporting-local-transactions"></a>ローカル トランザクションのサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  セッションでは、OLE DB 用のドライバーを SQL Server のローカル トランザクションのトランザクション スコープを区切ります。 ときに、コンシューマーの方向で、OLE DB Driver for SQL Server に送信した要求のインスタンスに接続[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]要求は、OLE DB Driver for SQL Server の作業の単位を構成します。 ローカル トランザクションは常に、SQL Server セッションの 1 つ OLE DB ドライバーの作業の 1 つまたは複数の単位をラップします。  
  
 SQL Server の自動コミット モードの既定の OLE DB Driver を使用して、単一の作業単位がローカル トランザクションのスコープとして扱われます。 ローカル トランザクションに参加するのは、1 単位のみです。 セッションの作成時に、OLE DB Driver for SQL Server は、セッションのトランザクションを開始します。 作業単位の処理が正常に完了すると、その作業がコミットされます。 失敗すると、開始された作業がすべてロールバックされ、エラーがコンシューマーに報告されます。 どちらの場合、OLE DB Driver for SQL Server は、トランザクション内ですべての作業を実行できるように、セッションに対して新しいローカル トランザクションを開始します。  
  
 使用して、OLE DB Driver for SQL Server コンシューマーがローカル トランザクションのスコープをより正確に制御を指示できます、 **ITransactionLocal**インターフェイスです。 セッションのすべての作業単位トランザクション間で開始ポイントと、最終的なコンシューマーのセッションを開始すると、トランザクション、**コミット**または**中止**メソッド呼び出しはアトミック単位として扱われます。 OLE DB Driver for SQL Server では、そのためには、コンシューマーによって指示された場合に、トランザクションに暗黙的に開始します。 コンシューマーがモードの保持を要求しないと、セッションは親のトランザクション レベルの動作 (通常は、自動コミット モード) に戻ります。  
  
 SQL Server の OLE DB ドライバーをサポートしている**itransactionlocal::starttransaction**パラメーターは次のようにします。  
  
|パラメーター|Description|  
|---------------|-----------------|  
|*isoLevel*[in]|このトランザクションで使用する分離レベルを指定します。 ローカル トランザクションの場合に、OLE DB Driver for SQL Server には、以下がサポートしています。<br /><br /> **ISOLATIONLEVEL_UNSPECIFIED**<br /><br /> **ISOLATIONLEVEL_CHAOS**<br /><br /> **ISOLATIONLEVEL_READUNCOMMITTED**<br /><br /> **ISOLATIONLEVEL_READCOMMITTED**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_CURSORSTABILITY**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_SERIALIZABLE**<br /><br /> **ISOLATIONLEVEL_ISOLATED**<br /><br /> **ISOLATIONLEVEL_SNAPSHOT**<br /><br /> <br /><br /> 注: が始まる[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]、ISOLATIONLEVEL_SNAPSHOT は有効、 *isoLevel*データベースのバージョン管理が有効になっているかどうかの引数。 ただし、ユーザーがステートメントを実行する際に、バージョン管理が有効か、データベースが読み取り専用の場合は、エラーが発生します。 として ISOLATIONLEVEL_SNAPSHOT を指定する場合に XACT_E_ISOLATIONLEVEL エラーが発生するさらに、 *isoLevel*のバージョンに接続しているときに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]よりも前[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]です。|  
|*アイソレーション*[in]|SQL Server の OLE DB Driver は、0 以外の値のエラーを返します。|  
|*pOtherOptions*[in]|指定しない場合、NULL の場合は、OLE DB Driver for SQL Server は、インターフェイスからのオプション オブジェクトを要求します。 場合、SQL Server の OLE DB Driver は XACT_E_NOTIMEOUT を返しますのオプション オブジェクトの*ulTimeout*メンバーが 0 ではありません。 SQL Server の OLE DB ドライバーの値を無視する、 *szDescription*メンバー。|  
|*pulTransactionLevel*[out]|ない場合 NULL の場合は、OLE DB Driver for SQL Server がトランザクションの入れ子になったレベルを返します。|  
  
 ローカル トランザクションの場合、OLE DB Driver for SQL Server を実装する**itransaction::abort**パラメーターは次のようにします。  
  
|パラメーター|Description|  
|---------------|-----------------|  
|*pboidReason*[in]|設定しても無視されます。 NULL を指定しても問題ありません。|  
|*:commit*[in]|TRUE のときは、セッションの新しいトランザクションが暗黙的に開始されます。 このトランザクションは、コンシューマーがコミットまたは終了する必要があります。 FALSE の場合、OLE DB Driver for SQL Server は、セッションの自動コミット モードに戻ります。|  
|*fAsync*[in]|SQL Server の OLE DB ドライバーによって、非同期アボートはサポートされていません。 値が FALSE でない場合、SQL Server の OLE DB Driver は XACT_E_NOTSUPPORTED を返します。|  
  
 ローカル トランザクションの場合、OLE DB Driver for SQL Server を実装する**itransaction::commit**パラメーターは次のようにします。  
  
|パラメーター|Description|  
|---------------|-----------------|  
|*:commit*[in]|TRUE のときは、セッションの新しいトランザクションが暗黙的に開始されます。 このトランザクションは、コンシューマーがコミットまたは終了する必要があります。 FALSE の場合、OLE DB Driver for SQL Server は、セッションの自動コミット モードに戻ります。|  
|*grfTC*[in]|非同期応答と 1 フェーズはサポートされていません、OLE DB Driver for SQL Server。 SQL Server の OLE DB Driver は、XACTTC_SYN 以外の値を XACT_E_NOTSUPPORTED を返します。|  
|*grfRM*[in]|0 を指定する必要があります。|  
  
 SQL Server セッション上の行セットが、ローカル コミットに保管されているまたは中止操作の OLE DB Driver は、DBPROP_ABORTPRESERVE と DBPROP_COMMITPRESERVE の行セット プロパティの値に基づいています。 既定では、これらのプロパティは、両方 VARIANT_FALSE すべて OLE DB Driver for SQL Server セッション上の行セットは次の中止失われたか、操作をコミットします。  
  
 OLE DB Driver for SQL Server を実装しません、 **ITransactionObject**インターフェイスです。 このインターフェイスへの参照を取得しようとすると、コンシューマーは E_NOINTERFACE を返します。  
  
 この例では**ITransactionLocal**です。  
  
```  
// Interfaces used in the example.  
IDBCreateSession*   pIDBCreateSession   = NULL;  
ITransaction*       pITransaction       = NULL;  
IDBCreateCommand*   pIDBCreateCommand   = NULL;  
IRowset*            pIRowset            = NULL;  
  
HRESULT             hr;  
  
// Get the command creation and local transaction interfaces for the  
// session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
if (FAILED(hr = pIDBCreateCommand->QueryInterface(IID_ITransactionLocal,  
    (void**) &pITransaction)))  
    {  
    // Process error. Release any references and return.  
    }  
  
// Start the local transaction.  
if (FAILED(hr = ((ITransactionLocal*) pITransaction)->StartTransaction(  
    ISOLATIONLEVEL_REPEATABLEREAD, 0, NULL, NULL)))  
    {  
    // Process error from StartTransaction. Release any references and  
    // return.  
    }  
  
// Get data into a rowset, then update the data. Functions are not  
// illustrated in this example.  
if (FAILED(hr = ExecuteCommand(pIDBCreateCommand, &pIRowset)))  
    {  
    // Release any references and return.  
    }  
  
// If rowset data update fails, then terminate the transaction, else  
// commit. The example doesn't retain the rowset.  
if (FAILED(hr = UpdateDataInRowset(pIRowset, bDelayedUpdate)))  
    {  
    // Get error from update, then terminate.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, XACTTC_SYNC, 0)))  
        {  
        // Get error from failed commit.  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a>参照  
 [トランザクション](../../oledb/ole-db-transactions/transactions.md)   
 [スナップショット分離の使用](../../oledb/features/working-with-snapshot-isolation.md)  
  
  
