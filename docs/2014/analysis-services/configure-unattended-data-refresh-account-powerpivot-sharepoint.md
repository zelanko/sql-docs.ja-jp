---
title: PowerPivot 自動データ更新アカウントの構成 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 81401eac-c619-4fad-ad3e-599e7a6f8493
author: minewiskan
ms.author: owend
ms.openlocfilehash: a7f373dfa85e80de6bfd3a0bb33e9b28ab33a697
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527248"
---
# <a name="configure-the-powerpivot-unattended-data-refresh-account-powerpivot-for-sharepoint"></a>PowerPivot 自動データ更新アカウントの構成 (PowerPivot for SharePoint)
  PowerPivot 自動データ更新アカウントは、SharePoint ファームで PowerPivot データ更新ジョブを実行するために指定されたアカウントです。 構成すると、データ更新スケジュールページの [**管理者によって構成されたデータ更新アカウントを使用**する] オプションが有効になります (以下を参照)。 データ更新をスケジュールするブックの作成者は、データ更新ジョブの実行に PowerPivot 自動データ更新アカウントを使用したい場合に、このオプションを選択できます。 データ更新スケジュールの資格情報オプションを表示する方法の詳細については、「[データ更新のスケジュール &#40;PowerPivot for SharePoint&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md)」を参照してください。  
  
 ![SSAS_PowerpivotKJ_DataRefreshCreds](media/ssas-powerpivotkj-datarefreshcreds.gif "SSAS_PowerpivotKJ_DataRefreshCreds")  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]** SharePoint 2010  
  
 サーバーを構成するときに選択したオプションによっては、自動データ更新アカウントが既に作成されている場合もあります。 既定の構成では、最初に自動データ更新アカウントの ID がファーム アカウントに設定されます。 別のユーザーとして実行するようにアカウントを変更すると、配置のセキュリティを強化できます。 アカウントを変更するには、次の手順に従います。[既存の PowerPivot 自動データ更新アカウントによって使用される資格情報を更新](#bkmk_editUA)します。  
  
 その他のすべてのインストール シナリオでは、次の手順に従ってアカウントを手動で構成する必要があります。  
  
 このトピックは、次のセクションで構成されています。  
  
 [前提条件](#bkmk_prereq)  
  
 [手順 1: 対象アプリケーションを作成して資格情報を設定する](#bkmk_create)  
  
 [手順 2: PowerPivot サーバー構成ページで自動アカウントを指定する](#bkmk_specifyUA)  
  
 [手順 3: アカウントに投稿権限を付与する](#bkmk_grant)  
  
 [手順 4: データの更新時に外部データ ソースにアクセスするための読み取り権限を付与する](#bkmk_dbread)  
  
 [手順 5: データ更新構成ページでアカウントを使用できるかどうかを確認する](#bkmk_verify)  
  
 [PowerPivot 自動データ更新アカウントを使用する](#bkmk_use)  
  
 [既存の PowerPivot 自動データ更新アカウントで使用する資格情報の更新](#bkmk_editUA)  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq"></a> 前提条件  
 Secure Store Service を有効にして構成し、マスター キーを生成する必要があります。 その方法については、「 [SharePoint 2010 での PowerPivot データ更新](powerpivot-data-refresh-with-sharepoint-2010.md)」を参照してください。  
  
 PowerPivot 自動データ更新アカウントとして使用する Windows ドメイン ユーザー アカウントを事前に決めておく必要があります。 ここでは、使用方法を確認できるように、PowerPivot 自動データ更新アカウント専用に作成されたアカウントを使用する必要があります。  
  
 PowerPivot System サービスのアプリケーション ID を把握しておく必要があります。 このサービスアカウントには、手順1でターゲットアプリケーションを作成するときに自動データ更新アカウントに対する**フルコントロール**アクセス許可を付与します。 これらの権限により、PowerPivot System サービスは、データ更新中に自動データ更新アカウントの資格情報を取得できます。 必要なサービスアカウント情報を取得するには、サーバーの全体管理の [**サービスアカウントの構成**] ページを開き、PowerPivot サービスアプリケーションによって使用されるサービスアプリケーションプールを選択します。 既定では、これは**サービスアプリケーションプール-SharePoint Web サービスシステム**です。  
  
## <a name="configure-the-unattended-powerpivot-data-refresh-account"></a>自動 PowerPivot データ更新アカウントの構成  
 PowerPivot サービス アプリケーションごとに構成できる PowerPivot 自動データ更新アカウントは 1 つだけです。 アカウント情報はターゲット アプリケーションの Secure Store Service に保存され、定義済みの Windows ドメイン ユーザー アカウントに設定されます。 ターゲット アプリケーションが作成されたら、PowerPivot サービス アプリケーションの構成ページで、そのアプリケーションを PowerPivot データ更新アカウントとして指定できます。  
  
> [!NOTE]  
>  データ更新を自動データ更新アカウントで実行すると、自動データ更新に使用した Windows ユーザー アカウントに対して、使用状況レポートとデータ更新履歴が記録されます。 データ更新を要求しているユーザーやスケジュールを所有しているユーザーについて、より正確な記録が必要になる場合は、データ更新を実行する場合に他のいずれかのオプションを検討してください。 つまり、ユーザーに各自の資格情報を指定させるか (既定)、データ更新用にすべての Windows 資格情報を保存するための追加のターゲット アプリケーションを作成します。 詳細については、「[PowerPivot データ更新用の保存された資格情報の構成 &#40;PowerPivot for SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)」を参照してください。  
  
 自動データ更新アカウントの作成には、次の 5 つの段階があります。  
  
-   Secure Store Service でアカウントのターゲット アプリケーションを作成し、資格情報を指定する。  
  
-   PowerPivot サーバー構成ページで自動データ更新アカウント用のターゲット アプリケーション ID を指定する。  
  
-   アカウントに投稿権限を付与する。  
  
-   データ更新中に外部データ ソースにアクセスするための読み取り権限をアカウントに付与する。  
  
-   [データ更新の管理] スケジュール ページで、パブリッシュされた PowerPivot ブックのアカウントが使用できることを確認する。  
  
###  <a name="step-1-create-a-target-application-and-set-the-credentials"></a><a name="bkmk_create"></a>手順 1: ターゲットアプリケーションを作成し、資格情報を設定する  
  
1.  サーバーの全体管理で、[アプリケーション管理] の [**サービスアプリケーションの管理**] をクリックします。  
  
2.  [ **Secure Store Service**] をクリックします。  
  
3.  [ターゲットアプリケーションの管理] で、[**新規**] をクリックします。  
  
4.  [ターゲットアプリケーション ID] に、「 **PowerPivotDataRefresh**」と入力します。  
  
5.  [表示名] に「 **PowerPivot データ更新**」と入力します。  
  
6.  [連絡先の電子メール] に、自分の電子メール アドレスを入力します。  
  
7.  [ターゲットアプリケーションの種類] で、[**個人**] を選択します。  
  
    > [!NOTE]  
    >  PowerPivot サービス アプリケーションだけが PowerPivot 自動データ更新アカウントの資格情報を要求するため、このシナリオでは [個人] アカウントの種類を指定するのが適切です。 実際には、サービス アプリケーションは自動データ更新アカウントの唯一のユーザーであるため、[個人] アカウントの種類がこのターゲット アプリケーションに対して最適な選択肢になります。  
  
8.  [対象アプリケーションのページ URL] はスキップします。 PowerPivot データ更新では使用されません。  
  
9. **[次へ]** をクリックします。  
  
10. [ **Secure Store のターゲットアプリケーションの資格情報フィールドの指定**] ページで、既定値をそのまま使用します。 フィールドの名前と種類は、Windows ユーザー名と Windows パスワードにする必要があります。  
  
11. **[次へ]** をクリックします。  
  
12. [ターゲット アプリケーションの管理者] で、PowerPivot サービス アプリケーションのアプリケーション プール ID を指定します。 サービスには、実行時に自動データ更新アカウント情報を取得できるように、**フルコントロール**のアクセス許可が必要です。 さらに、アプリケーション設定に対する管理アクセス権を必要とする他の SharePoint ユーザーの Windows ドメイン ユーザー アカウントを指定します。  
  
13. **[OK]** をクリックします。  
  
14. 先ほど作成したターゲットアプリケーションを選択し、下矢印をクリックして、[**資格情報の設定**] を選択します。  
  
15. [**資格情報の所有者**] に、資格情報を更新するアクセス許可を付与する Windows ドメインユーザーアカウントを入力します。 資格情報は、データの新規アクションに使用されます。資格情報の**所有者**には、資格情報を変更するためのアクセス許可があります。  
  
16. **[OK]** をクリックします。  
  
###  <a name="step-2-specify-the-unattended-account-in-powerpivot-server-configuration-pages"></a><a name="bkmk_specifyUA"></a>手順 2: PowerPivot サーバー構成ページで自動アカウントを指定する  
  
1.  サーバーの全体管理で、[アプリケーション管理] の [**サービスアプリケーションの管理**] をクリックします。  
  
2.  PowerPivot サービス アプリケーションを探します。 サービス アプリケーションは、型で識別できます。 PowerPivot サービス アプリケーションの型は、 **[PowerPivot サービス アプリケーション]** です。  
  
3.  PowerPivot サービス アプリケーションの名前をクリックします。 PowerPivot 管理ダッシュボードが表示されるまで待ちます。  
  
4.  [アクション] の右上隅にある [**サービスアプリケーション設定の構成**] をクリックします。  
  
5.  [データ更新] の [PowerPivot 自動データ更新アカウント] で、前の手順で作成したターゲットアプリケーション ID **PowerPivotDataRefresh**を入力します。  
  
6.  **[OK]** をクリックします。  
  
###  <a name="step-3-grant-contribute-permissions-to-the-account"></a><a name="bkmk_grant"></a>手順 3: アカウントに投稿権限を付与する  
 PowerPivot 自動データ更新アカウントを使用する前に、使用する任意の PowerPivot ブックに対する投稿権限をこのアカウントに割り当てる必要があります。 この権限レベルは、ライブラリからブックを開き、データの更新後に再度ライブラリに保存するために必要です。  
  
 権限の割り当ては、サイト コレクションの管理者が実行する手順です。 SharePoint の権限は、ルート サイト コレクションで割り当てるか、ルート サイト コレクションより下位の任意のレベル (個々のドキュメントやアイテムを含む) で割り当てることができます。 権限の設定方法は、権限をどのくらい細かく設定する必要があるかによって異なります。 次の手順は、権限を付与する方法の一例を示しています。  
  
1.  SharePoint サイトで、[サイトの操作] の [**サイトの権限**] をクリックします。  
  
2.  **[アクセス許可の付与]** をクリックします。  
  
3.  [ユーザーの選択] に、PowerPivot 自動データ更新アカウントとして指定した Windows ドメイン ユーザー アカウントの名前を入力します。 これは、Secure Store Service でターゲット アプリケーションに指定した Windows ドメイン ユーザー アカウントの名前です。  
  
4.  [アクセス許可の付与] で、[**ユーザーにアクセス許可を直接付与**する] を選択します。  
  
5.  [**投稿**] を選択し、[ **OK**] をクリックします。  
  
###  <a name="step-4-grant-read-permissions-to-access-external-data-sources-used-in-data-refresh"></a><a name="bkmk_dbread"></a>手順 4: データ更新で使用される外部データソースにアクセスするための読み取り権限を付与する  
 データを PowerPivot ブックにインポートする場合、通常、外部データへの接続は、信頼関係接続か、(現在のユーザーの ID を使用してデータ ソースに接続する) 権限を借用した接続に基づきます。 これらの種類の接続は、現在のユーザーがインポートする対象のデータに対する読み取り権限を持つ場合にのみ有効です。  
  
 データ更新シナリオでは、データをインポートするために使用された接続文字列が、データを更新するために再利用されます。 接続文字列が現在のユーザーを想定している (たとえば、Integrated_Security=SSPI を含む文字列) 場合、PowerPivot System サービスは、PowerPivot 自動データ更新アカウントのユーザー ID を現在のユーザーとして渡します。 この接続は、外部データ ソースに対する読み取り権限が PowerPivot 自動データ更新アカウントに付与されている場合にのみ成功します。  
  
 このため、自動アカウントで実行されるすべてのデータ更新操作で使用されるすべての外部データ ソースに対する読み取り専用権限を、PowerPivot 自動データ更新アカウントに付与する必要があります。  
  
 組織で使用しているデータ ソースの管理者であれば、ログインを作成し、必要な権限を付与することができます。 管理者でない場合は、データの所有者に対してアカウント情報を連絡する必要があります。 PowerPivot 自動データ更新アカウントにマップされる Windows ドメイン ユーザー アカウントを必ず指定してください。 これは、このトピックの「(手順 1): ターゲットアプリケーションを作成し、資格情報を設定する」で指定したアカウントです。  
  
###  <a name="step-5-verify-account-availability-in-data-refresh-configuration-pages"></a><a name="bkmk_verify"></a>手順 5: データ更新構成ページでアカウントの可用性を確認する  
  
1.  PowerPivot データが含まれているパブリッシュ済みのブックのデータ更新構成ページを開きます。 ページを開く方法については、「 [PowerPivot for SharePoint&#41;&#40;データ更新をスケジュールする](schedule-a-data-refresh-powerpivot-for-sharepoint.md)」を参照してください。  
  
2.  [データ更新の構成] ページで、[**管理者によって構成されたデータ更新アカウントを使用**する] オプションが有効になっていることを確認します。  
  
3.  [**直ちに更新**する] チェックボックスをオンにし、[ **OK**] をクリックします。  
  
4.  ブックが格納されているライブラリで、ブックを選択し、右側に表示される下矢印をクリックして、[ **PowerPivot データ更新の管理**] を選択します。 データ更新ジョブが返すデータ量が多い場合は、数分待つことが必要な場合があります。  
  
 エラーが発生した場合は、[データ更新の履歴] ページで [**スケジュールの構成**] をクリックして、別の資格情報を試すことができます。 元のブックのデータ ソース接続情報を調べて、データ更新時に使用される接続文字列を表示することが必要な場合もあります。 接続文字列は、問題のトラブルシューティングに使用できるサーバーの場所とデータベースに関する情報を提供します。  
  
 トラブルシューティングの詳細については、TechNet Wiki の「 [PowerPivot データ更新のトラブルシューティング](https://go.microsoft.com/fwlink/p/?LinkID=223279)」を参照してください。  
  
##  <a name="using-the-powerpivot-unattended-data-refresh-account"></a><a name="bkmk_use"></a>PowerPivot 自動データ更新アカウントの使用  
 PowerPivot データ更新スケジュール ページの 3 つの資格情報オプションのうち、自動データ更新アカウントに対応するのは最初のオプションだけです。 データ更新スケジュールを設定する場合は、必ずこのオプションを選択してください。  
  
 ![SSAS_PowerpivotKJ_DataRefreshCreds](media/ssas-powerpivotkj-datarefreshcreds.gif "SSAS_PowerpivotKJ_DataRefreshCreds")  
  
 PowerPivot 自動データ更新アカウントへのアクセスには第 3 の資格情報オプション (ターゲット アプリケーション ID の入力を必要とするオプション) を使用しないでください。 このオプションで実行される追加の権限借用チェックにより、このオプションを PowerPivot 自動データ更新アカウント (または、[個人] アカウントの種類に基づくターゲット アプリケーション) と共に使用しようとすると検証エラーが発生します。 3番目のオプションの使用方法の詳細については、「 [PowerPivot データ更新用の保存された資格情報の構成 &#40;PowerPivot for SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)」を参照してください。  
  
##  <a name="update-the-credentials-used-by-an-existing-powerpivot-unattended-data-refresh-account"></a><a name="bkmk_editUA"></a>既存の PowerPivot 自動データ更新アカウントで使用される資格情報を更新する  
 セットアップまたは管理者によって自動データ更新アカウントが既に構成されている場合は、資格情報が保存されているターゲット アプリケーションを編集することで、ユーザー名またはパスワードを更新できます。 以前に PowerPivot 自動データ更新アカウントに関連付けられていた元の Windows ID は、Secure Store Service で資格情報を編集するときに表示されません。 期限切れのパスワードを更新するか、別のアカウントを指定するかにかかわらず、常に Secure Store Service でそのターゲット アプリケーションのユーザー名とパスワードの両方を再入力する必要があります。  
  
1.  サーバーの全体管理で、[アプリケーション管理] の [**サービスアプリケーションの管理**] をクリックします。  
  
2.  [ **Secure Store Service**] をクリックします。  
  
3.  **PowerPivotDataRefresh**の横にあるチェックボックスをオンにします。  
  
4.  [資格情報] で、[**設定**] をクリックします。  
  
5.  [**資格情報の所有者**] に、資格情報を更新するアクセス許可を付与する Windows ドメインユーザーアカウントを入力します。 資格情報は、データの新規アクションに使用されます。資格情報の**所有者**には、資格情報を変更するためのアクセス許可があります。  
  
6.  [ユーザー名] に、自動データ更新資格情報の一部となる Windows ドメイン ユーザー アカウントを入力します。  
  
7.  [パスワード] に、アカウントのパスワードを入力し、確認のためもう一度パスワードを入力します。  
  
8.  **[OK]** をクリックします。  
  
 パスワードだけでなく、アカウントのユーザー名も変更する場合、通常は外部データ ソースに対する読み取り権限や PowerPivot ブックを更新するための SharePoint 権限の付与などの追加の構成手順を実行する必要があります。 手順については、「PowerPivot 自動データ更新アカウントの構成:[手順 3: アカウントに投稿のアクセス許可を付与](#bkmk_grant)する」の手順に進み、残りのすべての手順を続行します。その後、アカウントが正しく構成されていることを確認します。  
  
## <a name="see-also"></a>参照  
 [SharePoint 2010 での PowerPivot データ更新](powerpivot-data-refresh-with-sharepoint-2010.md)   
 [データ更新 &#40;PowerPivot for SharePoint をスケジュールする&#41;](schedule-a-data-refresh-powerpivot-for-sharepoint.md)   
 [PowerPivot のデータ更新](power-pivot-sharepoint/power-pivot-data-refresh.md)  
  
  
