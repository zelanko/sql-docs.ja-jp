---
title: 準備されたステートメント用のテーブル値パラメーターのメタデータ |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), metadata for prepared statements
ms.assetid: fd2fc705-2e98-4011-9822-c7e6cca4a535
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 54617a7649ad055002c5b84522ce231dbf6bd879
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43110704"
---
# <a name="table-valued-parameter-metadata-for-prepared-statements"></a>準備されたステートメント用のテーブル値パラメーターのメタデータ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  アプリケーションでは、SQLNumParams SQLDescribeParam して準備されたプロシージャ呼び出しのメタデータを取得できます。 テーブル値パラメーターの*DataTypePtr*が SQL_SS_TABLE に設定します。 追加のメタデータを SQLGetDescField SQL_CA_SS_TYPE_NAME、SQL_CA_SS_CATALOG_NAME、および SQL_CA_SS_SCHEMA_NAME を通じてご利用いただけます。  
  
 SQL_CA_SS_TYPE_NAME、SQL_CA_SS_CATALOG_NAME、および SQL_CA_SS_SCHEMA_NAME は、テーブル値パラメーターに関連付けられたテーブル型の列のメタデータを取得する SQLColumns で使用できます。 この場合、SQLColumns を呼び出す前に SQL_SOPT_SS_NAME_SCOPE を SQL_SS_NAME_SCOPE_TABLE_TYPE に設定する必要があります。 その後、アプリケーションでテーブル値パラメーターの列のメタデータの取得が完了したら、SQL_SOPT_SS_NAME_SCOPE を既定値の SQL_SS_NAME_SCOPE_TABLE に戻す必要があります。  
  
 SQL_CA_SS_TYPE_NAME、SQL_CA_SS_CATALOG_NAME、および SQL_CA_SS_SCHEMA_NAME は、CLR ユーザー定義型パラメーターでも使用できます。  
  
 ストアド プロシージャ呼び出しではない準備されたステートメント用にテーブル値パラメーターのメタデータを取得することはできません。 取得しようとすると、アプリケーションから SQLSTATE 42000 で "構文エラーまたはアクセス違反です" というメッセージの SQL_ERROR が返されます。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
