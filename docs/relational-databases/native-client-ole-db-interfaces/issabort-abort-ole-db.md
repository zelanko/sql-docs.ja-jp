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
ms.openlocfilehash: 835b526053bbf524f2b3d5a87ffea855aaad10c9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85785385"
---
# <a name="issabortabort-ole-db"></a>ISSAbort::Abort (OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  現在の行セットと、現在のコマンドに関連付けられているバッチ コマンドを取り消します。  
  
**Issabort**インターフェイスは、Native Client OLE DB プロバイダーで公開されています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Issabort:: Abort**メソッドを使用して、現在の行セットを取り消すために使用されます。また、行セットを最初に生成したコマンドを使用してバッチ処理されたコマンドと、まだ実行が完了していないコマンドを取り消します。  
  
 **Issabort**は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ICommand:: Execute**または**IOpenRowset:: OpenRowset**によって返される**IMultipleResults**オブジェクトに対して**QueryInterface**を使用して使用可能な Native Client プロバイダー固有のインターフェイスです。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT Abort(void);  
```  
  
## <a name="remarks"></a>Remarks  
 中止されるコマンドがストアド プロシージャの場合、ストアド プロシージャ (およびそのプロシージャを呼び出したすべてのプロシージャ) の実行と、そのストアド プロシージャの呼び出しが含まれるコマンド バッチの実行が終了します。 サーバーがクライアントに結果セットを転送中の場合、この処理も停止します。 クライアントが結果セットを使用しない場合、行セットを解放する前に **ISSAbort::Abort** を呼び出すと、行セットの解放が高速になります。ただし、開いているトランザクションがあり、XACT_ABORT が ON の場合、**ISSAbort::Abort** が呼び出されたときに、トランザクションがロールバックされます。  
  
 **Issabort:: Abort**が S_OK を返すと、関連付けられた**IMultipleResults**インターフェイスは使用できない状態になり、解放されるまで、すべてのメソッド呼び出し ( **IUnknown**インターフェイスによって定義されるメソッドを除く) に DB_E_CANCELED を返します。 **Abort** を呼び出す前に、**IMultipleResults** から **IRowset** を取得している場合、これも使用できない状態になり、**ISSAbort::Abort** の正常な呼び出し後にこのインターフェイスが解放されるまでは、すべてのメソッド呼び出しで DB_E_CANCELED が返されます (ただし、**IUnknown** インターフェイスと **IRowset::ReleaseRows** で定義されたメソッドは除きます)。  
  
> [!NOTE]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンでは、サーバーの XACT_ABORT 状態が ON の場合、**ISSAbort::Abort** を実行すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続するときに、現在のすべての暗黙的または明示的なトランザクションが終了し、ロールバックされます。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、現在のトランザクションは中止されません。  
  
## <a name="arguments"></a>引数  
 [なし] :  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 **ISSAbort::Abort** メソッドは、バッチが取り消された場合 S_OK を、それ以外の場合 DB_E_CANTCANCEL を返します。 バッチが既に取り消されている場合は、DB_E_CANCELED を返します。  
  
 DB_E_CANCELED  
 バッチは既に取り消されています。  
  
 DB_E_CANTCANCEL  
 バッチは取り消されませんでした。  
  
 E_FAIL  
 プロバイダー固有のエラーが発生しました。詳細については、 [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)インターフェイスを使用してください。  
  
 E_UNEXPECTED  
 メソッドの呼び出しが予期されませんでした。 たとえば、**ISSAbort::Abort** が既に呼び出されていたために、オブジェクトがゾンビ状態になっている場合などです。  
  
 E_OUTOFMEMORY  
 メモリ不足エラー。  
  
## <a name="see-also"></a>関連項目  
 [ISSAbort &#40;OLE DB&#41;](https://msdn.microsoft.com/library/7c4df482-4a83-4da0-802b-3637b507693a)  
  
  
