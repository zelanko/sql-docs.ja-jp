---
title: bcp_getcolfmt |Microsoft ドキュメント
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
- bcp_getcolfmt
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_getcolfmt function
ms.assetid: f8bdada5-7b2d-4475-8c98-f93e9d77b130
caps.latest.revision: 36
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 52d03c248e3fd7c3d41efb5abd5dd1b773aa6baa
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2018
ms.locfileid: "35697453"
---
# <a name="bcpgetcolfmt"></a>bcp_getcolfmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  列形式のプロパティ値を確認するために使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE bcp_getcolfmt (  
        HDBC hdbc,  
        INT field,  
        INT property,  
        void* pValue,  
        INT cbvalue,  
        INT* pcbLen);  
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
 列形式のプロパティの値は、「、 [bcp_setcolfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)トピックです。 呼び出して列形式のプロパティ値の設定、 **bcp_setcolfmt**関数、および**bcp_getcolfmt**列形式のプロパティ値を検索する関数を使用します。  
  
 接続するときの動作の変更を確認することがあります、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (またはそれ以降) と比較すると前のサーバー コンピューター[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バージョン。 詳細については、次を参照してください。[メタデータ検出](../../relational-databases/native-client/features/metadata-discovery.md)です。  
  
## <a name="bcpgetcolfmt-support-for-enhanced-date-and-time-features"></a>bcp_getcolfmt による機能強化された日付と時刻のサポート  
 使用される型、 **BCP_FMT_TYPE**日付/時刻型のプロパティで指定した[強化された日付と時刻型の変更の一括コピー &#40;OLE DB および ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)です。  
  
 詳細については、次を参照してください。[日付と時刻の強化&#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [一括コピー関数](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
