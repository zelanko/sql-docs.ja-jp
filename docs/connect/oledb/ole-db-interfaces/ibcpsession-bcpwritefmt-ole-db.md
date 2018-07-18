---
title: Ibcpsession::bcpwritefmt (OLE DB) |Microsoft ドキュメント
description: Ibcpsession::bcpwritefmt を使用して、xml またはテキストのいずれかの形式 (OLE DB) でフォーマット ファイルを保存するには
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IBCPSession::BCPWriteFmt (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPWriteFmt method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: f7ca4586cc14d98e8d5a714e314b2c1ee157ae15
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2018
ms.locfileid: "35689415"
---
# <a name="ibcpsessionbcpwritefmt-ole-db"></a>IBCPSession::BCPWriteFmt (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  フォーマット ファイルに列ごとのフォーマット情報を書き込みます。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT BCPWriteFmt(   
      const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>コメント  
 フォーマット ファイルでは、一括コピーで作成されるデータ ファイルのデータの形式を指定します。 呼び出し、 [ibcpsession::bcpcolumns](../../oledb/ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md)と[ibcpsession::bcpcolfmt](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)メソッドは、データ ファイルの形式を定義します。 **BCPWriteFmt**メソッドは、この定義を pwszFormatFile 引数で参照されているファイルに保存します。  
  
 **BCPWriteFmt**メソッドは、xml またはテキストのいずれかの形式でフォーマット ファイルを保存できます。 これは、BCP_OPTION_XML 制御オプションを使用して示す必要があります、 [ibcpsession::bcpcontrol](../../oledb/ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md)メソッドです。  
  
 保存されたフォーマット ファイルを読み込むを使用して、 [ibcpsession::bcpreadfmt](../../oledb/ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md)メソッドです。  
  
## <a name="arguments"></a>引数  
 *pwszFormatFile*[in]  
 データ ファイルのフォーマット情報を含むファイルのパスとファイル名。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。  
  
 E_FAIL  
 プロバイダー固有のエラーが発生しました。詳細についてを使用して、 [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)インターフェイスです。  
  
 E_OUTOFMEMORY  
 メモリ不足エラーです。  
  
 E_UNEXPECTED  
 メソッドの呼び出しが予期されませんでした。 たとえば、 [ibcpsession::bcpinit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)メソッドは、このメソッドを呼び出す前に呼び出されませんでした。  
  
## <a name="see-also"></a>参照  
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [一括コピー操作の実行](../../oledb/features/performing-bulk-copy-operations.md) 
  
  
