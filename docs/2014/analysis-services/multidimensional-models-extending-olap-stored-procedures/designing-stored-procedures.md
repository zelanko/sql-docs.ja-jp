---
title: ストアドプロシージャの設計 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [Analysis Services], designing
- dependent assemblies [Analysis Services]
- assemblies [Analysis Services]
ms.assetid: af4e7bd5-041b-4a40-9942-0ef6a3af46c6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 42b33873d6bdf28f7f702bcf186d681f57d6024d
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545365"
---
# <a name="designing-stored-procedures"></a>ストアド プロシージャのデザイン
  ストアド プロシージャでは、管理オブジェクト モデルである分析管理オブジェクト (AMO) とクライアント指向のオブジェクト モデルである [!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX&#xAE; Data Objects (Multidimensional) (ADO MD) の両方を使用できます。  
  
 ストアド プロシージャを呼び出すには、多次元式 (MDX) レベルで表示できるスコープ内 (サーバーまたはデータベース) に存在する必要があります。 ただし、ストアド プロシージャを呼び出した後、そのスコープがその親のアクションに制限されることはありません。 ストアド プロシージャは、サーバー上のどこでも変更を行うことができ、そのストアド プロシージャを呼び出すユーザー プロセスのセキュリティ制限と、そのストアド プロシージャが実行されるトランザクションの制限のみを受けます。  
  
 サーバー スコープ プロシージャは、サーバー上のすべてのコンテキストで使用できます。 データベース スコープ ストアド プロシージャは、そのプロシージャが定義されているデータベースのデータベース コンテキストのみで表示されます。  
  
 他のすべての MDX 関数と同様に、ストアド プロシージャは MDX セッションを続行する前に解決する必要があります。ストアド プロシージャでは、実行中に MDX セッションがロックされるためです。 ユーザーの操作があるまで MDX セッションを一時停止しておく特別な理由がある場合を除き、ユーザーの操作 (ダイアログ ボックスなど) は推奨されません。  
  
## <a name="dependent-assemblies"></a>依存アセンブリ  
 共通言語ランタイム (CLR) で検索できるようにするには、すべての依存アセンブリを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに読み込む必要があります [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではメイン アセンブリと同じフォルダーに依存アセンブリが保存されるので、そのようなアセンブリ内の関数に対するすべての関数参照は CLR によって自動的に解決されます。  
  
## <a name="see-also"></a>参照  
 [多次元モデルのアセンブリの管理](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [ストアド プロシージャの定義](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
