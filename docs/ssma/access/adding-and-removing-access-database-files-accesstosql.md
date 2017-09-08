---
title: "追加して、アクセスを削除してデータベース ファイル (AccessToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Access databases
- adding Access files
- adding and removing Access databases
- browsing Access metadata
- browsing metadata, Access databases
- connecting, Access databases
- databases
- files, adding and removing
- finding Access databases
- finding database files
- locating database files
- metadata
- metadata, browsing
- metadata, refreshing
- refreshing metadata
- removing Access files
- scanning for database files
- searching for database files
ms.assetid: e944c740-4c8a-4bc1-b0ed-be57bc06dced
caps.latest.revision: 15
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 24d93c5851e2d4192a32e0684a53b7939cc4c371
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="adding-and-removing-access-database-files-accesstosql"></a>追加して、Access データベース ファイル (AccessToSQL) を削除します。
アクセス データを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure、SSMA プロジェクトに 1 つまたは複数の Access データベースを追加する必要があります。 これらのデータベースは、Access 97 以降にする必要があります。 アクセスの以前のバージョンからのデータベースがある場合は、新しいバージョンにデータベースを変換する必要があります。 これを行うを開き、SSMA を追加する前に、Access 97 またはそれ以降のバージョンでデータベースを保存しています。  
  
## <a name="what-happens-when-you-add-access-database-files"></a>新機能は、Access データベース ファイルを追加するとどうなりますか。  
SSMA プロジェクトに Access データベースを追加して SSMA はデータベースのメタデータを読み取ってプロジェクト ファイルにこのメタデータを追加します。 このメタデータは、データベースとそのオブジェクトについて説明します。 SSMA は、オブジェクトに変換するときに、メタデータを使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure の構文にデータを移行したときと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 メタデータ エクスプ ローラーでのアクセスには、このメタデータを参照して、個々 のデータベース オブジェクトのプロパティを確認できます。  
  
> [!NOTE]  
> Access データベースは、複数のファイルに分割することができます。 テーブルを含んでいるバックエンド データベースとフロント エンドを含むデータベースをクエリ、フォーム、レポート、マクロ、モジュール、およびショートカットです。 分割データベースを移行する場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure、SSMA をフロント エンド データベースを追加します。  
  
## <a name="permissions-that-are-required-by-ssma"></a>SSMA によって必要なアクセス許可  
Access データベースを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure、ユーザー グループと管理者ユーザーは、管理アクセス許可が必要です。 ワークグループの保護でデータベースを移行する方法については、次を参照してください[Access データベースを移行の準備をしています。](http://msdn.microsoft.com/en-us/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)  
  
## <a name="selecting-databases-to-add"></a>追加するデータベースの選択  
SSMA プロジェクトに 1 つまたは複数のデータベースを追加して、すべて 1 つの既知の場所には場合、は、次の手順を使用して、ファイルを追加できます。  
  
**個々 のデータベース ファイルを追加するには**  
  
1.  **ファイル** メニューのをクリックして**データベースの追加**です。  
  
2.  **開く** ダイアログ ボックスで、データベース ファイルまたはファイルを含むフォルダーに移動します。  
  
3.  をクリックし、追加するファイルを選択**開く**です。  
  
## <a name="finding-databases-to-add"></a>追加するデータベースを検索します。  
複数データベースにアクセスを別のフォルダーから、SSMA プロジェクトに追加する場合や、ファイルを検索しますが、1 つのファイルを追加する、複数ファイルの 1 つを見つけて、プロジェクトに追加する手順を行うことができます。  
  
**検索し、データベースを追加するには**  
  
1.  **ファイル** メニューのをクリックして**検索データベース**です。  
  
2.  ウィザードで、検索データベースには、ドライブ、ファイル パスまたは UNC パスを検索する文字列の名前を入力します。 またはをクリックして**参照**ドライブやネットワーク フォルダーを検索します。  
  
3.  をクリックして**追加**場所を一覧に追加します。  
  
    複数の検索場所を追加する前の 2 つの手順を繰り返します。  
  
4.  必要に応じて、返されるデータベースの一覧を絞り込む検索条件を追加します。  
  
    > [!IMPORTANT]  
    > **ファイル名の全部または一部**テキスト ボックスでは、ワイルドカード文字はサポートされません。  
  
5.  をクリックして**スキャン**です。  
  
    スキャンのページが表示されます。 検出されたデータベースおよび検索の進行状況が表示されます。 検索を停止する をクリックして**停止**です。  
  
6.  ファイルの選択 ページで、プロジェクトに追加する必要のあるデータベースを選択します。  
  
    使用することができます、**すべて選択**と**すべてクリア**をオンまたはオフのすべてのデータベース一覧の上部にあるボタンです。 CTRL キーを押しながら複数のデータベースを選択したり、さまざまなデータベースを選択するように、SHIFT キーを保持できます。  
  
7.  **[次へ]**をクリックします。  
  
8.  確認してください ページで、をクリックして**完了**です。  
  
## <a name="browsing-access-metadata"></a>参照メタデータにアクセス  
Access データベースをプロジェクトに追加すると、アクセス メタデータ エクスプ ローラーでプロジェクトのメタデータが表示されます。 データベースと、エクスプ ローラーでデータベース オブジェクトの階層を参照することができます。  
  
**メタデータを参照するには**  
  
1.  メタデータ エクスプ ローラーでのアクセス、**アクセス メタベース**、順に展開**データベース**です。  
  
2.  確認、およびの順に展開するデータベースを展開**クエリ**です。  
  
    クエリの一覧を確認します。 クエリを選択する場合、 **SQL**  タブおよび**プロパティ**右側のウィンドウでタブが表示されます。  
  
3.  展開**テーブル**し、テーブルを選択します。  
  
    4 つのタブが表示されることに注意してください:**テーブル**、**型マッピング**、**プロパティ**、および**データ**です。  
  
4.  テーブルを展開し、**キー**、キーを選択します。  
  
    キー プロパティは、右側のペインに表示されます。  
  
5.  展開**インデックス**、し、インデックスを選択します。  
  
    インデックスのプロパティは、右側のペインに表示されます。  
  
## <a name="refreshing-databases"></a>データベースを更新します。  
そのファイルを追加した後に、Access データベースが変更された場合は、Access データベースからメタデータを更新できます。  
  
**アクセスのメタデータを更新するには**  
  
-   アクセス メタデータ エクスプ ローラーで、データベースを右クリックし、**データベースから更新**です。  
  
## <a name="removing-databases"></a>データベースの削除  
Access データベースは、次の手順で、プロジェクトから削除できます。  
  
**プロジェクトからデータベースを削除するには**  
  
1.  メタデータ エクスプ ローラーでのアクセス、**アクセス メタベース**、順に展開**データベース**です。  
  
2.  データベースを右クリックし、**データベースの削除**です。  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次の手順が、 [SQL Server に接続](http://msdn.microsoft.com/en-us/bb8c4bde-cfc2-4636-92ae-5dd24abe9536)です。  
  
## <a name="see-also"></a>参照  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[作成して、プロジェクトの管理](http://msdn.microsoft.com/en-us/f2d1f0b0-5394-4adb-b3f3-abd71eb68ca7)  
  

