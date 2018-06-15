---
title: 指定されたステートメントを使用してストアド プロシージャ |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0041f9e1-09b6-4487-b052-afd636c8e89a
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a2e5ff4dc6ffa18d553b0b0e3bbe0c9c3a629920
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32852957"
---
# <a name="using-statements-with-stored-procedures"></a>ストアド プロシージャでのステートメントの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  ストアド プロシージャは、データベースのプロシージャです。他のプログラミング言語のプロシージャと似ていますが、ストアド プロシージャはデータベースそのものに格納されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、ストアド プロシージャを使用して作成できます[!INCLUDE[tsql](../../includes/tsql_md.md)]、または共通言語ランタイム (CLR) および Visual Studio のいずれかを使用して、Visual Basic や c# などの言語をプログラミングします。 一般に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ストアド プロシージャは、次を実行できます。  
  
-   入力パラメーターを受け取り、呼び出し元のプロシージャまたはバッチに出力パラメーターの形式で複数の値を返す。  
  
-   他のプロシージャの呼び出しなど、データベース内での操作を実行するプログラミング ステートメントを含む。  
  
-   呼び出し元のプロシージャまたはバッチにステータス値を返し、成功、失敗、および失敗の原因を示す。  
  
> [!NOTE]  
>  詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、ストアド プロシージャのストアド プロシージャについて」を参照してください[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
 内のデータを使用する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ストアド プロシージャを使用して、データベース、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]提供、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)、 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)、および[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラスです。 使用するクラスは、ストアド プロシージャで IN (入力) パラメーターと OUT (出力) パラメーターのどちらが必要かによって異なります。 ストアド プロシージャも必要ない場合、または OUT パラメーター、SQLServerStatement クラスを使用することができます。ストアド プロシージャは、複数回呼び出されるまたは IN パラメーターのみが必要です、SQLServerPreparedStatement クラスを使用することができます。 ストアド プロシージャの両方が必要な場合、OUT パラメーターは、SQLServerCallableStatement クラスを使用する必要があります。 のみ、ストアド プロシージャが必要な場合 OUT パラメーター、SQLServerCallableStatement クラスを使用するオーバーヘッドが必要となることをお勧めします。  
  
> [!NOTE]  
>  ストアド プロシージャは、更新数および複数の結果セットを返すこともできます。 詳細については、次を参照してください。[更新数を含むストアド プロシージャを使用して](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md)と[複数の結果セットを使用して](../../connect/jdbc/using-multiple-result-sets.md)です。  
  
 JDBC ドライバーを使用してパラメーターを使用してストアド プロシージャを呼び出すときに行う必要があります、`call`と共に SQL エスケープ シーケンス、 [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)のメソッド、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)クラスです。 完全な構文、`call`エスケープ シーケンスは、次のようにします。  
  
 `{[?=]call procedure-name[([parameter][,[parameter]]...)]}`  
  
> [!NOTE]  
>  詳細については、`call`およびその他の SQL エスケープ シーケンスは、「 [SQL エスケープ シーケンスを使用して](../../connect/jdbc/using-sql-escape-sequences.md)です。  
  
 このセクションのトピックでは呼び出すことができる方法を説明[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]JDBC ドライバーを使用してストアド プロシージャ、および`call`SQL エスケープ シーケンスです。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[パラメーターのないストアド プロシージャの使用](../../connect/jdbc/using-a-stored-procedure-with-no-parameters.md)|JDBC ドライバーを使用して、入力または出力パラメーターのないストアド プロシージャを実行する方法を説明します。|  
|[入力パラメーターがあるストアド プロシージャの使用](../../connect/jdbc/using-a-stored-procedure-with-input-parameters.md)|JDBC ドライバーを使用して、入力パラメーターがあるストアド プロシージャを実行する方法を説明します。|  
|[出力パラメーターがあるストアド プロシージャの使用](../../connect/jdbc/using-a-stored-procedure-with-output-parameters.md)|JDBC ドライバーを使用して、出力パラメーターのないストアド プロシージャを実行する方法を説明します。|  
|[状態の戻り値があるストアド プロシージャの使用](../../connect/jdbc/using-a-stored-procedure-with-a-return-status.md)|JDBC ドライバーを使用して、状態の戻り値があるストアド プロシージャを実行する方法を説明します。|  
|[更新数があるストアド プロシージャの使用](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md)|JDBC ドライバーを使用して、更新数を返すストアド プロシージャを実行する方法を説明します。|  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーでのステートメントの使用](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  
