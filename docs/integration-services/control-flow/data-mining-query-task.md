---
title: "データ マイニング クエリ タスク |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.dataminingquerytask.f1
helpviewer_keywords:
- prediction queries [Integration Services]
- Data Mining Query task [Integration Services]
ms.assetid: f489348c-2008-4f66-8c2c-c07c3029439a
caps.latest.revision: 45
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0b171b2ce21054b6cca5f2de64fa1d04f4fa00c9
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="data-mining-query-task"></a>データ マイニング クエリ タスク
  データ マイニング クエリ タスクは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]に構築されたデータ マイニング モデルに基づいて、予測クエリを実行します。 予測クエリは、マイニング モデルを使用して新しいデータの予測を作成します。 たとえば、予測クエリにより、夏季のヨット販売数を予測したり、ヨットを購入する可能性の高い顧客の一覧を生成できます。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では、データ定義言語 (DDL) ステートメントの実行や分析オブジェクトの処理など、ビジネス インテリジェンス操作を実行するその他のタスクが用意されています。  
  
 その他のビジネス インテリジェンス タスクの詳細については、次のトピックのいずれかを参照してください。  
  
-   [Analysis Services DDL 実行タスク](../../integration-services/control-flow/analysis-services-execute-ddl-task.md)  
  
-   [Analysis Services 処理タスク](../../integration-services/control-flow/analysis-services-processing-task.md)  
  
## <a name="prediction-queries"></a>予測クエリ  
 予測クエリは、データ マイニング拡張機能 (DMX) ステートメントです。 DMX 言語は、マイニング モデルでの作業をサポートするための SQL 言語の拡張機能です。 DMX 言語の使用方法の詳細については、「[データ マイニング拡張機能 &#40;DMX&#41; リファレンス](../../dmx/data-mining-extensions-dmx-reference.md)」を参照してください。  
  
 このタスクは、同じマイニング構造で構築された複数のマイニング モデルに対してクエリを実行できます。 マイニング モデルは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が提供するデータ マイニング アルゴリズムのいずれかを使用して構築されます。 データ マイニング クエリ タスクが参照するマイニング構造には、異なるアルゴリズムを使用して構築された複数のマイニング モデルを含めることができます。 詳細については、「[マイニング構造 &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)」および「[データ マイニング アルゴリズム &#40;Analysis Services - データ マイニング&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)」を参照してください。  
  
 データ マイニング クエリ タスクが実行する予測クエリは、単一行または 1 つのデータセットを結果として返します。 単一行を返すクエリは、単一クエリと呼ばれます。たとえば、夏季のヨット販売数を予想するクエリは、1 つの数値を返します。 単一行を返す予測クエリの詳細については、「 [データ マイニング クエリ ツール](../../analysis-services/data-mining/data-mining-query-tools.md)」を参照してください。  
  
 クエリ結果は、テーブルに保存されます。 データ マイニング クエリ タスクで指定された名前のテーブルが既に存在している場合、タスクで同じ名前の末尾に番号を追加して新しいテーブルを作成することも、テーブルの内容を上書きすることもできます。  
  
 結果に入れ子が含まれる場合は、フラット化された後に保存されます。 結果をフラット化すると、入れ子の結果セットはテーブルに変更されます。 たとえば、 **Customer** 列に **Product** 列が入れ子になっている、入れ子の結果をフラット化すると、 **Customer** 列に行が追加され、顧客ごとの製品が含まれるテーブルが作成されます。 たとえば、3 つの異なる製品を購入した顧客は、3 行のテーブルになります。つまり、顧客は各行で繰り返され、行ごとに異なる製品が含まれます。 FLATTENED キーワードを省略すると、テーブルには、**Customer** 列と各顧客につき 1 行のみが含まれます。 詳細については、「[SELECT &#40;DMX&#41;](../../dmx/select-dmx.md)」を参照してください。  
  
## <a name="configuration-of-the-data-mining-query-task"></a>データ マイニング クエリ タスクの構成  
 データ マイニング クエリ タスクには 2 つの接続が必要です。 1 つ目の接続は [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 接続マネージャーで、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンス、またはマイニング構造とマイニング モデルを含む [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトのいずれかに接続します。 2 つ目の接続は OLE DB 接続マネージャーで、タスクが書き込むテーブルを含む [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続します。 詳細については、「 [Analysis Services 接続マネージャー](../../integration-services/connection-manager/analysis-services-connection-manager.md) 」および「 [OLE DB 接続マネージャー](../../integration-services/connection-manager/ole-db-connection-manager.md)」を参照してください。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[データ マイニング クエリ タスク エディター] &#40;[マイニング モデル] タブ&#41;](../../integration-services/control-flow/data-mining-query-task-editor-mining-model-tab.md)  
  
-   [[データ マイニング クエリ タスク エディター] &#40;[クエリ] タブ&#41;](../../integration-services/control-flow/data-mining-query-task-editor-query-tab.md)  
  
-   [[データ マイニング クエリ タスク エディター] &#40;[出力] タブ&#41;](../../integration-services/control-flow/data-mining-query-task-editor-output-tab.md)  
  
> [!NOTE]  
>  [データ マイニング クエリ変換エディター] には、[式] ページがありません。 代わりに **[プロパティ]** ウィンドウを使用して、データ マイニング クエリ タスクのプロパティのプロパティ式を作成、管理するツールにアクセスできます。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。  
  
-   [タスクまたはコンテナーのプロパティを設定する](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
## <a name="programmatic-configuration-of-data-mining-query-task"></a>プログラムによるデータ マイニング クエリ タスクの構成  
 プログラムによってこれらのプロパティを設定する方法の詳細については、次のトピックのいずれかを参照してください。  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.DMQueryTask.DMQueryTask>  
  
  
