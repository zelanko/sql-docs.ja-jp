---
title: 例のライセンスのトポロジおよびコストの SQL Server 2014 セルフ サービス ビジネス インテリジェンス |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 682b8711-407a-48d1-9807-415d4c24dad6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 56e290ef8bf680f44ee11ec2e8d918b7b1d22c76
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48091402"
---
# <a name="example-license-topologies-and-costs--for-sql-server-2014-self-service-business-intelligence"></a>ライセンスのトポロジの例と SQL Server 2014 セルフ サービス ビジネス インテリジェンスのコスト
  このトピックでは、選択するための高度な考慮事項を示しています、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Business Intelligence edition または[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Enterprise edition。 このトピックには、内部設置型の Microsoft セルフサービス Business Intelligence (BI) トポロジのサンプルがいくつか含まれています。 これらの例では、コストとパフォーマンスのバランスの最適化に利用できるエディションとライセンスが含まれています。 紹介されるトポロジ、サーバー数、およびライセンス コストは **例示のみ**を目的としています。 Microsoft [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] および Microsoft SharePoint 2013 ではライセンスに関していくつかの変更が行われ、サーバー、ユーザー、およびデバイスについてライセンスを取得する際に、より多くのオプションを利用できるようになりました。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のライセンスでは、同じビジネス インテリジェンスに関連するシナリオがサポートされます。  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は Business Intelligence Edition で提供され、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のいくつかのバージョン用にコア ベースのライセンスを提供します。  
  
-   SharePoint 2013 では、エクストラネットおよびイントラネットのシナリオ用の SharePoint Server のライセンス方法および SharePoint Online 用のオプションが簡素化されています。  
  
 個別のライセンス要件については、購入の前に、各製品の購入方法のセクションを確認し、Microsoft 担当者または地域の再販業者にご相談ください。 ライセンスに関する最新の計画とコストの詳細については、次を参照してください。  
  
-   [ライセンス情報-SQL Server 2014](http://www.microsoft.com/licensing/about-licensing/sql2014.aspx)  
  
-   [SharePoint 2013 のライセンス](http://office.microsoft.com/sharepoint/sharepoint-licensing-overview-collaboration-software-FX103789438.aspx)。  
  
 **このトピックの内容:**  
  
-   [SQL Server Business Intelligence コンポーネント](#bkmk_bi_components)  
  
-   [SQL Server 2014 のライセンスの概要](#bkmk_sql_server_license)  
  
-   [SharePoint 2013 のライセンスの概要](#bkmk_sharepoint_license)  
  
-   [個別の PowerPivot サーバーを使用した 3 層トポロジ](#bkmk_3tier_powerpivot)  
  
-   [3 層トポロジ](#bkmk_3tier)  
  
-   [2 層トポロジ](#bkmk_2tier)  
  
-   [リファレンスとコミュニティ コンテンツ](#bkmk_reference)  
  
##  <a name="bkmk_bi_components"></a> SQL Server Business Intelligence コンポーネント  
 このトピックでは、SQL Server および SharePoint サーバーのテクノロジについて説明します。 コストおよび例では、完全なクライアント サーバー ソリューションの構築に必要な Microsoft Windows Server または Microsoft Office のコンポーネントを具体的に示していません。 このトピックで説明される SQL Server Business Intelligence のコンポーネントは、SharePoint モードで実行される SQL Server Reporting Services と、PowerPivot for SharePoint です。 これらのコンポーネントには次の機能が搭載されています。  
  
-   ブラウザーの対話型 PowerPivot ブック。  
  
-   対話型[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]SharePoint でレポートします。  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリー、データ更新スケジュール、管理ダッシュボード。  
  
-   SharePoint モードの Reporting Services (データ警告を含む)。  
  
 詳細については、の機能の表を参照して[SharePoint と SQL Server BI 機能のインストール&#40;PowerPivot と Reporting Services&#41;](../../../2014/sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md)します。  
  
## <a name="license-summary"></a>ライセンスの概要  
 このセクションでは、SQL Server および SharePoint のライセンス要件をまとめます。 情報は大まかな概要であり、このドキュメントのトポロジ図とコスト例で使用されているシナリオ以外の情報は含まれていません。 ライセンスの詳細については、記載されているリンクのコンテンツをご確認ください。 価格例は Microsoft Open License プログラム (MOLP) の価格に基づいています。  
  
 一般的には、SQL Server データベース エンジンを実行するサーバーに **Enterprise Edition** を使用し、Reporting Services または PowerPivot for SharePoint を実行するサーバーには **Business Intelligence Edition** を使用します。 ただし、コストおよび使用するエディションの決定は、配置環境における **ユーザー数** と **サーバー コア数** の影響を受けます。  
  
###  <a name="bkmk_sql_server_license"></a> SQL Server 2014 のライセンスの概要  
  
-   SQL Server Enterprise Edition はコア ベース ライセンスを使用します。 コア ベース ライセンスは **2 コア** パックで販売されます。  
  
-   SQL Server BI Edition はサーバー ライセンスとクライアント アクセス ライセンス (CAL) の両方を使用します。  
  
-   CAL ライセンスは、接続するサーバー数に関係なく、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続するユーザーまたはデバイスの数に基づき計算します。  
  
-   コア ライセンスでは、サーバーのすべてのコアについてライセンスを取得する必要があります。 サーバーに搭載されている物理プロセッサごとに少なくとも **4** コア分のライセンスが必要です。  
  
 以下の表に、配置設計とライセンス コストの推定に使用されるライセンスの詳細をまとめます。 **注:**  記載されている価格は、情報提供のみを目的とします。  
  
|SQL Server のエディション|SQL Server サーバー ライセンス + クライアント アクセス ライセンス (CAL)|SQL Server コア ベース ライセンス|  
|-------------------------|---------------------------------------------------------|-----------------------------------|  
|Enterprise|適用なし|**(対応)** $6874 × [コア数] × [コア係数]|  
|Business Intelligence|**(対応)** $8592 + CAL ごとに $199|適用なし|  
|Standard|**(はい)**|**(はい)**|  
  
 サンプルの詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ライセンスの価格を参照してください。  
  
-   [仮想環境におけるライセンス](http://www.microsoft.com/licensing/about-licensing/virtualization.aspx)(http://www.microsoft.com/licensing/about-licensing/virtualization.aspx)します。  
  
-   [SQL Server 2014 ライセンス データシート - Microsoft ホーム ページ](http://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf)(http://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf)します。  
  
-   [SQL server 2014 のエディションとライセンス](http://www.microsoft.com/licensing/about-licensing/sql2014.aspx#tab=2)  
  
1.  **SQL Server の前提条件とライセンスに関する詳細情報:**  
  
2.  このトピックの図では、AlwaysOn 可用性グループなどの高可用性機能の完全なセットを利用するため、データベース サーバーに SQL Server Enterprise Edition を使用しています。 詳しくは「 [Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」をご覧ください。  
  
3.  この例のサーバーはすべて Intel Xeon 6 コア プロセッサを 2 基搭載しています。このため、ライセンス コストを計算する場合の **SQL Server コア係数** は **1** となります。 コア係数とライセンス コストの詳細については、次を参照してください。 [SQL Server コア係数表](http://download.microsoft.com/download/9/B/F/9BF63163-D8F9-4339-90AA-EBC9AAFC49AD/SQL2012_CoreFactorTable_Mar2012.pdf)(http://download.microsoft.com/download/0/C/8/0C85665B-11EA-4FF5-B37C-8CC21CF95AC4/BizTalk%202013_CoreFactorTable_**3.19.2013**。 v4.pdf)。  
  
###  <a name="bkmk_sharepoint_license"></a> SharePoint 2013 のライセンスの概要  
 以下の一覧に、配置設計とライセンス コストの推定に使用されるライセンス モデルをまとめます。 記載されている価格は、情報提供のみを目的とします。  
  
1.  Microsoft SharePoint Server の各インスタンスに SharePoint サーバー ライセンスが必要です。  
  
2.  ユーザーまたはエンド デバイスごとに SharePoint Enterprise のライセンスを取得するには、Microsoft SharePoint Server 2013 の **Enterprise CAL ライセンス** に加えて、Microsoft SharePoint Server 2013 の **Standard CAL ライセンス**を購入します。  
  
3.  SharePoint CAL ライセンスは、SharePoint サーバーにアクセスするユーザーまたはデバイスごとに購入します。 各サーバーに CAL ライセンスを購入する必要はありません。  
  
 たとえば、環境内に 2 つのインスタンスがあり、これらが 100 人のユーザーに使用されている場合、コストは次のように見積もられます。  
  
-   Microsoft SharePoint Server 2013 Standard CAL ライセンス: **$107.99**  
  
-   Microsoft SharePoint Server 2013 Enterprise CAL ライセンス: **$94.99**  
  
-   Microsoft SharePoint Server 2013 ライセンス: **$6,412.99**  
  
 コスト: **$33,123.98**  
  
-   CAL ライセンス: ($107.99 +$94.99) × 100 = $20,298.00  
  
-   サーバー ライセンス: ($6,412.99 × 2) = $12,825.98  
  
 **SharePoint の前提条件とライセンスに関する詳細情報:**  
  
 サンプルの配置はすべてイントラネット環境のため、SharePoint CAL ライセンスの習得が必要になります。  
  
-   [ライセンスの完全な一覧を SharePoint](http://technet.microsoft.com/en-in/library/jj819267.aspx#bkmk_FeaturesOnPremise) (http://technet.microsoft.com/en-in/library/jj819267.aspx#bkmk_FeaturesOnPremise)します。  
  
-   [SharePoint の購入方法](http://sharepoint.microsoft.com/en-in/Pages/buy.aspx)(http://sharepoint.microsoft.com/en-in/Pages/buy.aspx)します。  
  
##  <a name="bkmk_3tier_powerpivot"></a> 3 層トポロジで[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]サーバー  
 この例では、800 人以下のユーザーの場合について説明します。この場合、SharePoint アプリケーション サーバーと [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint サーバーに SQL Server BI Edition を使用するとコストが最も低くなります。 ただし、ユーザーが 800 人以上存在する場合は SQL Server Enterprise Edition が低コストです。 コア ライセンスの取得はユーザー数に関係ないため、コア ライセンスと CAL ライセンス、および増加ユーザー数を比較した場合に、コストの分岐点が存在することになります。 分岐点を越えた場合は、Enterprise Edition が低コストなソリューションになります。 コストのしきい値を判断するには、コアの数に基づいて取得されるライセンスのコストと、エンド ユーザーまたはエンド デバイスの数に基づいて取得される CAL のコストを比較します。  
  
-   この例はイントラネットへの配置であるため、SharePoint CAL ライセンスを SharePoint 2013 に適用します。  
  
-   アプリケーション ロール (2) には、SharePoint モードでインストールされる SQL Server Reporting Services が含まれます。  
  
     SharePoint サービス アプリケーション データベースが、データベース ロール (4) サーバーで実行されます。  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint は別のサーバー (3) で実行されます。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint 2013、SharePoint ファームの外部で実行して、パフォーマンスの向上、SharePoint のインストールを含まないサーバーにインストールすることができます。  
  
-   データベース ロール (4) は、SQL Server Enterprise を使用します。これによって [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能である AlwaysOn 可用性グループが利用できるようになります。  
  
 ![bi_license_3tiers_and_ASseparate](../../../2014/sql-server/install/media/bi-license-3tiers-and-asseparate.gif "bi_license_3tiers_and_ASseparate")  
  
 ユーザーが 100 人の場合、SQL Server BI Edition が低コストになります。  
  
 ![bi_license_3tiers_and_ASseperate_calcs](../../../2014/sql-server/install/media/bi-license-3tiers-and-asseperate-calcs.gif "bi_license_3tiers_and_ASseperate_calcs")  
  
 しかし、ユーザーが 300 人以上存在する場合は SQL Server Enterprise Edition がより低コストです。  
  
 ![bi_license_3tiers_and_ASseperate_calcs2](../../../2014/sql-server/install/media/bi-license-3tiers-and-asseperate-calcs2.gif "bi_license_3tiers_and_ASseperate_calcs2")  
  
##  <a name="bkmk_3tier"></a> 3 層トポロジ  
 この例では、ユーザーが 100 人以下の場合、SQL Server BI 機能を実行するサーバーには SQL BI Edition を使用すると低コストになることがわかります。 ただし、ユーザーが 500 人以上存在する場合は SQL Server Enterprise Edition が低コストです。  
  
-   この例はイントラネットへの配置であるため、SharePoint CAL ライセンスを SharePoint 2013 に適用します。  
  
-   (2) の実行、ファームの外部 PowerPivot モードで analysis Services しますが、PowerPivot が実行されている**同じ物理**他のアプリケーション ロール内のサーバー。  
  
-   データベース ロール (3) は、SQL Server Enterprise を使用できるように、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]機能、AlwaysOn 可用性グループは使用できます。  
  
 ![bi_license_3tiers](../../../2014/sql-server/install/media/bi-license-3tiers.gif "bi_license_3tiers")  
  
 ユーザーが 100 人の場合、SQL Server BI Edition が低コストになります。  
  
 ![bi_license_3tiers_calcs1](../../../2014/sql-server/install/media/bi-license-3tiers-calcs1.gif "bi_license_3tiers_calcs1")  
  
 しかし、ユーザーが 500 人以上存在する場合は SQL Server Enterprise Edition がより低コストです。  
  
 ![bi_license_3tiers_calcs3](../../../2014/sql-server/install/media/bi-license-3tiers-calcs3.gif "bi_license_3tiers_calcs3")  
  
##  <a name="bkmk_2tier"></a> 2 層トポロジ  
 2 層のみ場合、SQL Server Enterprise Edition を使用します。これによって [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能である AlwaysOn 可用性グループを、SQL Server データベース エンジンで利用できるようになります。 このため、SQL Server のエディション間でコストを比較しても差異が発生しません。 唯一の違いは、ユーザー数に基づく SharePoint CAL の価格です。  
  
-   この例はイントラネットへの配置であるため、SharePoint CAL ライセンスを SharePoint 2013 に適用します。  
  
-   PowerPivot モードの Analysis Services はファームの外側で実行されますが、PowerPivot は SQL server データベース エンジンと同じ物理サーバー (2) で実行されます。  
  
 ![bi_license_2tiers](../../../2014/sql-server/install/media/bi-license-2tiers.gif "bi_license_2tiers")  
  
 ![bi_license_2tiers_calcs1](../../../2014/sql-server/install/media/bi-license-2tiers-calcs1.gif "bi_license_2tiers_calcs1")  
  
##  <a name="bkmk_reference"></a> リファレンスとコミュニティ コンテンツ  
  
### <a name="license-tools"></a>ライセンスに関するツール  
  
-   [Microsoft License Advisor](http://mla.microsoft.com/default.aspx) (http://mla.microsoft.com/default.aspx)します。  
  
-   [クライアント アクセス ライセンス (CAL) の意思決定ツール](http://www.microsoft.com/licensing/CalTool/)(http://www.microsoft.com/licensing/CalTool/)します。  
  
-   [Microsoft Business Hub: 購入方法](http://www.microsoftbusinesshub.com/How_To_Buy#)(http://www.microsoftbusinesshub.com/How_To_Buy#)します。  
  
### <a name="microsoft-license-information"></a>Microsoft のライセンスに関する情報  
  
-   [についてライセンス: クライアント アクセス ライセンスとマネジメント ライセンス](http://www.microsoft.com/licensing/about-licensing/client-access-license.aspx)(http://www.microsoft.com/licensing/about-licensing/client-access-license.aspx)します。  
  
-   [についてライセンス: 検索のライセンス製品](http://www.microsoftvolumelicensing.com/default.aspx)(http://www.microsoftvolumelicensing.com/default.aspx)します。  
  
-   [ボリューム ライセンス: 価格と購入方法](http://www.microsoft.com/licensing/how-to-buy/how-to-buy.aspx)(http://www.microsoft.com/licensing/how-to-buy/how-to-buy.aspx)します。  
  
### <a name="community-content"></a>コミュニティ コンテンツ  
  
-   [SQL Server 2014 Developer Edition のライセンスに関するページ](http://sqlmag.com/sql-server-2014/sql-server-2014-developer-edition-licensing)。  
  
-   [SQL Server 2014 のライセンス変更](http://www.brentozar.com/archive/2014/04/sql-server-2014-licensing-changes)(http://www.brentozar.com/archive/2014/04/sql-server-2014-licensing-changes)します。  
  
-   [SQL Server 2014 のライセンスに対する変更](https://www.directionsonmicrosoft.com/sites/default/files/PDFs/Licensing_Changes_for_SQL_Server_2014.pdf)(https://www.directionsonmicrosoft.com/sites/default/files/PDFs/Licensing_Changes_for_SQL_Server_2014.pdf)します。  
  
-   [SharePoint 2013 のライセンス コストを見積もる](http://www.degdigital.com/blog/sharepoint-2013-licensing-for-dummies/)(http://www.degdigital.com/blog/sharepoint-2013-licensing-for-dummies/)します。  
  
-   [Microsoft ボリューム ライセンスのお客様のコミュニティ](http://www.microsoft.com/licensing/existing-customers/community.aspx)(http://www.microsoft.com/licensing/existing-customers/community.aspx)します。  
  
  
