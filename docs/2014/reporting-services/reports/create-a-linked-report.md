---
title: リンク レポートを作成する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- linked reports [Reporting Services], creating
ms.assetid: 12be8341-cb57-45e8-a421-2bf66b50234d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 27667eececc3905b927b7e888e692a8261d14d30
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78177061"
---
# <a name="create-a-linked-report"></a>リンク レポートを作成する
  リンク レポートは、既存のレポートへのアクセス ポイントとなるレポート サーバー アイテムです。 概念的には、プログラムを実行したりファイルを開くのに使用する、プログラム ショートカットに似ています。

 リンク レポートは、既存のレポートから派生し、元のレポート定義を保持しています。 リンク レポートは、常に、元のレポートのレポート レイアウトおよびデータ ソース プロパティを継承します。 セキュリティ、パラメーター、場所、サブスクリプション、スケジュールなど、その他のプロパティおよび設定はすべて、元のレポートとは異なる場合があります。

 既存のレポートの追加バージョンを作成するときに、リンク レポートを作成することができます。 たとえば、単一の地域の売上レポートを使用し、すべての販売区域について、地域固有のレポートを作成することができます。

 リンク レポートは通常はパラメーター化されたレポートに基づいていますが、パラメーター化されたレポートは必須ではありません。 リンク レポートは、異なる設定で既存のレポートを配置する場合にも作成できます。

### <a name="to-create-a-linked-report"></a>リンク レポートを作成するには

1.  レポート マネージャーで、リンク先のレポートのあるフォルダーに移動し、オプション メニューを開いて、 **[リンク レポートの作成]** をクリックします。

2.  新規リンク レポートの名前を入力します。 必要に応じて、説明を入力します。

3.  レポートを別のフォルダーに保存するには、 **[場所の変更]** をクリックします。 保存先のフォルダーをクリックするか、または **[場所]** ボックスにフォルダー名を入力します。 
  [!INCLUDE[clickOK](../../../includes/clickok-md.md)] 別のフォルダーを指定しない場合、現在のフォルダー (リンク先のレポートが保存されているフォルダー) にリンク レポートが作成されます。

4.  
  [!INCLUDE[clickOK](../../../includes/clickok-md.md)] リンク レポートが表示されます。

     リンク レポートのアイコンは、レポート サーバーによって管理されるその他のアイテムのアイコンとは異なります。 次のアイコンでリンク レポートを示します。

     ![リンク レポート アイコン](../media/hlp-16linked.gif "リンク レポート アイコン")

## <a name="see-also"></a>参照
 [レポートを開いて閉じる &#40;レポートマネージャー&#41;](../reports/open-and-close-a-report-report-manager.md) [新しいリンクレポートページ &#40;レポートマネージャー](../new-linked-report-page-report-manager.md)&#41;[[アイテムの場所の選択] ページ](../choose-item-location-page-report-manager.md)&#40;レポートマネージャー&#41;[全般プロパティ] ページ、レポート &#40;](../general-properties-page-reports-report-manager.md)レポートマネージャー&#41;REPORTING SERVICES の[概念 &#40;ssrs&#41;](../reporting-services-concepts-ssrs.md) [レポートマネージャー &#40;ssrs ネイティブモード](../report-manager-ssrs-native-mode.md)&#41;


