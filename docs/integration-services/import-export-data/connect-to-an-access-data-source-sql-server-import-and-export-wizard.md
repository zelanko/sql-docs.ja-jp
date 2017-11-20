---
title: "Access データ ソース (SQL Server インポートおよびエクスポート ウィザード) への接続 |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: import-export-data
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b44c159a-c33d-4f3c-bdb8-9832f35317c8
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 71bb3914e31259bc95a1116c2db03708c0442e8c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/28/2017

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
> ダウンロードして Access データベースに接続する追加ファイルをインストールする必要があります。 参照してください[アクセスへの接続に必要なファイルを取得](#officeDownloads)の詳細については、このページにします。

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

> [!NOTE]
> 64 ビット バージョンの SQL Server インポートおよびエクスポート ウィザードを使用するのには、SQL Server をインストールする必要があります。 SQL Server Data Tools (SSDT) および SQL Server Management Studio (SSMS) は 32 ビット アプリケーションであり、32 ビット バージョンのウィザードを含む、32 ビット ファイルのインストールのみです。

## <a name="officeDownloads"></a>Access に接続する必要があるファイルを取得します。  
まだインストールしていない場合に、Access や Excel をなど、Microsoft Office のデータ ソースに接続コンポーネントをダウンロードする必要があります。 最新バージョンの Access や Excel の両方のファイルをここで、接続コンポーネントのダウンロード: [Microsoft Access データベース エンジン 2016 再頒布可能パッケージ](https://www.microsoft.com/download/details.aspx?id=54920)です。
  
最新のバージョンのコンポーネントは、以前のバージョンの Access によって作成されたファイルを開くことができます。

コンピューターには、Office の 32 ビット バージョンが存在する場合、コンポーネントの 32 ビット バージョンをインストールする必要があるし、およびも 32 ビット モードでパッケージを実行することを確認する必要があります。

Office 365 サブスクリプションがある場合は、し、Microsoft Access 2016 ランタイムではなく、Access データベース エンジン 2016 再頒布可能パッケージをダウンロードすることを確認します。 インストーラーを実行するときに、Office 実行するための コンポーネントと、ダウンロード サイド バイ サイドをインストールすることはできません、エラー メッセージを参照してください可能性があります。 このエラー メッセージをバイパスするには、コマンド プロンプト ウィンドウを開きを実行している quiet モードでインストールを実行します。 します。EXE ファイルと共にダウンロードした、`/quiet`スイッチします。 例:

`C:\Users\<user name>\Downloads\AccessDatabaseEngine.exe /quiet`

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


