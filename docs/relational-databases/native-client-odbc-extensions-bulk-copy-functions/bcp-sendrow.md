---
title: bcp_sendrow |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_sendrow
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_sendrow function
ms.assetid: ddbdb4bd-ad4e-4bf1-9a75-656aa26ce10a
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5bc7b03405d6e43a6b19cc2903875685177942e1
ms.sourcegitcommit: 8732161f26a93de3aa1fb13495e8a6a71519c155
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2019
ms.locfileid: "71707536"
---
# <a name="bcp_sendrow"></a>bcp_sendrow
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
 **Bcp_sendrow**関数は、プログラム変数から行を構築し、それを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に送信します。  
  
 **Bcp_sendrow**を呼び出す前に、 [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)を呼び出して、行データを含むプログラム変数を指定する必要があります。  
  
 SQLTEXT の*Edatatype*パラメーターや NULL 以外の*pData*パラメーターなど、long 型の可変長データ型を指定して**bcp_bind**を呼び出すと、他のデータの場合と同じように、 **bcp_sendrow**はデータ値全体を送信します。各種. ただし、 **bcp_bind**に NULL の*pData*パラメーターがある場合、 **bcp_sendrow**は、指定されたデータを含むすべての列が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に送信された直後に、アプリケーションに制御を返します。 その後、アプリケーションは[bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md)を繰り返し呼び出して、長い可変長データをチャンクの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に送信できます。 詳細については、「 [bcp_moretext](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md)」を参照してください。  
  
 **Bcp_sendrow**を使用してプログラム変数から @no__t 1 つのテーブルに行を一括コピーする場合、行がコミットされるのは、ユーザーが[bcp_batch](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md)または[bcp_done](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-done.md)を呼び出したときだけです。 ユーザーは、 *n*行ごとに**bcp_batch**を呼び出すことも、受信データの期間間になどがあるときに呼び出すこともできます。 **Bcp_batch**が呼び出されない場合は、 **bcp_done**が呼び出されたときに行がコミットされます。  
  
 @No__t-0 以降の一括コピーの重大な変更については、「[一括コピー操作&#40;の実行&#41;ODBC](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
