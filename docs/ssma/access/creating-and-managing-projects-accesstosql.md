---
title: プロジェクトの作成と管理 (管理用 Sql) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- creating projects
- new projects
- opening projects
- projects
- projects, creating and managing
- saving metadata
- saving projects
ms.assetid: f2d1f0b0-5394-4adb-b3f3-abd71eb68ca7
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: abbe0746193df3fe341b4f66086291dc1055e11b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68006615"
---
# <a name="creating-and-managing-projects-accesstosql"></a>プロジェクトの作成と管理 (管理用 Sql)
Access データベースをまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Azure に移行するには、まず ssma プロジェクトを作成する必要があります。 このプロジェクトは、移行先[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または SQL Azure のアクセスデータベースに関するメタデータ、移行されたオブジェクトとデータ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続情報、およびプロジェクト設定を受け取る SQL Azure の対象インスタンスに関するメタデータを含むファイルです。  
  
## <a name="reviewing-default-project-settings"></a>既定のプロジェクト設定の確認  
SSMA には、データベースオブジェクトを変換および同期したり、データを変換したりするためのオプションがいくつか用意されています。 これらのオプションの既定の設定は、多くのユーザーに適しています。 ただし、新しい SSMA プロジェクトを作成する前に、オプションを確認し、必要に応じて、すべての新しいプロジェクトで使用される既定の設定を変更する必要があります。  
  
**既定のプロジェクト設定を確認するには**  
  
1.  [**ツール**] メニューの [**既定のプロジェクト設定**] をクリックします。  
  
2.  設定を表示または変更する [**移行ターゲットバージョン**] ドロップダウンでプロジェクトの種類を選択し、[**全般**] タブをクリックします。  
  
3.  左側のウィンドウで、[**変換**] をクリックします。  
  
4.  右ペインで、オプションを確認します。 これらのオプションの詳細については、「[プロジェクトの設定 (変換)](https://msdn.microsoft.com/bcebc635-c638-4ddb-924c-b9ccfef86388)」を参照してください。  
  
5.  必要に応じてオプションを変更します。  
  
6.  **移行**、 **GUI**、および**種類のマッピング**ページに対して、前の手順を繰り返します。  
  
    -   移行オプションの詳細については、「[プロジェクトの設定 (移行)](https://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d)」を参照してください。  
  
    -   ユーザーインターフェイスオプションの詳細については、「[プロジェクトの設定 (GUI)](https://msdn.microsoft.com/cf06baf1-8714-48a3-95dc-781f6ca53693)」を参照してください。  
  
    -   データ型マッピングの設定の詳細については、「[プロジェクトの設定 (型のマッピング)](https://msdn.microsoft.com/b87b9683-abed-4677-8c50-18bdba704655)」を参照してください。  
  
    -   SQL Azure 設定の詳細については、「[プロジェクトの設定 (SQL Azure)](https://msdn.microsoft.com/bbb8a204-d0e4-4f0b-9709-271feb1f136e)」を参照してください。  
  
**メモ**SQL Azure 設定は、プロジェクトの作成中に [SQL Azure に移行] を選択した場合にのみ使用できます。  
  
## <a name="creating-new-projects"></a>新しいプロジェクトの作成  
SSMA は、既定のプロジェクトを読み込まずに起動します。 Access データベースからまたは SQL Azure に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データを移行するには、プロジェクトを作成する必要があります。  
  
**新しいプロジェクトを作成するには**  
  
1.  **[ファイル]** メニューの **[新しいプロジェクト]** を選択します。  
  
    **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  [**名前**] ボックスに、プロジェクトの名前を入力します。  
  
3.  [**場所**] ボックスで、プロジェクトのフォルダーを入力または選択します。  
  
4.  [移行先] ドロップダウンで、SQL Server 2005/SQL Server 2008/SQL Server 2012/SQL Server 2014/SQL Server 2016/Azure SQL DB のいずれかを選択し、[ **OK**] をクリックします。  
  
SSMA により、プロジェクトファイルが作成されます。 これで、 [1 つ以上の Access データベースを追加](adding-and-removing-access-database-files-accesstosql.md)する次の手順を実行できます。  
  
## <a name="customizing-project-settings"></a>プロジェクト設定のカスタマイズ  
すべての新しい SSMA プロジェクトに適用される既定のプロジェクト設定を定義するだけでなく、各プロジェクトの設定をカスタマイズすることもできます。 詳細については、「[変換オプションと移行オプションの設定](setting-conversion-and-migration-options-accesstosql.md)」を参照してください。  
  
ソースデータベースとターゲットデータベース間のデータ型マッピングをカスタマイズする場合は、プロジェクト、データベース、またはオブジェクトレベルでマッピングを定義できます。 型マッピングの詳細については、「[ソースとターゲットのデータ型のマッピング](mapping-source-and-target-data-types-accesstosql.md)」を参照してください。  
  
## <a name="saving-projects"></a>プロジェクトの保存  
プロジェクトを保存すると、SSMA によってプロジェクトの設定が保持され、必要に応じてデータベースのメタデータをプロジェクトファイルに保存できます。  
  
**プロジェクトを保存するには**  
  
-   [**ファイル**] メニューの [**プロジェクトの保存**] をクリックします。  
  
    プロジェクト内のデータベースが変更された場合、または変換されていない場合は、SSMA によってメタデータをプロジェクトに保存するように求められます。 メタデータを保存すると、オフラインで作業できるようになります。 また、テクニカルサポート担当者を含む、他のユーザーに完全なプロジェクトファイルを送信することもできます。 メタデータを保存するかどうかを確認するメッセージが表示されたら、次の手順を実行します。  
  
    1.  [**メタデータが存在しません**] の状態を示すデータベースごとに、データベース名の横にあるチェックボックスをオンにします。  
  
        メタデータの保存には数分かかる場合があります。 この時点でメタデータを保存しない場合は、チェックボックスをオンにしないでください。  
  
    2.  **[Save]** (保存) をクリックします。  
  
        SSMA は、アクセススキーマを解析し、メタデータをプロジェクトファイルに保存します。  
  
## <a name="opening-projects"></a>プロジェクトを開く  
プロジェクトを開くと、そのプロジェクトはまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Azure から切断されます。 これにより、オフラインで作業できるようになります。 メタデータを更新するに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、データベースオブジェクトをまたは SQL Azure に読み込みます。 データを移行するには、また[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は SQL Azure に再接続する必要があります。  
  
**プロジェクトを開くには**  
  
1.  次の手順のいずれかを使用します。  
  
    -   [**ファイル**] メニューの [**最近使ったプロジェクト**] をポイントし、開くプロジェクトを選択します。  
  
    -   [**ファイル**] メニューの [**プロジェクトを開く**] を選択し、a2ssproj プロジェクトファイルを見つけて、ファイルを選択し、[**開く**] をクリックします。  
  
2.  に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]再接続するには、[**ファイル**] メニューの [ **SQL Server に再接続**] を選択します。  
  
3.  SQL Azure に再接続するには、[**ファイル**] メニューの [ **SQL Azure に再接続**] を選択します。  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次の手順では、 [Access データベースを1つ以上追加](adding-and-removing-access-database-files-accesstosql.md)します。  
  
## <a name="see-also"></a>参照  
[Access データベースの SQL Server への移行](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Access データベースファイルの追加と削除](adding-and-removing-access-database-files-accesstosql.md)  
  
