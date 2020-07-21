---
title: リンク レポートを作成する | Microsoft Docs
description: 既存のレポートの追加バージョンを作成できるように、リンク レポートを作成する方法について説明します。
ms.date: 05/30/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- linked reports [Reporting Services], creating
ms.assetid: 12be8341-cb57-45e8-a421-2bf66b50234d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: cb362f699e8bf87e0f386c3ec726869f67aec934
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "79510163"
---
# <a name="create-a-linked-report"></a>リンク レポートを作成する
  リンク レポートは、既存のレポートへのアクセス ポイントとなるレポート サーバー アイテムです。 概念的には、プログラムを実行したりファイルを開くのに使用する、プログラム ショートカットに似ています。  
  
 リンク レポートは、既存のレポートから派生し、元のレポート定義を保持しています。 リンク レポートは、常に、元のレポートのレポート レイアウトおよびデータ ソース プロパティを継承します。 セキュリティ、パラメーター、場所、サブスクリプション、スケジュールなど、その他のプロパティおよび設定はすべて、元のレポートとは異なる場合があります。  
  
 既存のレポートの追加バージョンを作成するときに、リンク レポートを作成することができます。 たとえば、単一の地域の売上レポートを使用し、すべての販売区域について、地域固有のレポートを作成することができます。  
  
 リンク レポートは通常はパラメーター化されたレポートに基づいていますが、パラメーター化されたレポートは必須ではありません。 リンク レポートは、異なる設定で既存のレポートを配置する場合にも作成できます。  
  
## <a name="to-create-a-linked-report"></a>リンク レポートを作成するには  
  
1. Web ポータルで、任意のレポートに移動してそれを右クリックし、ドロップダウン メニューから **[管理]** を選択します。

2. **[<reportname> の管理]** ページで **[リンク レポートの作成]** を選択します。  
  
3. 新しいリンク レポートの名前を入力します。 任意で説明を入力します。  
  
4. レポートに別のフォルダーを選択するには、***[場所]*** の右にある省略記号ボタン (...) を選択します。  レポートの新しいフォルダーに移動し、 **[選択]** を選択します。 別のフォルダーを選択しない場合、リンク レポートが現在のフォルダーで作成されます。  
  
5. **［作成］** を選択します リンク レポートが作成されます。  

6. **[詳細]** の下で、必要であれば別の **[レポート タイムアウト]** 値を選択し、 **[適用]** を選択し、変更内容を保存します。
  
     リンク レポートのアイコンは、レポート サーバーによって管理されるその他のアイテムのアイコンとは異なります。 次のアイコンでリンク レポートを示します。  
  
     ![リンク レポート アイコン](../../reporting-services/report-server/media/hlp-16linked.gif "リンク レポート アイコン")  
  
## <a name="see-also"></a>関連項目  

 [Reporting Services の概念 &#40;SSRS&#41;](../../reporting-services/reporting-services-concepts-ssrs.md)  
 [レポート サーバーの Web ポータル (SSRS ネイティブ モード)](../../reporting-services/web-portal-ssrs-native-mode.md)
  
