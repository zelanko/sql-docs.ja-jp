---
title: 基本的なテーブル レポートの作成 (SSRS チュートリアル) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [Reporting Services]
- tutorials [Reporting Services]
- reports [Reporting Services], creating
ms.assetid: 3b539b4b-26f2-4c0b-b506-80f175679a46
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 08ed0c207b92075952ffc71669b45100e4ff7d06
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109682"
---
# <a name="create-a-basic-table-report-ssrs-tutorial"></a>基本的なテーブル レポートの作成 (SSRS チュートリアル)
  このチュートリアルは、レポート デザイナーを使用して、 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベースを基にした基本的なテーブル レポートを作成することを目的としています。 レポートの作成には、レポート ビルダーまたはレポート ウィザードを使用することもできます。 ここでは、レポート プロジェクトの作成、接続情報の設定、クエリの定義、表のデータ領域、グループ フィールド、および合計フィールドの追加、レポートのプレビュー表示を行います。  
  
> [!NOTE]  
>  このチュートリアルを完了するには、[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] をネイティブ モードで実行する必要があります。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] を SharePoint 統合モードで実行していると、レポート サーバーの URL を使用するステップを実行できません。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]モードの詳細については、「[レポートサーバーの Reporting Services](reporting-services-report-server.md)」を参照してください。  
  
## <a name="requirements"></a>要件  
 このチュートリアルを使用するには、システムに以下のコンポーネントがインストールされている必要があります。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]データベースエンジン。  
  
-   [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベース。  詳細については、「 [Adventure works for SQL Server 2012 (adventure works for SQL Server 2012)](https://go.microsoft.com/fwlink/?LinkId=245471) 」 (https://go.microsoft.com/fwlink/?LinkId=245471).を参照してください。 の[!INCLUDE[ssExpress](../includes/ssexpress-md.md)]サンプルデータベースとサンプルコード[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のサポートの詳細については、CodePlex Web サイトの「[データベースとサンプルの概要](https://go.microsoft.com/fwlink/?LinkId=110391)」を参照してください。  
  
-   [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)].  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNote64Samp](../includes/ssnote64samp-md.md)]  
  
 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] データベースからデータを取得するには読み取り専用権限も必要です。  
  
## <a name="tasks"></a>タスク  
 [レッスン 1: レポート サーバー プロジェクトの作成 (Reporting Services)](lesson-1-creating-a-report-server-project-reporting-services.md)  
  
 [レッスン 2: 接続情報の指定 (Reporting Services)](lesson-2-specifying-connection-information-reporting-services.md)  
  
 [レッスン 3: テーブル レポートのデータセットの定義 (Reporting Services)](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md)  
  
 [レッスン 4: レポートへのテーブルの追加 (Reporting Services)](lesson-4-adding-a-table-to-the-report-reporting-services.md)  
  
 [レッスン 5: レポートの書式設定 (Reporting Services)](lesson-5-formatting-a-report-reporting-services.md)  
  
 [レッスン 6: グループと合計の追加 (Reporting Services)](lesson-6-adding-grouping-and-totals-reporting-services.md)  
  
> [!NOTE]  
>  チュートリアルを確認するときは、ドキュメントビューアーのツールバーに **[次へ**] ボタンと [**前**へ] ボタンを追加することをお勧めします。 詳細については、以下を参照してください。  
  
## <a name="see-also"></a>参照  
 [Reporting Services チュートリアル &#40;SSRS&#41;](reporting-services-tutorials-ssrs.md)  
  
  
