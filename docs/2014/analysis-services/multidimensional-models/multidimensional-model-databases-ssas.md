---
title: 多次元モデルデータベース (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [Analysis Services], databases
- SQL Server Analysis Services, databases
- SSAS, databases
- Analysis Services, databases
- databases [Analysis Services], designing
- Business Intelligence Development Studio, databases [Analysis Services]
- databases [Analysis Services]
ms.assetid: 78b2f22a-b7bd-4a2b-b6fc-0bff4d2b3168
author: minewiskan
ms.author: owend
ms.openlocfilehash: 966403d15843d7b2b572581d930f1c37416ddbe5
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546054"
---
# <a name="multidimensional-model-databases-ssas"></a>多次元モデル データベース (SSAS)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースは、データ ソース、データ ソース ビュー、キューブ、ディメンション、およびロールのコレクションです。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースには、データ マイニング用の構造、およびユーザー定義の関数をデータベースに追加するために使用されるカスタム アセンブリをオプションで含めることができます。  
  
 キューブは、Analysis Services における基本的なクエリ オブジェクトです。 クライアント アプリケーション経由で Analysis Services データベースに接続する場合は、そのデータベース内のキューブに接続します。 ディメンション、アセンブリ、ロール、またはマイニング構造を複数のコンテキストにわたって再利用している場合、データベースには複数のキューブが含まれていることがあります。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの作成と変更は、プログラムを使用して行うか、次のいずれかの対話的な方法で行うことができます。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] から [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] プロジェクトを、指定された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに配置します。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースは、その名前が付いたデータベースがそのインスタンス内に存在しない場合にこのプロセスによって作成されます。さらに、新しく作成されたデータベース内に、指定されたオブジェクトがインスタンス化されます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]データベースを使用する場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトのオブジェクトに加えた変更は、プロジェクトが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに配置されたときにのみ有効になります。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンス内に空の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベースを作成します。これを行うには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のどちらかを使用します。次に、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用してデータベースに直接接続し、プロジェクト内ではなくこのデータベース内にオブジェクトを作成します。 この方法で [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを使用するときは、オブジェクトに加えた変更は、変更したオブジェクトの保存時に接続しているデータベースで有効になります。  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] では、ソース管理ソフトウェアの統合を使用し、開発者が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクト内で同時に異なるオブジェクトを処理するのをサポートします。 また、開発者は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクト経由ではなく、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースと直接やり取りを行うことができますが、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースのオブジェクトが、配置のために使用された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトと同期しなくなるリスクがあります。 配置後、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]データベースを管理します。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を使用して、パーティションやロールなど、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]データベースに一定の変更を加えることもできます。これにより、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースのオブジェクトが、この配置のために使用された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトと同期しなくなることがあります。  
  
## <a name="related-tasks"></a>Related Tasks  
 [Analysis Services データベースのインポートとデタッチ](attach-and-detach-analysis-services-databases.md)  
  
 [Analysis Services データベースのバックアップと復元](backup-and-restore-of-analysis-services-databases.md)  
  
 [Analysis Services データベースのドキュメントとスクリプトの作成](document-and-script-an-analysis-services-database.md)  
  
 [Analysis Services データベースの変更または削除](modify-or-delete-an-analysis-services-database.md)  
  
 [Analysis Services データベースの移動](move-an-analysis-services-database.md)  
  
 [多次元データベース名の変更 (Analysis Services)](rename-a-multidimensional-database-analysis-services.md)  
  
 [多次元データベースの互換性レベルを設定する &#40;Analysis Services&#41;](compatibility-level-of-a-multidimensional-database-analysis-services.md)  
  
 [多次元データベースのプロパティ設定 (Analysis Services)](set-multidimensional-database-properties-analysis-services.md)  
  
 [Analysis Services データベースの同期](synchronize-analysis-services-databases.md)  
  
 [Analysis Services データベースの ReadOnly モードと ReadWrite モードの切り替え](switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
## <a name="see-also"></a>参照  
 [Analysis Services データベースへのオンラインモードでの接続](connect-in-online-mode-to-an-analysis-services-database.md)   
 [SSDT&#41;&#40;Analysis Services プロジェクトを作成する](create-an-analysis-services-project-ssdt.md)   
 [MDX による多次元データのクエリ](mdx/querying-multidimensional-data-with-mdx.md)  
  
  
