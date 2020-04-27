---
title: ストアドプロシージャの結果を処理しています |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], results
ms.assetid: 788ef2a4-17de-4526-960b-46bf29aafc9f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e7ffe8b73a7df4cbe2fddcaa0864e338b039f53
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "68205485"
---
# <a name="processing-stored-procedure-results"></a>ストアド プロシージャの結果の処理
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャには、データを返す際に使用する次の 4 つのメカニズムがあります。  
  
-   プロシージャ内の各 SELECT ステートメントで結果セットを生成する。  
  
-   プロシージャが出力パラメーターによってデータを返すことができる。  
  
-   カーソルの出力パラメーターから、[!INCLUDE[tsql](../../includes/tsql-md.md)] サーバー カーソルを返すことができる。  
  
-   プロシージャに整数のリターン コードを含めることができる。  
  
 アプリケーションでは、ストアド プロシージャからのこれらすべての出力を処理できる必要があります。 CALL ステートメントや EXECUTE ステートメントには、リターン コードと出力パラメーター用のパラメーター マーカーを含める必要があります。 [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md)を使用してすべてを出力パラメーターとし[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]てバインドすると、Native Client ODBC ドライバーは、バインドされた変数に出力値を転送します。 出力パラメーターとリターンコードは、によって[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアントに返される最後の項目です。[Sqlmoreresults](../native-client-odbc-api/sqlmoreresults.md)が SQL_NO_DATA を返すまで、アプリケーションには返されません。  
  
 ODBC は、[!INCLUDE[tsql](../../includes/tsql-md.md)] カーソル パラメーターのバインドをサポートしません。 プロシージャの実行前にすべての出力パラメーターをバインドしておく必要があるので、出力カーソル パラメーターを含む [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャを ODBC アプリケーションから呼び出すことはできません。  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャの実行](running-stored-procedures.md)  
  
  
