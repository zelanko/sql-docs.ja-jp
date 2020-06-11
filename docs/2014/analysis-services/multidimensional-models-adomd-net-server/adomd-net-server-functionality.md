---
title: ADOMD.NET サーバーの機能 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- functionality [ADOMD.NET]
- ADOMD.NET, functionality
ms.assetid: b74c6957-3f64-4e09-aa09-d06ee93f82fa
author: minewiskan
ms.author: owend
ms.openlocfilehash: 95e0627e4f794050438ba392be6911d661f243aa
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84537391"
---
# <a name="adomdnet-server-functionality"></a>ADOMD.NET のサーバー機能
  すべての ADOMD.NET サーバー オブジェクトは、サーバー上のデータやメタデータへの読み取り専用アクセスを提供します。 データやメタデータを取得するには、ADOMD.NET サーバー オブジェクト モデルを使用します。スキーマ行セットはサポートされていません。  
  
 ADOMD.NET server オブジェクトを使用すると、のユーザー定義関数 (UDF) またはストアドプロシージャを作成でき [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。 これらのインプロセス メソッドは、多次元式 (MDX)、データ マイニング拡張機能 (DMX)、SQL などの言語で作成されたクエリ ステートメントを通じて呼び出されます。 また、これらのインプロセス メソッドを使用すると、ネットワーク通信に関連する待機時間なしに追加の機能を利用できます。  
  
> [!NOTE]  
>  <xref:Microsoft.AnalysisServices.AdomdServer.AdomdCommand> オブジェクトでサポートされているのは DMX だけです。  
  
## <a name="what-is-a-udf"></a>UDF とは  
 *UDF*は、次の特性を持つメソッドです。  
  
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
 *ストアドプロシージャ*は、次の特性を持つメソッドです。  
  
-   MDX [call](/sql/mdx/mdx-data-manipulation-call)ステートメントを使用して、独自のストアドプロシージャを呼び出します。  
  
-   ストアドプロシージャは、任意の数のパラメーターを受け取ることができます。  
  
-   データセット、`IDataReader`、または空の結果を返すことができます。  
  
 次の例では、架空のストアド プロシージャである `FinalSalesNumbers` を使用しています。  
  
```  
CALL FinalSalesNumbers()  
```  
  
## <a name="see-also"></a>参照  
 [ADOMD.NET サーバー プログラミング](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
  
