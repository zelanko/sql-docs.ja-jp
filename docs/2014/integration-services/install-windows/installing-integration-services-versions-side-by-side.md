---
title: 相互運用性と共存 (Integration Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- interoperability and coexistence [Integration Services]
- Integration Services, interoperability and coexistence
ms.assetid: edfbcd56-012f-462e-a542-95491394fda9
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8f7face1f41fdf02f772c05427db9d45d1bd6050
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37277588"
---
# <a name="interoperability-and-coexistence-integration-services"></a>相互運用性と共存 (Integration Services)
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services (SSIS) は [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services および [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services と共存できます。  
  
## <a name="features-and-differences"></a>機能と相違点  
 次の表に、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の現在のバージョンと以前のバージョンの相違点を示します。  
  
|機能|[!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]|[!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)]|[!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]|  
|-------------|-------------------------------|---------------------------------|---------------------------------|  
|開発環境|[SQL Server 2014 Data Tools – Business Intelligence for Visual Studio 2012 CTP 2](http://www.microsoft.com/download/details.aspx?id=40736)<br /><br /> [SQL Server 2014 Data Tools - Business Intelligence for Visual Studio 2013](http://www.microsoft.com/download/details.aspx?id=42313)|[Visual Studio 2010 用 SQL Server Data Tools](http://msdn.microsoft.com/library/hh500335\(v=vs.103\).aspx)<br /><br /> [SQL Server Data Tools – Business Intelligence for Visual Studio 2012](http://www.microsoft.com/download/details.aspx?id=36843)|Business Intelligence Development Studio ([!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)])|  
|管理環境|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|  
|パッケージの格納に使用する msdb のメイン システム テーブル|sysssispackages|sysssispackages|sysssispackages|  
|パッケージの実行に使用するメイン コマンド プロンプト ユーティリティ|**dtexec** (dtexec.exe)、2014 バージョン|**dtexec** (dtexec.exe)、2012 バージョン|**dtexec** (dtexec.exe)、2008 バージョン|  
|既定のルート ファイル システム フォルダー|C:\Program Files\Microsoft SQL Server\120\DTS|C:\Program Files\Microsoft SQL Server\110\DTS|C:\Program Files\Microsoft SQL Server\100\DTS|  
|既定のルート レジストリ キー|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\SSIS|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS|  
  
## <a name="side-by-side-compatibility-issues"></a>サイド バイ サイド実行の互換性に関する問題  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services を [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services および [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services とサイド バイ サイドでインストールしている場合、次の作業を実行できます。  
  
-   **SQL Server データ ツールでパッケージを設計する**。 対応するバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に基づくパッケージを開発および管理するには、次のツールを使用します。  
  
    -   使用して、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]開発および管理に基づくパッケージを Business Intelligence Development Studio のバージョン [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]  
  
    -   使用して、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]バージョンの[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]に基づくパッケージ開発および管理する[!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]します。  
  
    -   使用して、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]バージョンの[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]に基づくパッケージ開発および管理する[!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]します。  
  
-   **パッケージを読み込んで実行する。** ロードしてで開発されたパッケージを実行する[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]と[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]の[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]バージョンの[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]します。 パッケージを既存のプロジェクトに追加すると、パッケージは [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services で使用される形式に永続的にアップグレードされます。 パッケージ ファイルを [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で開くと、パッケージは [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services で使用される形式に一時的にアップグレードされます。 パッケージの変更を保存すると、パッケージは永続的にアップグレードされます。 形式で保存するとする[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]Integration Services を使用して、対応するパッケージを開いてできなくできます[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]または[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]バージョンの Business Intelligence Development Studio では、対応する、実行することも[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]Integration Services または[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]Integration Services ツール。  
  
-   **SQL Server Management Studio でパッケージを管理する。** インスタンスに接続することはできません、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のバージョン、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]から、サービス、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]または[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]バージョンの[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]します。 インスタンスに接続することはできません、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]または[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]のバージョン、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]からサービス、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]版[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]します。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンの [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用して、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] または [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] のインスタンスに保存されている [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] パッケージを管理できます。 サービス構成ファイルを変更して、サービスによって管理される場所の一覧に [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] のインスタンスを追加する必要があります。 詳細については、「[Integration Services サービスの構成 &#40;SSIS サービス&#41;](../service/integration-services-service-ssis-service.md)」を参照してください。  
  
-   **SQL Server にパッケージを格納する。** パッケージは次のデータベースに保存できます。  
  
    |パッケージの形式|[データベース]|  
    |--------------------|--------------|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services|インスタンスの msdb データベース [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
    |[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services|インスタンスの msdb データベース [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|  
    |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services|インスタンスの msdb データベース [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
  
     インスタンスで[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のインスタンスからパッケージをインポートする[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]またはのインスタンスから[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]のインスタンスにパッケージをエクスポートすることはできませんが、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]またはのインスタンスに[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]します。  
  
     [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] または [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] のインスタンスでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインスタンスとの間で、パッケージをインポートすることも、エクスポートすることもできません。  
  
-   **パッケージを実行する。** 実行することができます[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]Integration Services と[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]Integration Services パッケージを使用して、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のバージョン、 **dtexec**ユーティリティまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント。 たびに、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services ツールで開発されたパッケージを読み込みます[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]または[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、ツール、一時的に変換されます、メモリ内で、パッケージにパッケージの形式で[!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]を使用します。 場合、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]または[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]パッケージが正常に変換できない問題により、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services ツールはこれらの問題が解決されるまでパッケージを実行できません。 詳細については、「 [Upgrade Integration Services Packages](upgrade-integration-services-packages.md)」を参照してください。  
  
  
