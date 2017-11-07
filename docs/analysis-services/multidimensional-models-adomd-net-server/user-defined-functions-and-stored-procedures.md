---
title: "ユーザー定義関数およびストアド プロシージャ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- stored procedures [ADOMD.NET]
- ADOMD.NET, user defined functions
- user defined functions [ADOMD.NET]
- ADOMD.NET, UDFs
- ADOMD.NET, stored procedures
ms.assetid: 07e8aa47-37d4-4bbc-8bff-49e422d12897
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 1c49bb0f4994883f7bee1accf8c6d983b31b657f
ms.contentlocale: ja-jp
ms.lasthandoff: 10/24/2017

---
# <a name="user-defined-functions-and-stored-procedures"></a>ユーザー定義関数およびストアド プロシージャ
  ユーザー定義関数 (UDF) または用のストアド プロシージャを作成する、ADOMD.NET サーバー オブジェクトと[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]あり、サーバーからメタデータとデータと対話します。 これらのインプロセス メソッドは、ネットワーク通信に関連する待機時間を伴わず、追加機能を提供する多次元式 (MDX) ステートメントまたはデータ マイニング拡張機能 (DMX) ステートメントを通して呼び出されます。  
  
## <a name="udf-examples"></a>UDF の例  
 UDF は、MDX ステートメントまたは DMX ステートメントのコンテキスト内で呼び出すことができます。また、任意の数のパラメーターを取り、任意の型のデータを返します。  
  
 MDX を使用して作成された UDF は、DMX の UDF と似ています。 主な相違点は、<xref:Microsoft.AnalysisServices.AdomdServer.Context> オブジェクトの一部のプロパティ (<xref:Microsoft.AnalysisServices.AdomdServer.Context.CurrentCube%2A>、<xref:Microsoft.AnalysisServices.AdomdServer.Context.CurrentMiningModel%2A> など) は、いずれか 1 つのスクリプト言語でしか使用できないということです。  
  
 次の例では、UDF を使用して、ノードの記述を取得し、組をフィルターし、組に対してフィルターを適用する方法を示します。  
  
### <a name="returning-a-node-description"></a>ノードの記述を取得する  
 次の例では、指定されたノードのノード記述を返す UDF を作成します。 UDF は、UDF が実行されている現在のコンテキストを使用し、DMX FROM 句を使用して現在のマイニング モデルからノードを取得します。  
  
```  
public string GetNodeDescription(string nodeUniqueName)  
{  
   return Context.CurrentMiningModel.GetNodeFromUniqueName(nodeUniqueName).Description;  
}  
```  
  
 前の例の UDF を配置すると、次の DMX 式で呼び出せるようになります。この式は、最も可能性が高い予測ノードを取得します。 ノード記述には、予測ノードを構成する条件についての情報が含まれます。  
  
```  
select Cluster(), SampleAssembly.GetNodeDescription( PredictNodeId(Cluster()) ) FROM [Customer Clusters]  
```  
  
### <a name="returning-tuples"></a>組を返す  
 次の例は、セットおよび返される回数を受け取り、そのセットからランダムに組を取得し、最後のサブセットを返します。  
  
```  
public Set RandomSample(Set set, int returnCount)  
{  
   //Return the original set if there are fewer tuples  
   //in the set than the number requested.  
   if (set.Tuples.Count <= returnCount)  
      return set;  
  
   System.Random r = new System.Random();  
   SetBuilder returnSet = new SetBuilder();  
  
   //Retrieve random tuples until the return set is filled.  
   int i = set.Tuples.Count;  
   foreach (Tuple t in set.Tuples)  
   {  
      if (r.Next(i) < returnCount)  
      {  
         returnCount--;  
         returnSet.Add(t);  
      }  
      i--;  
      //Stop the loop if we have enough tuples.  
      if (returnCount == 0)  
         break;  
   }  
   return returnSet.ToSet();  
}  
```  
  
 前の例は、次の MDX 式で呼び出されます。 この MDX 例から 5 つのランダムな州または郡を取得します。、 **Adventure Works**データベース。  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
### <a name="applying-a-filter-to-a-tuple"></a>組に対してフィルターを適用する  
 次の例では、UDF は、セットを受け取り、Expression オブジェクトを使用してそのセット内の各組に対してフィルターを適用するように定義されます。 フィルターの条件に合う組は、返されるセットに追加されます。  
  
 [!code-cs[Adomd.NetServer#FilterSet](../../analysis-services/multidimensional-models-adomd-net-server/codesnippet/csharp/user-defined-functions-a_1.cs)]  
  
 前の例は、次の MDX 例で呼び出されます。この MDX 例は、セットにフィルターを適用し、名前が "A" で始まる都市だけに絞り込みます。  
  
```  
Select Measures.Members on Rows,  
SampleAssembly.FilterSet([Customer].[Customer Geography].[City], "[Customer].[Customer Geography].[City].CurrentMember.Name < 'B'") on Columns  
From [Adventure Works]  
```  
  
## <a name="stored-procedure-example"></a>ストアド プロシージャの例  
 次の例では、MDX ベースのストアド プロシージャが AMO を使用して、必要に応じて Internet Sales のパーティションを作成します。  
  
 [!code-cs[Adomd.NetServer#CreateInternetSalesMeasureGroupPartitions](../../analysis-services/multidimensional-models-adomd-net-server/codesnippet/csharp/user-defined-functions-a_2.cs)]  
  
  

