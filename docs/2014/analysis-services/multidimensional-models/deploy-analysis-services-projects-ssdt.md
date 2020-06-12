---
title: Analysis Services プロジェクトの配置 (SSDT) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- deploy [Analysis Services]
- projects [Analysis Services], deploying
- Business Intelligence Development Studio, deploying projects [Analysis Services]
ms.assetid: 29490a5b-1573-4a35-9277-10c6a6e4ef0e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5317eea19d088a8d3f9d8bfb86da4e0429d62c3e
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546854"
---
# <a name="deploy-analysis-services-projects-ssdt"></a>Analysis Services プロジェクトの配置 (SSDT)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]プロジェクトを開発するにあたっては、プロジェクトによって定義された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを作成するために、プロジェクトを開発サーバーに配置することが頻繁に行われます。 このことは、キューブ内のセルの参照、ディメンション メンバーの参照、主要業績評価指標 (KPI) 式の検証など、プロジェクトをテストする際に必要となります。  
  
## <a name="deploying-a-project"></a>プロジェクトの配置  
 プロジェクトは個別に配置することも、ソリューション内のプロジェクトをすべてまとめて配置することもできます。 プロジェクトを配置すると、いくつかの処理が連続して行われます。 まず、プロジェクトが構築されます。 この段階では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースとそれを構成するオブジェクトを定義した出力ファイルが作成されます。 次に、配置先サーバーが検証されます。 最後に、配置先データベースとそのオブジェクトが配置先サーバーで作成されます。 配置が行われると、プロジェクトのコンテンツが前の展開時にプロジェクトによって作成されたものでない限り、配置エンジンによって既存のデータベースがこれらのオブジェクトで完全に置き換えられます。  
  
 初期デプロイの後、\ obj フォルダーに IncrementalSnapshot.xml ファイルが生成され \<Project Name> ます。 このファイルは、配置先サーバーのデータベースまたはそのオブジェクトがプロジェクトの外部で変更されたかどうかを判断するために使用されます。 変更されている場合は、配置先データベースのすべてのオブジェクトを上書きするように求めるメッセージが表示されます。 すべての変更がプロジェクト内で行われたものであり、プロジェクトが増分配置用に構成されている場合は、変更内容だけが配置先サーバーに配置されます。  
  
 プロジェクトの配置に使用される配置プロパティは、プロジェクト構成とそれに関連付けられた設定によって決められます。 共有プロジェクトの場合、各開発者は独自の構成とプロジェクト構成オプションを使用できます。 たとえば、各開発者が別々のテスト サーバーを指定することによって、他の開発者から分離された環境で作業することができます。  
  
## <a name="see-also"></a>参照  
 [Analysis Services プロジェクトの作成 (SSDT)](create-an-analysis-services-project-ssdt.md)  
  
  
