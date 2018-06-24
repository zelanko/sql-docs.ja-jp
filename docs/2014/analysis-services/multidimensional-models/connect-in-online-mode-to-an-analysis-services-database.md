---
title: Analysis Services データベースをオンライン モードで接続 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Analysis Services, connecting
ms.assetid: 33041234-7106-404f-a289-8e904f32aff2
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 4233f9d50cb64bb3827e4dec49251e382ca3c4b3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076325"
---
# <a name="connect-in-online-mode-to-an-analysis-services-database"></a>Analysis Services データベースへのオンライン モードでの接続
  既存の [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに直接接続すると、そのデータベース内のオブジェクトを直接変更できます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに直接接続すると、オブジェクトに対する変更処理が直ちに行われ、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトは [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]内に作成されません。  
  
### <a name="to-connect-directly-to-an-analysis-services-database-by-using-sql-server-data-tools"></a>SQL Server データ ツールを使用して Analysis Services データベースに直接接続するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]を開きます。  
  
2.  **[ファイル]** メニューの **[開く]** をポイントし、 **[Analysis Services データベース]** をクリックします。  
  
3.  **[既存のデータベースに接続する]** を選択します。  
  
4.  サーバー名とデータベース名を指定します。  
  
     データベース名は直接入力することも、サーバーをクエリして、サーバー上の既存のデータベースを表示してから選択することもできます。  
  
5.  **[OK]** をクリックします。  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース内のオブジェクトを直接編集できるようになりました。  
  
## <a name="see-also"></a>参照  
 [Analysis Services 操作プロジェクトおよびデータベース開発フェーズ](work-with-analysis-services-projects-and-databases-in-development.md)   
 [マルチ ディメンションを作成する SQL Server データ ツールの使用をモデル化&#40;SSDT&#41;](creating-multidimensional-models-using-sql-server-data-tools-ssdt.md)  
  
  