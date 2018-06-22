---
title: アップグレード アドバイザー (ユーザー インターフェイス) を実行している |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Upgrade Advisor Report Viewer
- Upgrade Advisor [SQL Server], running
- launching Upgrade Advisor
- Upgrade Advisor Analysis Wizard
- starting Upgrade Advisor
- SQL Server Upgrade Advisor, running
ms.assetid: 7f47c9b3-88d3-43d6-837e-f157b49a55ac
caps.latest.revision: 40
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 36a31e74e95b966137df96f5e3f2ab05fa7a991f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070873"
---
# <a name="running-upgrade-advisor-user-interface"></a>アップグレード アドバイザーの実行 (ユーザー インターフェイス)
  アップグレード アドバイザーを実行すると、アップグレードの計画時にローカルまたはリモートのコンポーネントを分析できます。 アップグレード アドバイザーでは、各コンポーネントとは、分析するインスタンスのレポートを生成します。  
  
> [!IMPORTANT]  
>  アップグレード アドバイザーは [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のリモート インスタンスを分析しません。 [!INCLUDE[ssRS](../../includes/ssrs-md.md)] のインスタンスを分析するには、[!INCLUDE[ssRS](../../includes/ssrs-md.md)] がインストールされているコンピューターにアップグレード アドバイザーをインストールしておく必要があります。  
>   
>  分析する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Integration Services, が必要、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]インストールされていると[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]同じコンピューターにインストールします。  
  
## <a name="running-the-upgrade-advisor-analysis-wizard"></a>アップグレード アドバイザー分析ウィザードを実行します。  
 アップグレード アドバイザー分析ウィザードの実行には、次の 6 つの手順があります。  
  
1.  アップグレード アドバイザーの開始ページからウィザードを起動します。  
  
2.  分析するサーバーとコンポーネントを特定します。  
  
3.  認証情報を取得します。  
  
4.  コンポーネントの種類に基づいて追加パラメーターを取得します。  
  
5.  選択したコンポーネントを分析します。  
  
6.  アップグレードの問題に関するレポートを生成します。  
  
 アップグレード アドバイザー分析ウィザードの詳細については、次を参照してください。[する方法: アップグレード アドバイザー分析ウィザードを実行](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)です。  
  
 各ステップに必要な特定の情報を参照してください。[アップグレード アドバイザーのユーザー インターフェイス リファレンス](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)です。  
  
## <a name="running-the-upgrade-advisor-report-viewer"></a>アップグレード アドバイザー レポート ビューアーを実行します。  
 アップグレード アドバイザー分析ウィザードによって生成されたレポートを表示するのにには、アップグレード アドバイザー レポート ビューアーを使用します。 レポートを読み込んだら、次の条件でレポートのコンポーネントをフィルター選択できます。  
  
-   すべての問題  
  
-   アップグレードに関するすべての問題  
  
-   アップグレード前の問題  
  
-   移行に関するすべての問題  
  
-   解決した問題  
  
-   未解決の問題  
  
 レポート ビューアーを使用するための操作手順については、次のトピックを参照してください。  
  
-   [方法: アップグレード アドバイザーのレポートの表示](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md)  
  
-   [方法: レポートのフィルター処理](../../../2014/sql-server/install/how-to-filter-reports.md)  
  
-   [方法: レポートのエクスポート](../../../2014/sql-server/install/how-to-export-reports.md)  
  
## <a name="see-also"></a>参照  
 [方法: アップグレード アドバイザー分析ウィザードを実行](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)   
 [アップグレード アドバイザーのユーザー インターフェイス リファレンス](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)   
 [アップグレードの問題を解決します。](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  