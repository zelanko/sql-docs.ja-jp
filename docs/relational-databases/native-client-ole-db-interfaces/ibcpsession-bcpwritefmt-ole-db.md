---
title: Ibcpsession::bcpwritefmt (OLE DB) |Microsoft Docs
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
- IBCPSession::BCPWriteFmt (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPWriteFmt method
ms.assetid: add50425-2ed6-411a-a391-4ce63c364892
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 15ff67f43bf08c6fc56f3667899f7d3a4bd5ffc7
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420471"
---
# <a name="ibcpsessionbcpwritefmt-ole-db"></a>IBCPSession::BCPWriteFmt (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  フォーマット ファイルに列ごとのフォーマット情報を書き込みます。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT BCPWriteFmt(   
      const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>コメント  
 フォーマット ファイルでは、一括コピーで作成されるデータ ファイルのデータの形式を指定します。 呼び出し、 [ibcpsession::bcpcolumns](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md)と[ibcpsession::bcpcolfmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)メソッドは、データ ファイルの形式を定義します。 **BCPWriteFmt**メソッドは、この定義を pwszFormatFile 引数で参照されているファイルに保存します。  
  
 **BCPWriteFmt**メソッドは xml またはテキスト形式でフォーマット ファイルを保存することができます。 これで、BCP_OPTION_XML 制御オプションを使用して示す必要があります、 [ibcpsession::bcpcontrol](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md)メソッド。  
  
 保存されたフォーマット ファイルを読み込むには、使用、 [ibcpsession::bcpreadfmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md)メソッド。  
  
## <a name="arguments"></a>引数  
 *pwszFormatFile*[in]  
 データ ファイルのフォーマット情報を含むファイルのパスとファイル名。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。  
  
 E_FAIL  
 プロバイダー固有のエラーが発生しました。詳細については、使用、 [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)インターフェイス。  
  
 E_OUTOFMEMORY  
 メモリ不足エラーです。  
  
 E_UNEXPECTED  
 メソッドの呼び出しが予期されませんでした。 たとえば、 [ibcpsession::bcpinit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)メソッドは、このメソッドを呼び出す前に呼び出されませんでした。  
  
## <a name="see-also"></a>参照  
 [IBCPSession &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [一括コピー操作の実行](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
