---
title: "ストアド プロシージャを呼び出して |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- calling stored procedures
- stored procedures [Analysis Services], calling
- MDX queries [Analysis Services]
- CALL statement
ms.assetid: 96a9660d-875b-4ee4-b339-90020b1d9895
caps.latest.revision: "22"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: aa00161709980550644f07a7330198d9369b706e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="calling-stored-procedures"></a>ストアド プロシージャの呼び出し
  ストアド プロシージャは、サーバーまたはクライアント アプリケーションから呼び出すことができます。 どちらの場合も、ストアド プロシージャはサーバーまたはデータベースのコンテキストで常にサーバー上で実行します。 ストアド プロシージャを実行するのに特別なアクセス権は不要です。 ストアド プロシージャがアセンブリによってサーバーまたはデータベースのコンテキストに追加されると、ストアド プロシージャが行う処理がユーザーのロールで許可されている限り、どのユーザーでもストアド プロシージャを実行できます。  
  
 MDX でのストアド プロシージャの呼び出しは、固有の MDX 関数を呼び出す場合と同じ方法で行われます。 パラメーターのないストアド プロシージャの場合は、次のようにストアド プロシージャ名と空のかっこを使用します。  
  
```  
MyStoredProcedure()  
```  
  
 ストアド プロシージャに 1 つ以上のパラメーターを付ける場合は、それらをコンマで区切って順番に入力します。 次の例は、3 つのパラメーターがあるストアド プロシージャのサンプルを示しています。  
  
```  
MyStoredProcedure("Parameter1", 2, 800)  
```  
  
## <a name="calling-stored-procedures-in-mdx-queries"></a>MDX クエリでストアド プロシージャを呼び出す  
 MDX クエリでは必ず、MDX の式で必要とされる正しい構文の型をストアド プロシージャが返す必要があります。 ストアド プロシージャが正しい型を返さなければ、MDX のエラーが発生します。 次の例は、セット、メンバー、および数学的演算の結果を返すストアド プロシージャを示しています。  
  
### <a name="returning-a-set"></a>セットを返す  
 次の例は、セットを返す MySproc というストアド プロシージャを実装します。 最初の例では、MySproc が SELECT 式でセットを直接返します。 2 番目の 2 つの例では、MySproc が Crossjoin 関数と DrilldownLevel 関数の引数としてセットを返します。  
  
```  
SELECT MySetProcedure(a,b,c) ON 0 FROM Sales  
SELECT Crossjoin(MySetProcedure(a,b,c)) ON 0 FROM Sales  
SELECT DrilldownLevel(MySetProcedure(a,b,c)) ON 0 FROM Sales  
```  
  
### <a name="returning-a-member"></a>メンバーを返す  
 次の例は、メンバーを返す MySproc 関数を示しています。  
  
```  
SELECT Descendants(MySproc(a,b,c),3) ON 0 FROM Sales  
```  
  
### <a name="returning-the-result-of-a-math-operation"></a>数学的演算の結果を返す  
  
```  
SELECT Country.Members on 0, MySproc(Measures.Sales) ON 1 FROM Sales  
```  
  
## <a name="calling-stored-procedures-with-the-call-statement"></a>Call ステートメントを使用したストアド プロシージャの呼び出し  
 MDX を使用して MDX クエリのコンテキストの外部でストアド プロシージャを呼び出すことができます**呼び出す**ステートメントです。  
  
 このメソッドは、保存されているクエリの副作用をインスタンス化する場合や、保存されているクエリの結果をアプリケーションが取得する場合に使用できます。 一般的な用途、**呼び出す**分析管理オブジェクト (AMO) を使用して、返される結果がない管理機能を実行するステートメントになります。 たとえば、次のコマンドはストアド プロシージャを呼び出します。  
  
```  
Call MyStoredProcedure(a,b,c)  
```  
  
 ストアド プロシージャから返される型に、唯一サポートされている、**呼び出す**ステートメントが行セット。 行セットのシリアル化は XML forAnaysis で定義されます。 場合のストアド プロシージャ、**呼び出す**ステートメントには、その他の種類が返されます、それは無視され、呼び出し元アプリケーションに XML では返されません。 XML for Analysis 行セットの詳細については、「XML for Analysis のスキーマ行セット｣を参照してください。  
  
 ストアド プロシージャが .NET の行セットを返した場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] はサーバーの結果を XML for Analysis の行セットに変換します。 XML for Analysis の行セットが常にストアド プロシージャによって返されます、**呼び出す**関数。 XML for Analysis の行セットで表せない機能がデータセットに含まれている場合は、エラーが返されます。  
  
 無効な値を返すプロシージャ (たとえば、Visual Basic でのサブルーチン) も CALL キーワードと一緒に使用できます。 たとえば、MDX ステートメントで MyVoidFunction() 関数を使用する場合は、次の構文を使用します。  
  
```  
CALL(MyVoidFunction)  
```  
  
## <a name="see-also"></a>参照  
 [多次元モデルのアセンブリの管理](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [ストアド プロシージャの定義](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
