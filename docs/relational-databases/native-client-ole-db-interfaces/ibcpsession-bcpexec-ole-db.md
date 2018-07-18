---
title: :Bcpexec (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IBCPSession::BCPExec (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPExec method
ms.assetid: 0f4ebb63-cf03-4e53-846e-6c3021cde007
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c1dcfcc58a17382981cb8b282c86c71a890b00cf
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37419251"
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
  
## <a name="remarks"></a>コメント  
 **BCPExec**メソッドでは、データベース テーブルまたはその逆に、ユーザー ファイルからデータをコピーの値に応じて、 *eDirection*で使用するパラメーター、 [ibcpsession::bcpinit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)メソッド。  
  
 呼び出しの前に**BCPExec**を呼び出し、 **BCPInit**有効なユーザーのファイル名を持つメソッド。 この操作を行わないと、エラーが発生します。 唯一の例外は、一括コピーの出力操作にクエリを使用する場合です。 その場合は NULL のテーブル名を指定、 **BCPInit**メソッドし、BCP_OPTION_HINTS オプションを使用してクエリを指定します。  
  
 **BCPExec**メソッドは、唯一の一括コピー メソッドを任意の長さの時間の未処理になる可能性があります。 そのため、このメソッドは非同期モードをサポートする唯一の一括コピー メソッドでもあります。 非同期モードを使用するプロバイダー固有のセッション プロパティ SSPROP_ASYNCH_BULKCOPY を VARIANT_TRUE に設定呼び出しの前に、 **BCPExec**メソッド。 このプロパティは、DBPROPSET_SQLSERVERSESSION プロパティ セットに含まれています。 完了をテストするには、呼び出し、 **BCPExec**メソッドを同じパラメーターを使用します。 一括コピーがまだ完了していない場合、 **BCPExec**メソッドは DB_S_ASYNCHRONOUS を返します。 返されます、 *pRowsCopied*引数またはに送信された、サーバーから受信した行の数の状態の数。 サーバーに送信された行は、バッチの終わりに到達するまではコミットされません。  
  
## <a name="arguments"></a>引数  
 *pRowsCopied*[out]  
 DWORD へのポインターです。 **BCPExec**メソッドが正常にコピーされる行の数で、DWORD を塗りつぶします。 場合、 *pRowsCopied*引数が NULL に設定されているでは無視されます、 **BCPExec**メソッド。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。  
  
 E_FAIL  
 プロバイダー固有のエラーが発生しました。詳細については、使用、 [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)インターフェイス。  
  
 E_UNEXPECTED  
 メソッドの呼び出しが予期されませんでした。 たとえば、 **BCPInit**メソッドは、このメソッドを呼び出す前に呼び出されませんでした。 操作が BCP_OPTION_ABORT オプションを使用して、中止された場合にも発生し、 **BCPExec**メソッドが後で呼び出されました。  
  
 E_OUTOFMEMORY  
 メモリ不足エラーです。  
  
 DB_S_ENDOFROWSET  
 一括コピー操作が終了し、すべてのデータ転送が完了しました。  
  
 DB_S_ASYNCHRONOUS  
 行の現在のバッチがコピーされました。 呼び出す、 **BCPExec**メソッドを再び、次のバッチを転送します。  
  
 DB_S_ERRORSOCCURRED  
 一括コピー操作中にエラーが発生しました。そのため、一部の行がコピーされなかった可能性があります。 エラー数は、許容されるエラーの最大数には達していません。  
  
## <a name="see-also"></a>参照  
 [IBCPSession &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [一括コピー操作の実行](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
