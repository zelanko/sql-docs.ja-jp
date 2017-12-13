---
title: "ストアド プロシージャの設計 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- stored procedures [Analysis Services], designing
- dependent assemblies [Analysis Services]
- assemblies [Analysis Services]
ms.assetid: af4e7bd5-041b-4a40-9942-0ef6a3af46c6
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4fa8e3b4bf7a5fcd7817a662a5e4c4d6b5db59cc
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="designing-stored-procedures"></a>ストアド プロシージャのデザイン
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]管理の両方のオブジェクト モデルで分析管理オブジェクト (AMO) とクライアント指向のオブジェクト モデル[!INCLUDE[msCoName](../../includes/msconame-md.md)]ActiveX® Data Objects (Multidimensional) (ADO MD) はストアド プロシージャで使用できます。  
  
 ストアド プロシージャを呼び出すには、多次元式 (MDX) レベルで表示できるスコープ内 (サーバーまたはデータベース) に存在する必要があります。 ただし、ストアド プロシージャを呼び出した後、そのスコープがその親のアクションに制限されることはありません。 ストアド プロシージャは、サーバー上のどこでも変更を行うことができ、そのストアド プロシージャを呼び出すユーザー プロセスのセキュリティ制限と、そのストアド プロシージャが実行されるトランザクションの制限のみを受けます。  
  
 サーバー スコープ プロシージャは、サーバー上のすべてのコンテキストで使用できます。 データベース スコープ ストアド プロシージャは、そのプロシージャが定義されているデータベースのデータベース コンテキストのみで表示されます。  
  
 他のすべての MDX 関数と同様に、ストアド プロシージャは MDX セッションを続行する前に解決する必要があります。ストアド プロシージャでは、実行中に MDX セッションがロックされるためです。 ユーザーの操作があるまで MDX セッションを一時停止しておく特別な理由がある場合を除き、ユーザーの操作 (ダイアログ ボックスなど) は推奨されません。  
  
## <a name="dependent-assemblies"></a>依存アセンブリ  
 共通言語ランタイム (CLR) で検索できるようにするには、すべての依存アセンブリを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに読み込む必要があります [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではメイン アセンブリと同じフォルダーに依存アセンブリが保存されるので、そのようなアセンブリ内の関数に対するすべての関数参照は CLR によって自動的に解決されます。  
  
## <a name="see-also"></a>参照  
 [多次元モデルのアセンブリの管理](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [ストアド プロシージャの定義](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
