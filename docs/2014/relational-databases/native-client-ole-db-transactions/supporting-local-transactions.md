---
title: ローカル トランザクションのサポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- SQL Server Native Client OLE DB provider, transactions
- local transactions [OLE DB]
ms.assetid: 78f2e5fc-b6fb-4eda-9f71-991a4d6c4902
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b75104940cca183005f8a465ea19d0a517247c25
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63213813"
---
# <a name="supporting-local-transactions"></a>ローカル トランザクションのサポート
  セッションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのローカルトランザクションのトランザクションスコープを区切ります。 コンシューマーの指示によって、native Client OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プロバイダーがの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続されたインスタンスに要求を送信すると、要求は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native client OLE DB プロバイダーの作業単位になります。 ローカルトランザクションでは、1つの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーセッションで、1つまたは複数の作業単位が常にラップされます。  
  
 既定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の Native Client OLE DB プロバイダーの自動コミットモードを使用すると、1つの作業単位がローカルトランザクションのスコープとして扱われます。 ローカル トランザクションに参加するのは、1 単位のみです。 セッションが作成されると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、セッションのトランザクションを開始します。 作業単位の処理が正常に完了すると、その作業がコミットされます。 失敗すると、開始された作業がすべてロールバックされ、エラーがコンシューマーに報告されます。 どちらの場合も、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、すべての作業がトランザクション内で実行されるように、セッションの新しいローカルトランザクションを開始します。  
  
 Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーコンシューマーは、 **ITransactionLocal**インターフェイスを使用して、ローカルトランザクションスコープをより細かく制御できます。 コンシューマーのセッションがトランザクションを開始すると、トランザクションの開始時点から、最終的に **Commit** または **Abort** メソッドが呼び出されるまでのセッションの作業単位すべてが、1 つのアトミックな単位として扱われます。 Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーは、コンシューマーに指示されたときにトランザクションを暗黙的に開始します。 コンシューマーがモードの保持を要求しないと、セッションは親のトランザクション レベルの動作 (通常は、自動コミット モード) に戻ります。  
  
 Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーでは、次のように**ITransactionLocal:: starttransaction**パラメーターがサポートされています。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*isoLevel*[in]|このトランザクションで使用する分離レベルを指定します。 ローカルトランザクションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは次の機能をサポートします。<br /><br /> -ISOLATIONLEVEL_UNSPECIFIED<br />-ISOLATIONLEVEL_CHAOS<br />-ISOLATIONLEVEL_READUNCOMMITTED<br />-ISOLATIONLEVEL_READCOMMITTED<br />-ISOLATIONLEVEL_REPEATABLEREAD<br />-ISOLATIONLEVEL_CURSORSTABILITY<br />-ISOLATIONLEVEL_REPEATABLEREAD<br />-ISOLATIONLEVEL_SERIALIZABLE<br />-ISOLATIONLEVEL_ISOLATED<br />-ISOLATIONLEVEL_SNAPSHOT**注意:** 以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]は、データベースのバージョン管理が有効になっているかどうかにかかわらず、ISOLATIONLEVEL_SNAPSHOT は*isoLevel*引数に対して有効です。 ただし、ユーザーがステートメントを実行する際に、バージョン管理が有効か、データベースが読み取り専用の場合は、エラーが発生します。 また、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] より前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続している場合に、*isoLevel* に ISOLATIONLEVEL_SNAPSHOT を指定すると、XACT_E_ISOLATIONLEVEL エラーが発生します。|  
|*isoFlags*[in]|Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーは、0以外の値に対してエラーを返します。|  
|*pOtherOptions*[in]|NULL 以外の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、インターフェイスから options オブジェクトを要求します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、オプションオブジェクトの*ultimeout*メンバーが0でない場合に XACT_E_NOTIMEOUT を返します。 Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーは、 *szdescription*メンバーの値を無視します。|  
|*pulTransactionLevel*[out]|NULL 以外の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、トランザクションの入れ子になったレベルを返します。|  
  
 ローカルトランザクションの場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、次のように**ITransaction:: Abort**パラメーターを実装します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*pboidReason*[in]|設定しても無視されます。 NULL を指定しても問題ありません。|  
|*fRetaining*[in]|TRUE のときは、セッションの新しいトランザクションが暗黙的に開始されます。 このトランザクションは、コンシューマーがコミットまたは終了する必要があります。 FALSE の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、セッションの自動コミットモードに戻ります。|  
|*fAsync*[in]|非同期中止は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーではサポートされていません。 値[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が FALSE でない場合、Native Client OLE DB プロバイダーは XACT_E_NOTSUPPORTED を返します。|  
  
 ローカルトランザクションの場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、次のように**ITransaction:: Commit**パラメーターを実装します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*fRetaining*[in]|TRUE のときは、セッションの新しいトランザクションが暗黙的に開始されます。 このトランザクションは、コンシューマーがコミットまたは終了する必要があります。 FALSE の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、セッションの自動コミットモードに戻ります。|  
|*grfTC*[in]|非同期およびフェーズ1の戻り値は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーではサポートされていません。 Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーは、XACTTC_SYNC 以外の値に対して XACT_E_NOTSUPPORTED を返します。|  
|*grfRM*[in]|0 を指定する必要があります。|  
  
 セッション[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の Native Client OLE DB プロバイダーの行セットは、行セットのプロパティ DBPROP_ABORTPRESERVE および DBPROP_COMMITPRESERVE の値に基づいて、ローカルのコミットまたは中止操作で保持されます。 既定では、これらのプロパティは両方と[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]も VARIANT_FALSE ます。また、セッションのすべての Native Client OLE DB プロバイダー行セットは、abort または commit 操作後に失われます。  
  
 Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーには、 **ITransactionObject**インターフェイスが実装されていません。 このインターフェイスへの参照を取得しようとすると、コンシューマーは E_NOINTERFACE を返します。  
  
 次の例では、**ITransactionLocal** を使用します。  
  
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
 [トランザクション](transactions.md)   
 [スナップショット分離を使用した作業](../native-client/features/working-with-snapshot-isolation.md)  
  
  
