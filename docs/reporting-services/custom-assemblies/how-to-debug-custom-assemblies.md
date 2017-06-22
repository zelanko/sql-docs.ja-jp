---
title: "方法: カスタム アセンブリのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom assemblies [Reporting Services], debugging
- debugging custom assemblies [Reporting Services]
- troubleshooting [Reporting Services], custom assemblies
ms.assetid: 3a3215b3-548c-4474-81ba-3a98dd3912bf
caps.latest.revision: 44
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: b6cdc41f90765a3fc1a568bc76ddf0d41c15b38a
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="how-to-debug-custom-assemblies"></a>カスタム アセンブリをデバッグする方法
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]するのに役立ついくつかのデバッグ ツール、カスタム アセンブリ コードを分析エラーを探すことを示します。 どのツールが最適であるかは、何を実行するかによって異なります。 この例では [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)]を使用します。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のカスタム アセンブリの設計、開発、およびテストに関して推奨する方法は、テスト レポートおよびカスタム アセンブリを含むソリューションを作成することです。  
  
### <a name="to-debug-assemblies-using-a-single-instance-of-visual-studio"></a>Visual Studio の 1 つのインスタンスを使用してアセンブリをデバッグするには  
  
1.  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] を使用して新しいレポート プロジェクトを作成します。  
  
     [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] でレポート プロジェクトを作成すると、そのプロジェクトを格納するソリューションも作成されます。  
  
2.  新しいクラス ライブラリ プロジェクトを既存のソリューションに追加します。 レポート プロジェクトがスタートアップ プロジェクトとして設定されていることを確認します。 この方法の詳細については、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] のマニュアルを参照してください。  
  
3.  ソリューション エクスプローラーで、ソリューションを選択します。  
  
4.  **ビュー**  メニューのをクリックして**プロパティ ページ**です。  
  
     **ソリューション プロパティ ページ** ダイアログ ボックスが表示されます。  
  
5.  左側のウィンドウで展開**共通プロパティ**必要に応じて、をクリックして**プロジェクトの依存関係**です。 レポート プロジェクトを選択して、**プロジェクト**ドロップダウン リスト。 アセンブリ プロジェクトを選択して、**依存** ボックスの一覧です。  
  
6.  をクリックして**OK**を変更を保存して閉じます、**プロパティ ページ**ダイアログ。  
  
7.  ソリューション エクスプローラーで、カスタム アセンブリ プロジェクトを選択します。  
  
8.  **ビュー**  メニューのをクリックして**プロパティ ページ**です。  
  
     **プロジェクト プロパティ ページ** ダイアログ ボックスが表示されます。  
  
9. クリックして、**ビルド** タブの c# プロジェクトの場合、または**コンパイル**] タブの [している場合、[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]プロジェクト。  
  
10. **ビルド**/**コンパイル** ページで、レポート デザイナー フォルダーへのパスを入力します。 既定では、これは、C:\Program files \microsoft SQL server \100\tools\binn\vsshell\common7\ide です) で、**出力パス**テキスト ボックス。 これにより、レポートの実行前に、更新されたカスタム アセンブリのバージョンがレポート デザイナーに直接構築、配置されます。  
  
11. レポートを設計してカスタム アセンブリを開発したら、カスタム アセンブリ コードにブレークポイントを設定します。  
  
12. レポートの実行**DebugLocal**モード、F5 キーを押します。 ポップアップ プレビュー ウィンドウでレポートを実行すると、デバッガーはアセンブリの実行可能コードに対応するブレークポイントに到達します。 F11</localizedText> キーを使用して、カスタム アセンブリ コードを実行します。  
  
### <a name="to-debug-assemblies-using-two-instances-of-visual-studio"></a>Visual Studio の 2 つのインスタンスを使用してアセンブリをデバッグするには  
  
1.  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] を起動して、カスタム アセンブリ プロジェクトを開きます。  
  
2.  プロジェクトを構築し、カスタム アセンブリと付随する .pdb ファイルをレポート デザイナーに配置します。 展開の詳細については、次を参照してください。[カスタム アセンブリの配置](../../reporting-services/custom-assemblies/deploying-a-custom-assembly.md)です。  
  
3.  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の別のインスタンスでカスタム アセンブリ コードを開いた状態で、カスタム アセンブリを使用するレポート プロジェクトを開きます。  
  
4.  カスタム アセンブリ プロジェクトを含む [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] のインスタンスに移動し、コードに複数のブレークポイントを設定します。  
  
5.  カスタム アセンブリ プロジェクトをまだアクティブなウィンドウ、をクリックして**プロセスにアタッチする**上、**デバッグ**メニュー。  
  
     **プロセスにアタッチする**ダイアログ ボックスが開きます。  
  
6.  、プロセスの一覧から、レポート プロジェクトに対応する devenv.exe プロセスを選択し、をクリックして**アタッチ**です。  
  
7.  カスタム アセンブリのレポートで使用する式を定義し、レポートを設計します。  
  
8.  レポートのデザインが完了したらをクリックして、**プレビュー**タブです。  
  
     レポートが実行され、カスタム アセンブリ コードが定義済みのブレークポイントで停止します。  
  
    > [!NOTE]  
    >  使用して、**プレビュー**  タブでは、アセンブリのコード アクセス許可は強制されません。 コード アクセス セキュリティ エラーが含まれている、完全なテスト対象のレポート プロジェクトを開始、 **DebugLocal**構成設定。  
  
9. F11 キーを使用してコードを実行します。 使用したデバッグの詳細については[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]を参照してください、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]ドキュメント。  
  
## <a name="see-also"></a>参照  
 [レポートでカスタム アセンブリの使用](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
