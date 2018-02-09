---
title: "CLR ユーザー定義集計の要件 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 204a01f25e90be1885bad41361aa41d919159bd0
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="clr-user-defined-aggregates---requirements"></a>CLR ユーザー定義集計の要件
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
CLR (共通言語ランタイム) アセンブリの型は、必要な集計コントラクトが実装されていれば、ユーザー定義集計関数として登録できます。 このコントラクトで構成されます、 **SqlUserDefinedAggregate**属性と集計コントラクトのメソッドです。 集計コントラクトには、集計の中間の状態を保存するためのメカニズムと 4 つの方法で構成される新しい値を積算するメカニズムが含まれています: **Init**、 **Accumulate**、 **マージ**、および**終了**です。 これらの要件が満たされることができますでのユーザー定義集計をフル活用する[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 このトピックの次のセクションでは、ユーザー定義集計を作成し、そのユーザー定義集計を使用して作業する方法について詳しく説明します。 例については、次を参照してください。 [Invoking CLR User-Defined 集計関数](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregate-invoking-functions.md)です。  
  
## <a name="sqluserdefinedaggregate"></a>SqlUserDefinedAggregate  
 詳細については、次を参照してください。 [SqlUserDefinedAggregateAttribute](http://go.microsoft.com/fwlink/?LinkId=124626)です。  
  
## <a name="aggregation-methods"></a>集計のメソッド  
 ユーザー定義集計として登録するクラスでは、次のインスタンス メソッドをサポートする必要があります。 次に、集計を計算するためにクエリ プロセッサで使用されるメソッドを示します。  
  
|方法|構文|Description|  
|------------|------------|-----------------|  
|**Init**|`public void Init();`|クエリ プロセッサは、このメソッドを使用して集計計算を初期化します。 このメソッドは、クエリ プロセッサで集計されるグループごとに 1 回ずつ呼び出されます。 クエリ プロセッサでは、複数のグループの集計を計算するために、集計クラスの同じインスタンスの再利用を選択することがあります。 **Init**方法は必要があります、このインスタンスの前に使用クリーンアップ必要に応じてを実行し、新たな集計計算を再度開始するように有効にします。|  
|**蓄積**|`public void Accumulate ( input-type value[, input-type value, ...]);`|関数のパラメーターを表す 1 つ以上のパラメーター。 *input_type*マネージにする必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型をネイティブに相当する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で指定されたデータ型*input_sqltype*で、 **CREATE AGGREGATE**ステートメント. 詳細については、次を参照してください。 [CLR パラメーター データのマッピング](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)です。<br /><br /> UDT (ユーザー定義型) の場合、input-type 型は UDT 型と同じです。 クエリ プロセッサでは、このメソッドを使用して集計値を積算します。 このメソッドは、集計されるグループの値ごとに 1 回ずつ呼び出されます。 クエリ プロセッサは、常に呼び出すこの呼び出した後にだけ、 **Init**集計クラスの特定のインスタンス上のメソッドです。 このメソッドの実装では、渡された引数値の積算を反映してインスタンスの状態を更新する必要があります。|  
|**Merge**|`public void Merge( udagg_class value);`|このメソッドは、この集計クラスの別のインスタンスを現在のインスタンスとマージする場合に使用できます。 クエリ プロセッサでは、このメソッドを使用して、1 つの集計の複数の部分計算をマージできます。|  
|**終了**|`public return_type Terminate();`|このメソッドは、集計計算を完了し、集計の結果を返します。 *Return_type*マネージにする必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]となるデータ型の対応するマネージ*return_sqltype*で指定されている、 **CREATE AGGREGATE**ステートメントです。 *Return_type*ユーザー定義型をすることもできます。|  
  
### <a name="table-valued-parameters"></a>テーブル値パラメーター  
 テーブル値パラメーター (TVP) とは、プロシージャや関数に渡されるユーザー定義のテーブル型です。TVP を使用すると、複数行のデータを効率的にサーバーに渡すことができます。 TVP の機能はパラメーター配列に似ていますが、より柔軟性が高く、[!INCLUDE[tsql](../../includes/tsql-md.md)] との統合も緊密です。 テーブル値パラメーターを使用するとパフォーマンスが向上する可能性もあります。 また、サーバーへのラウンド トリップを減らすのにも役立ちます。 スカラー パラメーターのリストを使用するなどしてサーバーに複数の要求を送信する代わりに、データを TVP としてサーバーに送信できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のプロセスで実行されているマネージ ストアド プロシージャやマネージ関数にユーザー定義のテーブル型をテーブル値パラメーターとして渡したり、戻り値として受け取ったりすることはできません。 また、TVP はコンテキスト接続のスコープ内では使用できません。 ただし、コンテキスト接続ではない接続で使用されている SqlClient を使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のプロセスで実行されているマネージ ストアド プロシージャやマネージ関数で TVP を使用できます。 その接続は、マネージ プロシージャやマネージ関数を実行しているのと同じサーバーへの接続でかまいません。 Tvp の詳細については、次を参照してください。[テーブル値パラメーター &#40;データベース エンジン&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)です。  
  
## <a name="change-history"></a>変更履歴  
  
|変更内容|  
|---------------------|  
|説明を更新、 **Accumulate**メソッド以外の場合は、1 つ以上のパラメーターを受け入れるようになりました。|  
  
## <a name="see-also"></a>参照  
 [CLR ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [CLR ユーザー定義集計関数の呼び出し](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregate-invoking-functions.md)  
  
  
