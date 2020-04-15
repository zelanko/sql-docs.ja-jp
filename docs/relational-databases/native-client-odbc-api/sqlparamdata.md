---
title: データ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLParamData function
ms.assetid: 92349482-ea22-4a6a-8484-e9c6566794fa
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7a2cc7bfdf35bf30a0883eecf6767e03b6805253
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81289064"
---
# <a name="sqlparamdata"></a>SQLParamData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SQLParamData がテーブル値パラメーターに関連付けられた*ValuePtrr*を返す場合、アプリケーションは*StrLen_Or_Ind*を指定して SQLPutData を呼び出す必要があります。 *StrLen_Or_Ind*の値が 0 より大きい場合は、アプリケーションがネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアントが次のテーブル値パラメーター行のパラメーター データを収集する準備が整っていることを意味します。 *StrLen_Or_Ind*値が 0 の場合、テーブル値パラメーターのデータ行がなくなったということになります。 詳細については、「[テーブル値パラメーターのバインドとデータ転送」および「列値](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)」を参照してください。  
  
 テーブル値パラメーターの詳細については、「 [ODBC&#41;&#40;テーブル値パラメーター ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データ](https://go.microsoft.com/fwlink/?LinkId=80706)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
