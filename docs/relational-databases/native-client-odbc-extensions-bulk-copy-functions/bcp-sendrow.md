---
title: bcp_sendrow |マイクロソフトのドキュメント
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 937ea3a4086e65712f77b569976902fbd2038007
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39561912"
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
 **Bcp_sendrow**関数は、プログラム変数からの行をビルドしに送信します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
 呼び出しの前に**bcp_sendrow**への呼び出しを行う必要があります[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)行のデータを格納しているプログラム変数を指定します。  
  
 場合**bcp_bind**長い可変長データ型を指定すると呼ばれますが、 *eDataType* SQLTEXT と NULL 以外のパラメーター *pData*パラメーター、 **bcp_sendrow**は他のデータ型の場合と同様に、すべてのデータ値を送信します。 場合、ただし、 **bcp_bind** null になります*pData*パラメーター、 **bcp_sendrow**に指定したデータを持つすべての列を送信した後すぐに、アプリケーションにコントロールを返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. アプリケーションを呼び出して[bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) 、長い可変長データを送信するには、繰り返し[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、一度にチャンクです。 詳細については、次を参照してください。 [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md)します。  
  
 ときに**bcp_sendrow**一括にプログラム変数から行をコピーするために使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル、行はコミットされた場合にのみユーザーを呼び出して[bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md)または[bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md). 呼び出して、ユーザーが選択できます**bcp_batch**したらすべて*n*行または着信データの期間の間で転送がある場合。 場合**bcp_batch**は呼び出されず、行がコミットされたときに**bcp_done**が呼び出されます。  
  
 以降では一括コピーでの変更については、互換性に影響する[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]を参照してください[一括コピー操作を実行する&#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)します。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
