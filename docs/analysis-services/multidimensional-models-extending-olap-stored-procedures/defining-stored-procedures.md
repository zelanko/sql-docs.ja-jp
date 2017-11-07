---
title: "ストアド プロシージャの定義 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- stored procedures [Analysis Services]
- OLAP [Analysis Services], stored procedures
- external routines [Analysis Services]
- stored procedures [Analysis Services], about stored procedures
ms.assetid: f9c57d91-f60f-4f0e-8f7f-d87f4ba97b7c
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b70d20ea8ad3cc108076261b692129bf72ccb6ef
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="defining-stored-procedures"></a>ストアド プロシージャの定義
  外部ルーチンを呼び出すストアド プロシージャを使用することができます[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。 ストアド プロシージャによって呼び出される外部ルーチンは、C、C++、C#、Visual Basic、Visual Basic .NET などの共通言語ランタイム (CLR) 言語でも書き込むことができます。 ストアド プロシージャを作成すると、他のストアド プロシージャ、計算されるメジャー、クライアント アプリケーションなどの多くのコンテキストから呼び出すことができます。 ストアド プロシージャを使用すると、共通コードを開発し、1 つの場所に格納できるようにすることによって、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの開発および実装が簡単になります。 ストアド プロシージャを使用して、アプリケーションに、MDX のネイティブ機能によって提供されていないビジネス機能を追加できます。  
  
 このセクションでは、ストアド プロシージャの理解、デザイン、および実装に必要な情報を提供します。  
  
|トピック|Description|  
|-----------|-----------------|  
|[ストアド プロシージャの設計](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/designing-stored-procedures.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で使用するアセンブリをデザインする方法を説明します。|  
|[ストアド プロシージャの作成](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/creating-stored-procedures.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のアセンブリを構成する方法を説明します。|  
|[ストアド プロシージャの呼び出し](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/calling-stored-procedures.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でアセンブリを使用する方法の詳細について説明します。|  
|[ストアド プロシージャでクエリのコンテキストにアクセスします。](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/accessing-query-context-in-stored-procedures.md)|スコープ、およびアセンブリを持つコンテキスト情報にアクセスする方法を説明します。|  
|[ストアド プロシージャのセキュリティの設定](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/setting-security-for-stored-procedures.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のアセンブリのセキュリティを構成する方法を説明します。|  
|[ストアド プロシージャのデバッグ](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/debugging-stored-procedures.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のアセンブリをデバッグする方法を説明します。|  
  
## <a name="see-also"></a>参照  
 [多次元モデルのアセンブリの管理](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  

