---
title: AMO クラスの概要 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Management Objects]
- classes [AMO]
ms.assetid: d3c066bc-f812-4d53-9e96-9e306f2fc580
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3e525dec6972d68ce8695bc7fab6aa6ab177e0a1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173591"
---
# <a name="introducing-amo-classes"></a>AMO クラスの概要
  分析管理オブジェクト (AMO) のインスタンスを管理するためのクラスのライブラリは、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]クライアント アプリケーションからです。 AMO クラスは、データベース、ディメンション、キューブ、マイニング構造およびマイニング モデル、ロールおよび権限、例外などの [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] オブジェクトを管理するために使用されるクラスです。  
  
 次の図は、このトピックで説明するクラスの関係を示しています。  
  
 ![クラスは、AMO の概念説明のトピックで確認](../../../analysis-services/dev-guide/media/amo-reviewedclasses.gif "クラスは、AMO の概念トピックのレビュー")  
  
 AMO ライブラリは、特定のタスクの実行に使用される、論理的に関連したオブジェクトのグループとして考えることができます。 AMO クラスは次の方法で分類できます。 このセクションの内容は次のとおりです。  
  
|トピック|説明|  
|-----------|-----------------|  
|[AMO 基礎クラス](amo-fundamental-classes.md)|他のクラスのセットを操作するために必要なクラスについて説明します。|  
|[AMO OLAP クラス](amo-olap-classes.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] の OLAP オブジェクトの管理を可能にするクラスについて説明します。|  
|[AMO データ マイニング クラス](amo-data-mining-classes.md)|[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のデータ マイニング オブジェクトの管理を可能にするクラスについて説明します。|  
|[AMO セキュリティ クラス](amo-security-classes.md)|他のオブジェクトへのアクセスの制御やセキュリティのメンテナンスを可能にするクラスについて説明します。|  
|[AMO のその他のクラスとメソッド](amo-other-classes-and-methods.md)|OLAP またはデータ マイニングの管理者の日常業務の遂行に役立つクラスとメソッドについて説明します。|  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices>   
 [論理アーキテクチャ&#40;Analysis Services - 多次元データ&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [データベース オブジェクト&#40;Analysis Services - 多次元データ&#41;](../olap-logical/database-objects-analysis-services-multidimensional-data.md)   
 [分析管理オブジェクトを使用した開発&#40;AMO&#41;](developing-with-analysis-management-objects-amo.md)  
  
  