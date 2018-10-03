---
title: Ibcpsession::bcpreadfmt (OLE DB) |Microsoft Docs
description: Ibcpsession::bcpreadfmt を使用して、フォーマット ファイル (OLE DB) からデータを読み取る
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- IBCPSession::BCPReadFmt (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPReadFmt method
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: e3e1ee36165308235f1fbe3e3779253655483237
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47771490"
---
# <a name="ibcpsessionbcpreadfmt-ole-db"></a>IBCPSession::BCPReadFmt (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  フォーマット ファイルから列ごとにフォーマット情報を読み取ります。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT BCPReadFmt(   
      const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Remarks  
 **BCPReadFmt** メソッドは、データ ファイルのデータ形式を指定するフォーマット ファイルからデータを読み取る場合に使用されます。 このメソッドでは、適切なバージョンのフォーマット ファイルを検出することができます。 また、フォーマット ファイルが xml 形式か、または古いスタイルのテキスト形式かを自動的に検出し、フォーマット ファイルに適した動作をします。 SQL Server の BCP の OLE DB ドライバーでサポートされるフォーマット ファイルのバージョンは、バージョン 6.0 以降です。  
  
 **BCPReadFmt** メソッドは形式の値を読み取ると、適宜、[IBCPSession::BCPColumns](../../oledb/ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md) メソッドと [IBCPSession::BCPColFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md) メソッドを呼び出します。 ユーザーがフォーマット ファイルを解析し、これらのメソッドを呼び出す必要はありません。  
  
 フォーマット ファイルを保存するには、[IBCPSession::BCPWriteFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md) メソッドを呼び出します。 **BCPReadFmt** メソッドの呼び出しでは、保存した形式を参照することができます。 また、一括コピー ユーティリティ (**bcp**) を使用して、**BCPReadFmt** メソッドで参照できるファイルに、ユーザー定義のデータ形式を保存することもできます。  
  
 **BCP_OPTION_DELAYREADFMT**の値、 *eOption*パラメーターの[ibcpsession::bcpcontrol](../../oledb/ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md) ibcpsession::bcpreadfmt の動作を変更します。  
  
## <a name="arguments"></a>引数  
 *pwszFormatFile*[in]  
 データ ファイルのフォーマット情報を含むファイルのパスとファイル名。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。  
  
 E_FAIL  
 プロバイダー固有のエラーが発生しました。詳細を確認するには、[ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) インターフェイスを使用してください。  
  
 E_OUTOFMEMORY  
 メモリ不足エラー。  
  
 E_UNEXPECTED  
 メソッドの呼び出しが予期されませんでした。 たとえば、このメソッドが呼び出される前に、[IBCPSession::BCPInit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md) メソッドが呼び出されなかった場合などです。  
  
## <a name="see-also"></a>参照  
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [一括コピー操作の実行](../../oledb/features/performing-bulk-copy-operations.md)  
  
  
