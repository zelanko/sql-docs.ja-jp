---
title: 分散トランザクションのサポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- distributed transactions [OLE DB]
- MS DTC
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
- ITransactionJoin interface
- MS DTC, about distributed transaction support
ms.assetid: d250b43b-9260-4ea4-90cc-57d9a2f67ea7
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bae96ffb9b49aead4282193c510a50098d0e0d54
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073474"
---
# <a name="supporting-distributed-transactions"></a>分散トランザクションのサポート
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコンシューマーが使用できる、 **itransactionjoin::jointransaction** Microsoft 分散トランザクション コーディネーター (MS DTC) によってコーディネートされる分散トランザクションに参加するメソッド。  
  
 MS DTC が公開する COM オブジェクトを使用すると、クライアントは、さまざまなデータ ストアに対する複数の接続にまたがってコーディネートされるトランザクションを起動したり、このトランザクションに参加することができます。 トランザクションを開始する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコンシューマーが MS DTC を使用して**ITransactionDispenser**インターフェイスです。 **BeginTransaction**のメンバー **ITransactionDispenser**分散トランザクション オブジェクトの参照を返します。 この参照に渡される、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを使用して**JoinTransaction**です。  
  
 MS DTC は、分散トランザクションでの非同期のコミットとアボートをサポートします。 非同期トランザクションの状態の通知の場合、コンシューマーを実装する、 **ITransactionOutcomeEvents**インターフェイスし、インターフェイスを MS DTC トランザクション オブジェクトに接続します。  
  
 分散トランザクションで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを実装して**itransactionjoin::jointransaction**パラメーターは次のようにします。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*punkTransactionCoord*|MS DTC トランザクション オブジェクトへのポインター。|  
|*IsoLevel*|は無視されます、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーです。 MS DTC によりコーディネートされるトランザクションの分離レベルは、コンシューマーが MS DTC からトランザクション オブジェクトを取得するときに決まります。|  
|*IsoFlags*|0 を指定する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンシューマーでその他の値が指定された場合は、Native Client OLE DB プロバイダーは XACT_E_NOISORETAIN を返します。|  
|*POtherOptions*|NULL 以外の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、インターフェイスからのオプション オブジェクトを要求します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]場合は、Native Client OLE DB プロバイダーは XACT_E_NOTIMEOUT を返しますのオプション オブジェクトの*ulTimeout*メンバーが 0 ではありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの値を無視する、 *szDescription*メンバー。|  
  
 次の例では、MS DTC を使用してトランザクションをコーディネートします。  
  
```  
// Interfaces used in the example.  
IDBCreateSession*       pIDBCreateSession   = NULL;  
ITransactionJoin*       pITransactionJoin   = NULL;  
IDBCreateCommand*       pIDBCreateCommand   = NULL;  
IRowset*                pIRowset            = NULL;  
  
// Transaction dispenser and transaction from MS DTC.  
ITransactionDispenser*  pITransactionDispenser = NULL;  
ITransaction*           pITransaction       = NULL;  
  
    HRESULT             hr;  
  
// Get the command creation interface for the session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
// Get a transaction dispenser object from MS DTC and  
// start a transaction.  
if (FAILED(hr = DtcGetTransactionManager(NULL, NULL,  
    IID_ITransactionDispenser, 0, 0, NULL,  
    (void**) &pITransactionDispenser)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
if (FAILED(hr = pITransactionDispenser->BeginTransaction(  
    NULL, ISOLATIONLEVEL_READCOMMITTED, ISOFLAG_RETAIN_DONTCARE,  
    NULL, &pITransaction)))  
    {  
    // Process error message from MS DTC, release any references,  
    // and then return.  
    }  
  
// Join the transaction.  
if (FAILED(pIDBCreateCommand->QueryInterface(IID_ITransactionJoin,  
    (void**) &pITransactionJoin)))  
    {  
    // Process failure to get an interface, release any references, and  
    // then return.  
    }  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) pITransaction, 0, 0, NULL)))  
    {  
    // Process join failure, release any references, and then return.  
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
    // Get error from update, then abort.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, 0, 0)))  
        {  
        // Get error from failed commit.  
        //  
        // If a distributed commit fails, application logic could  
        // analyze failure and retry. In this example, terminate. The   
        // consumer must resolve this somehow.  
        pITransaction->Abort(NULL, FALSE, FALSE);  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Un-enlist from the distributed transaction by setting   
// the transaction object pointer to NULL.  
if (FAILED(pITransactionJoin->JoinTransaction(  
    (IUnknown*) NULL, 0, 0, NULL)))  
    {  
    // Process failure, and then return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a>参照  
 [トランザクション](transactions.md)  
  
  