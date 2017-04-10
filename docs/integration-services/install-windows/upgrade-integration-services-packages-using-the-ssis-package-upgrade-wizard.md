---
title: "SSIS パッケージ アップグレード ウィザードを使用した Integration Services パッケージのアップグレード | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Integration Services パッケージ, アップグレード"
  - "Integration Services パッケージのアップグレード"
ms.assetid: 9359275a-48f5-4d1e-8ae7-e797759e3ccf
caps.latest.revision: 22
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 22
---
# SSIS パッケージ アップグレード ウィザードを使用した Integration Services パッケージのアップグレード
  以前のバージョンの [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] で作成したパッケージは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] で使用される [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 形式にアップグレードできます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、このプロセスを容易に行うための [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ アップグレード ウィザードが用意されています。 このウィザードは元のパッケージをバックアップするように構成できるため、アップグレードが難しい場合は、元のパッケージを引き続き使用できます。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ アップグレード ウィザードは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のインストール時にインストールされます。  
  
> [!NOTE]  
>  [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ アップグレード ウィザードは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の Standard Edition、Enterprise Edition、および Developer Edition で使用できます。  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのアップグレード方法については、「[Integration Services パッケージのアップグレード](../../integration-services/install-windows/upgrade-integration-services-packages.md)」をご覧ください。  
  
 以降では、ウィザードの実行方法と元のパッケージのバックアップ方法について説明します。  
  
## SSIS パッケージ アップグレード ウィザードの実行  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ アップグレード ウィザードは、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、またはコマンド プロンプトから実行できます。  
  
#### SQL Server データ ツールからウィザードを実行するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを作成または開きます。  
  
2.  ソリューション エクスプローラーで、**[SSIS パッケージ]** ノードを右クリックして **[すべてのパッケージをアップグレード]** をクリックし、このノードの下のすべてのパッケージをアップグレードします。  
  
    > [!NOTE]  
    >  [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] 以降のパッケージが含まれる [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開いた場合、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ アップグレード ウィザードが自動的に開きます。  
  
#### SQL Server Management Studio からウィザードを実行するには  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に接続し、**[格納されたパッケージ]** ノードを展開して **[ファイル システム]** ノードまたは **[MSDB]** ノードを右クリックし、**[パッケージのアップグレード]** をクリックします。  
  
#### コマンド プロンプトでウィザードを実行するには  
  
-   コマンド プロンプトで、**C:\Program Files\Microsoft SQL Server\130\DTS\Binn** フォルダーから SSISUpgrade.exe ファイルを実行します。  
  
## 元のパッケージのバックアップ  
 元のパッケージをバックアップするには、元のパッケージとアップグレードされたパッケージの両方をファイル システム内の同一フォルダーに格納する必要があります。 この格納場所は、ウィザードの実行方法に応じて、自動的に選択される場合があります。  
  
-   [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ アップグレード ウィザードを [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] から実行すると、元のパッケージとアップグレードされたパッケージの両方がファイル システム内の同一フォルダーに自動的に格納されます。  
  
-   [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ アップグレード ウィザードを [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] またはコマンド プロンプトから実行すると、元のパッケージとアップグレードされたパッケージに異なる格納場所を指定することができます。 元のパッケージをバックアップするには、元のパッケージとアップグレードされたパッケージの両方がファイル システム内の同一フォルダーに格納されるように指定する必要があります。 他の格納オプションを指定すると、元のパッケージをバックアップできません。  
  
 ウィザードで元のパッケージをバックアップすると、元のパッケージのコピーが **SSISBackupFolder** フォルダーにバックアップされます。 この **SSISBackupFolder** フォルダーは、元のパッケージとアップグレードされたパッケージが格納されるフォルダーのサブフォルダーとして作成されます。  
  
#### SQL Server Management Studio またはコマンド プロンプトで元のパッケージをバックアップするには  
  
1.  元のパッケージをファイル システム上の場所に保存します。  
  
    > [!NOTE]  
    >  ウィザードのバックアップ オプションは、ファイル システムに格納されているパッケージに対してのみ機能します。  
  
2.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] またはコマンド プロンプトで、[!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ アップグレード ウィザードを実行します。  
  
3.  ウィザードの **[アップグレード元の場所の選択]** ページで、**[パッケージのアップグレード元]** プロパティを **[ファイル システム]** に設定します。  
  
4.  ウィザードの **[アップグレード先の場所の選択]** ページで、**[アップグレード元の場所に保存する]** をクリックして、アップグレードされたパッケージを、元のパッケージと同じ場所に保存します。  
  
    > [!NOTE]  
    >  ウィザードのバックアップ オプションを使用できるのは、アップグレードされたパッケージが元のパッケージと同じフォルダーに格納されている場合のみです。  
  
5.  ウィザードの **[パッケージ管理オプションの選択]** ページで、**[元のパッケージをバックアップする]** チェック ボックスをオンにします。  
  
#### SQLServer データ ツールの元のパッケージをバックアップするには  
  
1.  元のパッケージをファイル システム上の場所に保存します。  
  
2.  ウィザードの **[パッケージ管理オプションの選択]** ページで、**[元のパッケージをバックアップする]** チェック ボックスをオンにします。  
  
    > [!WARNING]  
    >  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] 以降のプロジェクトを開いた場合は、ウィザードが自動的に起動され、**[元のパッケージをバックアップする]** オプションは表示されません。  
  
3.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で、[!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ アップグレード ウィザードを実行します。  
  
  