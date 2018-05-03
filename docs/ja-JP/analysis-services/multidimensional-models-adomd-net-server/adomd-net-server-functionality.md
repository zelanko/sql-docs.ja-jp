---
title: ADOMD.NET サーバー機能 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: adomd
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f0b7a5ba034006e7dd23c69a57c9f2b5fd330851
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="adomdnet-server-functionality"></a>ADOMD.NET のサーバー機能
  すべての ADOMD.NET サーバー オブジェクトは、サーバー上のデータやメタデータへの読み取り専用アクセスを提供します。 データやメタデータを取得するには、ADOMD.NET サーバー オブジェクト モデルを使用します。スキーマ行セットはサポートされていません。  
  
 ADOMD.NET サーバー オブジェクトを使用または作成するユーザー定義関数 (UDF) のストアド プロシージャを[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。 これらのインプロセス メソッドは、多次元式 (MDX)、データ マイニング拡張機能 (DMX)、SQL などの言語で作成されたクエリ ステートメントを通じて呼び出されます。 また、これらのインプロセス メソッドを使用すると、ネットワーク通信に関連する待機時間なしに追加の機能を利用できます。  
  
> [!NOTE]  
>  <xref:Microsoft.AnalysisServices.AdomdServer.AdomdCommand> オブジェクトでサポートされているのは DMX だけです。  
  
## <a name="what-is-a-udf"></a>UDF とは  
 A *UDF*は、次の特性を持つメソッドです。  
  
-   クエリのコンテキストで呼び出すことができます。  
  
-   任意の数のパラメーターを受け取ることができます。  
  
-   さまざまな種類のデータを返すことができます。  
  
 次の例では、架空の UDF である `FinalSalesNumber` を使用しています。  
  
```  
SELECT SalesPerson.Name ON ROWS,  
       FinalSalesNumber() ON COLUMNS  
FROM SalesModel  
```  
  
## <a name="what-is-a-stored-procedure"></a>ストアド プロシージャとは  
 A*ストアド プロシージャ*は、次の特性を持つメソッドです。  
  
-   呼び出すストアド プロシージャに、MDX を使用した独自[呼び出す](../../mdx/mdx-data-manipulation-call.md)ステートメントです。  
  
-   ストアド プロシージャは、パラメーターの任意の数を受け取ることができます。  
  
-   ストアド プロシージャは、データセットを返すことができます、 **IDataReader**、または空の結果。  
  
 次の例では、架空のストアド プロシージャである `FinalSalesNumbers` を使用しています。  
  
```  
CALL FinalSalesNumbers()  
```  
  
## <a name="see-also"></a>参照  
 [ADOMD.NET サーバー プログラミング](../../analysis-services/multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
  
