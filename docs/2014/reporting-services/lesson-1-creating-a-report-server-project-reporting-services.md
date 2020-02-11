---
title: 'レッスン 1: レポート サーバー プロジェクトの作成 (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 675671ca-e6c9-48a2-82e9-386778f3a49f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3f97834b5df61df836b7cfd4cc4d890877f8855a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108531"
---
# <a name="lesson-1-creating-a-report-server-project-reporting-services"></a>レッスン 1 : レポート サーバー プロジェクトの作成 (Reporting Services)
  
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] でレポートを作成するには、まずレポート サーバー プロジェクトを作成して、レポート定義ファイル (.rdl) やその他レポートに必要なリソース ファイルを格納できるようにする必要があります。 次に、実際のレポート定義ファイルを作成し、レポートのデータ ソース、データセット、レイアウトを定義します。 作成したレポートを実行すると、実際のデータが取得され、レイアウト定義に従って画面上に表示されるので、その状態からエクスポート、印刷、保存を行うことができます。  
  
 このレッスンでは、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]でレポート サーバー プロジェクトを作成する方法を学習します。 レポート サーバー プロジェクトを使用して、レポート サーバーで実行するレポートを作成します。  
  
### <a name="to-create-a-report-server-project"></a>レポート サーバー プロジェクトを作成するには  
  
1.  [**スタート**] をクリックし、[**すべて**の[!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)]プログラム]、[] の順にポイントして、[ **SQL Server Data Tools**] をクリックします。 初めてを開い[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]た場合は、既定の環境設定の [**ビジネスインテリジェンスの設定**] をクリックします。  
  
2.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。  
  
3.  
  **[インストールされているテンプレート]** ボックスの一覧で、 **[ビジネス インテリジェンス プロジェクト]** をクリックします。  
  
4.  [**レポートサーバープロジェクト**] をクリックします。  
  
5.  
  **[名前]** に「 **Tutorial**」と入力します。  
  
6.  
  **[OK]** をクリックして、プロジェクトを作成します。  
  
     Tutorial プロジェクトがソリューション エクスプローラーに表示されます。  
  
### <a name="to-create-a-new-report-definition-file"></a>新しいレポート定義ファイルを作成するには  
  
1.  ソリューションエクスプローラーで、[**レポート**] を右クリックして [**追加**] をポイントし、[**新しいアイテム**] をクリックします。  
  
    > [!NOTE]  
    >  
  **[ソリューション エクスプローラー]** ウィンドウが表示されない場合は、 **[表示]** メニューの **[ソリューション エクスプローラー]** をクリックします。  
  
2.  [**新しい項目の追加**] ダイアログボックスの [**テンプレート**] の下にある [**レポート**] をクリックします。  
  
3.  
  **[名前]** に「 **Sales Orders.rdl** 」と入力して、 **[追加]** をクリックします。  
  
     レポート デザイナーを開き、デザイン ビューで新しい .rdl ファイルを表示します。  
  
 レポート デザイナーは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] で実行される [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]コンポーネントです。 
  **[デザイン]** ビューと **[プレビュー]** ビューの 2 つのビューがあります。 ビューを変更するには該当するタブをクリックします。  
  
 
  **[レポート データ]** ペインでデータを定義します。 
  **[デザイン]** ビューではレポートのレイアウトを定義します。 
  **[プレビュー]** ビューではレポートを実行して結果を確認できます。  
  
## <a name="next-task"></a>次の作業  
 ここでは、"Tutorial" というレポート プロジェクトを作成し、このレポート プロジェクトにレポート定義ファイル (.rdl) を追加しました。 次に、レポートで使用するデータ ソースを指定します。 「[レッスン 2: 接続情報の指定 &#40;Reporting Services&#41;](lesson-2-specifying-connection-information-reporting-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [基本的なテーブル レポートの作成 (SSRS チュートリアル)](create-a-basic-table-report-ssrs-tutorial.md)  
  
  
