---
title: ストアド プロシージャの結果を処理します。マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], results
ms.assetid: 788ef2a4-17de-4526-960b-46bf29aafc9f
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 5bab085024fc53e60d2b217721c8a9e3d6b7670e
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39540832"
---
# <a name="processing-stored-procedure-results"></a>ストアド プロシージャの結果の処理
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャには、データを返す際に使用する次の 4 つのメカニズムがあります。  
  
-   プロシージャ内の各 SELECT ステートメントで結果セットを生成する。  
  
-   プロシージャが出力パラメーターによってデータを返すことができる。  
  
-   カーソルの出力パラメーターから、[!INCLUDE[tsql](../../includes/tsql-md.md)] サーバー カーソルを返すことができる。  
  
-   プロシージャに整数のリターン コードを含めることができる。  
  
 アプリケーションでは、ストアド プロシージャからのこれらすべての出力を処理できる必要があります。 CALL ステートメントや EXECUTE ステートメントには、リターン コードと出力パラメーター用のパラメーター マーカーを含める必要があります。 使用[場合は、SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md)にすべての出力パラメーターとしてバインドして、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアントの ODBC ドライバーは出力値をバインド変数に転送されます。 出力パラメーターと戻り、コードによってクライアントに返される最後のアイテムとは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; までのアプリケーションには返されません[SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md) SQL_NO_DATA が返されます。  
  
 ODBC は、[!INCLUDE[tsql](../../includes/tsql-md.md)] カーソル パラメーターのバインドをサポートしません。 プロシージャの実行前にすべての出力パラメーターをバインドしておく必要があるので、出力カーソル パラメーターを含む [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャを ODBC アプリケーションから呼び出すことはできません。  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャの実行](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
