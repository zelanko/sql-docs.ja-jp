---
title: 'レッスン 5: 自動化クレンジングと照合を使用して SSIS |Microsoft ドキュメント'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f068d4db-2d56-41b1-bed2-0cffa3ca411d
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 00dff9ac204e5e1b86feafc51da643222bce1758
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072460"
---
# <a name="lesson-5-automating-the-cleansing-and-matching-using-ssis"></a>レッスン 5: SSIS を使用してクレンジングと照合を自動化する
  レッスン 1 で Suppliers ナレッジ ベースを構築およびレッスン 2 でのデータをクレンジングし、ツールを使用して、レッスン 3 でのデータと一致するために使用**DQS クライアント**です。 実際のシナリオを使用しなくても、DQS がサポートしていないか、クレンジングを自動化するソースと一致するプロセスからデータをプルする必要があります、 **DQS クライアント**ツールです。 SQL Server Integration Services (SSIS) が使用できるさまざまな異種ソースからデータを統合するコンポーネントと**[ハイパーリンク"http://msdn.microsoft.com/library/ee677619.aspx"\t"_blank"DQS クレンジング変換](http://msdn.microsoft.com/library/ee677619.aspx)** DQS によって公開されるクレンジング機能を起動するコンポーネントです。 現時点では、DQS は、SSIS の照合機能を公開しませんが、使用することができます、 **[あいまいグループ化変換](http://msdn.microsoft.com/library/ms141764.aspx)** データの重複を識別します。  
  
 使用してデータを MDS にアップロードできる、**エンティティ ベースのステージング機能**します。 MDS でエンティティを作成する場合、対応するステージング テーブルとストアド プロシージャが自動的に作成されます。 たとえば、Supplier エンティティを作成したときに、 **stg.supplier_Leaf**テーブルおよび**stg.udp_Supplier_Leaf**ストアド プロシージャが自動的に作成します。 ステージング テーブルとプロシージャを使用して、エンティティ メンバーを作成、更新、および削除できます。 このレッスンでは、Supplier エンティティの新しいエンティティ メンバーを作成します。 MDS サーバーにデータを読み込むには、最初に SSIS パッケージでデータをステージング テーブル stg.supplier_Leaf に読み込み、関連するストアド プロシージャ stg.udp_Supplier_Leaf をトリガーします。 参照してください[データのインポート](http://msdn.microsoft.com/library/ee633726.aspx)詳細についてはします。  
  
 このレッスンでは、次のタスクを行います。  
  
1.  MDS で仕入先データを削除します (前の 4 レッスンを終了している場合)。 このレッスンで作成する SSIS パッケージにより、MDS に自動的にデータがアップロードされます。 前の手順では、DQS クライアントを使用して MDS サーバーに手動でクレンジングした照合仕入先データをアップロードしました。  
  
2.  他のアプリケーションのエンティティでデータを公開するために、Supplier エンティティでサブスクリプション ビューを作成します。 この操作により、SQL ビューを作成します。このビューは SQL Server Management Studio を使用して検証します。 このバージョンのチュートリアルでは、このビューを使用しません。  
  
3.  作成しを使用して SSIS プロジェクトを実行**SQL Server Data Tools**です。 プロジェクトを使用して**データ クレンジング**DQS サーバーにクレンジング要求を送信する変換です。 DQS は公開しません照合機能、まだ使用するように**あいまいグループ化**重複部分を識別する変換です。  
  
4.  マスター データ マネージャーを使用して、MDS にデータが作成されていることを確認します。  
  
5.  SSIS パッケージによって作成された DQS クレンジング プロジェクトの結果を確認し、必要に応じてインタラクティブなクレンジングを実行して、ナレッジ ベースを拡充します。  
  
## <a name="next-step"></a>次の手順  
 [タスク 1&#40;前提条件となる&#41;: MDS の仕入先データを削除します。](../../2014/tutorials/task-1-prerequisite-removing-supplier-data-in-mds.md)  
  
  