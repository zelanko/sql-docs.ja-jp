---
title: bcp_colptr |Microsoft ドキュメント
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
- bcp_colptr
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_colptr function
ms.assetid: 02ece13e-1da3-4f9d-b860-3177e43d2471
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c0fa867ec82520f1dcc0def040d7a8edf8a2a713
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174160"
---
# <a name="bcpcolptr"></a>bcp_colptr
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への現在のコピー操作に関するプログラム変数のデータ アドレスを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_colptr (  
HDBC   
hdbc  
,  
LPCBYTE   
pData  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
 *pData*  
 コピーするデータを指すポインターです。 バインドされたデータ型は、大きな値型 (SQLTEXT や SQLIMAGE) 場合*pData* NULL にすることができます。 NULL *pData*を使用してチャンクで長い形式のデータ値は SQL Server に送信することを示します[bcp_moretext](bcp-moretext.md)です。  
  
 場合*pData*は NULL に設定され、列、バインドされるフィールドに対応するが、大きな値型ではない**bcp_colptr**は失敗します。  
  
 大きな値の型の詳細については、次を参照してください。 [bcp_bind](bcp-bind.md)**です。**  
  
 *idxServerCol*  
 データベース テーブル内にある、データのコピー先となる列の序数位置です。 テーブル内の最初の列は列 1 です。 列の序数位置がによって報告された[SQLColumns](../native-client-odbc-api/sqlcolumns.md)です。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>コメント  
 **Bcp_colptr**関数では、データを使用した SQL Server にコピーするときに特定の列のソース データのアドレスを変更できます。 [bcp_sendrow](bcp-sendrow.md)です。  
  
 呼び出しによってユーザー データへのポインターを設定する最初に、 **bcp_bind**です。 呼び出しの間、プログラム変数のデータのアドレスが変更された場合は**bcp_sendrow**、呼び出すことができます**bcp_colptr**データへのポインターをリセットします。 次に呼び出した**bcp_sendrow**への呼び出しによってアドレス指定されるデータを送信**bcp_colptr**です。  
  
 個別である必要があります**bcp_colptr**データのアドレスをテーブルの各列に対して呼び出しが変更します。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  