---
title: 準備されたステートメントのテーブル値パラメーターのメタデータ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), metadata for prepared statements
ms.assetid: fd2fc705-2e98-4011-9822-c7e6cca4a535
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8e526b01f8e33006c01861cdafef1fd9cd03d2ef
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705169"
---
# <a name="table-valued-parameter-metadata-for-prepared-statements"></a>準備されたステートメント用のテーブル値パラメーターのメタデータ
  アプリケーションでは、SQLNumParams と SQLDescribeParam を使用して、準備されたプロシージャ呼び出しのメタデータを取得できます。 テーブル値パラメーターの場合、 *DataTypePtr*は SQL_SS_TABLE に設定されます。 追加のメタデータは、SQL_CA_SS_TYPE_NAME、SQL_CA_SS_CATALOG_NAME、および SQL_CA_SS_SCHEMA_NAME の SQLGetDescField を通じて入手できます。  
  
 SQL_CA_SS_TYPE_NAME、SQL_CA_SS_CATALOG_NAME、および SQL_CA_SS_SCHEMA_NAME を SQLColumns と共に使用すると、テーブル値パラメーターに関連付けられているテーブル型の列のメタデータを取得できます。 この場合、SQLColumns が呼び出される前に、SQL_SOPT_SS_NAME_SCOPE を SQL_SS_NAME_SCOPE_TABLE_TYPE に設定する必要があります。 その後、アプリケーションでテーブル値パラメーターの列のメタデータの取得が完了したら、SQL_SOPT_SS_NAME_SCOPE を既定値の SQL_SS_NAME_SCOPE_TABLE に戻す必要があります。  
  
 SQL_CA_SS_TYPE_NAME、SQL_CA_SS_CATALOG_NAME、および SQL_CA_SS_SCHEMA_NAME は、CLR ユーザー定義型パラメーターでも使用できます。  
  
 ストアド プロシージャ呼び出しではない準備されたステートメント用にテーブル値パラメーターのメタデータを取得することはできません。 取得しようとすると、アプリケーションから SQLSTATE 42000 で "構文エラーまたはアクセス違反です" というメッセージの SQL_ERROR が返されます。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
