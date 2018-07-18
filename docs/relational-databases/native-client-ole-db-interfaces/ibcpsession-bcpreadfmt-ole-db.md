---
title: Ibcpsession::bcpreadfmt (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IBCPSession::BCPReadFmt (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPReadFmt method
ms.assetid: e2a12050-94e4-48a3-8a48-b780d646f116
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4cdd98f828a69965a3a610ad27aeb2196e747d0c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37424351"
---
# <a name="ibcpsessionbcpreadfmt-ole-db"></a>IBCPSession::BCPReadFmt (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  フォーマット ファイルから列ごとにフォーマット情報を読み取ります。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT BCPReadFmt(   
      const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>コメント  
 **BCPReadFmt**メソッドは、データ ファイル内のデータの形式を示すフォーマット ファイルからデータを読み取るために使用します。 このメソッドでは、適切なバージョンのフォーマット ファイルを検出することができます。 また、フォーマット ファイルが xml 形式か、または古いスタイルのテキスト形式かを自動的に検出し、フォーマット ファイルに適した動作をします。 フォーマット ファイルのバージョンでサポートされている、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー BCP がバージョン 6.0 以降。  
  
 後に、 **BCPReadFmt**メソッドが値を書式設定を読み取り、適切な呼び出し、 [ibcpsession::bcpcolumns](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md)と[ibcpsession::bcpcolfmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)メソッド。 ユーザーがフォーマット ファイルを解析し、これらのメソッドを呼び出す必要はありません。  
  
 フォーマット ファイルを保存する、 [ibcpsession::bcpwritefmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)メソッド。 呼び出し、 **BCPReadFmt**メソッドは、保存されている形式を参照できます。 または、一括コピー ユーティリティ (**bcp**) で参照できるファイルでユーザー定義のデータ形式を保存することができます、 **BCPReadFmt**メソッド。  
  
 **BCP_OPTION_DELAYREADFMT**の値、 *eOption*パラメーターの[ibcpsession::bcpcontrol](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md) ibcpsession::bcpreadfmt の動作を変更します。  
  
## <a name="arguments"></a>引数  
 *pwszFormatFile*[in]  
 データ ファイルのフォーマット情報を含むファイルのパスとファイル名。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。  
  
 E_FAIL  
 詳細な情報を使用するためのプロバイダー固有のエラーが発生しました、 [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)インターフェイス。  
  
 E_OUTOFMEMORY  
 メモリ不足エラー。  
  
 E_UNEXPECTED  
 メソッドの呼び出しが予期されませんでした。 たとえば、 [ibcpsession::bcpinit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)メソッドは、このメソッドを呼び出す前に呼び出されませんでした。  
  
## <a name="see-also"></a>参照  
 [IBCPSession &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [一括コピー操作の実行](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
