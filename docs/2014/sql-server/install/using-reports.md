---
title: レポートの使用 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- displaying reports
- overriding reports
- Upgrade Advisor Report Viewer
- reports [Upgrade Advisor], about reports
- formatting reports
- resolved issues [Upgrade Advisor]
- distributing reports [Reporting Services]
- filtering reports [Reporting Services]
- removing report items
- viewing reports
- rerunning analysis
- information issues [Upgrade Advisor]
- deleting report items
- icons [Upgrade Advisor]
- Upgrade Advisor [SQL Server], reports
- sending reports
- blocking issues [Upgrade Advisor]
- sharing reports
- reports [Upgrade Advisor]
- SQL Server Upgrade Advisor, reports
- modifying reports
- distributing reports [Reporting Services], about report distribution
- warnings [Upgrade Advisor]
- analyzing system [Upgrade Advisor], reports
ms.assetid: 4a3cb94a-a7ac-4cec-94c7-db26fcf6d161
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fc3a08e707f6b51059145c69fdee15f78c933135
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66091229"
---
# <a name="using-reports"></a>レポートの使用
  アップグレード アドバイザー分析ウィザードによってサーバー上で分析されたコンポーネントごとまたはインスタンスごとに、個別のレポートが生成されます。 レポートでは、アップグレードに影響する既知の問題の詳細を参照できます。 また、特定された問題に対処するための情報と推奨される操作へのリンクも示します。  
  
> [!NOTE]  
>  アップグレードアドバイザーのレポートビューアーで、既定のレポートディレクトリにレポートが見つからない場合、[**レポートを開く**] リンクを使用して別のディレクトリからレポートを読み込むことができます。  
  
## <a name="viewing-reports"></a>レポートの表示  
 アップグレード アドバイザー レポート ビューアーを使用して、アップグレード アドバイザー レポートを表示します。 レポートを表示するには、アップグレードアドバイザーの開始ページで、[**アップグレードアドバイザーレポートビューアーの起動**] をクリックします。  
  
 サーバーのレポートを読み込んだ後、アップグレード問題を確認するコンポーネントを選択できます。 [**フィルター** ] ボックスからフィルターを適用すると、次のことを確認できます。  
  
-   すべての問題  
  
-   アップグレードに関するすべての問題  
  
-   アップグレード前の問題  
  
-   移行に関するすべての問題  
  
-   解決した問題  
  
-   未解決の問題  
  
 レポートに20件を超える問題がある場合は、問題の一覧の上部または下部にある **[次の 20** ] または [**前の 20** ] をクリックして、問題の次のグループまたは前のグループに移動できます。  
  
 [**レポート**] ボックスの一覧からレポートを選択すると、最大5つのレポートを表示できます。 レポートは、生成日時を示すタイムスタンプ順に一覧表示されます。  
  
## <a name="report-format"></a>レポート形式  
 レポート ビューアーには、レポート内の問題が 3 列で表示されます。 それぞれの問題を折りたたむと、説明が非表示になり、重要な情報だけが表示されます。  
  
 最初の列は、[**重要度**列です。 アイコンは各問題の重要度を示します。移行がブロックされる問題や重要な問題の場合は、赤い円の中に X マークが表示されます。警告および情報を表す場合は、黄色い三角形の中に感嘆符が表示されます。 2番目の列 (**修正する場合**) は、問題を解決する必要がある時期を示します。 レポートは、[**重要度**] 列または [**修正するタイミング**] 列で並べ替えることができます。 3番目の [**説明**] 列には、問題のタイトルが表示されます。  
  
 問題を展開して、追加情報、問題の解決に関する詳細情報のリンク、および問題の詳細を示すリンクを表示できます。 問題の詳細情報を入手できるリンクをクリックすると、問題に関する情報および問題を解決するための指示を含むヘルプ トピックが表示されます。 問題を修正した後、またはアクション項目を管理するには、[**この問題は解決され**ました] チェックボックスをオンにして、問題を完了としてマークできます。 解決済みの問題をアップグレードの問題の一覧から削除する場合は、[最新の状態に**更新**] をクリックします。 同じコンポーネントに対してアップグレードアドバイザー分析ウィザードを実行するか、[**フィルター条件**] オプションから**解決済みの問題**フィルターを適用するまで、この問題は再び表示されません。  
  
## <a name="report-files"></a>レポート ファイル  
 Upgrade Advisor 分析ウィザードでは、My Documents\\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] upgrade Advisor\110\Reports ディレクトリにレポートが作成され、分析するサーバーごとにサブディレクトリが作成されます。 レポート ファイルは、特定の名前付け規則に従った XML ファイルです。 アップグレード アドバイザー レポート ビューアーを起動すると、既定のディレクトリにあるレポート ファイルが表示されます。 レポート ファイルをこのフォルダーにコピーする場合、名前付け規則に従う必要があります。名前付け規則に従わないと、レポート ビューアーでレポート ファイルが自動的に表示されません。  
  
 他のユーザーと情報を共有するには、XML レポートを他のユーザーに送信できます。 また、レポートをコンマ区切り形式のファイルにエクスポートすれば、スプレッドシート、テキスト ファイル、電子メール メッセージなどを別のアプリケーションで作成できます。  
  
## <a name="see-also"></a>参照  
 [アップグレードアドバイザーレポートを表示する方法](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md)   
 [レポートをエクスポートする方法](../../../2014/sql-server/install/how-to-export-reports.md)   
 [方法: レポートをフィルター処理する](../../../2014/sql-server/install/how-to-filter-reports.md)   
 [アップグレードに関する問題の解決](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
