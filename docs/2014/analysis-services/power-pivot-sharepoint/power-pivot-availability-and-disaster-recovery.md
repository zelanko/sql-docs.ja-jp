---
title: PowerPivot の可用性と災害復旧 (SQL Server 2014) |Microsoft Docs
ms.custom: ''
ms.date: 03/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 4aaf008c-3bcb-4dbf-862c-65747d1a668c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1f975fe18b76c4e748d7d2969d20c53b5818f0c3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66071328"
---
# <a name="powerpivot-availability-and-disaster-recovery-sql-server-2014"></a>PowerPivot の可用性と災害復旧 (SQL Server 2014)
  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] の可用性とディザスター リカバリー計画は主に、SharePoint ファームの設計、さまざまなコンポーネントで許容されるダウンタイムの長さ、SharePoint の可用性を高めるために実装するツールとベスト プラクティスに依存します。 このトピックでは、さまざまなテクノロジについて要約し、 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)][!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] の配置に関して可用性とディザスター リカバリーを計画するときに考慮する必要のあるトポロジ図の例を示します。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010|  
  
 **このトピックの内容:**  
  
-   [PowerPivot の高可用性 SharePoint 2013 のトポロジの例](#bkmk_sharepoint2013)  
  
-   [PowerPivot の高可用性 SharePoint 2010 のトポロジの例](#bkmk_sharepoint2010)  
  
-   [PowerPivot サービス アプリケーション データベースおよび SQL Server の可用性と復旧に関連したテクノロジ](#bkmk_sql_server_technologies)  
  
-   [詳細情報へのリンク](#bkmk_more_resources)  
  
##  <a name="bkmk_sharepoint2013"></a> PowerPivot の高可用性 SharePoint 2013 のトポロジの例  
 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 を配置するときに、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] の可用性を設計する方法に関してより大きな柔軟性を実現できます。 SharePoint 2013 では、SharePoint モードで配置された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスは、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] サーバーとも呼ばれますが、SharePoint ファームの外部で実行され、別のサーバーにインストールすることもできます。 SharePoint モードにある [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の各インスタンスは、Excel Services に登録されます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] の共有サービスとサービス アプリケーションは、SharePoint アプリケーション サーバー上で実行されます。  
  
 次の図に、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 の配置に関する例を示します。 この例では、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] サービスの適切な可用性をサポートしており、データベースを定期的にバックアップすることを前提としています。  
  
 ![2013 での powerpivot の可用性](../media/ssas-powerpivot-services-2013.png "2013年での powerpivot の可用性")  
  
-   **(1)** Web フロントエンド サーバー。 各サーバーにデータ プロバイダーをインストールするには、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 のアドインを使用します。 詳細については、次を参照してください。[インストールまたは PowerPivot を SharePoint アドインのアンインストール&#40;SharePoint 2013&#41;](../instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)します。  
  
-   **(2)** [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 共有サービスは **各** アプリケーション サーバー上で動作し、サービス アプリケーションが複数のアプリケーション サーバーに **またがって** 動作できるようにします。 そのため、1 台のアプリケーション サーバーがオフラインになったときでも、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] アプリケーションは引き続き使用できます。  
  
-   **(3)** Excel Calculation Services は各アプリケーション サーバー上で動作し、サービス アプリケーションが複数のアプリケーション サーバーにまたがって動作できるようにします。 そのため、1 台のアプリケーション サーバーがオフラインになったときでも、Excel Calculation Services は引き続き使用できます。  
  
-   **(4)** と **(6)** のインスタンス[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を SharePoint モードは、SharePoint ファームの外部のサーバーで実行、Windows サービスが含まれます**SQL Server Analysis Services (POWERPIVOT)** します。 これらのインスタンスのそれぞれは、Excel Services **(3)** に登録されます。 Excel Services は、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] サーバーに対する要求の負荷分散を管理します。 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 アーキテクチャを活用して、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] に対応する複数のサーバーを用意することができ、その結果、必要に応じてより多くのインスタンスを追加できます。 詳細については、「 [Excel Services のデータ モデルの設定を管理する (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780\(v=office.15\).aspx)」を参照してください。  
  
-   **(5)** コンテンツ、構成、およびアプリケーション データベースとして使用される SQL Server データベース。 これには、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション データベースが含まれます。 DR (災害復旧) 計画に、データベース層を含める必要があります。 この設計では、データベースは、 **(4)** [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] インスタンスのいずれかと同じサーバーで実行されます。 **(4)** と **(5)** を、互いに異なるサーバーで実行することもできます。  
  
-   **(7)** SQL Server データベースのバックアップまたは冗長性に関するなんらかの形式です。  
  
##  <a name="bkmk_sharepoint2010"></a> PowerPivot の高可用性 SharePoint 2010 のトポロジの例  
 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 のアーキテクチャでは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] のすべてのコンポーネントを同じ SharePoint アプリケーション サーバーで実行することが必要です。 これには、SharePoint モードで配置された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスと、2 つの共有サービスが含まれますが、後者は SharePoint 2013 の配置で 1 つのみが使用される点とは対照的です。  
  
 次の図に、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 の配置に関する例を示します。 この例では、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] サービスの適切な可用性をサポートしており、データベースを定期的にバックアップすることを前提としています。  
  
 ![sharepoint 2010 で powerpivot の可用性](../media/ssas-powerpivot-services-2010.png "sharepoint 2010 で powerpivot の可用性")  
  
-   **(1)** Web フロントエンド サーバー。 各サーバーにデータ プロバイダーをインストールします。 「 [SharePoint サーバーへの Analysis Services OLE DB プロバイダーのインストール](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)」を参照してください。  
  
-   **(2)** 、2 つ[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]共有サービスと **(4)** Windows サービス**SQL Server Analysis Services (POWERPIVOT)** SharePoint アプリケーション サーバーにインストールされます。  
  
     [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスは **各** アプリケーション サーバー上で動作し、サービス アプリケーションが複数のアプリケーション サーバーに **またがって** 動作できるようにします。 1 台のアプリケーション サーバーがオフラインになったときでも、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] サービス アプリケーションは引き続き使用できます。  
  
     SharePoint 2010 で [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] のキャパシティを向上させるには、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスを実行する SharePoint アプリケーション サーバーをさらに配置します。  
  
-   **(3)** Excel Calculation Services は各アプリケーション サーバー上で動作し、サービス アプリケーションが複数のアプリケーション サーバーにまたがって動作できるようにします。 そのため、1 台のアプリケーション サーバーがオフラインになったときでも、Excel Calculation Services は引き続き使用できます。  
  
-   **(5)** コンテンツ、構成、およびアプリケーション データベースとして使用される SQL Server データベース。 これには、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション データベースが含まれます。 DR (災害復旧) 計画に、データベース層を含める必要があります。  
  
-   **(6)** SQL Server データベースのバックアップまたは冗長性に関するなんらかの形式です。  
  
##  <a name="bkmk_sql_server_technologies"></a> PowerPivot サービス アプリケーション データベースおよび SQL Server の可用性と復旧に関連したテクノロジ  
 SharePoint の高可用性実現計画には、 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] サービス アプリケーション データベースを加えてください。 データベースの既定の名前は、 `DefaultPowerPivotServiceApplicationDB-<GUID>`です。 以下の表は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースと組み合わせて使用される [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] の可用性テクノロジと推奨事項をまとめたものです。 詳細については、「 [サポートされている SharePoint データベース用の高可用性とディザスター リカバリーのオプション (SharePoint 2013)](https://technet.microsoft.com/library/jj841106.aspx)」を参照してください。  
  
||コメント|  
|-|--------------|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] と [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] の同期ミラーリングを同じファーム内で行うことによる可用性の確保|サポートはされますが、推奨はされません。 同期 - コミット モードで AlwaysOn を使用することをお勧めします。|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] 同期コミット モードの|サポートされ、なおかつ推奨されます。|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 非同期ミラーリングまたはログ配布を別のファームとの間で行うことによるディザスター リカバリー|サポートされています。|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] と非同期コミットによるディザスター リカバリー|サポートされている|  
  
-   [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログ配布  
  
 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]を含んだコールド スタンドバイのシナリオを計画する方法の詳細については、 [PowerPivot の災害復旧](https://social.technet.microsoft.com/wiki/contents/articles/22137.sharepoint-powerpivot-disaster-recovery.aspx)に関するページを参照してください。  
  
## <a name="verification"></a>検証  
 ガイダンスと確認に役立つスクリプト、[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]前に、と後、ディザスター リカバリー サイクルのデプロイに確認[チェックリスト。PowerShell Verify PowerPivot for SharePoint を使用して](../instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint.md)します。  
  
##  <a name="bkmk_more_resources"></a> 詳細情報へのリンク  
  
-   [サポートされている SharePoint データベース用の高可用性とディザスター リカバリーのオプション (SharePoint 2013)](https://technet.microsoft.com/library/jj841106.aspx)  
  
-   [ディザスター リカバリーを計画する (SharePoint Server 2010)](https://technet.microsoft.com/library/ff628971\(v=office.14\).aspx)  
  
-   [Microsoft® SQL Server Backup to Microsoft Windows® Azure®Tool](https://www.microsoft.com/download/details.aspx?id=40740)  
  
 **コミュニティ コンテンツ**  
  
-   [SharePoint 2013 でのサービス インスタンスの管理](http://www.petri.co.il/manage-service-instances-sharepoint-2013.htm)  
  
-   [データベースのバックアップ SQL Server スクリプト](http://megaupl0ad.net/free/backup%20database%20sql%20server%20script)  
  
  
