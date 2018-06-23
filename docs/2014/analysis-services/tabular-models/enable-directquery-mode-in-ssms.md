---
title: メモリ内またはテーブル モデル データベースの DirectQuery アクセスの構成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5d439a9-5be1-4145-90e8-90777d80e98b
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c91dd8529fa6ddfb111ebb87cb84d87a55d3a709
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176483"
---
# <a name="configure-in-memory-or-directquery-access-for-a-tabular-model-database"></a>テーブル モデルのデータベースの In-Memory または DirectQuery アクセスの構成
  このトピックでは、既に配置されたテーブル モデルの接続プロパティを変更し、モデルを直接クエリ モードで使用できるようにする方法について説明します。  
  
 これらのプロパティ、および最も一般的なシナリオの構成に関する詳細については、次を参照してください。 [DirectQuery の配置シナリオ&#40;SSAS 表形式&#41;](../directquery-deployment-scenarios-ssas-tabular.md)です。  
  
## <a name="requirements"></a>要件  
 テーブル モデルで直接クエリ モードを使用できるようにする操作は、複数の手順から成るプロセスです。 次の手順が必要です。  
  
1.  直接クエリ モードで検証エラーが発生するような機能がモデルにないことを確認します。  
  
2.  直接クエリをサポートするように、モデルのストレージ モードを変更します。  
  
3.  ハイブリッド モードと純粋な直接クエリ モードの両方のクエリをサポートするモードでモデルを配置します。  
  
4.  配置されたデータベースの接続文字列を、直接クエリ モードをサポートするように編集します。  
  
 このトピックは、モデルが既に作成および検証済みで、[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] などのクライアントからの直接クエリ アクセスの有効化だけが必要であることを前提としています。  
  
## <a name="procedure"></a>手順  
  
#### <a name="change-the-connection-string-properties-of-the-model"></a>モデルの接続文字列プロパティの変更  
  
1.  SQLServer Management Studio で、モデルを配置するインスタンスを開きます。  
  
2.  オブジェクト エクスプ ローラーでは、モデル データベースの名前を右クリックして**プロパティ**です。  
  
3.  プロパティを探します**DirectQueryMode**です。 リレーショナル データ ソースを使用できるようにするには、このプロパティを次のいずれかの値に設定する必要があります。  
  
    -   **DirectQuery**  
  
    -   **InMemoryWithDirectQuery**  
  
    -   **DirectQueryWithInMemory**  
  
  