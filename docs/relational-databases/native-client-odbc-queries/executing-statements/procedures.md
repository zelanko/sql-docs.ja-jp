---
title: プロシージャ |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC]
- stored procedures [ODBC], about ODBC stored procedures
- ODBC applications, statements
- statements [ODBC], stored procedures
- ODBC applications, stored procedures
ms.assetid: c64d5f3a-376b-48ef-84f3-b6148ac8600a
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a4e9576ce93b196968b28b6cc91cadd662d2a3fb
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2018
ms.locfileid: "35694893"
---
# <a name="procedures"></a>手順
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  ストアド プロシージャは、1 つ以上の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを含むプリコンパイルされた実行可能オブジェクトです。 ストアド プロシージャは、入力パラメーターと出力パラメーターを使用でき、整数のリターン コードを出力することもできます。 アプリケーションは、カタログ関数を使用することで、使用可能なストアド プロシージャを列挙できます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を対象とする ODBC アプリケーションからストアド プロシージャを呼び出す場合、直接実行だけを使用する必要があります。 以前のバージョンに接続しているときに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーを実装して[SQLPrepare 関数](http://go.microsoft.com/fwlink/?LinkId=59360)、一時ストアド プロシージャを作成すると、しと呼ばれるで**SQLExecute**. オーバーヘッドが追加**SQLPrepare**しか作成できない、一時ストアド プロシージャを呼び出し、対象のストアド プロシージャではなくストアド プロシージャをターゲットの実行は直接です。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続している場合でも、呼び出しの準備には、ネットワーク経由のやり取りが増え、ストアド プロシージャ実行プランを呼び出すだけの実行プランの構築が必要になります。  
  
 ODBC アプリケーションでは、ストアド プロシージャの実行時に ODBC CALL 構文を使用する必要があります。 ドライバーは、ODBC CALL 構文の使用時に、リモート プロシージャ コールのメカニズムを使用してプロシージャを呼び出すように最適化されます。 これは、[!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE ステートメントをサーバーに送信するときに使用するメカニズムよりも効率的です。  
  
 詳細については、次を参照してください。[ストアド プロシージャを実行している](../../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)です。  
  
## <a name="see-also"></a>参照  
 [ステートメントを実行する&#40;ODBC&#41;](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
