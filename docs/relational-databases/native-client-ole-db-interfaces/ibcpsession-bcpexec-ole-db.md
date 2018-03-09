---
title: ":Bcpexec (OLE DB) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-interfaces
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IBCPSession::BCPExec (OLE DB)
apitype: COM
helpviewer_keywords: BCPExec method
ms.assetid: 0f4ebb63-cf03-4e53-846e-6c3021cde007
caps.latest.revision: "23"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d746c01ed19368ab4502681d946cc3f06a61be35
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="ibcpsessionbcpexec-ole-db"></a>IBCPSession::BCPExec (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  一括コピー操作を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT BCPExec(   
      DBROWCOUNT *pRowsCopied);  
```  
  
## <a name="remarks"></a>解説  
 **BCPExec**メソッドでは、データベース テーブルまたはその逆の場合、ユーザー ファイルからデータをコピーの値に応じて、 *eDirection*で使用するパラメーター、 [ibcpsession::bcpinit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)メソッドです。  
  
 呼び出しの前に**BCPExec**を呼び出し、 **BCPInit**有効なユーザー ファイル名を持つメソッドです。 この操作を行わないと、エラーが発生します。 唯一の例外は、一括コピーの出力操作にクエリを使用する場合です。 その場合は、テーブル名に NULL を指定、 **BCPInit**メソッドしから、BCP_OPTION_HINTS オプションを使用してクエリを指定します。  
  
 **BCPExec**メソッドは、唯一の一括コピー メソッドを任意の長さの時間の未処理する可能性があります。 そのため、このメソッドは非同期モードをサポートする唯一の一括コピー メソッドでもあります。 非同期モードを使用するには、プロバイダー固有のセッション プロパティ SSPROP_ASYNCH_BULKCOPY を VARIANT_TRUE に設定呼び出しの前に、 **BCPExec**メソッドです。 このプロパティは、DBPROPSET_SQLSERVERSESSION プロパティ セットに含まれています。 完了をテストするには、呼び出し、 **BCPExec**同じパラメーターを持つメソッドです。 一括コピーがまだ完了していない場合、 **BCPExec**メソッドには、DB_S_ASYNCHRONOUS が返されます。 返されます、 *pRowsCopied*引数に送信またはサーバーから受信されている行の数の状態カウントします。 サーバーに送信された行は、バッチの終わりに到達するまではコミットされません。  
  
## <a name="arguments"></a>引数  
 *pRowsCopied*[out]  
 DWORD へのポインターです。 **BCPExec**メソッドが正常にコピーされた行の数で DWORD を塗りつぶします。 場合、 *pRowsCopied*引数が NULL に設定されているでは無視されます、 **BCPExec**メソッドです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。  
  
 E_FAIL  
 プロバイダー固有のエラーが発生しました。詳細についてを使用して、 [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)インターフェイスです。  
  
 E_UNEXPECTED  
 メソッドの呼び出しが予期されませんでした。 たとえば、 **BCPInit**メソッドは、このメソッドを呼び出す前に呼び出されませんでした。 操作が BCP_OPTION_ABORT オプションを使用してから中止された場合にも発生し、 **BCPExec**メソッドが後で呼び出されました。  
  
 E_OUTOFMEMORY  
 メモリ不足エラーです。  
  
 DB_S_ENDOFROWSET  
 一括コピー操作が終了し、すべてのデータ転送が完了しました。  
  
 DB_S_ASYNCHRONOUS  
 行の現在のバッチがコピーされました。 呼び出す、 **BCPExec**メソッドを再び次のバッチを転送します。  
  
 DB_S_ERRORSOCCURRED  
 一括コピー操作中にエラーが発生しました。そのため、一部の行がコピーされなかった可能性があります。 エラー数は、許容されるエラーの最大数には達していません。  
  
## <a name="see-also"></a>参照  
 [IBCPSession &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [一括コピー操作の実行](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
