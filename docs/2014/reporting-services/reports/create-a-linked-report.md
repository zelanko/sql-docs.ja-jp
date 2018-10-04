---
title: リンク レポートを作成する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- linked reports [Reporting Services], creating
ms.assetid: 12be8341-cb57-45e8-a421-2bf66b50234d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 277ee4ff416ad9710eecf501651b5a5143b0fa68
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48210211"
---
# <a name="create-a-linked-report"></a>リンク レポートを作成する
  リンク レポートは、既存のレポートへのアクセス ポイントとなるレポート サーバー アイテムです。 概念的には、プログラムを実行したりファイルを開くのに使用する、プログラム ショートカットに似ています。  
  
 リンク レポートは、既存のレポートから派生し、元のレポート定義を保持しています。 リンク レポートは、常に、元のレポートのレポート レイアウトおよびデータ ソース プロパティを継承します。 セキュリティ、パラメーター、場所、サブスクリプション、スケジュールなど、その他のプロパティおよび設定はすべて、元のレポートとは異なる場合があります。  
  
 既存のレポートの追加バージョンを作成するときに、リンク レポートを作成することができます。 たとえば、単一の地域の売上レポートを使用し、すべての販売区域について、地域固有のレポートを作成することができます。  
  
 リンク レポートは通常はパラメーター化されたレポートに基づいていますが、パラメーター化されたレポートは必須ではありません。 リンク レポートは、異なる設定で既存のレポートを配置する場合にも作成できます。  
  
### <a name="to-create-a-linked-report"></a>リンク レポートを作成するには  
  
1.  レポート マネージャーで、リンク先のレポートのあるフォルダーに移動し、オプション メニューを開いて、 **[リンク レポートの作成]** をクリックします。  
  
2.  新規リンク レポートの名前を入力します。 必要に応じて、説明を入力します。  
  
3.  レポートを別のフォルダーに保存するには、 **[場所の変更]** をクリックします。 保存先のフォルダーをクリックするか、または **[場所]** ボックスにフォルダー名を入力します。 [!INCLUDE[clickOK](../../../includes/clickok-md.md)] 別のフォルダーを選択しない場合は、(基にして、レポートの保存先) 現在のフォルダーで、リンク レポートが作成されます。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)] リンク レポートが開きます。  
  
     リンク レポートのアイコンは、レポート サーバーによって管理されるその他のアイテムのアイコンとは異なります。 次のアイコンでリンク レポートを示します。  
  
     ![リンク レポート アイコン](../media/hlp-16linked.gif "リンク レポート アイコン")  
  
## <a name="see-also"></a>参照  
 [レポートを開閉&#40;レポート マネージャー&#41;](../reports/open-and-close-a-report-report-manager.md)   
 [新しいリンク レポート ページ &#40;レポート マネージャー&#41;](../new-linked-report-page-report-manager.md)   
 [アイテムの場所の選択 ページ &#40;レポート マネージャー&#41;](../choose-item-location-page-report-manager.md)   
 [全般プロパティ ページ、レポート &#40;レポート マネージャー&#41;](../general-properties-page-reports-report-manager.md)   
 [Reporting Services の概念 &#40;SSRS&#41;](../reporting-services-concepts-ssrs.md)   
 [レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md)  
  
  
