---
title: ADOMD.NET のサーバー機能 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6c1f37be45b702828d3c663eac0fb575a0af3bbd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63059465"
---
# <a name="adomdnet-server-functionality"></a>ADOMD.NET のサーバー機能
  すべての ADOMD.NET サーバー オブジェクトは、サーバー上のデータやメタデータへの読み取り専用アクセスを提供します。 データやメタデータを取得するには、ADOMD.NET サーバー オブジェクト モデルを使用します。スキーマ行セットはサポートされていません。  
  
 ユーザー定義関数 (UDF) またはのストアド プロシージャを作成する、ADOMD.NET サーバー オブジェクトと[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]します。 これらのインプロセス メソッドは、多次元式 (MDX)、データ マイニング拡張機能 (DMX)、SQL などの言語で作成されたクエリ ステートメントを通じて呼び出されます。 また、これらのインプロセス メソッドを使用すると、ネットワーク通信に関連する待機時間なしに追加の機能を利用できます。  
  
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
  
-   呼び出すストアド プロシージャに、MDX を使用した独自[呼び出す](../../mdx/mdx-data-manipulation-call.md)ステートメント。  
  
-   ストアド プロシージャには、パラメーターの任意の数を取得できます。  
  
-   ストアド プロシージャは、データセットを返すことができます、 **IDataReader**、または空の結果。  
  
 次の例では、架空のストアド プロシージャである `FinalSalesNumbers` を使用しています。  
  
```  
CALL FinalSalesNumbers()  
```  
  
## <a name="see-also"></a>関連項目  
 [ADOMD.NET サーバー プログラミング](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
  
