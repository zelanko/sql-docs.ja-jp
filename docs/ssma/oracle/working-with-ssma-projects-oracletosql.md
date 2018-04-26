---
title: SSMA プロジェクト (OracleToSQL) の使用 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Customizing Project Settings
ms.assetid: ee5d94c0-c7a6-4779-bd32-729bdaf61e1b
caps.latest.revision: 11
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: On Demand
ms.openlocfilehash: e34ac2455e6de1f35925045504e0e3224ee56560
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="working-with-ssma-projects-oracletosql"></a>SSMA プロジェクト (OracleToSQL) での作業
Oracle データベースを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、SSMA プロジェクトを作成します。 プロジェクトは、次の情報を含むファイルです。  
  
-   移行する Oracle データベースに関するメタデータ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
-   ターゲット インスタンスに関するメタデータ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]移行済みのオブジェクトとデータを受信します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 接続情報です。  
  
-   プロジェクトの設定。  
  
Oracle から切断されているプロジェクトを開くときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 オフラインで作業することができます。 再接続について[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を参照してください[SQL Server に接続する&#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)です。  
  
## <a name="reviewing-default-project-settings"></a>既定のプロジェクト設定を確認します。  
SSMA には、変換すると、Oracle と SSMA を同期し、データを移行するデータベース オブジェクトを読み込み、いくつかの設定が含まれていますと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 既定の設定は、多くのユーザーに適しています。 ただし、新しい SSMA プロジェクトを作成する前に、設定を確認する必要があります。 をする場合は、すべての新しいプロジェクトに使用される既定の設定を変更できます。  
  
**既定のプロジェクト設定を確認するには**  
  
1.  **ツール** メニューのをクリックして**プロジェクト設定の既定の**します。  
  
2.  プロジェクトの種類を選択して**移行のターゲット バージョン**どの設定を表示または変更するために必要としをクリックしてドロップダウン**全般** タブ。  
  
3.  左側のウィンドウでをクリックして**変換**です。  
  
4.  右側のウィンドウで確認し、必要に応じて設定を変更します。 これらの設定の詳細については、次を参照してください。[プロジェクト設定&#40;変換&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md)です。  
  
5.  移行、同期、システム オブジェクトの読み込み、GUI、および種類のマッピングのページの手順 1. ~ 3. を繰り返します。  
  
    -   移行設定については、次を参照してください。[プロジェクト設定&#40;移行&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-migration-oracletosql.md)です。  
  
    -   システム オブジェクトの設定については、次を参照してください。[プロジェクト設定&#40;読み込みシステム オブジェクト&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-loading-system-objects-oracletosql.md)です。  
  
    -   同期するための設定については[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を参照してください[プロジェクト設定&#40;同期&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-synchronization-oracletosql.md)です。  
  
    -   GUI の設定については、次を参照してください。[プロジェクト設定&#40;GUI&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-gui-oracletosql.md)です。  
  
    -   データ型マッピングの設定については、次を参照してください。[プロジェクト設定&#40;型マッピング&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-type-mapping-oracletosql.md)です。  
  
## <a name="creating-new-projects"></a>新しいプロジェクトの作成  
Oracle データベースからデータを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、まずプロジェクトを作成する必要があります。  
  
**プロジェクトを作成するには**  
  
1.  **ファイル** メニューのをクリックして**新しいプロジェクト**です。  
  
    **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  **名前**ボックスで、プロジェクトの名前を入力します。  
  
3.  **場所**ボックスに入力し、プロジェクトのフォルダーの選択、またはをクリックして**OK**です。  
  
4.  **移行に**ドロップダウンで、対象のバージョンを選択して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]移行に使用します。 使用可能なオプションは次のとおりです。  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016  
  
    -   Azure SQL DB  
  
## <a name="customizing-project-settings"></a>プロジェクト設定のカスタマイズ  
すべての新しい SSMA プロジェクトに適用される既定のプロジェクト設定を定義するだけでなく、各プロジェクトの設定をカスタマイズできます。 詳細については、次を参照してください。[プロジェクト オプションの設定&#40;OracleToSQL&#41;](../../ssma/oracle/setting-project-options-oracletosql.md)です。  
  
ソースとターゲット データベース間のデータ型マッピングをカスタマイズする場合は、プロジェクト、データベース、またはオブジェクト レベルでは、マッピングを定義できます。 詳細については、次を参照してください。[マッピング Oracle と SQL Server データ型&#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md)です。  
  
## <a name="saving-projects"></a>プロジェクトの保存  
プロジェクトを保存すると、SSMA は、プロジェクト設定、および必要に応じて、プロジェクト ファイルに、データベースのメタデータを保持します。  
  
**プロジェクトを保存するには**  
  
-   **ファイル** メニューのをクリックして**プロジェクトの保存**です。  
  
    プロジェクトのスキーマが変更されたか、変換されていない場合、SSMA は読み込みおよびメタデータを保存することを求められます。 読み込みとメタデータの保存はでオフラインで作業できます。 テクニカル サポート担当者など、他のユーザーに完全なプロジェクト ファイルを送信することもできます。 メタデータを保存するメッセージが表示されたら、次の操作を行います。  
  
    1.  状態が表示される各スキーマ用**メタデータがありません**データベース名の横にあるチェック ボックスをオンにします。  
  
        メタデータの保存には数分かかる場合があります。 まだのメタデータを保存したくない場合は、チェック ボックスをオンされません。  
  
    2.  クリックして、 **保存**  ボタンをクリックします。  
  
        SSMA は、Oracle スキーマが解析され、プロジェクト ファイルにメタデータを保存します。  
  
## <a name="opening-projects"></a>プロジェクトを開く  
プロジェクトを開くときに、切断されていると Oracle から[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 オフラインで作業することができます。 メタデータを更新するにデータベース オブジェクトを読み込む[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]します。 データを移行するには Oracle に再接続する必要がありますと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
**プロジェクトを開く**  
  
1.  次の手順のいずれかを使用します。  
  
    -   **ファイル** メニューのをポイント**最近使ったプロジェクト**、開きたいプロジェクトをクリックします。  
  
    -   **ファイル**メニューの **プロジェクトを開く**.o2ssproj プロジェクト ファイルを探し、ファイルを選択し、をクリックして**開く**です。  
  
2.  Oracle への再接続、**ファイル** メニューのをクリックして**Oracle への再接続**です。  
  
3.  再接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]の**ファイル** メニューのをクリックして**SQL Server に再接続**です。  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次の手順が、 [Oracle データベース (OracleToSQL) に接続する](http://msdn.microsoft.com/en-us/e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6)です。  
  
## <a name="see-also"></a>参照  
[SQL Server にデータベースを移行する Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
[Oracle データベースに接続する&#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md)  
[SQL Server に接続する&#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)  
  
