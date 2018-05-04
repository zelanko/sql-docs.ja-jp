---
title: Ibcpsession::bcpreadfmt (OLE DB) |Microsoft ドキュメント
description: フォーマット ファイル (OLE DB) からデータを読み取るため ibcpsession::bcpreadfmt を使用します。
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IBCPSession::BCPReadFmt (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPReadFmt method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: bfe9d310a1bf3bd37b148649ed17d41ae4d48c85
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ibcpsessionbcpreadfmt-ole-db"></a>IBCPSession::BCPReadFmt (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  フォーマット ファイルから列ごとにフォーマット情報を読み取ります。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT BCPReadFmt(   
      const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>解説  
 **BCPReadFmt**メソッドは、データ ファイル内のデータ形式を指定するフォーマット ファイルからデータを読み取るために使用します。 このメソッドでは、適切なバージョンのフォーマット ファイルを検出することができます。 また、フォーマット ファイルが xml 形式か、または古いスタイルのテキスト形式かを自動的に検出し、フォーマット ファイルに適した動作をします。 SQL Server の BCP for OLE DB ドライバーでサポートされるフォーマット ファイルのバージョンは、バージョン 6.0 以降です。  
  
 後に、 **BCPReadFmt**メソッドが値を書式設定を読み取り、適切な呼び出しがなさ、 [ibcpsession::bcpcolumns](../../oledb/ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md)と[ibcpsession::bcpcolfmt](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)メソッドです。 ユーザーがフォーマット ファイルを解析し、これらのメソッドを呼び出す必要はありません。  
  
 フォーマット ファイルを保存する、 [ibcpsession::bcpwritefmt](../../oledb/ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)メソッドです。 呼び出し、 **BCPReadFmt**メソッドは、保存されている形式を参照できます。 また、一括コピー ユーティリティ (**bcp**) によって参照されることができるファイルにユーザー定義のデータ形式を保存することができます、 **BCPReadFmt**メソッドです。  
  
 **BCP_OPTION_DELAYREADFMT**の値、 *eOption*のパラメーター [ibcpsession::bcpcontrol](../../oledb/ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md) ibcpsession::bcpreadfmt の動作を変更します。  
  
## <a name="arguments"></a>引数  
 *pwszFormatFile*[in]  
 データ ファイルのフォーマット情報を含むファイルのパスとファイル名。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。  
  
 E_FAIL  
 詳細な情報を使用するためのプロバイダー固有のエラーが発生しました、 [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)インターフェイスです。  
  
 E_OUTOFMEMORY  
 メモリ不足エラー。  
  
 E_UNEXPECTED  
 メソッドの呼び出しが予期されませんでした。 たとえば、 [ibcpsession::bcpinit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)メソッドは、このメソッドを呼び出す前に呼び出されませんでした。  
  
## <a name="see-also"></a>参照  
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [一括コピー操作の実行](../../oledb/features/performing-bulk-copy-operations.md)  
  
  
