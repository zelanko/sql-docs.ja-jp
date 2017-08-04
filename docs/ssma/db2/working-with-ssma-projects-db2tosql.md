---
title: "SSMA プロジェクト (DB2ToSQL) の使用 |Microsoft ドキュメント"
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
ms.assetid: 07abef8a-28e8-4a66-927c-c9a5b8c938ef
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 548e434c6f14c789c38ac041dd4e6d28369da087
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="working-with-ssma-projects-db2tosql"></a>SSMA プロジェクト (DB2ToSQL) での作業
DB2 データベースを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、SSMA プロジェクトを作成します。 プロジェクトは、次の情報を含むファイルです。  
  
-   移行する場合、DB2 データベースに関するメタデータ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
-   ターゲット インスタンスに関するメタデータ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]移行済みのオブジェクトとデータを受信します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]接続情報です。  
  
-   プロジェクトの設定。  
  
DB2 から切断されているプロジェクトを開くときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 オフラインで作業することができます。 再接続について[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を参照してください[SQL Server (&) #40";"DB2eToSQL"&"#41; への接続](../../ssma/db2/connecting-to-sql-server-db2etosql.md)です。  
  
## <a name="reviewing-default-project-settings"></a>既定のプロジェクト設定を確認します。  
SSMA には、変換してデータベース オブジェクトの読み込み、データの移行および同期するため SSMA DB2 といくつかの設定が含まれていますと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 既定の設定は、多くのユーザーに適しています。 ただし、新しい SSMA プロジェクトを作成する前に、設定を確認する必要があります。 をする場合は、すべての新しいプロジェクトに使用される既定の設定を変更できます。  
  
**既定のプロジェクト設定を確認するには**  
  
1.  **ツール** メニューのをクリックして**プロジェクト設定の既定の**します。  
  
2.  プロジェクトの種類を選択して**移行のターゲット バージョン**どの設定を表示または変更するために必要としをクリックしてドロップダウン**全般** タブ。  
  
3.  左側のウィンドウでをクリックして**変換**です。  
  
4.  右側のウィンドウで確認し、必要に応じて設定を変更します。 これらの設定の詳細については、次を参照してください。[プロジェクトの設定 & #40 です。変換"&"#41;&#40; DB2ToSQL &#41;](../../ssma/db2/project-settings-conversion-db2tosql.md).  
  
5.  移行、同期、システム オブジェクトの読み込み、GUI、および種類のマッピングのページの手順 1. ~ 3. を繰り返します。  
  
    -   移行設定については、次を参照してください。[プロジェクトの設定 & #40 です。移行"&"#41;&#40; DB2ToSQL &#41;](../../ssma/db2/project-settings-migration-db2tosql.md).  
  
    -   システム オブジェクトの設定については、次を参照してください。[プロジェクトの設定 & #40 です。システム オブジェクトの読み込み"&"#41;&#40; DB2ToSQL &#41;](../../ssma/db2/project-settings-loading-system-objects-db2tosql.md).  
  
    -   同期するための設定については[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を参照してください[プロジェクトの設定 & #40 です。同期 &#41;&#40; DB2ToSQL &#41;](../../ssma/db2/project-settings-synchronization-db2tosql.md).  
  
    -   GUI の設定については、次を参照してください。[プロジェクトの設定 & #40 です。GUI &#41;&#40; DB2ToSQL &#41;](../../ssma/db2/project-settings-gui-db2tosql.md).  
  
    -   データ型マッピングの設定については、次を参照してください。[プロジェクトの設定 & #40 です。型のマッピング &#41;&#40; DB2ToSQL &#41;](../../ssma/db2/project-settings-type-mapping-db2tosql.md).  
  
## <a name="creating-new-projects"></a>新しいプロジェクトの作成  
DB2 データベースからデータを移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、まずプロジェクトを作成する必要があります。  
  
**プロジェクトを作成するには**  
  
1.  **ファイル** メニューのをクリックして**新しいプロジェクト**です。  
  
    **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  **名前**ボックスで、プロジェクトの名前を入力します。  
  
3.  **場所**ボックスに入力し、プロジェクトのフォルダーの選択、またはをクリックして**OK**です。  
  
4.  **移行に**ドロップダウンで、対象のバージョンを選択して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]移行に使用します。 使用可能なオプションは次のとおりです。  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016  
  
    -   Azure SQL DB  
  
## <a name="customizing-project-settings"></a>プロジェクト設定のカスタマイズ  
すべての新しい SSMA プロジェクトに適用される既定のプロジェクト設定を定義するだけでなく、各プロジェクトの設定をカスタマイズできます。 詳細については、次を参照してください。[プロジェクト オプションの設定 (&) #40";"OracleToSQL"&"#41;](../../ssma/oracle/setting-project-options-oracletosql.md)セクションを関連するとします。  
  
ソースとターゲット データベース間のデータ型マッピングをカスタマイズする場合は、プロジェクト、データベース、またはオブジェクト レベルでは、マッピングを定義できます。 詳細については、次を参照してください。 [DB2 のマッピングと SQL Server データ型 (&) #40";"DB2ToSQL"&"#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md)です。  
  
## <a name="saving-projects"></a>プロジェクトの保存  
プロジェクトを保存すると、SSMA は、プロジェクト設定、および必要に応じて、プロジェクト ファイルに、データベースのメタデータを保持します。  
  
**プロジェクトを保存するには**  
  
-   **ファイル** メニューのをクリックして**プロジェクトの保存**です。  
  
    プロジェクトのスキーマが変更されたか、変換されていない場合、SSMA は読み込みおよびメタデータを保存することを求められます。 読み込みとメタデータの保存はでオフラインで作業できます。 テクニカル サポート担当者など、他のユーザーに完全なプロジェクト ファイルを送信することもできます。 メタデータを保存するメッセージが表示されたら、次の操作を行います。  
  
    1.  状態が表示される各スキーマ用**メタデータがありません**データベース名の横にあるチェック ボックスをオンにします。  
  
        メタデータの保存には数分かかる場合があります。 まだのメタデータを保存したくない場合は、チェック ボックスをオンされません。  
  
    2.  クリックして、 **保存**  ボタンをクリックします。  
  
        SSMA は、DB2 スキーマが解析され、プロジェクト ファイルにメタデータを保存します。  
  
## <a name="opening-projects"></a>プロジェクトを開く  
プロジェクトを開くときに、切断されている DB2 およびから[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 オフラインで作業することができます。 メタデータを更新するにデータベース オブジェクトを読み込む[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]します。 データを移行するには、DB2 に再接続する必要がありますと[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
**プロジェクトを開く**  
  
1.  次の手順のいずれかを使用します。  
  
    -   **ファイル** メニューのをポイント**最近使ったプロジェクト**、開きたいプロジェクトをクリックします。  
  
    -   **ファイル**メニューの **プロジェクトを開く**.o2ssproj プロジェクト ファイルを探し、ファイルを選択し、をクリックして**開く**です。  
  
2.  DB2 への再接続、**ファイル** メニューのをクリックして**DB2 への再接続**です。  
  
3.  再接続[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]の**ファイル** メニューのをクリックして**SQL Server に再接続**です。  
  
## <a name="next-step"></a>次の手順  
移行プロセスの次の手順が、 [DB2 データベースに接続する](http://msdn.microsoft.com/en-us/5eb5801d-f0c3-4127-97c0-0b1ef49f4844)です。  
  
## <a name="see-also"></a>参照  
[SQL Server (&) #40";"DB2ToSQL"&"#41; への DB2 データベースの移行](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
[DB2 データベース (&) #40";"DB2ToSQL"&"#41; への接続](../../ssma/db2/connecting-to-db2-database-db2tosql.md)  
[SQL Server (&) #40";"DB2eToSQL"&"#41; への接続](../../ssma/db2/connecting-to-sql-server-db2etosql.md)  
  

