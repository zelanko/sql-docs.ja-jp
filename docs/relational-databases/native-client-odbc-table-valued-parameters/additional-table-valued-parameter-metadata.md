---
title: 追加のテーブル値パラメーター メタデータ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), catalog functions to retrieve metadata
- table-valued parameters (ODBC), metadata
ms.assetid: 6c193188-5185-4373-9a0d-76cfc150c828
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6b52f83e36c315ccd86d1516df9e11b913c80ba8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304539"
---
# <a name="additional-table-valued-parameter-metadata"></a>テーブル値パラメーターの追加メタデータ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  テーブル値パラメーターのメタデータを取得するには、アプリケーションは SQLProcedureColumns を呼び出します。 テーブル値パラメーターの場合、1 行を返します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル値パラメーターに関連付けられたテーブル型のスキーマおよびカタログ情報を提供するために、SS_TYPE_CATALOG_NAMEとSS_TYPE_SCHEMA_NAMEの 2 つの列が追加されました。 ODBC 仕様に準拠して、SS_TYPE_CATALOG_NAMEとSS_TYPE_SCHEMA_NAMEは、以前のバージョンの で追加されたすべてのドライバー固有の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列の前、および ODBC 自体によって指定されたすべての列の後に表示されます。  
  
 テーブル値パラメーターにとって重要な列を次の表に示します。  
  
|列名|データ型|値およびコメント|  
|-----------------|---------------|---------------------|  
|DATA_TYPE|Smallint (NULL 以外)|SQL_SS_TABLE|  
|TYPE_NAME|WVarchar(128) (NULL 以外)|テーブル値パラメーターの型名|  
|COLUMN_SIZE|Integer|NULL|  
|BUFFER_LENGTH|Integer|0|  
|DECIMAL_DIGITS|Smallint|NULL|  
|NUM_PREC_RADIX|Smallint|NULL|  
|NULLABLE|Smallint (NULL 以外)|SQL_NULLABLE|  
|REMARKS|Varchar|NULL|  
|COLUMN_DEF|WVarchar(4000)|NULL|  
|SQL_DATA_TYPE|Smallint (NULL 以外)|SQL_SS_TABLE|  
|SQL_DATETIME_SUB|Smallint|NULL|  
|CHAR_OCTET_LENGTH|Integer|NULL|  
|ORDINAL_POSITION|Integer (NULL 以外)|パラメーターの序数位置。|  
|IS_NULLABLE|Varchar|"YES"|  
|SS_TYPE_CATALOG_NAME|WVarchar(128) (NULL 以外)|テーブル値パラメーターのテーブル型の型定義が格納されているカタログ。|  
|SS_TYPE_SCHEMA_NAME|WVarchar(128) (NULL 以外)|テーブル値パラメーターのテーブル型の型定義が格納されているスキーマ。|  
  
 WVarchar 列は、ODBC 仕様では Varchar として定義されていますが、実際には、最近のすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC ドライバーでは、WVarchar として返されます。 この変更は、ODBC 3.5 仕様に Unicode のサポートが追加されたときに行われましたが、明示されていませんでした。  
  
 テーブル値パラメーターの追加のメタデータを取得するには、アプリケーションは、カタログ関数 SQLColumns と SQLPrimaryKeys を使用します。 これらの関数がテーブル値パラメーターのために呼び出される前に、アプリケーションでは、ステートメント属性 SQL_SOPT_SS_NAME_SCOPE を SQL_SS_NAME_SCOPE_TABLE_TYPE に設定する必要があります。 この値は、アプリケーションが実際のテーブルではなくテーブル型のメタデータを必要としていることを示します。 その後、アプリケーションはテーブル値パラメーターのTYPE_NAMEを*TableName*パラメーターとして渡します。 SS_TYPE_CATALOG_NAMEとSS_TYPE_SCHEMA_NAMEは、それぞれ*CatalogName*パラメーターと*SchemaName*パラメーターと共に使用され、テーブル値パラメーターのカタログとスキーマを識別します。 テーブル値パラメーターのメタデータの取得が完了すると、アプリケーションによって、SQL_SOPT_SS_NAME_SCOPE は既定値 SQL_SS_NAME_SCOPE_TABLE に設定し直す必要があります。  
  
 SQL_SOPT_SS_NAME_SCOPE が SQL_SS_NAME_SCOPE_TABLE に設定されると、リンク サーバーへのクエリは失敗します。 サーバー コンポーネントを含むカタログを使用して SQLColumns または SQLPrimaryKeys を呼び出すと、失敗します。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;テーブル値パラメーター](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
