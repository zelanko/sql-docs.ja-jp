---
title: 'レッスン 2: xsd ツールを使用して RDL スキーマからクラスを生成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a81c87f1-7977-4b30-b6ac-b38b3e2b6398
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: f5f74c6621d329885e9149fce9a37c7418d9c37b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62653750"
---
# <a name="lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool"></a>レッスン 2 : xsd ツールを使用して RDL スキーマからクラスを作成
  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロジェクトを作成したら、次はレポート定義スキーマのローカル コピーを取得して、XML スキーマ定義ツール (Xsd.exe) を実行します。  
  
### <a name="to-generate-the-rdl-classes"></a>RDL クラスを生成するには  
  
1.  Internet Explorer のインスタンス[!INCLUDE[msCoName](../includes/msconame-md.md)] (または同等の Web ブラウザー) を開き、次の URL に移動します。  
  
    ```  
    https://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition/ReportDefinition.xsd  
    ```  
  
2.  RDL スキーマがブラウザーで開かれたら、[**ファイル**] メニューに移動し、[名前を付け**て保存**] を選択します。  
  
3.  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロジェクトを作成した場所に移動して、スキーマをファイル名 ReportDefinition.xsd として保存します。  
  
4.  ファイルが保存されたら、 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]コマンドプロンプトのインスタンスを開きます。 コマンドプロンプトのインスタンスを開くには、[スタート] ボタンをクリックし、[**すべてのプログラム**]、[ **Microsoft Visual Studio 2010**]、[ **Visual Studio Tools**の順にポイントし、[ **Visual Studio コマンドプロンプト (2010)**] をクリックします。  
  
5.  現在のパスを、ReportDefinition.xsd ファイルを保存した場所に変更します。  
  
     `CD\<ReportDefinition.xsd Path>`  
  
6.  次のコマンドを使用して、RDL スキーマのクラスを含む ReportDefinition.cs ファイルを生成します。  
  
     `xsd /c /n:SampleRDLSchema ReportDefinition.xsd`  
  
     ReportDefinition.vb ファイルを生成するには、次のコマンドを使用します。  
  
     `xsd /c /l:VB /n:SampleRDLSchema ReportDefinition.xsd`  
  
7.  プロジェクトに ReportDefinition.xsd を追加します。 [**プロジェクト**] メニューの [**既存項目の追加**] をクリックします。 ReportDefinition .xsd ファイルの場所を参照し、[ReportDefinition. xsd] を選択して、[**追加**] をクリックします。  
  
    > [!NOTE]  
    >  プロジェクトに ReportDefinition .xsd ファイルを追加すると、ReportDefinition.cs (.vb) ファイルが存在しないことが**ソリューションエクスプローラー**わかります。 ファイルを表示するには、ReportDefinition.xsd ファイルの横にある展開/折りたたみのボタンをクリックします。  
  
## <a name="next-lesson"></a>次のレッスン  
 次のレッスンでは、RDL スキーマから生成したクラスを使って、レポート サーバーからレポート定義を読み込むコードを作成します。 「[レッスン 3: レポートサーバーからレポート定義を読み込む](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [RDL スキーマから生成されたクラスを使用したレポートの更新 SSRS チュートリアル &#40;&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [レポート定義言語 &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
