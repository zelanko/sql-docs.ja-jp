---
title: 'レッスン 2: xsd ツールを使用して、RDL スキーマからクラスを生成します |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a81c87f1-7977-4b30-b6ac-b38b3e2b6398
caps.latest.revision: 13
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 67cbc84882683fcb31d6b42f69274d5166556450
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178346"
---
# <a name="lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool"></a>レッスン 2 : xsd ツールを使用して RDL スキーマからクラスを作成
  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロジェクトを作成したら、次はレポート定義スキーマのローカル コピーを取得して、XML スキーマ定義ツール (Xsd.exe) を実行します。  
  
### <a name="to-generate-the-rdl-classes"></a>RDL クラスを生成するには  
  
1.  インスタンスを開いて[!INCLUDE[msCoName](../includes/msconame-md.md)]Internet Explorer (または同等の Web ブラウザー) し、次の URL に移動します。  
  
    ```  
    http://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition/ReportDefinition.xsd  
    ```  
  
2.  RDL スキーマに開くと、ブラウザーで、参照、**ファイル**メニューのおよび選択**名前を付けて保存**です。  
  
3.  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロジェクトを作成した場所に移動して、スキーマをファイル名 ReportDefinition.xsd として保存します。  
  
4.  ファイルを保存すると後のインスタンスを開いて、[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]コマンド プロンプトです。 コマンド プロンプトのインスタンスを開くには、スタート メニューをクリックし、**すべてのプログラム**、指す**Microsoft Visual Studio 2010**、 をポイント**Visual Studio Tools**  をクリック**Visual Studio コマンド プロンプト (2010)** です。  
  
5.  現在のパスを、ReportDefinition.xsd ファイルを保存した場所に変更します。  
  
     `CD\<ReportDefinition.xsd Path>`  
  
6.  次のコマンドを使用して、RDL スキーマのクラスを含む ReportDefinition.cs ファイルを生成します。  
  
     `xsd /c /n:SampleRDLSchema ReportDefinition.xsd`  
  
     ReportDefinition.vb ファイルを生成するには、次のコマンドを使用します。  
  
     `xsd /c /l:VB /n:SampleRDLSchema ReportDefinition.xsd`  
  
7.  プロジェクトに ReportDefinition.xsd を追加します。 **プロジェクト** メニューをクリックして**既存項目の追加**です。 ReportDefinition.xsd ファイルの場所を参照し、ReportDefinition.xsd を選択し、をクリックして**追加**です。  
  
    > [!NOTE]  
    >  プロジェクトに ReportDefinition.xsd ファイルを追加した後で確認すると**ソリューション エクスプ ローラー** ReportDefinition.cs (.vb) ファイルがないことがあります。 ファイルを表示するには、ReportDefinition.xsd ファイルの横にある展開/折りたたみのボタンをクリックします。  
  
## <a name="next-lesson"></a>次のレッスン  
 次のレッスンでは、RDL スキーマから生成したクラスを使って、レポート サーバーからレポート定義を読み込むコードを作成します。 参照してください[レッスン 3: レポート サーバーからレポート定義の読み込み](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md)です。  
  
## <a name="see-also"></a>参照  
 [RDL スキーマから生成されたクラスを使用してレポートの更新&#40;SSRS チュートリアル&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [レポート定義言語 &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  