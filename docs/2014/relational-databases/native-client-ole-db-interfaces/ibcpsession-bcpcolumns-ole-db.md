---
title: Ibcpsession::bcpcolumns (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IBCPSession::BCPColumns (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- BCPColumns method
ms.assetid: c338abe8-9e30-4853-a7c6-b1a6c00095e1
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a1fc6c8da0e46ac40bf6ddd2fbd821cdd6986dc8
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426341"
---
# <a name="ibcpsessionbcpcolumns-ole-db"></a>IBCPSession::BCPColumns (OLE DB)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブル内の列にバインドされるフィールド数を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT BCPColumns(   
DBCOUNTITEMnColumns);  
```  
  
## <a name="remarks"></a>コメント  
 内部的に呼び出します[ibcpsession::bcpcolfmt](ibcpsession-bcpcolfmt-ole-db.md)フィールド データの既定値を設定します。 これらの既定値をテーブル名を指定した場合、プロバイダーが内部的に取得された SQL Server 列情報から取得[ibcpsession::bcpinit](ibcpsession-bcpinit-ole-db.md)します。  
  
> [!NOTE]  
>  このメソッドは、後でのみ呼び出すことが**BCPInit**は有効なファイル名で呼び出されました。  
  
 既定とは異なる形式のユーザー ファイルを使用する場合にのみ、このメソッドを呼び出す必要があります。 既定のユーザー ファイル形式の説明の詳細については、次を参照してください。、 **BCPInit**メソッド。  
  
 呼び出した後、 **BCPColumns**メソッドを呼び出す必要があります、 **BCPColFmt**カスタム ファイル形式を完全に定義するユーザー ファイル内の各列のメソッド。  
  
## <a name="arguments"></a>引数  
 *nColumns*[in]  
 ユーザー ファイル内のフィールドの総数です。 設定する必要がある準備を行う場合でも、SQL Server にユーザー ファイルから一括コピー データ テーブルが表示され、ユーザー ファイル内のすべてのフィールドをコピーする予定がない、 *nColumns*ユーザー ファイルのフィールドの合計数の引数。 スキップしたフィールドを指定できます**BCPColFmt**します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。  
  
 E_FAIL  
 プロバイダー固有のエラーが発生しました。詳細については、使用、 [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)インターフェイス。  
  
 E_UNEXPECTED  
 メソッドの呼び出しが予期されませんでした。 たとえば、 **BCPInit**メソッドは、このメソッドを呼び出す前に呼び出されませんでした。 また、1 回の一括コピー操作でこのメソッドが複数回呼び出されたときもこのリターン コードが返されます。  
  
 E_OUTOFMEMORY  
 メモリ不足エラーです。  
  
## <a name="see-also"></a>参照  
 [IBCPSession &#40;OLE DB&#41;](ibcpsession-ole-db.md)   
 [一括コピー操作の実行](../native-client/features/performing-bulk-copy-operations.md)  
  
  
