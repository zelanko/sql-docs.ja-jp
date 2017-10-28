---
title: "作成するプロジェクトと管理 (AccessToSQL) |Microsoft ドキュメント"
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
- creating projects
- new projects
- opening projects
- projects
- projects, creating and managing
- saving metadata
- saving projects
ms.assetid: f2d1f0b0-5394-4adb-b3f3-abd71eb68ca7
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: bc89d40afd125aef5c874c4578bb153cdfcf6993
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="creating-and-managing-projects-accesstosql"></a>作成して、プロジェクト (AccessToSQL) の管理
Access データベースを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure、SSMA プロジェクト最初に作成する必要があります。 プロジェクトに移行する Access データベースに関するメタデータを含むファイルは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure でのターゲット インスタンスに関するメタデータ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure 移行済みのオブジェクトとデータを受け取る[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]接続情報、およびプロジェクトの設定。  
  
## <a name="reviewing-default-project-settings"></a>既定のプロジェクト設定を確認します。  
SSMA には、データを変換したり、変換、およびデータベース オブジェクトを同期するためのいくつかのオプションが含まれています。 これらのオプションの既定の設定は、多くのユーザーに適しています。 ただし、新しい SSMA プロジェクトを作成する前にする必要がありますオプションを確認し、する場合、すべての新しいプロジェクトに使用される既定の設定を変更します。  
  
**既定のプロジェクト設定を確認するには**  
  
1.  **ツール**メニューの **プロジェクト設定の既定の**します。  
  
2.  プロジェクトの種類を選択して**移行のターゲット バージョン**のどの設定を表示/変更をクリックしてドロップダウン**全般** タブ。  
  
3.  左側のウィンドウでをクリックして**変換**です。  
  
4.  右側のペインで、オプションを確認します。 これらのオプションの詳細については、次を参照してください。[プロジェクトの設定 (変換)](http://msdn.microsoft.com/en-us/bcebc635-c638-4ddb-924c-b9ccfef86388)です。  
  
5.  必要に応じてオプションを変更します。  
  
6.  前の手順を繰り返します、**移行**、 **GUI**、および**型マッピング**ページ。  
  
    -   移行オプションについては、次を参照してください。[プロジェクトの設定 (移行)](http://msdn.microsoft.com/en-us/4caebc9c-8680-4b99-a8fa-89c43161c95d)です。  
  
    -   ユーザー インターフェイス オプションについては、次を参照してください。[プロジェクトの設定 (GUI)](http://msdn.microsoft.com/en-us/cf06baf1-8714-48a3-95dc-781f6ca53693)です。  
  
    -   データ型マッピングの設定の詳細については、次を参照してください。[プロジェクトの設定 (型のマッピング)](http://msdn.microsoft.com/en-us/b87b9683-abed-4677-8c50-18bdba704655)です。  
  
    -   SQL Azure の設定については、次を参照してください。[プロジェクトの設定 (SQL Azure)](http://msdn.microsoft.com/en-us/bbb8a204-d0e4-4f0b-9709-271feb1f136e)です。  
  
**注**プロジェクトを作成するときに SQL Azure への移行を選択する場合にのみに、SQL Azure の設定が使用できます。  
  
## <a name="creating-new-projects"></a>新しいプロジェクトの作成  
SSMA は、既定のプロジェクトを読み込むことがなく開始します。 Access データベースからデータを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure でプロジェクトを作成する必要があります。  
  
**新しいプロジェクトを作成するには**  
  
1.  **[ファイル]** メニューの **[新しいプロジェクト]** を選択します。  
  
    **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  **名前**ボックスで、プロジェクトの名前を入力します。  
  
3.  **場所**ボックス入力するか、プロジェクトのフォルダーの選択  
  
4.  移行にドロップ ダウン、SQL Server 2005 のいずれかを選択/SQL Server 2008/SQL Server 2012/SQL Server 2014/SQL Server 2016/Azure SQL DB、順にクリック**OK**です。  
  
SSMA では、プロジェクト ファイルを作成します。 次の手順を実行できるようになりました[1 つまたは複数の Access データベースを追加する](http://msdn.microsoft.com/en-us/e944c740-4c8a-4bc1-b0ed-be57bc06dced)です。  
  
## <a name="customizing-project-settings"></a>プロジェクト設定のカスタマイズ  
すべての新しい SSMA プロジェクトに適用の既定のプロジェクト設定を定義するだけでなく、各プロジェクトの設定をカスタマイズすることもできます。 詳細については、次を参照してください。[設定の変換と移行オプション](http://msdn.microsoft.com/en-us/0a7304df-2f35-4453-96ef-7ac83dea1167)です。  
  
ソースとターゲット データベース間のデータ型マッピングをカスタマイズする場合は、プロジェクト、データベース、またはオブジェクト レベルでは、マッピングを定義できます。 型のマッピングの詳細については、次を参照してください。[マッピング ソースとターゲットのデータ型](http://msdn.microsoft.com/en-us/b362a075-16e7-423f-b63f-e1e9f02844a9)です。  
  
## <a name="saving-projects"></a>プロジェクトの保存  
プロジェクトを保存するときに、SSMA は、プロジェクト設定、および必要に応じて、プロジェクト ファイルに、データベースのメタデータを保持します。  
  
**プロジェクトを保存するには**  
  
-   **ファイル**メニューの **プロジェクトの保存**です。  
  
    プロジェクト内のデータベースが変更されたか、変換されていない場合、SSMA は、プロジェクトにメタデータを保存することを求められます。 メタデータを保存するには、オフラインで作業することができます。 テクニカル サポート担当者を含む、他のユーザーに完全なプロジェクト ファイルを送信することもできます。 メタデータを保存するメッセージが表示されたら、次の操作を行います。  
  
    1.  各データベースの状態を示す**メタデータがありません**データベース名の横にあるチェック ボックスをオンにします。  
  
        メタデータの保存には数分かかる場合があります。 この時点でメタデータを保存したくない場合は、チェック ボックスをオンされません。  
  
    2.  **[保存]**をクリックします。  
  
        SSMA は、アクセスのスキーマが解析され、プロジェクト ファイルにメタデータを保存します。  
  
## <a name="opening-projects"></a>プロジェクトを開く  
切断されているプロジェクトを開くときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 オフラインで作業できます。 メタデータの読み込みデータベース オブジェクトを更新する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 データを移行するに再接続する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。  
  
**プロジェクトを開く**  
  
1.  次の手順のいずれかを使用します。  
  
    -   **ファイル** メニューのをポイント**最近使ったプロジェクト**、し、開きたいプロジェクトを選択します。  
  
    -   **ファイル**メニューの **プロジェクトを開く**.a2ssproj プロジェクト ファイルを探し、ファイルを選択し、をクリックして**開く**です。  
  
2.  再接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]の**ファイル**メニューの  **SQL Server に再接続**です。  
  
3.  SQL Azure への再接続、**ファイル**メニューの  **SQL Azure に再接続します。**  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次の手順が、 [1 つまたは複数の Access データベースの追加](http://msdn.microsoft.com/en-us/e944c740-4c8a-4bc1-b0ed-be57bc06dced)です。  
  
## <a name="see-also"></a>参照  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[追加して、Access データベース ファイルを削除します。](http://msdn.microsoft.com/en-us/e944c740-4c8a-4bc1-b0ed-be57bc06dced)  
  

