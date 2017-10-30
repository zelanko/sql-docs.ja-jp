---
title: "Excel データ ソース (SQL Server インポートおよびエクスポート ウィザード) への接続 |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43fbaca0-36d8-4583-9056-af7010209b87
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: b4411fdd2337d93f15b149febf845fb7b0762c40
ms.contentlocale: ja-jp
ms.lasthandoff: 08/28/2017

---
# <a name="connect-to-an-excel-data-source-sql-server-import-and-export-wizard"></a>Excel データ ソース (SQL Server インポートおよびエクスポート ウィザード) への接続します。
このトピックに接続する方法、 **Excel**データ ソースから、**データ ソースを選択**または**変換先の選択**SQL Server インポートおよびエクスポート ウィザードのページです。

Microsoft Excel ブックへの接続例を次のスクリーン ショットに示します。

![Excel 接続](../../integration-services/import-export-data/media/excel-connection.png) 

## <a name="options-to-specify"></a>指定するオプション

> [!NOTE]
> このデータ プロバイダーの接続オプションは、Excel が、ソースまたは変換先であるかどうかは同じです。 表示オプションは、両方で同じ、**データ ソースを選択**と**変換先の選択**ウィザードのページです。

**[Excel ファイル パス]**  
 Excel ファイルのパスとファイル名を指定します。 例:
-   ローカル コンピューター上のファイルの**c:\\MyData.xlsx**です。
-   ネットワーク共有上のファイルの **\\ \\Sales\\データベース\\Northwind.xlsx**です。

または、**[参照]** をクリックします。  
  
 **参照**  
 **[ファイルを開く]** ダイアログ ボックスを使用して、ワークシートを検索します。  

> [!NOTE]
> パスワードで保護された Excel ファイルはウィザードで開くことができません。

 **Excel バージョン**  
ソース ブックで使用される Excel のバージョンを選択します。

> [!IMPORTANT]
> ダウンロードして Excel ファイルに接続する追加のファイルをインストールする必要があります。 参照してください[Excel への接続に必要なファイルを取得](#officeDownloads)の詳細については、このページにします。

**[先頭行に列名を含める]**  
データの最初の行が列の名前を含むかどうかを示します。
-   データには列名が含まれていない場合は、このオプションを有効にするウィザードは ソース データの最初の行を列名として扱います。
-   データには、列名が含まれています。 このオプションを無効にする場合は、ウィザードによって、列名の行がデータの最初の行として扱われます。

データに列名が必要がないことを指定する場合、ウィザードは F1、f2 キー、およびなど、列見出しとして使用します。

## <a name="i-dont-see-excel-in-the-list-of-data-sources"></a>Excel データ ソースの一覧に表示されません。
Excel は、データ ソースの一覧に表示されない場合、は、ウィザードを実行して、64 ビットか。 Excel および Access のプロバイダーは、通常、32 ビットし、64 ビットのウィザードでは表示されません。 代わりに 32 ビットのウィザードを実行します。

> [!NOTE]
> 64 ビット バージョンの SQL Server インポートおよびエクスポート ウィザードを使用するのには、SQL Server をインストールする必要があります。 SQL Server Data Tools (SSDT) および SQL Server Management Studio (SSMS) は 32 ビット アプリケーションであり、32 ビット バージョンのウィザードを含む、32 ビット ファイルのインストールのみです。

## <a name="officeDownloads"></a>Excel への接続に必要なファイルを取得します。  
Microsoft Office などデータ ソース、Excel、アクセスがまだインストールしていない場合の接続コンポーネントをダウンロードする必要があります。 両方の Excel および Access ファイルの接続コンポーネントの最新バージョンをダウンロード: [Microsoft Access データベース エンジン 2016 再頒布可能パッケージ](https://www.microsoft.com/download/details.aspx?id=54920)です。
  
最新のバージョンのコンポーネントは、以前のバージョンの Excel で作成されたファイルを開くことができます。

コンピューターには、Office の 32 ビット バージョンが存在する場合、コンポーネントの 32 ビット バージョンをインストールする必要があるし、およびも 32 ビット モードでパッケージを実行することを確認する必要があります。

Office 365 サブスクリプションがある場合は、し、Microsoft Access 2016 ランタイムではなく、Access データベース エンジン 2016 再頒布可能パッケージをダウンロードすることを確認します。 インストーラーを実行するときに、Office 実行するための コンポーネントと、ダウンロード サイド バイ サイドをインストールすることはできません、エラー メッセージを参照してください可能性があります。 このエラー メッセージをバイパスするには、コマンド プロンプト ウィンドウを開きを実行している quiet モードでインストールを実行します。 します。EXE ファイルと共にダウンロードした、`/quiet`スイッチします。 例:

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`

## <a name="see-also"></a>参照
[データ ソースを選択します。](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[変換先を選択します。](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


