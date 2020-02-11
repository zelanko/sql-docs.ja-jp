---
title: アップグレードアドバイザーレポートを表示する方法 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- displaying reports
- viewing reports
- Upgrade Advisor [SQL Server], reports
- SQL Server Upgrade Advisor, reports
- reports [Upgrade Advisor], viewing
ms.assetid: d13b38af-0ac3-4030-83cd-e7d7825dd09f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c0ae231e380530f11d4c97a917927ed62e99fb47
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66094802"
---
# <a name="how-to-view-an-upgrade-advisor-report"></a>アップグレード アドバイザーのレポートを表示する方法
  アップグレード アドバイザーでは、分析対象として選択したコンポーネントごとにレポートが作成されます。 このトピックでは、アップグレード アドバイザーの開始ページからアップグレード アドバイザーのレポートを表示する方法について説明します。  
  
> [!IMPORTANT]  
>  レポート ビューアーは、標準のファイル名に基づいてファイルを読み込みます。 ファイル名が変更されると、そのファイルは読み込まれません。  
  
### <a name="to-view-a-report"></a>レポートを表示するには  
  
1.  [**スタート**]、[**すべて**のプログラム**[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**]、[]、[ ** [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]アップグレードアドバイザー**] の順にクリックします。  
  
2.  アップグレードアドバイザーの開始ページで、[**アップグレードアドバイザーレポートビューアーの起動**] をクリックします。  
  
3.  コンピューターの既定の場所にあるレポートを選択するには、次の手順を実行します。  
  
    1.  [**サーバー** ] ボックスの一覧で、サーバーを選択します。  
  
    2.  [**インスタンス] また**は [コンポーネント] の一覧で、コンポーネントまたはコンポーネント/インスタンスの組み合わせを選択します。  
  
     別の場所でレポートを選択するには、次の手順を実行します。  
  
    1.  [**レポートを開く**] リンクをクリックします。  
  
    2.  レポートの場所を参照し、XML ファイルをダブルクリックします。  
  
     アップグレード アドバイザーでは、以前に行った分析の履歴として最大 5 件のレポートが保持されます。 これらのレポートを表示するには、[**レポート**] ドロップダウンリストボックスをクリックし、レポートを選択します。 レポートは、生成日時を示すタイムスタンプ順に一覧表示されます。  
  
     レポートには、検出されたすべての問題に対して次の詳細が含まれます。  
  
    -   [**重要度**]: 問題を解決するための重要度を示します。  
  
    -   **修正する**場合は、アプリケーションまたはデータを移行する前または後に、またはいつ[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]でもアップグレードする前または後に、問題を修正する必要があるかどうかを示します。  
  
    -   問題の簡潔な説明。  
  
4.  レポートに含まれている項目が 20 項目を超える場合、レポートの上部または下部にある緑色の次へ進む矢印をクリックし、次の項目セットを表示します。 前の 20 項目を表示するには、緑色の "戻る" ボタンをクリックします。  
  
5.  レポートを並べ替えるには、列見出しをクリックします。  
  
6.  特定の項目の詳細を表示するには、その項目をクリックします。 問題の説明が追加のオプションと共に表示されます。  
  
    -   この問題が検出されたオブジェクトを表示するには、[**影響を受けるオブジェクトの表示**] をクリックします。  
  
    -   問題のヘルプを表示するには、[**この問題とその解決方法について詳しく**教えてください] をクリックします。  
  
    -   問題を解決済みとしてマークするには、レポートを再度表示したときに問題が表示されないようにするには、[**この問題は解決されまし**た] を選択します。  
  
> [!NOTE]  
>  レポートには、検出不可能な問題に対する項目が含まれる場合があります。 これらは、検出できない問題か、または誤って検出された結果が大量に生成される問題です。 [**この問題の詳細**を確認してください] リンクをクリックすると、コンポーネントの検出できない問題の一覧が表示されます。  
  
## <a name="see-also"></a>参照  
 [レポートをエクスポートする方法](../../../2014/sql-server/install/how-to-export-reports.md)   
 [アップグレードアドバイザー分析ウィザードを実行する方法](../../../2014/sql-server/install/how-to-run-the-upgrade-advisor-analysis-wizard.md)   
 [アップグレードに関する問題の解決](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [アップグレードアドバイザーの操作方法に関するトピック](../../../2014/sql-server/install/upgrade-advisor-how-to-topics.md)   
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
