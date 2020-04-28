---
title: レポートの全般プロパティの構成 (レポートマネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], properties
- properties [Reporting Services], general
ms.assetid: 10b941b2-28e6-4408-9ee4-acebc63c8496
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 23184e77efbe41eae3d4de434a30ff8f3a4847ff
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "78177032"
---
# <a name="configure-general-properties-for-a-report-report-manager"></a>レポートの全般プロパティを構成する (レポート マネージャー)
  
### <a name="to-configure-general-report-properties"></a>全般レポート プロパティを構成するには

1.  [レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) を開始します。

2.  レポート マネージャーで **[コンテンツ]** ページに移動します。 全般プロパティを構成するレポートに移動し、そのレポートを開きます。

3.  **[プロパティ]** タブをクリックします。

     または、[**コンテンツ**] ページが詳細ビューに表示されている場合は、[プロパティページ] アイコンをクリックします。

     ![プロパティ ページのアイコン](media/prop.gif "プロパティ ページのアイコン")

4.  **[全般**] プロパティページが表示され、次のようにプロパティを構成できます。

    -   [**プロパティ**] セクションでは、レポートの名前と説明を変更できます。

    -   [**リストビューで非表示**にする] チェックボックスをオンにすると、既定のページレイアウト (リストビュー) でページを開いたときにアイテムを非表示にすることができます。このページでは、アイテムがページの上下に配置されます。

    -   [**レポート定義**] セクションで、[**編集**] をクリックして、レポート定義のコピーを抽出します。 ローカルでレポート定義に加えた変更は、レポート サーバーに保存されません。

         または、.rdl ファイルからレポート定義を更新するには、[**更新**] をクリックします。

        > [!NOTE]
        >  レポート定義を更新する場合、更新の完了後にデータ ソースの設定を再設定する必要があります。

    -   レポートを削除または移動するには、[**削除**] または [**移動**] ボタンを使用します。

    -   また、リンク レポートを作成することもできます。

5.  レポートの全般プロパティの構成が完了したら、[**適用**] をクリックします。

## <a name="see-also"></a>参照
 [アイテムの移動または削除 &#40;レポートマネージャー&#41;](report-server/move-or-delete-an-item-report-manager.md) [コンテンツ] ページ &#40;](../../2014/reporting-services/contents-page-report-manager.md)レポートマネージャー&#41;[レポートの検索、表示、および管理 &#40;レポートビルダーと SSRS &#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) [全般プロパティページ、レポート &#40;レポートマネージャー](../../2014/reporting-services/general-properties-page-reports-report-manager.md)&#41;


