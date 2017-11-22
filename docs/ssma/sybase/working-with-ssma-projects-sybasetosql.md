---
title: "SSMA プロジェクト (SybaseToSQL) の使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 11091d95-c488-48c3-891a-743cac94ac93
caps.latest.revision: "10"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d122e966ec77c7a0d7e8f70dd3145d81bdfbcef2
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="working-with-ssma-projects-sybasetosql"></a>SSMA プロジェクト (SybaseToSQL) での作業
Sybase Adaptive Server Enterprise (ASE) データベースを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SQL Azure では、まずプロジェクトを作成する SSMA またはします。 プロジェクトに移行する必要のある ASE データベースに関するメタデータを含むファイルは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure でのターゲット インスタンスに関するメタデータ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure 移行済みのオブジェクトとデータを受け取る[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure 接続情報、およびプロジェクトの設定。  
  
切断されているプロジェクトを開くときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 オフラインで作業できます。 再接続できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 詳細については、次を参照してください[SQL Server &#40; に接続する。SybaseToSQL &#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)  /  [Azure SQL DB &#40; に接続します。SybaseToSQL &#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).  
  
## <a name="reviewing-default-project-settings"></a>既定のプロジェクト設定を確認します。  
SSMA には変換と、データの移行し ASE と SSMA を同期するデータベース オブジェクトを読み込み、いくつかのオプションが含まれていますと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 これらのオプションの既定の設定は、多くのユーザーに適しています。 ただし、新しい SSMA プロジェクトを作成する前にする必要がありますオプションを確認し、する場合、すべての新しいプロジェクトに使用される既定値を変更します。  
  
**既定のプロジェクト設定を確認するには**  
  
1.  **ツール**メニューの **プロジェクト設定の既定の**します。  
  
2.  プロジェクトの種類を選択して**移行のターゲット バージョン**どの設定を表示または変更するために必要としをクリックしてドロップダウン**全般** タブ。  
  
3.  左側のウィンドウでをクリックして**変換**です。  
  
4.  右側のウィンドウで、必要に応じてオプションを変更する、オプションを確認します。 これらのオプションの詳細については、次を参照してください。[プロジェクトの設定 &#40;です。変換&#41;&#40;です。SybaseToSQL &#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md).  
  
5.  移行、SQL Azure、オブジェクトの読み込み、GUI、および種類のマッピングのページの手順 1. ~ 3. を繰り返します。  
  
    -   移行オプションについては、次を参照してください。[プロジェクトの設定 &#40;です。移行&#41;&#40;です。SybaseToSQL &#41;](../../ssma/sybase/project-settings-migration-sybasetosql.md).  
  
    -   オブジェクトを読み込むためのオプションについては[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を参照してください[プロジェクトの設定 &#40;です。同期 &#41;&#40;です。SybaseToSQL &#41;](../../ssma/sybase/project-settings-synchronization-sybasetosql.md).  
  
    -   フル インストール オプションの詳細については、次を参照してください。[プロジェクトの設定 &#40;です。GUI &#41;&#40;です。SybaseToSQL &#41;](../../ssma/sybase/project-settings-gui-sybasetosql.md).  
  
    -   データ型マッピングの設定の詳細についてをクリックして[プロジェクトの設定 &#40;です。型のマッピング &#41;&#40;です。SybaseToSQL &#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md).  
  
    -   SQL Azure のオプションの詳細については、次を参照してください。[プロジェクトの設定 &#40;です。Azure SQL DB &#41;&#40;です。SybaseToSQL &#41;](../../ssma/sybase/project-settings-azure-sql-db-sybasetosql.md).  
  
    > [!NOTE]  
    > SQL Azure の設定が選択した場合にのみ表示されます**SQL Azure への移行**してプロジェクトを作成します。  
  
## <a name="creating-new-projects"></a>新しいプロジェクトの作成  
ASE データベースからデータを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure、する必要がありますまずプロジェクトを作成します。  
  
**プロジェクトを作成するには**  
  
1.  **[ファイル]** メニューの **[新しいプロジェクト]** を選択します。  
  
    **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  **名前**ボックスで、プロジェクトの名前を入力します。  
  
3.  **場所**ボックス入力するか、プロジェクトのフォルダーを選択します。  
  
4.  **移行に**ドロップダウンで、対象のバージョンを選択して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]移行に使用します。 使用可能なオプションは次のとおりです。  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016  
  
    -   Azure SQL DB  
  
クリックして**OK**です。  
  
## <a name="customizing-project-settings"></a>プロジェクト設定のカスタマイズ  
すべての新しい SSMA プロジェクトに適用される既定のプロジェクト設定を定義するだけでなく、各プロジェクトの設定をカスタマイズできます。 詳細については、次を参照してください。[プロジェクト オプションの設定 &#40;です。SybaseToSQL &#41;](../../ssma/sybase/setting-project-options-sybasetosql.md).  
  
ソースとターゲット データベース間のデータ型マッピングをカスタマイズする場合は、プロジェクト、データベース、またはオブジェクト レベルでは、マッピングを定義できます。 型のマッピングの詳細については、次を参照してください。[マッピング Sybase ASE と SQL Server データ型 &#40;です。SybaseToSQL &#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
## <a name="saving-projects"></a>プロジェクトの保存  
プロジェクトを保存すると、SSMA は、プロジェクト設定、および必要に応じて、プロジェクト ファイルに、データベースのメタデータを保持します。  
  
**プロジェクトを保存するには**  
  
-   **ファイル**メニューの **プロジェクトの保存**です。  
  
    プロジェクト内のデータベースが変更されたか、変換されていない場合、SSMA は、プロジェクトにメタデータを保存することを求められます。 メタデータの保存と、オフラインで作業して、テクニカル サポート担当者を含む、他のユーザーに完全なプロジェクト ファイルを送信します。 メタデータを保存するメッセージが表示されたら、次の操作を行います。  
  
    1.  各データベースの状態を示す**メタデータがありません**データベース名の横にあるチェック ボックスをオンにします。  
  
        メタデータの保存には数分かかる場合があります。 この時点でメタデータを保存したくない場合は、チェック ボックスをオンされません。  
  
    2.  クリックして、**保存**ボタンをクリックします。  
  
        SSMA は、Sybase ASE スキーマが解析され、プロジェクト ファイルにメタデータを保存します。  
  
## <a name="opening-projects"></a>プロジェクトを開く  
プロジェクトを開くときに、切断されていると ASE から[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 オフラインで作業できます。 メタデータを更新するにデータベース オブジェクトを読み込む[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 データを移行する ASE に再接続する必要がありますと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。  
  
**プロジェクトを開く**  
  
1.  次の手順のいずれかを使用します。  
  
    -   **ファイル** メニューのをポイント**最近使ったプロジェクト**、し、開きたいプロジェクトを選択します。  
  
    -   **ファイル**メニューの **プロジェクトを開く**.s2ssproj プロジェクト ファイルを探し、ファイルを選択し、をクリックして**開く**です。  
  
2.  ASE への再接続、**ファイル**メニューの  **sybase 再接続**です。  
  
3.  再接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure で、**ファイル**メニューの  **SQL Server に再接続** / **SQL Azure への再接続**です。  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次の手順が、 [Sybase ASE への接続](http://msdn.microsoft.com/en-us/a45a2330-9175-4c9e-af38-ef920e350614)です。  
  
## <a name="see-also"></a>参照  
[SQL Server - Azure SQL DB &#40; への Sybase ASE データベースの移行SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
[Sybase ASE &#40; に接続します。SybaseToSQL &#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md)  
[SQL Server &#40; に接続します。SybaseToSQL &#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)  
[Azure SQL DB &#40; に接続します。SybaseToSQL &#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)  
  
