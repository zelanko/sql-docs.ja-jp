---
title: ISSAbort::Abort (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSAbort::Abort (OLE DB)
apitype: COM
helpviewer_keywords:
- Abort method
ms.assetid: a5bca169-694b-4895-84ac-e8fba491e479
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8ce2c92dad8c0ff97cdbcf4e77a58e8dd6ceb18c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303995"
---
# <a name="issabortabort-ole-db"></a>ISSAbort::Abort (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  現在の行セットと、現在のコマンドに関連付けられているバッチ コマンドを取り消します。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダーで公開されている**ISSAbort**インターフェイスは、現在の行セットと、最初に行セットを生成したコマンドでバッチ処理されたコマンドをキャンセルするために使用される**ISSAbort::Abort**メソッドを提供します。  
  
 **ISSAbort**は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**、ICommand::実行**または**IOpenRowset::OpenRowset**によって返される**IMultipleResults**オブジェクトの**クエリ インターフェイス**を使用して使用できるネイティブ クライアント プロバイダー固有のインターフェイスです。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a>解説  
 中止されるコマンドがストアド プロシージャの場合、ストアド プロシージャ (およびそのプロシージャを呼び出したすべてのプロシージャ) の実行と、そのストアド プロシージャの呼び出しが含まれるコマンド バッチの実行が終了します。 サーバーがクライアントに結果セットを転送中の場合、この処理も停止します。 クライアントが結果セットを使用しない場合、行セットを解放する前に **ISSAbort::Abort** を呼び出すと、行セットの解放が高速になります。ただし、開いているトランザクションがあり、XACT_ABORT が ON の場合、**ISSAbort::Abort** が呼び出されたときに、トランザクションがロールバックされます。  
  
 **ISSAbort::Abort**がS_OKを返した後、関連付けられた**IMultipleResults**インターフェイスは使用できない状態になり、解放されるまですべてのメソッド呼び出し **(IUnknown**インターフェイスで定義されたメソッドを除く) にDB_E_CANCELEDを返します。 **Abort** を呼び出す前に、**IMultipleResults** から **IRowset** を取得している場合、これも使用できない状態になり、**ISSAbort::Abort** の正常な呼び出し後にこのインターフェイスが解放されるまでは、すべてのメソッド呼び出しで DB_E_CANCELED が返されます (ただし、**IUnknown** インターフェイスと **IRowset::ReleaseRows** で定義されたメソッドは除きます)。  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンでは、サーバーの XACT_ABORT 状態が ON の場合、**ISSAbort::Abort** を実行すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続するときに、現在のすべての暗黙的または明示的なトランザクションが終了し、ロールバックされます。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、現在のトランザクションは中止されません。  
  
## <a name="arguments"></a>引数  
 なし。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 **ISSAbort::Abort** メソッドは、バッチが取り消された場合 S_OK を、それ以外の場合 DB_E_CANTCANCEL を返します。 バッチが既に取り消されている場合は、DB_E_CANCELED を返します。  
  
 DB_E_CANCELED  
 バッチは既に取り消されています。  
  
 DB_E_CANTCANCEL  
 バッチは取り消されませんでした。  
  
 E_FAIL  
 プロバイダ固有のエラーが発生しました。詳細については、インターフェイス[を](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)使用します。  
  
 E_UNEXPECTED  
 メソッドの呼び出しが予期されませんでした。 たとえば、**ISSAbort::Abort** が既に呼び出されていたために、オブジェクトがゾンビ状態になっている場合などです。  
  
 E_OUTOFMEMORY  
 メモリ不足エラー。  
  
## <a name="see-also"></a>参照  
 [OLE DB&#41;&#40;アボート](https://msdn.microsoft.com/library/7c4df482-4a83-4da0-802b-3637b507693a)  
  
  
