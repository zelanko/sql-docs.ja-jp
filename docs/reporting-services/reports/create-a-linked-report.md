---
title: リンク レポートを作成する | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- linked reports [Reporting Services], creating
ms.assetid: 12be8341-cb57-45e8-a421-2bf66b50234d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: df16c043688de82a549ec506ece457730626dda1
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50029061"
---
# <a name="create-a-linked-report"></a>リンク レポートを作成する
  リンク レポートは、既存のレポートへのアクセス ポイントとなるレポート サーバー アイテムです。 概念的には、プログラムを実行したりファイルを開くのに使用する、プログラム ショートカットに似ています。  
  
 リンク レポートは、既存のレポートから派生し、元のレポート定義を保持しています。 リンク レポートは、常に、元のレポートのレポート レイアウトおよびデータ ソース プロパティを継承します。 セキュリティ、パラメーター、場所、サブスクリプション、スケジュールなど、その他のプロパティおよび設定はすべて、元のレポートとは異なる場合があります。  
  
 既存のレポートの追加バージョンを作成するときに、リンク レポートを作成することができます。 たとえば、単一の地域の売上レポートを使用し、すべての販売区域について、地域固有のレポートを作成することができます。  
  
 リンク レポートは通常はパラメーター化されたレポートに基づいていますが、パラメーター化されたレポートは必須ではありません。 リンク レポートは、異なる設定で既存のレポートを配置する場合にも作成できます。  
  
### <a name="to-create-a-linked-report"></a>リンク レポートを作成するには  
  
1.  レポート マネージャーで、リンク先のレポートのあるフォルダーに移動し、オプション メニューを開いて、 **[リンク レポートの作成]** をクリックします。  
  
2.  新規リンク レポートの名前を入力します。 必要に応じて、説明を入力します。  
  
3.  レポートを別のフォルダーに保存するには、 **[場所の変更]** をクリックします。 保存先のフォルダーをクリックするか、または **[場所]** ボックスにフォルダー名を入力します。 [!INCLUDE[clickOK](../../includes/clickok-md.md)] 別のフォルダーを指定しない場合、現在のフォルダー (リンク先のレポートが保存されているフォルダー) にリンク レポートが作成されます。  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] リンク レポートが表示されます。  
  
     リンク レポートのアイコンは、レポート サーバーによって管理されるその他のアイテムのアイコンとは異なります。 次のアイコンでリンク レポートを示します。  
  
     ![リンク レポート アイコン](../../reporting-services/report-server/media/hlp-16linked.gif "リンク レポート アイコン")  
  
## <a name="see-also"></a>参照  
 [レポートを開閉する (レポート マネージャー)](../../reporting-services/reports/open-and-close-a-report-report-manager.md)   
 [新しいリンク レポート ページ (レポート マネージャー)](https://msdn.microsoft.com/library/fefb46e8-6901-4d50-a3f8-7c49ad72e7b1)   
 [アイテムの場所の選択 ページ &#40;レポート マネージャー&#41;](https://msdn.microsoft.com/library/4a53a1a8-d1e1-47ef-b1fc-63352ece7d3c)   
 [全般プロパティ ページ、レポート &#40;レポート マネージャー&#41;](https://msdn.microsoft.com/library/66c99d28-ab41-45f0-bf02-ed560293595d)   
 [Reporting Services の概念 &#40;SSRS&#41;](../../reporting-services/reporting-services-concepts-ssrs.md)   
 [レポート マネージャー (SSRS ネイティブ モード)](https://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)  
  
  
