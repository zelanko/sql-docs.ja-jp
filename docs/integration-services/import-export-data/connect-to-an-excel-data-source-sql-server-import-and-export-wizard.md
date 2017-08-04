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
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d744e84aa2b4ae0462a5d5a1e4453a9e86abb890
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

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
> 選択したバージョンの Excel に接続するために追加のファイルのダウンロード、インストールが必要になる場合もあります。 参照してください[Excel への接続に必要なファイルを取得](#officeDownloads)の詳細については、このページにします。

バージョンを指定するときに問題がある場合は、以前のバージョンでも、別のバージョンを指定してください。 たとえば、Microsoft Office 365 サブスクリプションがあるために、Office 2016 データ プロバイダーをインストールすることができません。 Excel 2016 とアクセス 2016年用データ プロバイダーは、Microsoft Office のデスクトップ バージョンにのみインストールできます。 この例では、Excel 2016 ではなく Excel 2013 を指定することができます。 2 つのバージョンのプロバイダーは、機能的に等価です。 Office 2016 ランタイムのこのような制限に記載されて[このブログの投稿](https://blogs.office.com/2015/12/16/access-2016-runtime-is-now-available-for-download/)です。

**[先頭行に列名を含める]**  
データの最初の行が列の名前を含むかどうかを示します。
-   データには列名が含まれていない場合は、このオプションを有効にするウィザードは ソース データの最初の行を列名として扱います。
-   データには、列名が含まれています。 このオプションを無効にする場合は、ウィザードによって、列名の行がデータの最初の行として扱われます。

データに列名が必要がないことを指定する場合、ウィザードは F1、f2 キー、およびなど、列見出しとして使用します。

## <a name="i-dont-see-excel-in-the-list-of-data-sources"></a>Excel データ ソースの一覧に表示されません。
Excel は、データ ソースの一覧に表示されない場合、は、ウィザードを実行して、64 ビットか。 Excel および Access のプロバイダーは、通常、32 ビットし、64 ビットのウィザードでは表示されません。 代わりに 32 ビットのウィザードを実行します。

## <a name="officeDownloads"></a>Excel への接続に必要なファイルを取得します。  
Microsoft Office などデータ ソース、Excel、アクセスがまだインストールしていない場合の接続コンポーネントをダウンロードする必要があります。

以前のバージョンのプログラムで作成したファイルは、新しいバージョンのコンポーネントで開くことができます。 場合によっては、新しいバージョンのプログラムで作成したファイルを古いバージョンのコンポーネントで開くこともできます。 たとえば場合、Office 2016 コンポーネントをインストールすることはできません、Office 2013 コンポーネント代わりに使用します。 2 つのバージョンのプロバイダーは、機能的に等価です。 Office 2016 ランタイムのこのような制限に記載されて[このブログの投稿](https://blogs.office.com/2015/12/16/access-2016-runtime-is-now-available-for-download/)です。

コンピューターが 32 ビット バージョンの Office - これは 64 ビット コンピューター上であっても、一般的な場合は、32 ビット バージョンのコンポーネントをインストールする必要があります。 また、32 ビットのウィザードを実行するか、または 32 ビット モードでウィザードが作成される SQL Server Integration Services パッケージを実行する必要があります。 
 
|Microsoft Office のバージョン|ダウンロード|  
|------------------------------|--------------|  
|2016|[Microsoft Access 2016 Runtime](https://www.microsoft.com/download/details.aspx?id=50040)|
|2013|[Microsoft Access 2013 Runtime](http://www.microsoft.com/download/details.aspx?id=39358)|
|2010|[Microsoft Access 2010 Runtime](https://www.microsoft.com/download/details.aspx?id=10910)|  
|2007|[2007 Office system ドライバー: データ接続コンポーネント](https://www.microsoft.com/download/details.aspx?id=23734)|  

## <a name="see-also"></a>参照
[データ ソースを選択します。](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[変換先を選択します。](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


