---
title: "Excel 接続マネージャー | Microsoft Docs"
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.dts.designer.excelconnection.f1
helpviewer_keywords:
- files [Integration Services], connections
- connections [Integration Services], Excel
- Excel [Integration Services]
- connection managers [Integration Services], Excel
ms.assetid: 667419f2-74fb-4b50-b963-9197d1368cda
caps.latest.revision: "41"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 5785a2753b61cde59a5ed157d697b05a93796fc7
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="excel-connection-manager"></a>Excel 接続マネージャー
  Excel 接続マネージャーを使用すると、パッケージは既存の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel ブック ファイルに接続できます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に含まれる Excel ソースと Excel 変換先は、Excel 接続マネージャーを使用します。  
  
 Excel 接続マネージャーをパッケージに追加するときに、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] により、実行時に Excel 接続として解決される接続マネージャーを作成し、接続マネージャーのプロパティを設定して、接続マネージャーをパッケージの **Connections** コレクションに追加します。  
  
 接続マネージャーの **ConnectionManagerType** プロパティは、 **EXCEL**に設定されます。  
  
## <a name="configuration-of-the-excel-connection-manager"></a>Excel 接続マネージャーの構成  
 Excel 接続マネージャーは、次の方法で構成できます。  
  
-   Excel ブック ファイルのパスを指定します。  
  
    > [!NOTE]  
    >  パスワードで保護された Excel ファイルには接続できません。  
  
-   ファイルの作成に使用した Excel のバージョンを指定します。  
  
-   選択したワークシート内または範囲内でアクセスするデータの最初の行に、列名が格納されているかどうかを示します。  
  
 Excel ソースによって Excel 接続マネージャーが使用された場合は、抽出したデータに列名が含められます。 Excel 変換先によって使用された場合は、出力されたデータに列名が含められます。  
  
 Excel ソースおよび Excel 変換先の動作の詳細については、「 [Excel ソース](../../integration-services/data-flow/excel-source.md) 」および「 [Excel 変換先](../../integration-services/data-flow/excel-destination.md)」を参照してください。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [Excel 接続マネージャー](../../integration-services/connection-manager/excel-connection-manager-editor.md)」を参照してください。  
  
 プログラムによる接続マネージャーの構成の詳細については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」および「 [プログラムによる接続の追加](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)に設定されます。  
  
 Excel ファイルのグループによるループ処理については、「 [Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)」をご覧ください。  
  
## <a name="excel-connection-manager-editor"></a>Excel 接続マネージャー
  **[Excel 接続マネージャー]** ダイアログ ボックスを使用すると、既存または新規の [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] ブック ファイルへの接続を追加できます。  
  
 Excel 接続マネージャーの詳細については、「 [Excel Connection Manager](../../integration-services/connection-manager/excel-connection-manager.md)」を参照してください。  
  
### <a name="options"></a>オプション  
 **[Excel ファイル パス]**  
 既存または新規の Excel ブック ファイル (.xls) のパスおよびファイル名を入力します。  
  
> [!NOTE]  
>  パスワードで保護された Excel ファイルには接続できません。  
  
> [!WARNING]  
>  既存ではない新規のファイルを示す **[Excel 接続]** を選択し、 **[Excel シートの名前]** で **[新規]** をクリックすると、 **Excel 変換先エディター**は自動的に Excel ファイルを作成します。  
  
 **参照**  
 **[開く]** ダイアログ ボックスを使用して、Excel ファイルが存在するフォルダー、または新しいファイルを作成するフォルダーを指定します。  
  
 **[Excel バージョン]**  
 ファイルを作成するために使用した Microsoft Excel のバージョンを指定します。  
  
 **[先頭行に列名を含める]**  
 選択されているワークシートのデータの 1 行目に列名が含まれているかどうかを指定します。 このオプションの既定値は **[true]**です。  
  
## <a name="connectivity-components-for-microsoft-excel-and-access-files"></a>Microsoft Excel および Access ファイルの接続コンポーネント
  
Microsoft Office ファイルの接続コンポーネントがまだインストールされていない場合は、必要に応じてダウンロードします。 [Microsoft Access データベース エンジン 2016 再頒布可能パッケージ](https://www.microsoft.com/download/details.aspx?id=54920)で、Excel と Access の両方のファイルの最新バージョンの接続コンポーネントをダウンロードします。
  
以前のバージョンの Excel で作成したファイルは、最新バージョンのコンポーネントで開くことができます。

コンピューターに 32 ビット バージョンの Office が存在する場合は、32 ビット バージョンのコンポーネントをインストールする必要があるほか、32 ビット モードでパッケージが実行されるようにする必要があります。

Office 365 サブスクリプションがある場合は、Microsoft Access 2016 ランタイムではなく、必ず Access データベース エンジン 2016 再頒布可能パッケージをダウンロードしてください。 インストーラーを実行するときに、ダウンロードを Office のクイック実行コンポーネントとサイド バイ サイドでインストールできないことを示すエラー メッセージが表示される場合があります。 このエラー メッセージを回避するには、コマンド プロンプト ウィンドウを開き、`/quiet` スイッチを使用してダウンロードした .EXE ファイルを実行して、Quiet モードでインストールを実行します。 例:

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`
  
## <a name="related-tasks"></a>関連タスク  
  
-   [Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
-   [Excel ブックに接続する](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)  
  
  
