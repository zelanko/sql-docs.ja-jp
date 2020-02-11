---
title: bcp_columns |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_columns
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_columns function
ms.assetid: 5376f6fe-9508-439a-8c66-778d77f19ac3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fcfbbdb1881662401e791ea197115120444cf855
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63225525"
---
# <a name="bcp_columns"></a>bcp_columns
  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] との一括コピー入出力に使用する、ユーザー ファイル内の合計列数を設定します。 bcp_columns と[bcp_colfmt](bcp-colfmt.md)の代わりに[bcp_setbulkmode](bcp-setbulkmode.md)を使用できます。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_columns (  
HDBC   
hdbc  
,  
INT   
nColumns  
);  
  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
 *nColumns*  
 ユーザー ファイル内の合計列数です。 ユーザーファイルから[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブルにデータを一括コピーする準備をしていて、ユーザーファイル内のすべての列をコピーする予定がない場合でも、 *ncolumns*をユーザーファイルの列の合計数に設定する必要があります。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>解説  
 この関数は、有効なファイル名を指定して[bcp_init](bcp-init.md)が呼び出された後にのみ呼び出すことができます。  
  
 この関数を呼び出す必要があるのは、既定とは異なる形式のユーザー ファイルを使用する場合のみです。 既定のユーザーファイル形式の詳細については、「 **bcp_init**」を参照してください。  
  
 を呼び出し`bcp_columns`た後、ユーザーファイルの各列に対して[bcp_colfmt](bcp-colfmt.md)を呼び出して、カスタムファイル形式を完全に定義する必要があります。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
