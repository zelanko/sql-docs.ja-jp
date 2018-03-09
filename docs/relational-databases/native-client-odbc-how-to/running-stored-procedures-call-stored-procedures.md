---
title: "ストアド プロシージャ (ODBC) を呼び出して |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], calling
ms.assetid: 31176be8-d40e-4f93-8d44-a46e804a3e2d
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7e8aa0ae9c68313671e3d6e9c8ad1a71392f9524
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="running-stored-procedures---call-stored-procedures"></a>ストアド プロシージャの実行にストアド プロシージャを呼び出し
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC ドライバーは、リモート ストアド プロシージャとしてのストアド プロシージャの実行をサポートします。 ストアド プロシージャをリモート ストアド プロシージャとして実行すると、ドライバーとサーバーでプロシージャ実行のパフォーマンスが最適化されます。  
  
  SQL ステートメントで ODBC CALL エスケープ句を使用してストアド プロシージャを呼び出すと、Microsoft® SQL Server™ ドライバーは、リモート ストアド プロシージャ コール (RPC) メカニズムを使用して、プロシージャを SQL Server に送信します。 RPC 要求は、SQL Server でのステートメント解析やパラメーター処理の多くを省略するため、Transact-SQL の EXECUTE ステートメントを使用するよりも高速です。  
  
 この機能を示すサンプル アプリケーションを参照してください。[プロセスのリターン コードと出力パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/running-stored-procedures-process-return-codes-and-output-parameters.md)です。  
  
### <a name="to-run-a-procedure-as-an-rpc"></a>プロシージャを RPC として実行するには  
  
1.  ODBC CALL エスケープ シーケンスを使用する SQL ステートメントを作成します。 このステートメントでは、各入力、入出力、出力パラメーター、およびプロシージャの戻り値 (存在する場合) に対してパラメーター マーカーを使用します。  
  
    ```  
    {? = CALL procname (?,?)}  
    ```  
  
2.  呼び出す[SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md)各入力には、入出力、出力パラメーター、およびプロシージャの戻り値 (存在する場合)。  
  
3.  使用してステートメントを実行[SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399)です。  
  
> [!NOTE]  
>  アプリケーションでプロシージャの送信に (ODBC CALL エスケープ シーケンスではなく) Transact-SQL の EXECUTE 構文を使用した場合、プロシージャ コールは、SQL Server ODBC ドライバーから SQL Server に、RPC ではなく SQL ステートメントとして渡されます。 また、Transact-SQL の EXECUTE ステートメントを使用した場合、出力パラメーターは返されません。  
  
## <a name="see-also"></a>参照  
  [ストアド プロシージャの呼び出しをバッチ処理](../../relational-databases/native-client-odbc-stored-procedures/batching-stored-procedure-calls.md)   
 [ストアド プロシージャの実行](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [ストアド プロシージャを呼び出す](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md)   
 [手順](../../relational-databases/native-client-odbc-queries/executing-statements/procedures.md)  
  
  
