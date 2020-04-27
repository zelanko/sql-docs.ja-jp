---
title: 'レッスン 5: SSIS を使用したクレンジングと照合の自動化 |Microsoft Docs'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f068d4db-2d56-41b1-bed2-0cffa3ca411d
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: ec6f347cdbc6d14e8f621466a1708b8ee9fe7d36
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "65489752"
---
# <a name="lesson-5-automating-the-cleansing-and-matching-using-ssis"></a>レッスン 5: SSIS を使用してクレンジングと照合を自動化する
  レッスン1では、サプライヤーナレッジベースを構築し、それを使用してレッスン2でデータをクレンジングし、ツール**DQS クライアント**を使用してレッスン3でデータを照合しました。 実際のシナリオでは、dqs**クライアント**ツールを使用しなくても、dqs がサポートしていないソースからデータを取得したり、クレンジングと照合プロセスを自動化したりすることが必要になる場合があります。 SQL Server Integration Services (SSIS) には、さまざまな異種ソースからのデータを統合するために使用できるコンポーネントと、dqs によって公開されているクレンジング機能を呼び出すための**[Dqs クレンジング変換](https://msdn.microsoft.com/library/ee677619.aspx)** コンポーネントがあります。 現在、DQS では、SSIS で使用する照合機能が公開されていませんが、**[あいまいグループ化変換](../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md)** を使用してデータ内の重複部分を識別できます。  
  
 データを MDS にアップロードするには、**エンティティベースのステージング機能**を使用します。 MDS でエンティティを作成する場合、対応するステージング テーブルとストアド プロシージャが自動的に作成されます。 たとえば、Supplier エンティティを作成したときに、 **stg. supplier_Leaf**テーブルと**stg. udp_Supplier_Leaf**ストアドプロシージャが自動的に作成されました。 ステージング テーブルとプロシージャを使用して、エンティティ メンバーを作成、更新、および削除できます。 このレッスンでは、Supplier エンティティの新しいエンティティ メンバーを作成します。 MDS サーバーにデータを読み込むには、最初に SSIS パッケージでデータをステージング テーブル stg.supplier_Leaf に読み込み、関連するストアド プロシージャ stg.udp_Supplier_Leaf をトリガーします。 詳細については、「[データのインポート](../master-data-services/overview-importing-data-from-tables-master-data-services.md)」を参照してください。  
  
 このレッスンでは、次のタスクを行います。  
  
1.  MDS で仕入先データを削除します (前の 4 レッスンを終了している場合)。 このレッスンで作成する SSIS パッケージにより、MDS に自動的にデータがアップロードされます。 前の手順では、DQS クライアントを使用して MDS サーバーに手動でクレンジングした照合仕入先データをアップロードしました。  
  
2.  他のアプリケーションのエンティティでデータを公開するために、Supplier エンティティでサブスクリプション ビューを作成します。 この操作により、SQL ビューを作成します。このビューは SQL Server Management Studio を使用して検証します。 このバージョンのチュートリアルでは、このビューを使用しません。  
  
3.  **SQL Server Data Tools**を使用して、SSIS プロジェクトを作成して実行します。 このプロジェクトでは、**データクレンジング**変換を使用して、DQS サーバーにクレンジング要求を送信します。 DQS では、照合機能がまだ公開されていないため、**あいまいグループ化**変換を使用して重複を識別します。  
  
4.  マスター データ マネージャーを使用して、MDS にデータが作成されていることを確認します。  
  
5.  SSIS パッケージによって作成された DQS クレンジング プロジェクトの結果を確認し、必要に応じてインタラクティブなクレンジングを実行して、ナレッジ ベースを拡充します。  
  
## <a name="next-step"></a>次の手順  
 [タスク 1 &#40;前提条件&#41;: MDS での仕入先データの削除](../../2014/tutorials/task-1-prerequisite-removing-supplier-data-in-mds.md)  
  
  
