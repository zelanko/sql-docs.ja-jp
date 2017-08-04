---
title: "Access データ ソース (SQL Server インポートおよびエクスポート ウィザード) への接続 |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b44c159a-c33d-4f3c-bdb8-9832f35317c8
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b2a5deb6e6ec95e6f6707abe9ad85374b2334e05
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="connect-to-an-access-data-source-sql-server-import-and-export-wizard"></a>Access データ ソース (SQL Server インポートおよびエクスポート ウィザード) への接続します。
このトピックに接続する方法、 **Access**データ ソースから、**データ ソースを選択**または**変換先の選択**SQL Server インポートおよびエクスポート ウィザードのページです。

Microsoft Access データベースへの接続例を次のスクリーン ショットに示します。 この例でがないユーザー名とパスワードを入力するターゲット データベースは、ワークグループ情報ファイルを使用しないためです。

![アクセスに接続します。](../../integration-services/import-export-data/media/connect-to-access.jpg)

## <a name="options-to-specify"></a>指定するオプション

> [!NOTE]
> このデータ プロバイダーの接続オプションは、アクセスが、ソースまたは変換先であるかどうかは同じです。 表示オプションは、両方で同じ、**データ ソースを選択**と**変換先の選択**ウィザードのページです。

**データ ソース**  
データ プロバイダーの一覧は、Microsoft Access のいくつかのエントリを含めることがあります。 いる最新のバージョン、またはデータベース ファイルを作成したアクセスのバージョンに対応するバージョンを選択します。

|データ ソース|Office のバージョン|
|-------|-------|
|Microsoft Access (Microsoft.ACE.OLEDB.16.0)|Office 2016|
|Microsoft Access (Microsoft.ACE.OLEDB.15.0)|Office 2013|
|Microsoft Access (Microsoft Access データベース エンジン)|Office 2010 および Office 2007|
|Microsoft Access (Jet データベース エンジン)|Office 2007 より前の office バージョン|

> [!IMPORTANT]
> ダウンロードして、選択したアクセスのバージョンに接続する追加のファイルをインストールする必要があります。 参照してください[アクセスへの接続に必要なファイルを取得](#officeDownloads)の詳細については、このページにします。

バージョンを指定するときに問題がある場合は、以前のバージョンでも、別のバージョンを指定してください。 たとえば、Microsoft Office 365 サブスクリプションがあるために、Office 2016 データ プロバイダーをインストールすることができません。 アクセス 2016年と Excel 2016 データ プロバイダーは、Microsoft Office のデスクトップ バージョンにのみインストールできます。 この場合、アクセス 2016年ではなく Access 2013 を指定できます。 2 つのバージョンのプロバイダーは、機能的に等価です。 Office 2016 ランタイムのこのような制限に記載されて[このブログの投稿](https://blogs.office.com/2015/12/16/access-2016-runtime-is-now-available-for-download/)です。

 **[ファイル名]**  
Access ファイルのパスとファイル名を指定します。 たとえば、 **c:\\MyData.mdb** 、ローカル コンピューター上のファイルのまたは **\\ \\Sales\\データベース\\Northwind.mdb**ネットワーク共有上のファイルにします。 または、**[参照]** をクリックします。 

 >   [!NOTE] 
 > クリックすると**参照**Access ファイルを検索する、**開く**ファイルは古いのダイアログ ボックスのフィルター。既定で MDB 形式とファイル拡張子。 ただし、データ プロバイダーで、新しいファイルが開くことができますも。ACCDB 形式およびファイルの拡張子です。
  
 **参照**  
 **[ファイルを開く]** ダイアログ ボックスを使用して、データベース ファイルを検索します。  
  
 **ユーザー名**  
ワークグループ情報ファイルが、データベースと関連付けられている場合は、有効なユーザー名を提供します。  
  
 **Password**  
ワークグループ情報ファイルが、データベースと関連付けられている場合は、ここに、ユーザーのパスワードを提供します。
 
データベースがすべてのユーザーに対して 1 つのパスワードで保護されている場合は、次を参照してください。[パスワードで保護されたデータベース ファイルは、?](#database_password)です。
  
 **高度な**  
データベースのパスワードや既定以外のワークグループ情報ファイルなどの高度なオプションを指定、**データ リンク プロパティ** ダイアログ ボックス。  

## <a name="i-dont-see-access-in-the-list-of-data-sources"></a>データ ソースの一覧で、アクセスが表示されません。
アクセスは、データ ソースの一覧に表示されない場合、は、ウィザードを実行して、64 ビットか。 Excel および Access のプロバイダーは、通常、32 ビットし、64 ビットのウィザードでは表示されません。 代わりに 32 ビットのウィザードを実行します。
  
## <a name="officeDownloads"></a>Access に接続する必要があるファイルを取得します。  
Microsoft Office などデータ ソース、Excel、アクセスがまだインストールしていない場合の接続コンポーネントをダウンロードする必要があります。

以前のバージョンのプログラムで作成したファイルは、新しいバージョンのコンポーネントで開くことができます。 多くの場合、以前のバージョンのコンポーネントは以降のバージョンのプログラムによって作成されるファイルのも開くことができます。 たとえば場合、Office 2016 コンポーネントをインストールすることはできません、Office 2013 コンポーネント代わりに使用します。 2 つのバージョンのプロバイダーは、機能的に等価です。 Office 2016 ランタイムのこのような制限に記載されて[このブログの投稿](https://blogs.office.com/2015/12/16/access-2016-runtime-is-now-available-for-download/)です。

コンピューターが 32 ビット バージョンの Office - これは 64 ビット コンピューター上であっても、一般的な場合は、32 ビット バージョンのコンポーネントをインストールする必要があります。 また、32 ビットのウィザードを実行するか、または 32 ビット モードでウィザードが作成される SQL Server Integration Services パッケージを実行する必要があります。

|Microsoft Office のバージョン|ダウンロード|  
|------------------------------|--------------|  
|2016|[Microsoft Access 2016 Runtime](https://www.microsoft.com/download/details.aspx?id=50040)|
|2013|[Microsoft Access 2013 Runtime](http://www.microsoft.com/download/details.aspx?id=39358)|
|2010|[Microsoft Access 2010 Runtime](https://www.microsoft.com/download/details.aspx?id=10910)|  
|2007|[2007 Office system ドライバー: データ接続コンポーネント](https://www.microsoft.com/download/details.aspx?id=23734)|    

## <a name="database_password"></a>パスワードで保護されたデータベース ファイルですか。
場合によっては、Access データベースがパスワードで保護されたが、ワークグループ情報ファイルが使用されていません。 すべてのユーザーは、同じパスワードを指定する必要があるが、ユーザー名を入力する必要はありません。 データベース パスワードを指定するには、次のように操作します。

1.  **データ ソースを選択**または**変換先の選択** ページで、をクリックして、 **詳細設定**を開く ボタン、**データ リンク プロパティ** ダイアログ ボックス。  
2.  **データ リンク プロパティ**ダイアログ ボックスで、**すべて**タブです。  
3.  プロパティと値の一覧で選択**Jet OLEDB:Database パスワード**です。   
    
    ![アクセスのパスワード、画面 1 を指定します。](../../integration-services/import-export-data/media/specify-access-password-screen-1.jpg) 
4.  をクリックして**値の編集**を開くには、**プロパティの値を編集** ダイアログ ボックス。  
    
    ![アクセスのパスワード、画面 2 を指定します。](../../integration-services/import-export-data/media/specify-access-password-screen-2.jpg)
5.  **プロパティの値を編集** ダイアログ ボックスで、データベースのパスワードを入力します。
6.  をクリックして**[ok]**に戻るには、各ダイアログ ボックスで、**データ ソースを選択**または**変換先を選択**ウィザードのページを続行します。

## <a name="keep-your-autonumber-values-when-you-export-from-access"></a>Access からエクスポートするときに、autonumber 値を保持します。
を変換先テーブルに id 列に挿入されるソース データ内の既存の id 値を許可するのには、選択、 **id の挿入を有効にする**オプション、**列マッピング** ダイアログ ボックス。 既定では、先の id 列通常しないを挿入できるように既存の値。 表示する、**列マッピング**ダイアログ ボックスで、**マッピングを編集**に達すると、 **ソース テーブルおよびビュー**ウィザードのページです。 これらのページを見るを参照してください。 [ソース テーブルおよびビュー](../../integration-services/import-export-data/select-source-tables-and-views-sql-server-import-and-export-wizard.md)と[列マッピング](../../integration-services/import-export-data/column-mappings-sql-server-import-and-export-wizard.md)です。

既存のプライマリ キーが id 列、autonumber 列、または同等の列である場合、既存のプライマリ キー値を保持するには、通常、このオプションを選択する必要があります。 その他の場合、変換先の ID 列には通常、新しい値が割り当てられます。

## <a name="see-also"></a>参照
[データ ソースを選択します。](../../integration-services/import-export-data/choose-a-data-source-sql-server-import-and-export-wizard.md)  
[変換先を選択します。](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)


