---
title: Microsoft Access (Reporting Services) からレポートをインポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Access reports [Reporting Services]
- importing reports
ms.assetid: 4f29d5b8-b77d-4714-a84a-05523df55646
caps.latest.revision: 39
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: ec0461f278bfe6556d4a1fa221d5b33426d8ed01
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164963"
---
# <a name="import-reports-from-microsoft-access-reporting-services"></a>Microsoft Access からレポートをインポートする (Reporting Services)
  レポート デザイナーからレポートをインポートすることができます、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Access データベースまたはプロジェクト。 レポート デザイナーがインストールされているコンピューターに、Access 2002 以降のバージョンがインストールされている必要があります。  
  
 インポート機能を使用すると、Access データベースまたはプロジェクト ファイルのすべてのレポートがインポートされます。 Access ファイルに多数のレポートが含まれている場合は、レポートのインポート先に別のレポート プロジェクトを作成し、その後各 RDL ファイルをメインのレポート プロジェクトで開くことをお勧めします。 レポートは、レポート デザイナーにインポートした後に、編集できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] では、Access のレポート オブジェクトがすべてサポートされているわけではありません。 変換されていない項目が表示される、**タスク一覧**ウィンドウです。 詳細については、次を参照してください。 [Access レポート機能のサポートされている&#40;SSRS&#41;](../../2014/reporting-services/supported-access-report-features-ssrs.md)です。  
  
### <a name="to-import-reports-from-microsoft-access"></a>Microsoft Access からレポートをインポートするには  
  
1.  レポートをインポートするプロジェクトを開くか、作成します。  
  
2.  **プロジェクト** メニューのをポイント**レポートのインポート**、順にクリック**Access**です。 または、ソリューション エクスプ ローラーでプロジェクトを右クリックし、**レポートのインポート**、順にクリック**Access**です。  
  
3.  **開く** ダイアログ ボックスで、Access データベース (.mdb、.accdb) を選択またはプロジェクト (.adp) をクリックし、レポートを含む**開く**です。 データベースまたはプロジェクト ファイルのすべてのレポートがインポートされて、ソリューション エクスプローラーの [レポート] フォルダーに一覧表示されます。  
  
4.  チェック、**タスク一覧**ウィンドウで、ビルド エラーです。 表示する、**タスク一覧**ウィンドウを開いた、**ビュー**  メニューのをポイント**その他のウィンドウ**、順にクリック**タスク一覧**です。  
  
## <a name="see-also"></a>参照  
 [レポート デザイナーを使用してレポートをデザインする &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  