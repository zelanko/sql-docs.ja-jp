---
title: 追加のテーブル値パラメーターのメタデータ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), catalog functions to retrieve metadata
- table-valued parameters (ODBC), metadata
ms.assetid: 6c193188-5185-4373-9a0d-76cfc150c828
author: rothja
ms.author: jroth
ms.openlocfilehash: 362699ca4aec82315d86b99a440e8714fe6e0e72
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85048103"
---
# <a name="additional-table-valued-parameter-metadata"></a>テーブル値パラメーターの追加メタデータ
  アプリケーションは、テーブル値パラメーターのメタデータを取得するために SQLProcedureColumns を呼び出します。 テーブル値パラメーターの場合、SQLProcedureColumns は単一の行を返します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル値パラメーターに関連付けられているテーブル型のスキーマとカタログの情報を提供するために、SS_TYPE_CATALOG_NAME と SS_TYPE_SCHEMA_NAME という2つの追加固有の列が追加されました。 ODBC 仕様に準拠して、SS_TYPE_CATALOG_NAME と SS_TYPE_SCHEMA_NAME は、以前のバージョンので追加されたすべてのドライバー固有の列の前、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および odbc 自体によって必須とされるすべての列の前に表示されます。  
  
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
  
 アプリケーションでは、テーブル値パラメーターの追加のメタデータを取得するために、SQLColumns および SQLPrimaryKeys カタログ関数を使用します。 これらの関数がテーブル値パラメーターのために呼び出される前に、アプリケーションでは、ステートメント属性 SQL_SOPT_SS_NAME_SCOPE を SQL_SS_NAME_SCOPE_TABLE_TYPE に設定する必要があります。 この値は、アプリケーションが実際のテーブルではなくテーブル型のメタデータを必要としていることを示します。 その後、アプリケーションはテーブル値パラメーターの TYPE_NAME を*TableName*パラメーターとして渡します。 SS_TYPE_CATALOG_NAME と SS_TYPE_SCHEMA_NAME は、 *CatalogName*パラメーターと*SchemaName*パラメーターでそれぞれ使用され、テーブル値パラメーターのカタログとスキーマを識別します。 テーブル値パラメーターのメタデータの取得が完了すると、アプリケーションによって、SQL_SOPT_SS_NAME_SCOPE は既定値 SQL_SS_NAME_SCOPE_TABLE に設定し直す必要があります。  
  
 SQL_SOPT_SS_NAME_SCOPE が SQL_SS_NAME_SCOPE_TABLE に設定されると、リンク サーバーへのクエリは失敗します。 サーバーコンポーネントを含むカタログを使用した SQLColumns または Sqlprimarykey の呼び出しは失敗します。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
