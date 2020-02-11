---
title: クエリプランの移行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- query plans [SQL Server], migrating
- upgrading SQL Server, migrating query plans
- plan guides [SQL Server], migrating query plans
ms.assetid: 7e02a137-6867-4f6a-a45a-2b02674f7e65
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 66f1f8f57dca3ad2edba3f4b63100b2de3ae5659
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62779114"
---
# <a name="migrate-query-plans"></a>クエリ プランの移行
  データベースを最新バージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にアップグレードすると、ほとんどの場合、クエリのパフォーマンスが向上します。 ただし、慎重にパフォーマンス チューニングされたミッションクリティカルなクエリがある場合は、アップグレードする前に、各クエリのプラン ガイドを作成してこれらのクエリのクエリ プランを保存しておくことをお勧めします。 アップグレード後に、効率性の劣るクエリ プランが 1 つ以上のクエリに対してクエリ オプティマイザーで選択される場合は、プラン ガイドを有効にし、強制的にアップグレード前のプランが使用されるように設定できます。  
  
 アップグレードする前にプラン ガイドを作成するには、次の手順を実行します。  
  
1.  [Sp_create_plan_guide](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)ストアドプロシージャを使用し、USE plan クエリヒントでクエリプランを指定することにより、各ミッションクリティカルなクエリの現在のプランを記録します。  
  
2.  プラン ガイドがクエリに適用されていることを確認します。  
  
3.  データベースを最新のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にアップグレードします。  
  
     このクエリ プランは、アップグレードしたデータベースのプラン ガイドに保存され、アップグレード後に効率性の劣るプランが選択された場合のフォールバックとして機能します。  
  
     アップグレード後にプラン ガイドを有効にしないようお勧めします。統計の更新により、新しいリリースに含まれる優れたプランや有益な再コンパイルを利用できなくなる可能性があるためです。  
  
4.  アップグレード後に効率性の劣るプランが選択される場合は、すべてのプラン ガイドまたはその一部を有効にして新しいプランをオーバーライドします。  
  
## <a name="example"></a>例  
 次の例は、プラン ガイドを作成することにより、アップグレード前のプランを記録する方法を示しています。  
  
### <a name="step-1-collect-the-plan"></a>手順 1: プランを収集する  
 プラン ガイドに記録するクエリ プランは XML 形式にする必要があります。 XML 形式のクエリ プランは、次の方法で生成できます。  
  
-   [SHOWPLAN_XML の設定](/sql/t-sql/statements/set-showplan-xml-transact-sql)  
  
-   [SET STATISTICS XML](/sql/t-sql/statements/set-statistics-xml-transact-sql)  
  
-   動的管理関数[dm_exec_query_plan](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql)の query_plan 列を照会しています。  
  
-   [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] [Showplan xml](../../relational-databases/event-classes/showplan-xml-event-class.md)、 [showplan xml Statistics Profile](../../relational-databases/event-classes/showplan-xml-statistics-profile-event-class.md)、および[showplan xml For Query Compile](../../relational-databases/event-classes/showplan-xml-for-query-compile-event-class.md)イベントクラス。  
  
 次の例では、動的管理ビューに対してクエリを実行することにより、`SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;` ステートメントのクエリ プランを収集します。  
  
```  
USE AdventureWorks;  
GO  
SELECT query_plan  
    FROM sys.dm_exec_query_stats AS qs   
    CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
    CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, DEFAULT, DEFAULT) AS qp  
    WHERE st.text LIKE N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;%';  
GO  
```  
  
### <a name="step-2-create-the-plan-guide-to-force-the-plan"></a>手順 2: プラン ガイドを作成しプランを適用する  
 プラン ガイドで (前述のいずれかの方法で取得した) XML 形式のクエリ プランを使用し、sp_create_plan_guide の OPTION 句に指定した USE PLAN クエリ ヒント内に、文字列リテラルとしてそのクエリ プランをコピーして貼り付けます。  
  
 プラン ガイドを作成する前に、XML プラン自体に含まれている引用符 (') には引用符をもう 1 つ付けてエスケープします。 たとえば、`WHERE A.varchar = 'This is a string'` を含むプランの場合は、コードを `WHERE A.varchar = ''This is a string''` のように変更してエスケープする必要があります。  
  
 次の例では、手順 1 で収集したクエリ プランのプラン ガイドを作成し、クエリの XML プラン表示を `@hints` パラメーターに挿入します。 簡略にするため、この例には一部のプラン表示出力しか含まれていません。  
  
```  
EXECUTE sp_create_plan_guide   
@name = N'Guide1',  
@stmt = N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;',  
@type = N'SQL',  
@module_or_batch = NULL,  
@params = NULL,  
@hints = N'OPTION(USE PLAN N''<ShowPlanXML xmlns=''''https://schemas.microsoft.com/sqlserver/2004/07/showplan''''   
    Version=''''0.5'''' Build=''''9.00.1116''''>  
    <BatchSequence><Batch><Statements><StmtSimple>  
    ...  
    </StmtSimple></Statements></Batch>  
    </BatchSequence></ShowPlanXML>'')';  
GO  
```  
  
### <a name="step-3-verify-that-the-plan-guide-is-applied-to-the-query"></a>手順 3: プラン ガイドがクエリに適用されていることを確認する  
 クエリを再実行し、生成されたクエリ プランを調べます。 このプランがプラン ガイドで指定したプランに一致していることを確認してください。  
  
## <a name="see-also"></a>参照  
 [sp_create_plan_guide &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Transact-sql&#41;&#40;クエリヒント](/sql/t-sql/queries/hints-transact-sql-query)   
 [プランガイド](../../relational-databases/performance/plan-guides.md)  
  
  
