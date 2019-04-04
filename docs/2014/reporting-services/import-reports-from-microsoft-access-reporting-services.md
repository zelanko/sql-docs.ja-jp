---
title: Microsoft Access (Reporting Services) からレポートをインポート |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Access reports [Reporting Services]
- importing reports
ms.assetid: 4f29d5b8-b77d-4714-a84a-05523df55646
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 7458de1c7424bf3c5b856c263e5180e33e207f76
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2019
ms.locfileid: "56286350"
---
# <a name="import-reports-from-microsoft-access-reporting-services"></a>Microsoft Access からレポートをインポートする (Reporting Services)
  レポート デザイナーからのレポートをインポートすることができます、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Access データベースまたはプロジェクト。 レポート デザイナーがインストールされているコンピューターに、Access 2002 以降のバージョンがインストールされている必要があります。  
  
 インポート機能を使用すると、Access データベースまたはプロジェクト ファイルのすべてのレポートがインポートされます。 Access ファイルに多数のレポートが含まれている場合は、レポートのインポート先に別のレポート プロジェクトを作成し、その後各 RDL ファイルをメインのレポート プロジェクトで開くことをお勧めします。 レポートは、レポート デザイナーにインポートした後に、編集できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] では、Access のレポート オブジェクトがすべてサポートされているわけではありません。 変換されていない項目が表示される、**タスク一覧**ウィンドウ。 詳細については、[Access レポート機能のサポートされている&#40;SSRS&#41;](../../2014/reporting-services/supported-access-report-features-ssrs.md)を参照してください。  
  
### <a name="to-import-reports-from-microsoft-access"></a>Microsoft Access からレポートをインポートするには  
  
1.  レポートをインポートするプロジェクトを開くか、作成します。  
  
2.  **プロジェクト**メニューで、**レポートをインポートする**、 をクリックし、 **Microsoft Access**。 または、ソリューション エクスプ ローラーでプロジェクトを右クリックし、 をポイント**レポートをインポートする**、 をクリックし、 **Access**します。  
  
3.  **オープン** ダイアログ ボックスで、Access データベース (.mdb、.accdb) を選択またはプロジェクト (.adp) をクリックし、レポートを含む**オープン**します。 データベースまたはプロジェクト ファイルのすべてのレポートがインポートされて、ソリューション エクスプローラーの [レポート] フォルダーに一覧表示されます。  
  
4.  チェック、**タスク一覧**ウィンドウで、ビルド エラー。 表示する、**タスク一覧**ウィンドウを開いて、**ビュー**メニューで、**その他の Windows**、順にクリックします**タスク一覧**します。  
  
## <a name="see-also"></a>参照  
 [レポート デザイナーを使用してレポートをデザインする &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
