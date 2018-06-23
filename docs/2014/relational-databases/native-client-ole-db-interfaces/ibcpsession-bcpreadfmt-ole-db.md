---
title: Ibcpsession::bcpreadfmt (OLE DB) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPReadFmt (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPReadFmt method
ms.assetid: e2a12050-94e4-48a3-8a48-b780d646f116
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f47369cb66f6695ca7a235beb72536ce34495bb5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179109"
---
# <a name="ibcpsessionbcpreadfmt-ole-db"></a>IBCPSession::BCPReadFmt (OLE DB)
  フォーマット ファイルから列ごとにフォーマット情報を読み取ります。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT BCPReadFmt(   
const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>コメント  
 **BCPReadFmt**メソッドは、データ ファイル内のデータ形式を指定するフォーマット ファイルからデータを読み取るために使用します。 このメソッドでは、適切なバージョンのフォーマット ファイルを検出することができます。 また、フォーマット ファイルが xml 形式か、または古いスタイルのテキスト形式かを自動的に検出し、フォーマット ファイルに適した動作をします。 フォーマット ファイルのバージョンでサポートされている、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー BCP がバージョン 6.0 またはそれ以降。  
  
 後に、 **BCPReadFmt**メソッドが値を書式設定を読み取り、適切な呼び出しがなさ、 [ibcpsession::bcpcolumns](ibcpsession-bcpcolumns-ole-db.md)と[ibcpsession::bcpcolfmt](ibcpsession-bcpcolfmt-ole-db.md)メソッドです。 ユーザーがフォーマット ファイルを解析し、これらのメソッドを呼び出す必要はありません。  
  
 フォーマット ファイルを保存する、 [ibcpsession::bcpwritefmt](ibcpsession-bcpwritefmt-ole-db.md)メソッドです。 呼び出し、 **BCPReadFmt**メソッドは、保存されている形式を参照できます。 また、一括コピー ユーティリティ (**bcp**) によって参照されることができるファイルにユーザー定義のデータ形式を保存することができます、 **BCPReadFmt**メソッドです。  
  
 `BCP_OPTION_DELAYREADFMT`の値、 *eOption*のパラメーター [ibcpsession::bcpcontrol](ibcpsession-bcpcontrol-ole-db.md) ibcpsession::bcpreadfmt の動作を変更します。  
  
## <a name="arguments"></a>引数  
 *pwszFormatFile*[in]  
 データ ファイルのフォーマット情報を含むファイルのパスとファイル名。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。  
  
 E_FAIL  
 詳細な情報を使用するためのプロバイダー固有のエラーが発生しました、 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)インターフェイスです。  
  
 E_OUTOFMEMORY  
 メモリ不足エラー。  
  
 E_UNEXPECTED  
 メソッドの呼び出しが予期されませんでした。 たとえば、 [ibcpsession::bcpinit](ibcpsession-bcpinit-ole-db.md)メソッドは、このメソッドを呼び出す前に呼び出されませんでした。  
  
## <a name="see-also"></a>参照  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [一括コピー操作の実行](../native-client/features/performing-bulk-copy-operations.md)  
  
  