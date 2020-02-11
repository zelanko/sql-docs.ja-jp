---
title: プロシージャ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
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
ms.openlocfilehash: d030d4fb12ce9217bbdb88f501a0b0674c5a5828
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68206751"
---
# <a name="procedures"></a>手順
  ストアド プロシージャは、1 つ以上の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを含むプリコンパイルされた実行可能オブジェクトです。 ストアド プロシージャは、入力パラメーターと出力パラメーターを使用でき、整数のリターン コードを出力することもできます。 アプリケーションは、カタログ関数を使用することで、使用可能なストアド プロシージャを列挙できます。  
  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を対象とする ODBC アプリケーションからストアド プロシージャを呼び出す場合、直接実行だけを使用する必要があります。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]以前のバージョンのに接続して[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]いる場合、Native Client ODBC ドライバーは、一時ストアドプロシージャを作成することによって[SQLPrepare 関数](https://go.microsoft.com/fwlink/?LinkId=59360)を実装します。このストアドプロシージャは、 **sqlexecute**で呼び出されます。 **SQLPrepare**によって、対象のストアドプロシージャを呼び出すだけでなく、対象のストアドプロシージャを直接実行する一時ストアドプロシージャを作成することにより、オーバーヘッドが増加します。 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに接続している場合でも、呼び出しの準備には、ネットワーク経由のやり取りが増え、ストアド プロシージャ実行プランを呼び出すだけの実行プランの構築が必要になります。  
  
 ODBC アプリケーションでは、ストアド プロシージャの実行時に ODBC CALL 構文を使用する必要があります。 ドライバーは、ODBC CALL 構文の使用時に、リモート プロシージャ コールのメカニズムを使用してプロシージャを呼び出すように最適化されます。 これは、[!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE ステートメントをサーバーに送信するときに使用するメカニズムよりも効率的です。  
  
 詳細については、「[ストアドプロシージャの実行](../../native-client-odbc-stored-procedures/running-stored-procedures.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;のステートメントの実行](executing-statements-odbc.md)  
  
  
