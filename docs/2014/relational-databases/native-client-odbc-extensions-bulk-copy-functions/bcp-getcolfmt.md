---
title: bcp_getcolfmt |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- bcp_getcolfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_getcolfmt function
ms.assetid: f8bdada5-7b2d-4475-8c98-f93e9d77b130
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b31203c3f8627102ec3320f2c038afe2886eeeec
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420885"
---
# <a name="bcpgetcolfmt"></a>bcp_getcolfmt
  列形式のプロパティ値を確認するために使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_getcolfmt (  
HDBC   
hdbc  
,  
INT   
field  
,  
INT   
property  
,  
void*   
pValue  
,  
INT   
cbvalue,  
INT*   
pcbLen  
);  
  
```  
  
## <a name="arguments"></a>引数  
 *hdbc*  
 一括コピーが有効な ODBC 接続ハンドルです。  
  
 *field*  
 プロパティを取得する列番号です。  
  
 *property*  
 プロパティ定数のいずれかを指定します。  
  
 *pValue*  
 プロパティ値を取得するバッファーへのポインターです。  
  
 *cbValue*  
 プロパティ バッファーのバイト単位の長さです。  
  
 *pcbLen*  
 プロパティ バッファーに返されるデータの長さへのポインターです。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>コメント  
 列形式のプロパティの値が記載されて、 [bcp_setcolfmt](bcp-setcolfmt.md)トピック。 呼び出して列形式のプロパティ値を設定、 **bcp_setcolfmt**関数、および**bcp_getcolfmt**列形式のプロパティ値を検索する関数を使用します。  
  
 接続するときの動作の変更が発生する可能性があります、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (またはそれ以降) サーバーのコンピューター、以前と比較して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バージョン。 詳細については、次を参照してください。[メタデータ検出](../native-client/features/metadata-discovery.md)します。  
  
## <a name="bcpgetcolfmt-support-for-enhanced-date-and-time-features"></a>bcp_getcolfmt による機能強化された日付と時刻のサポート  
 使用される型、`BCP_FMT_TYPE`日付/時刻型のプロパティがで指定されている[強化された日付と時刻型向けの一括コピーの変更&#40;OLE DB および ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)します。  
  
 詳細については、次を参照してください。[日付と時刻の強化&#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)します。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
