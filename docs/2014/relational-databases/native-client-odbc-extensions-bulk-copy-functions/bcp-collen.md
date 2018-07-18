---
title: bcp_collen |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- bcp_collen
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_collen function
ms.assetid: faaf1f7a-81f2-4852-a178-56602c33673a
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c1d12a0dd303405fd32eec5091d1d7d50e2d7d1f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431111"
---
# <a name="bcpcollen"></a>bcp_collen
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に対する現在の一括コピー用のプログラム変数にデータ長を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_collen (  
HDBC   
hdbc  
,  
DBINT   
cbData  
,  
INT   
idxServerCol  
);  
  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
 *cbData*  
 プログラム変数内のデータ長です。長さのインジケーターやターミネータの長さは含まれません。 設定*cbData* SQL_NULL_DATA するには、サーバーにコピーされるすべての行が列の NULL 値を含むを示します。 また、SQL_VARLEN_DATA に設定すると、文字列ターミネータや他の方法を使用してコピーするデータ長が決定されます。 長さのインジケーターとターミネータの両方を指定した場合、システムはコピーするデータ量が少なくなる方法を使用します。  
  
 *idxServerCol*  
 テーブル内にある、データのコピー先となる列の序数位置です。 最初の列は 1 です。 列の序数位置がによって報告された[SQLColumns](../native-client-odbc-api/sqlcolumns.md)します。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>コメント  
 **Bcp_collen**関数では、データをコピーするときに、特定の列をプログラム変数内のデータ長を変更できます。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で[bcp_sendrow](bcp-sendrow.md)します。  
  
 最初に、データの長さを決定と[bcp_bind](bcp-bind.md)が呼び出されます。 呼び出しの間でデータの長さが変更された場合**bcp_sendrow**プレフィックス長もターミネータが使用されていないを呼び出して、 **bcp_collen**長さをリセットします。 次回の呼び出し**bcp_sendrow**への呼び出しで設定される長さを使用して**bcp_collen**します。  
  
 呼び出す必要があります**bcp_collen**がデータの長さを変更するテーブルの各列に対して 1 回です。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
