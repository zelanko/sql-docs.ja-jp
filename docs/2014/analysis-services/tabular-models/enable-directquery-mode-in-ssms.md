---
title: メモリ内またはテーブル モデル データベース用 DirectQuery アクセスの構成 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a5d439a9-5be1-4145-90e8-90777d80e98b
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ee6b2f55d1b630b489f65e16a39cb602d5fd5a6d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37243442"
---
# <a name="configure-in-memory-or-directquery-access-for-a-tabular-model-database"></a>テーブル モデルのデータベースの In-Memory または DirectQuery アクセスの構成
  このトピックでは、既に配置されたテーブル モデルの接続プロパティを変更し、モデルを直接クエリ モードで使用できるようにする方法について説明します。  
  
 これらのプロパティ、および最も一般的なシナリオの構成に関する詳細については、次を参照してください。 [DirectQuery の配置シナリオ&#40;SSAS 表形式&#41;](../directquery-deployment-scenarios-ssas-tabular.md)します。  
  
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
  
2.  オブジェクト エクスプ ローラーで、モデル データベースの名前を右クリックして**プロパティ**します。  
  
3.  プロパティを探します**DirectQueryMode**します。 リレーショナル データ ソースを使用できるようにするには、このプロパティを次のいずれかの値に設定する必要があります。  
  
    -   **DirectQuery**  
  
    -   **InMemoryWithDirectQuery**  
  
    -   **DirectQueryWithInMemory**  
  
  
