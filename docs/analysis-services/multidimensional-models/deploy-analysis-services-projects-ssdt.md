---
title: "Analysis Services プロジェクト (SSDT) の配置 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploy [Analysis Services]
- projects [Analysis Services], deploying
- Business Intelligence Development Studio, deploying projects [Analysis Services]
ms.assetid: 29490a5b-1573-4a35-9277-10c6a6e4ef0e
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dbfe19ac5da2fee064dd19d06aa1bf7992c3429b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="deploy-analysis-services-projects-ssdt"></a>Analysis Services プロジェクトの配置 (SSDT)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]開発時に、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクト[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]、多くの場合、プロジェクトを配置する開発サーバーを作成するために、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクトで定義されているデータベース。 このことは、キューブ内のセルの参照、ディメンション メンバーの参照、主要業績評価指標 (KPI) 式の検証など、プロジェクトをテストする際に必要となります。  
  
## <a name="deploying-a-project"></a>プロジェクトの配置  
 プロジェクトは個別に配置することも、ソリューション内のプロジェクトをすべてまとめて配置することもできます。 プロジェクトを配置すると、いくつかの処理が連続して行われます。 まず、プロジェクトが構築されます。 この段階では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースとそれを構成するオブジェクトを定義した出力ファイルが作成されます。 次に、配置先サーバーが検証されます。 最後に、配置先データベースとそのオブジェクトが配置先サーバーで作成されます。 配置が行われると、プロジェクトのコンテンツが前の展開時にプロジェクトによって作成されたものでない限り、配置エンジンによって既存のデータベースがこれらのオブジェクトで完全に置き換えられます。  
  
 最初の展開後、IncrementalSnapshot.xml ファイルがで生成された、\<プロジェクト名 > \obj フォルダーです。 このファイルは、配置先サーバーのデータベースまたはそのオブジェクトがプロジェクトの外部で変更されたかどうかを判断するために使用されます。 変更されている場合は、配置先データベースのすべてのオブジェクトを上書きするように求めるメッセージが表示されます。 すべての変更がプロジェクト内で行われたものであり、プロジェクトが増分配置用に構成されている場合は、変更内容だけが配置先サーバーに配置されます。  
  
 プロジェクトの配置に使用される配置プロパティは、プロジェクト構成とそれに関連付けられた設定によって決められます。 共有プロジェクトの場合、各開発者は独自の構成とプロジェクト構成オプションを使用できます。 たとえば、各開発者が別々のテスト サーバーを指定することによって、他の開発者から分離された環境で作業することができます。  
  
## <a name="see-also"></a>参照  
 [Analysis Services プロジェクトの作成 (SSDT)](../../analysis-services/multidimensional-models/create-an-analysis-services-project-ssdt.md)  
  
  
