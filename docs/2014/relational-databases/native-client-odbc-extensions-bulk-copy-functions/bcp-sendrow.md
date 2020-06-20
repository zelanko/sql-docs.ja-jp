---
title: bcp_sendrow |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_sendrow
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_sendrow function
ms.assetid: ddbdb4bd-ad4e-4bf1-9a75-656aa26ce10a
author: rothja
ms.author: jroth
ms.openlocfilehash: c45e87fdd8e00e9456718c4c9c8160c22bac03a1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85019379"
---
# <a name="bcp_sendrow"></a>bcp_sendrow
  プログラム変数から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にデータ行を送信します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_sendrow (  
    HDBC   
hdbc  
);  
  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>Remarks  
 **Bcp_sendrow**関数は、プログラム変数から行を作成し、に送信し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
 **Bcp_sendrow**を呼び出す前に、行データを含むプログラム変数を指定するために[bcp_bind](bcp-bind.md)の呼び出しを行う必要があります。  
  
 Long 型の可変長データ型を指定して**bcp_bind**が呼び出された場合 (たとえば、SQLTEXT の*Edatatype*パラメーターと null 以外の*pData*パラメーター)、 **bcp_sendrow**他のデータ型の場合と同様に、entiredata 値が送信されます。 ただし、 **bcp_bind**に*PDATA*パラメーターが NULL の場合は、指定されたデータを含むすべての列がに送信された直後に、 **bcp_sendrow**制御がアプリケーションに返され [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 その後、アプリケーションは[bcp_moretext](bcp-moretext.md)を繰り返し呼び出して、長い可変長データをチャンクとして一度に送信でき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 詳細については、「 [bcp_moretext](bcp-moretext.md)」を参照してください。  
  
 プログラム変数からテーブルに行を一括コピーするために**bcp_sendrow**を使用する場合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、ユーザーが[bcp_batch](bcp-batch.md)または[bcp_done](bcp-done.md)を呼び出したときにのみ行がコミットされます。 ユーザーは、 *n*行ごとに**bcp_batch**を呼び出すことも、受信データの期間間になどがあるときに呼び出すこともできます。 **Bcp_batch**が呼び出されない場合、 **bcp_done**が呼び出されたときに行がコミットされます。  
  
 での一括コピーの重大な変更については [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 、「 [ODBC&#41;&#40;の一括コピー操作の実行](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
