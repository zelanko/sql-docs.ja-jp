---
title: "Excel データ ソースに接続する (SQL Server インポートおよびエクスポート ウィザード) | Microsoft Docs"
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43fbaca0-36d8-4583-9056-af7010209b87
caps.latest.revision: "12"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 2aeb225037970b8a77169db18c204ecf6d4c19d6
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="connect-to-an-excel-data-source-sql-server-import-and-export-wizard"></a>Excel データ ソースに接続する (SQL Server インポートおよびエクスポート ウィザード)
このトピックでは、SQL Server インポートおよびエクスポート ウィザードの **[データ ソースの選択]** ページまたは **[変換先の選択]** ページから **Microsoft Excel** データ ソースに接続する方法を説明します。

Microsoft Excel ブックへの接続例を次のスクリーン ショットに示します。

![Excel 接続](../../integration-services/import-export-data/media/excel-connection.png) 

## <a name="options-to-specify"></a>指定するオプション

> [!NOTE]
> このデータ プロバイダーの接続オプションは、Excel が変換元または変換先の場合でも同じです。 つまり、表示されるオプションは、ウィザードの **[データ ソースの選択]** ページまたは **[変換先の選択]** ページともに同じです。

**[Excel ファイル パス]**  
 Excel ファイルのパスとファイル名を指定します。 例:
-   ローカル コンピューター上の上のファイルの場合、**C:\\MyData.xlsx** です。
-   ネットワーク共有上のファイルの場合、**\\\\Sales\\Database\\Northwind.xlsx** です。

または、**[参照]** をクリックします。  
  
 **参照**  
 **[ファイルを開く]** ダイアログ ボックスを使用して、ワークシートを検索します。  

> [!NOTE]
> パスワードで保護された Excel ファイルはウィザードで開くことができません。

 **Excel バージョン**  
ソース ブックで使用される Excel のバージョンを選択します。

> [!IMPORTANT]
> Excel ファイルに接続するために追加のファイルのダウンロードとインストールが必要になる場合もあります。 詳細については、このページの「[Excel に接続するために必要なファイルを取得する](#officeDownloads)」を参照してください。

**[先頭行に列名を含める]**  
データの最初の行に列名が含まれるかどうかを指定します。
-   データに列名が含まれていないのにこのオプションを有効にすると、ウィザードではソース データの最初の行が列名として扱われます。
-   データに列名が含まれているのにこのオプションを無効にすると、ウィザードでは列名の行がデータの最初の行として扱われます。

データに列名を付けない場合、ウィザードでは列見出しとして F1、F2 などが使用されます。

## <a name="i-dont-see-excel-in-the-list-of-data-sources"></a>データ ソースのリストに Excel が表示されない
データ ソースのリストに Excel が表示されない場合は、64 ビットのウィザードを実行していないか確認してください。 Excel と Access のプロバイダーは、通常 32 ビットで、64 ビットのウィザードでは表示されません。 代わりに 32 ビットのウィザードを実行します。

> [!NOTE]
> 64 ビット バージョンの SQL Server インポートおよびエクスポート ウィザードを使用するには、SQL Server をインストールする必要があります。 SQL Server Data Tools (SSDT) および SQL Server Management Studio (SSMS) は 32 ビット アプリケーションであり、32 ビット バージョンのウィザードを含む、32 ビット ファイルのみがインストールされます。

## <a name="officeDownloads"></a>Excel に接続するために必要なファイルを取得する  
Access と Excel を含む Microsoft Office データ ソース用の接続コンポーネントがまだインストールされていない場合は、必要に応じてダウンロードします。 [Microsoft Access データベース エンジン 2016 再頒布可能パッケージ](https://www.microsoft.com/download/details.aspx?id=54920)で、Excel と Access の両方のファイルの最新バージョンの接続コンポーネントをダウンロードします。
  
以前のバージョンの Excel で作成したファイルは、最新バージョンのコンポーネントで開くことができます。

コンピューターに 32 ビット バージョンの Office が存在する場合は、32 ビット バージョンのコンポーネントをインストールする必要があるほか、32 ビット モードでパッケージが実行されるようにする必要があります。

Office 365 サブスクリプションがある場合は、Microsoft Access 2016 ランタイムではなく、必ず Access データベース エンジン 2016 再頒布可能パッケージをダウンロードしてください。 インストーラーを実行するときに、ダウンロードを Office のクイック実行コンポーネントとサイド バイ サイドでインストールできないことを示すエラー メッセージが表示される場合があります。 このエラー メッセージを回避するには、コマンド プロンプト ウィンドウを開き、`/quiet` スイッチを使用してダウンロードした .EXE ファイルを実行して、Quiet モードでインストールを実行します。 例:

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`

## <a name="see-also"></a>参照
[データ ソースの選択](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[変換先の選択](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)

