---
title: CLR ユーザー定義集計の要件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- aggregate functions [CLR integration]
- user-defined types [CLR integration], user-defined aggregates
- CREATE AGGREGATE statement
- SqlUserDefinedAggregate attribute
- aggregate methods [CLR integration]
- assemblies [CLR integration], user-defined aggregate functions
- custom aggregates [CLR integration]
- user-defined functions [CLR integration]
- UDTs [CLR integration], user-defined aggregates
ms.assetid: dbf9eb5a-bd99-42f7-b275-556d0def045d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 31b22b1dce53bb82f85ae946290024408d2facd3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62874479"
---
# <a name="requirements-for-clr-user-defined-aggregates"></a>CLR ユーザー定義集計の要件
  CLR (共通言語ランタイム) アセンブリの型は、必要な集計コントラクトが実装されていれば、ユーザー定義集計関数として登録できます。 このコントラクトは、`SqlUserDefinedAggregate` 属性と集計コントラクトのメソッドで構成されます。 集計コントラクトには、集計の中間状態を保存するためのメカニズムと、`Init`、`Accumulate`、`Merge`、および `Terminate` の 4 つのメソッドで構成される新しい値を積算するメカニズムが含まれます。 これらの要件を満たしている場合は、で[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ユーザー定義集計を最大限に活用することができます。 このトピックの次のセクションでは、ユーザー定義集計を作成し、そのユーザー定義集計を使用して作業する方法について詳しく説明します。 例については、「 [CLR ユーザー定義集計関数の呼び出し](clr-user-defined-aggregate-invoking-functions.md)」を参照してください。  
  
## <a name="sqluserdefinedaggregate"></a>SqlUserDefinedAggregate  
 詳細については、「 [SqlUserDefinedAggregateAttribute](https://go.microsoft.com/fwlink/?LinkId=124626)」を参照してください。  
  
## <a name="aggregation-methods"></a>集計のメソッド  
 ユーザー定義集計として登録するクラスでは、次のインスタンス メソッドをサポートする必要があります。 次に、集計を計算するためにクエリ プロセッサで使用されるメソッドを示します。  
  
|メソッド|構文|説明|  
|------------|------------|-----------------|  
|`Init`|public void Init ();|クエリ プロセッサは、このメソッドを使用して集計計算を初期化します。 このメソッドは、クエリ プロセッサで集計されるグループごとに 1 回ずつ呼び出されます。 クエリ プロセッサでは、複数のグループの集計を計算するために、集計クラスの同じインスタンスの再利用を選択することがあります。 `Init` メソッドは、現在のインスタンスが以前に使用されていれば必要になるクリーンアップを実行し、新たな集計計算を再開できるようにします。|  
|`Accumulate`|public void 累積 (入力型の値 [, 入力型の値,...]);|関数のパラメーターを表す 1 つ以上のパラメーター。 *input_type*は、 `CREATE AGGREGATE`ステートメントで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *input_sqltype*によって指定さ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]れたネイティブデータ型に相当するマネージデータ型である必要があります。 詳細については、「 [CLR パラメーターデータのマッピング](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)」を参照してください。<br /><br /> UDT (ユーザー定義型) の場合、input-type 型は UDT 型と同じです。 クエリ プロセッサでは、このメソッドを使用して集計値を積算します。 このメソッドは、集計されるグループの値ごとに 1 回ずつ呼び出されます。 クエリ プロセッサでは、集計クラスの特定のインスタンスの `Init` メソッドが呼び出された後にのみ、常に、このメソッドが呼び出されます。 このメソッドの実装では、渡された引数値の積算を反映してインスタンスの状態を更新する必要があります。|  
|`Merge`|public void Merge (udagg_class 値);|このメソッドは、この集計クラスの別のインスタンスを現在のインスタンスとマージする場合に使用できます。 クエリ プロセッサでは、このメソッドを使用して、1 つの集計の複数の部分計算をマージできます。|  
|`Terminate`|パブリック return_type 終了 ();|このメソッドは、集計計算を完了し、集計の結果を返します。 *Return_type*は、 `CREATE AGGREGATE`ステートメントで指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]された*return_sqltype*と同等のマネージデータ型である必要があります。 *Return_type*は、ユーザー定義型でもかまいません。|  
  
### <a name="table-valued-parameters"></a>テーブル値パラメーター  
 テーブル値パラメーター (TVP) とは、プロシージャや関数に渡されるユーザー定義のテーブル型です。TVP を使用すると、複数行のデータを効率的にサーバーに渡すことができます。 TVP の機能はパラメーター配列に似ていますが、より柔軟性が高く、[!INCLUDE[tsql](../../includes/tsql-md.md)] との統合も緊密です。 テーブル値パラメーターを使用するとパフォーマンスが向上する可能性もあります。 また、サーバーへのラウンド トリップを減らすのにも役立ちます。 スカラー パラメーターのリストを使用するなどしてサーバーに複数の要求を送信する代わりに、データを TVP としてサーバーに送信できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のプロセスで実行されているマネージド ストアド プロシージャやマネージド関数にユーザー定義のテーブル型をテーブル値パラメーターとして渡したり、戻り値として受け取ったりすることはできません。 また、TVP はコンテキスト接続のスコープ内では使用できません。 ただし、コンテキスト接続ではない接続で使用されている SqlClient を使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のプロセスで実行されているマネージド ストアド プロシージャやマネージド関数で TVP を使用できます。 その接続は、マネージド プロシージャやマネージド関数を実行しているのと同じサーバーへの接続でかまいません。 Tvp の詳細については、「[データベースエンジン&#41;&#40;テーブル値パラメーターの使用](../tables/use-table-valued-parameters-database-engine.md)」を参照してください。  
  
## <a name="change-history"></a>変更履歴  
  
|変更内容|  
|---------------------|  
|`Accumulate` メソッドの説明を更新しました。このメソッドは、現在は複数のパラメーターを受け取ります。|  
  
## <a name="see-also"></a>参照  
 [CLR ユーザー定義型](../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [CLR ユーザー定義集計関数の呼び出し](clr-user-defined-aggregate-invoking-functions.md)  
  
  
