---
title: SSMA プロジェクト (SybaseToSQL) の使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 11091d95-c488-48c3-891a-743cac94ac93
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 82691f362769b0bb5f929cf74678f125ce219c5a
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34779528"
---
# <a name="working-with-ssma-projects-sybasetosql"></a>SSMA プロジェクト (SybaseToSQL) での作業
Sybase Adaptive Server Enterprise (ASE) データベースを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SQL Azure では、まずプロジェクトを作成する SSMA またはします。 プロジェクトに移行する必要のある ASE データベースに関するメタデータを含むファイルは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure でのターゲット インスタンスに関するメタデータ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure 移行済みのオブジェクトとデータを受け取る[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure 接続情報、およびプロジェクトの設定。  
  
切断されているプロジェクトを開くときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 オフラインで作業できます。 再接続できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 詳細については、次を参照してください。 [SQL Server に接続する&#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md) / [Azure SQL DB に接続する&#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)です。  
  
## <a name="reviewing-default-project-settings"></a>既定のプロジェクト設定を確認します。  
SSMA には変換と、データの移行し ASE と SSMA を同期するデータベース オブジェクトを読み込み、いくつかのオプションが含まれていますと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 これらのオプションの既定の設定は、多くのユーザーに適しています。 ただし、新しい SSMA プロジェクトを作成する前にする必要がありますオプションを確認し、する場合、すべての新しいプロジェクトに使用される既定値を変更します。  
  
**既定のプロジェクト設定を確認するには**  
  
1.  **ツール**メニューの **プロジェクト設定の既定の**します。  
  
2.  プロジェクトの種類を選択して**移行のターゲット バージョン**どの設定を表示または変更するために必要としをクリックしてドロップダウン**全般** タブ。  
  
3.  左側のウィンドウでをクリックして**変換**です。  
  
4.  右側のウィンドウで、必要に応じてオプションを変更する、オプションを確認します。 これらのオプションの詳細については、次を参照してください。[プロジェクト設定&#40;変換&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md)です。  
  
5.  移行、SQL Azure、オブジェクトの読み込み、GUI、および種類のマッピングのページの手順 1. ~ 3. を繰り返します。  
  
    -   移行オプションについては、次を参照してください。[プロジェクト設定&#40;移行&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-migration-sybasetosql.md)です。  
  
    -   オブジェクトを読み込むためのオプションについては[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を参照してください[プロジェクト設定&#40;同期&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-synchronization-sybasetosql.md)です。  
  
    -   フル インストール オプションの詳細については、次を参照してください。[プロジェクト設定&#40;GUI&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-gui-sybasetosql.md)です。  
  
    -   データ型マッピングの設定の詳細についてをクリックして[プロジェクト設定&#40;型マッピング&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md)です。  
  
    -   SQL Azure のオプションの詳細については、次を参照してください。[プロジェクト設定&#40;Azure SQL DB &#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-azure-sql-db-sybasetosql.md)です。  
  
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
すべての新しい SSMA プロジェクトに適用される既定のプロジェクト設定を定義するだけでなく、各プロジェクトの設定をカスタマイズできます。 詳細については、次を参照してください。[プロジェクト オプションの設定&#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md)です。  
  
ソースとターゲット データベース間のデータ型マッピングをカスタマイズする場合は、プロジェクト、データベース、またはオブジェクト レベルでは、マッピングを定義できます。 型のマッピングの詳細については、次を参照してください。[マッピング Sybase ASE、および SQL Server データ型&#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md)です。  
  
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
[SQL Server - Azure SQL DB に ASE Sybase データベースを移行する&#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
[Sybase ASE に接続する&#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md)  
[SQL Server に接続する&#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)  
[Azure SQL DB に接続する&#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)  
  
