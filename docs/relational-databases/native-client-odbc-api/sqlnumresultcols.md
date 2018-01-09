---
title: "SQLNumResultCols |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6b4cfc7416b2e4438cc8462353e5f9bea6e125a7
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ステートメントの実行、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーに結果セット内の列の数を報告するサーバーがアクセスしていません。 この場合、 **SQLNumResultCols**サーバーとのやり取りは行われません。 同様に[SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md)と[SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md)、呼び出し元**SQLNumResultCols**準備されてが実行されていないステートメントには、サーバーとのやり取りが生成されます。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントまたはステートメント バッチが複数の結果行セットを返すときは、結果セットの列数を報告する場合、あるセットから別のセットへ結果セットを変更することができます。 **SQLNumResultCols**セットごとに呼び出す必要があります。 列数が変化すると、アプリケーションでは行の結果をフェッチする前に、データ値を再バインドする必要があります。 セットを返す複数の結果を処理の詳細についてを参照してください[SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md)です。  
  
 以降で、データベース エンジンの機能強化[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]SQLNumResultCols を期待する結果のより正確な記述を取得できるようにします。 以前のバージョンの SQLNumResultCols によって返される値からこれらのより正確な結果が異なる場合があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 詳細については、次を参照してください。[メタデータ検出](../../relational-databases/native-client/features/metadata-discovery.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLNumResultCols 関数](http://go.microsoft.com/fwlink/?LinkId=59359)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
