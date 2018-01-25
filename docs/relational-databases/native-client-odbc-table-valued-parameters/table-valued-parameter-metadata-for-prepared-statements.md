---
title: "準備されたステートメント用のテーブル値パラメーターのメタデータ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-table-valued-parameters
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: table-valued parameters (ODBC), metadata for prepared statements
ms.assetid: fd2fc705-2e98-4011-9822-c7e6cca4a535
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b6e0b5dea804f5a49387bf8aec08625ec079c81f
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="table-valued-parameter-metadata-for-prepared-statements"></a>準備されたステートメント用のテーブル値パラメーターのメタデータ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  アプリケーションでは、SQLNumParams と SQLDescribeParam を通じて準備されたプロシージャ呼び出しのメタデータを取得できます。 テーブル値パラメーターの*DataTypePtr*が SQL_SS_TABLE に設定します。 追加のメタデータは SQL_CA_SS_TYPE_NAME、SQL_CA_SS_CATALOG_NAME、および SQL_CA_SS_SCHEMA_NAME SQLGetDescField しています。  
  
 SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME, and SQL_CA_SS_SCHEMA_NAME can be used with SQLColumns to obtain column metadata for table types associated with table-valued parameters. この場合、SQLColumns を呼び出す前に、SQL_SOPT_SS_NAME_SCOPE を SQL_SS_NAME_SCOPE_TABLE_TYPE に設定する必要があります。 その後、アプリケーションでテーブル値パラメーターの列のメタデータの取得が完了したら、SQL_SOPT_SS_NAME_SCOPE を既定値の SQL_SS_NAME_SCOPE_TABLE に戻す必要があります。  
  
 SQL_CA_SS_TYPE_NAME、SQL_CA_SS_CATALOG_NAME、および SQL_CA_SS_SCHEMA_NAME は、CLR ユーザー定義型パラメーターでも使用できます。  
  
 ストアド プロシージャ呼び出しではない準備されたステートメント用にテーブル値パラメーターのメタデータを取得することはできません。 取得しようとすると、アプリケーションから SQLSTATE 42000 で "構文エラーまたはアクセス違反です" というメッセージの SQL_ERROR が返されます。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40; ODBC &#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
