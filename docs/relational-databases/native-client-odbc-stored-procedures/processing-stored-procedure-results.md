---
title: ストアド プロシージャの結果の処理 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], results
ms.assetid: 788ef2a4-17de-4526-960b-46bf29aafc9f
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b3ae5c1d858b153c947347fd8a8bc07f1dd9557c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32944202"
---
# <a name="processing-stored-procedure-results"></a>ストアド プロシージャの結果の処理
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャには、データを返す際に使用する次の 4 つのメカニズムがあります。  
  
-   プロシージャ内の各 SELECT ステートメントで結果セットを生成する。  
  
-   プロシージャが出力パラメーターによってデータを返すことができる。  
  
-   カーソルの出力パラメーターから、[!INCLUDE[tsql](../../includes/tsql-md.md)] サーバー カーソルを返すことができる。  
  
-   プロシージャに整数のリターン コードを含めることができる。  
  
 アプリケーションでは、ストアド プロシージャからのこれらすべての出力を処理できる必要があります。 CALL ステートメントや EXECUTE ステートメントには、リターン コードと出力パラメーター用のパラメーター マーカーを含める必要があります。 使用して[SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md)これらをすべて出力パラメーターとしてバインドして、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、出力値はバインドされた変数に転送します。 出力パラメーターとリターン コードはによってクライアントに返される最終項目[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; まで、アプリケーションに返されません[SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md) SQL_NO_DATA が返されます。  
  
 ODBC は、[!INCLUDE[tsql](../../includes/tsql-md.md)] カーソル パラメーターのバインドをサポートしません。 プロシージャの実行前にすべての出力パラメーターをバインドしておく必要があるので、出力カーソル パラメーターを含む [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャを ODBC アプリケーションから呼び出すことはできません。  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャの実行](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
