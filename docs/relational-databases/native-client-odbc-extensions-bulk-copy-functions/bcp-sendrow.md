---
title: bcp_sendrow |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bcp_sendrow
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_sendrow function
ms.assetid: ddbdb4bd-ad4e-4bf1-9a75-656aa26ce10a
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d78aceec83230cc8772186d5360b80b2ff656053
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2018
ms.locfileid: "35695743"
---
# <a name="bcpsendrow"></a>bcp_sendrow
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  プログラム変数から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にデータ行を送信します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_sendrow (  
    HDBC hdbc);  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>コメント  
 **Bcp_sendrow**関数は、プログラム変数から行を作成し、送信に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 呼び出しの前に**bcp_sendrow**への呼び出しを行う必要があります[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)行データを含むプログラム変数を指定します。  
  
 場合**bcp_bind**長い可変長データ型を指定すると呼ばれますが、 *eDataType* SQLTEXT と NULL 以外のパラメーター *pData*パラメーター、 **bcp_sendrow**は他の任意のデータ型の場合と同様に、データ値全体を送信します。 場合、ただし、 **bcp_bind** 、null *pData*パラメーター、 **bcp_sendrow**に指定したデータを持つすべての列を送信した後すぐに、アプリケーションに制御を返す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. アプリケーションが呼び出すことができますし、 [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) 、長い可変長データを送信するには、繰り返し[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、一度にチャンクです。 詳細については、次を参照してください。 [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md)です。  
  
 ときに**bcp_sendrow**行を一括コピーにプログラム変数から使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル、行はコミットされた場合にのみユーザーを呼び出して[bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md)または[bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md). 呼び出して、ユーザーが選択できる**bcp_batch**したらすべて*n*行受信データの期間の間、一時的な静止状態がある場合またはします。 場合**bcp_batch**が呼び出されない行がコミットされたときに**bcp_done**と呼びます。  
  
 以降では、一括コピーでの変更については、互換性に影響する[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]を参照してください[一括コピー操作の実行&#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
