---
title: "ADOMD.NET サーバー機能 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- functionality [ADOMD.NET]
- ADOMD.NET, functionality
ms.assetid: b74c6957-3f64-4e09-aa09-d06ee93f82fa
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 40d68e739a9628113b7adfeab5db2a6b1445981f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

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
  
  

