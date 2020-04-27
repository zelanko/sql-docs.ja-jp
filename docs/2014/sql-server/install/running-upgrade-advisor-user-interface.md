---
title: アップグレードアドバイザーの実行 (ユーザーインターフェイス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor Report Viewer
- Upgrade Advisor [SQL Server], running
- launching Upgrade Advisor
- Upgrade Advisor Analysis Wizard
- starting Upgrade Advisor
- SQL Server Upgrade Advisor, running
ms.assetid: 7f47c9b3-88d3-43d6-837e-f157b49a55ac
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5aecaea9bef359ad24aebbd20dd5e9547497043b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66092447"
---
# <a name="running-upgrade-advisor-user-interface"></a>アップグレード アドバイザーの実行 (ユーザー インターフェイス)
  アップグレード アドバイザーを実行すると、アップグレードの計画時にローカルまたはリモートのコンポーネントを分析できます。 アップグレードアドバイザーによって、分析されるコンポーネントとインスタンスごとにレポートが作成されます。  
  
> [!IMPORTANT]  
>  アップグレード アドバイザーは [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のリモート インスタンスを分析しません。 [!INCLUDE[ssRS](../../includes/ssrs.md)] のインスタンスを分析するには、[!INCLUDE[ssRS](../../includes/ssrs.md)] がインストールされているコンピューターにアップグレード アドバイザーをインストールしておく必要があります。  
>   
>  Integration Services を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]分析するには[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 、がインストールさ[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]れ、同じコンピューターにインストールされている必要があります。  
  
## <a name="running-the-upgrade-advisor-analysis-wizard"></a>アップグレードアドバイザー分析ウィザードの実行  
 アップグレード アドバイザー分析ウィザードの実行には、次の 6 つの手順があります。  
  
1.  アップグレード アドバイザーの開始ページからウィザードを起動します。  
  
2.  分析するサーバーとコンポーネントを特定します。  
  
3.  認証情報を取得します。  
  
4.  コンポーネントの種類に基づいて追加パラメーターを取得します。  
  
5.  選択したコンポーネントを分析します。  
  
6.  アップグレードの問題に関するレポートを生成します。  
  
 アップグレードアドバイザー分析ウィザードの詳細については、「[アップグレードアドバイザー分析ウィザードを実行する方法](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)」を参照してください。  
  
 各手順に必要な特定の情報については、「 [Upgrade Advisor User Interface Reference](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)」を参照してください。  
  
## <a name="running-the-upgrade-advisor-report-viewer"></a>アップグレードアドバイザーレポートビューアーの実行  
 アップグレードアドバイザー分析ウィザードで生成されたレポートを表示するには、アップグレードアドバイザーレポートビューアーを使用します。 レポートを読み込んだら、次の条件でレポートのコンポーネントをフィルター選択できます。  
  
-   すべての問題  
  
-   アップグレードに関するすべての問題  
  
-   アップグレード前の問題  
  
-   移行に関するすべての問題  
  
-   解決した問題  
  
-   未解決の問題  
  
 レポート ビューアーを使用するための操作手順については、次のトピックを参照してください。  
  
-   [アップグレード アドバイザーのレポートを表示する方法](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md)  
  
-   [レポートに表示する問題を選択する方法](../../../2014/sql-server/install/how-to-filter-reports.md)  
  
-   [レポートをエクスポートする方法](../../../2014/sql-server/install/how-to-export-reports.md)  
  
## <a name="see-also"></a>参照  
 [アップグレードアドバイザー分析ウィザードを実行する方法](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)   
 [アップグレードアドバイザーのユーザーインターフェイスリファレンス](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)   
 [アップグレードに関する問題の解決](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
