---
title: 多次元モデル データベース (SSAS) |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1ec839c9638b3baf79cba0148cc932ead7820f7b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68208684"
---
# <a name="multidimensional-model-databases-ssas"></a>多次元モデル データベース (SSAS)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースは、データ ソース、データ ソース ビュー、キューブ、ディメンション、およびロールのコレクションです。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースには、データ マイニング用の構造、およびユーザー定義の関数をデータベースに追加するために使用されるカスタム アセンブリをオプションで含めることができます。  
  
 キューブは、Analysis Services における基本的なクエリ オブジェクトです。 クライアント アプリケーション経由で Analysis Services データベースに接続する場合は、そのデータベース内のキューブに接続します。 ディメンション、アセンブリ、ロール、またはマイニング構造を複数のコンテキストにわたって再利用している場合、データベースには複数のキューブが含まれていることがあります。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの作成と変更は、プログラムを使用して行うか、次のいずれかの対話的な方法で行うことができます。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] から [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] プロジェクトを、指定された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに配置します。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースは、その名前が付いたデータベースがそのインスタンス内に存在しない場合にこのプロセスによって作成されます。さらに、新しく作成されたデータベース内に、指定されたオブジェクトがインスタンス化されます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]データベースを使用する場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトのオブジェクトに加えた変更は、プロジェクトが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに配置されたときにのみ有効になります。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンス内に空の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベースを作成します。これを行うには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のどちらかを使用します。次に、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用してデータベースに直接接続し、プロジェクト内ではなくこのデータベース内にオブジェクトを作成します。 この方法で [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを使用するときは、オブジェクトに加えた変更は、変更したオブジェクトの保存時に接続しているデータベースで有効になります。  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] では、ソース管理ソフトウェアの統合を使用し、開発者が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクト内で同時に異なるオブジェクトを処理するのをサポートします。 また、開発者は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクト経由ではなく、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースと直接やり取りを行うことができますが、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースのオブジェクトが、配置のために使用された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトと同期しなくなるリスクがあります。 配置後、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]データベースを管理します。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を使用して、パーティションやロールなど、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]データベースに一定の変更を加えることもできます。これにより、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースのオブジェクトが、この配置のために使用された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトと同期しなくなることがあります。  
  
## <a name="related-tasks"></a>Related Tasks  
 [Analysis Services データベースのインポートとデタッチ](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
 [Analysis Services データベースのバックアップと復元](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
 [Analysis Services データベースのドキュメントとスクリプトの作成](../../analysis-services/multidimensional-models/document-and-script-an-analysis-services-database.md)  
  
 [Analysis Services データベースの変更または削除](../../analysis-services/multidimensional-models/modify-or-delete-an-analysis-services-database.md)  
  
 [Analysis Services データベースの移動](../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)  
  
 [多次元データベース名の変更 (Analysis Services)](../../analysis-services/multidimensional-models/rename-a-multidimensional-database-analysis-services.md)  
  
 [多次元データベースの互換性レベル (Analysis Services)](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md)  
  
 [多次元データベースのプロパティ設定 (Analysis Services)](../../analysis-services/multidimensional-models/set-multidimensional-database-properties-analysis-services.md)  
  
 [Analysis Services データベースの同期](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)  
  
 [Analysis Services データベースの ReadOnly モードと ReadWrite モードの切り替え](../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
## <a name="see-also"></a>関連項目  
 [Analysis Services データベースへのオンライン モードでの接続](../../analysis-services/multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md)   
 [Analysis Services プロジェクトの作成 (SSDT)](../../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md)   
 [MDX による多次元データのクエリ](../../analysis-services/multidimensional-models/mdx/querying-multidimensional-data-with-mdx.md)  
  
  
