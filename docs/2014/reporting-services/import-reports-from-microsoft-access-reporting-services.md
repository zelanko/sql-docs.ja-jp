---
title: Microsoft Access からレポートをインポートする (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Access reports [Reporting Services]
- importing reports
ms.assetid: 4f29d5b8-b77d-4714-a84a-05523df55646
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 862d8b90f3c91dffda35971677db7fdc231c1b63
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108928"
---
# <a name="import-reports-from-microsoft-access-reporting-services"></a>Microsoft Access からレポートをインポートする (Reporting Services)
  レポートデザイナーでは、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Access データベースまたはプロジェクトからレポートをインポートできます。 レポート デザイナーがインストールされているコンピューターに、Access 2002 以降のバージョンがインストールされている必要があります。  
  
 インポート機能を使用すると、Access データベースまたはプロジェクト ファイルのすべてのレポートがインポートされます。 Access ファイルに多数のレポートが含まれている場合は、レポートのインポート先に別のレポート プロジェクトを作成し、その後各 RDL ファイルをメインのレポート プロジェクトで開くことをお勧めします。 レポートは、レポート デザイナーにインポートした後に、編集できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] では、Access のレポート オブジェクトがすべてサポートされているわけではありません。 変換されていない項目は、[**タスク一覧**] ウィンドウに表示されます。 詳細については、「[サポートされているアクセスレポート機能 &#40;SSRS&#41;](../../2014/reporting-services/supported-access-report-features-ssrs.md)」を参照してください。  
  
### <a name="to-import-reports-from-microsoft-access"></a>Microsoft Access からレポートをインポートするには  
  
1.  レポートをインポートするプロジェクトを開くか、作成します。  
  
2.  [**プロジェクト**] メニューの [**レポートのインポート**] をポイントし、[ **Microsoft access**] をクリックします。 または、ソリューションエクスプローラーでプロジェクトを右クリックして [**レポートのインポート**] をポイントし、[ **Microsoft access**] をクリックします。  
  
3.  [**開く**] ダイアログボックスで、レポートが格納されている Access データベース (.mdb、.accdb) またはプロジェクト (.adp) を選択し、[**開く**] をクリックします。 データベースまたはプロジェクト ファイルのすべてのレポートがインポートされて、ソリューション エクスプローラーの [レポート] フォルダーに一覧表示されます。  
  
4.  [**タスク一覧**] ウィンドウでビルドエラーを確認します。 **タスク一覧**ウィンドウを表示するには、[**表示**] メニューの [**その他のウィンドウ**] をポイントし、[**タスク一覧**] をクリックします。  
  
## <a name="see-also"></a>参照  
 [レポート デザイナーを使用してレポートをデザインする &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
