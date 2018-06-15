---
title: Ibcpsession::bcpcolumns (OLE DB) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IBCPSession::BCPColumns (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPColumns method
ms.assetid: c338abe8-9e30-4853-a7c6-b1a6c00095e1
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f26a4a4d844767966dd3529789580d05363116bb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32945957"
---
# <a name="ibcpsessionbcpcolumns-ole-db"></a>IBCPSession::BCPColumns (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブル内の列にバインドされるフィールド数を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
HRESULT BCPColumns(   
      DBCOUNTITEM nColumns);  
```  
  
## <a name="remarks"></a>解説  
 内部的に呼び出す[ibcpsession::bcpcolfmt](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)フィールド データの既定値を設定します。 これらの既定値はを通じて、テーブル名が指定されている場合、プロバイダーが内部的に取得された SQL Server 列情報から取得されます[ibcpsession::bcpinit](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)です。  
  
> [!NOTE]  
>  このメソッドは、後にのみ呼び出すことができる**BCPInit**有効なファイル名で呼び出されました。  
  
 既定とは異なる形式のユーザー ファイルを使用する場合にのみ、このメソッドを呼び出す必要があります。 既定のユーザー ファイル形式の説明の詳細については、次を参照してください。、 **BCPInit**メソッドです。  
  
 呼び出した後、 **BCPColumns**メソッドを呼び出す必要があります、 **BCPColFmt**独自のファイル形式を完全に定義するユーザー ファイル内の各列のメソッドです。  
  
## <a name="arguments"></a>引数  
 *nColumns*[in]  
 ユーザー ファイル内のフィールドの総数です。 設定する必要がある準備を行う場合でも、データの一括コピーのユーザー ファイルから SQL Server にテーブルが表示され、ユーザー ファイル内のすべてのフィールドをコピーする予定がない、 *nColumns*ユーザー ファイルのフィールドの合計数に渡す引数。 スキップしたフィールドを指定できます**BCPColFmt**です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。  
  
 E_FAIL  
 プロバイダー固有のエラーが発生しました。詳細についてを使用して、 [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1)インターフェイスです。  
  
 E_UNEXPECTED  
 メソッドの呼び出しが予期されませんでした。 たとえば、 **BCPInit**メソッドは、このメソッドを呼び出す前に呼び出されませんでした。 また、1 回の一括コピー操作でこのメソッドが複数回呼び出されたときもこのリターン コードが返されます。  
  
 E_OUTOFMEMORY  
 メモリ不足エラーです。  
  
## <a name="see-also"></a>参照  
 [IBCPSession &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/ibcpsession-ole-db.md)   
 [一括コピー操作の実行](../../relational-databases/native-client/features/performing-bulk-copy-operations.md)  
  
  
