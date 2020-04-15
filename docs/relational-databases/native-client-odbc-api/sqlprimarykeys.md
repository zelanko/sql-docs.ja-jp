---
title: プライマリ キー |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2695d253030f13f71785046a25997ec6ee768622
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81289005"
---
# <a name="sqlprimarykeys"></a>SQLPrimaryKeys
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  テーブルには一意の行識別子として使用できる列が存在する場合があり、PRIMARY KEY 制約を指定せずに作成されたテーブルは空の結果セットを SQLPrimaryKeys に返します。 ODBC 関数[SQLSpecialColumns は、](../../relational-databases/native-client-odbc-api/sqlspecialcolumns.md)主キーを持たないテーブルの行 ID 候補を報告します。  
  
 △*カタログ名*、*スキーマ名*、または*テーブル名*の各パラメーターに値が存在するかどうかSQL_SUCCESSが返されます。 SQLFetch では、これらのパラメーターに無効な値が使用されると SQL_NO_DATA が返されます。  
  
 SQLPrimaryKeys は、静的サーバー カーソルで実行できます。 更新可能な (動的またはキーセット) カーソルに対して SQLPrimaryKeys を実行しようとすると、カーソルの種類が変更されたことを示すSQL_SUCCESS_WITH_INFOが返されます。  
  
 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ODBC ドライバは *、CatalogName* Linked_Server_Name パラメータの 2 つの部分から構成される名前を受け取ることによって、リンク サーバー上のテーブルのレポート情報*をサポートCatalog_Name。*  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a>SQLPrimaryKeys とテーブル値パラメーター  
 ステートメント属性の値がSQL_SS_NAME_SCOPE_TABLEの既定値ではなく、SQL_SS_NAME_SCOPE_TABLE_TYPESQL_SOPT_SS_NAME_SCOPE場合、SQLPrimaryKeys はテーブル型の主キー列に関する情報を返します。 SQL_SOPT_SS_NAME_SCOPEの詳細については、 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)を参照してください。  
  
 テーブル値パラメーターの詳細については、「 [ODBC&#41;&#40;テーブル値パラメーター ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL プライマリキー機能](https://go.microsoft.com/fwlink/?LinkId=59361)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
