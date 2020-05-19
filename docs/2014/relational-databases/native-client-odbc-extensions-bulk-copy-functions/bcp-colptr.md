---
title: bcp_colptr |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 38e4b2590bebd09da764e6249e59d32b0c28d356
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705299"
---
# <a name="bcp_colptr"></a>bcp_colptr
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
 コピーするデータを指すポインターです。 バインドされたデータ型が大きな値の型 (SQLTEXT や SQLIMAGE など) の場合は、 *pData*を NULL にすることができます。 NULL *pData*は、長いデータ値が[bcp_moretext](bcp-moretext.md)を使用してチャンク内の SQL Server に送信されることを示します。  
  
 *PData*が NULL に設定されていて、バインドされたフィールドに対応する列が大きな値型ではない場合、 **bcp_colptr**は失敗します。  
  
 大きな値の型の詳細については、「 [bcp_bind](bcp-bind.md)」を参照してください **。**  
  
 *idxServerCol*  
 データベース テーブル内にある、データのコピー先となる列の序数位置です。 テーブル内の最初の列は列 1 です。 列の序数位置は[Sqlcolumns](../native-client-odbc-api/sqlcolumns.md)によって報告されます。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>解説  
 **Bcp_colptr**関数を使用すると[bcp_sendrow](bcp-sendrow.md)で SQL Server にデータをコピーするときに、特定の列のソースデータのアドレスを変更できます。  
  
 初期状態では、ユーザーデータへのポインターは**bcp_bind**を呼び出すことによって設定されます。 **Bcp_sendrow**の呼び出しの間でプログラム変数のデータアドレスが変更された場合は、 **bcp_colptr**を呼び出して、データへのポインターをリセットできます。 次に**bcp_sendrow**を呼び出すと、 **bcp_colptr**への呼び出しによってアドレス指定されたデータが送信されます。  
  
 データアドレスを変更するテーブルのすべての列に対して、個別の**bcp_colptr**呼び出しが必要です。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
