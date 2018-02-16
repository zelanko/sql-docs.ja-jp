---
title: "Power Pivot の認証と承認 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48230cc0-4037-4f99-8360-dadf4bc169bd
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 691bf8b3fd2e26a3f906c88fbc8ceb840b636f6c
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="power-pivot-authentication-and-authorization"></a>Power Pivot の認証および承認
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
SharePoint 2010 ファーム内で実行される [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint の配置では、SharePoint サーバーによって提供される認証サブシステムと承認モデルを使用します。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 関連のすべてのコンテンツは SharePoint コンテンツ データベースに格納され、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]関連のすべての操作はファーム内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]共有サービスによって実行されるので、SharePoint のセキュリティ インフラストラクチャは [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] のコンテンツや操作にまで及ぶことになります。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データが含まれているブックを要求するユーザーは、Windows ユーザー ID に基づく SharePoint ユーザー ID を使用して認証されます。 この要求が許可されるか拒否されるかは、ブックに対する表示権限によって決まります。  
  
 セルフサービス型のデータ分析には Excel Services との統合が必要となるため、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバーをセキュリティで保護する場合、Excel Services のセキュリティについても理解している必要があります。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データへのデータ接続があるピボットテーブルに対してユーザーがクエリを実行すると、データ接続要求が Excel Services からファームの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバーに転送され、データが読み込まれます。 サーバー間のこの連携では、両方のサーバーのセキュリティ設定を構成する方法を理解している必要があります。  
  
 このトピックの特定のセクションを参照するには、次のリンクをクリックしてください。  
  
 [クラシック モード サインインを使用した Windows 認証の要件](../../analysis-services/power-pivot-sharepoint/power-pivot-authentication-and-authorization.md#bkmk_auth)  
  
 [ユーザーの承認を必要とする Power Pivot の操作](#UserConnections)  
  
 [Power Pivot データ アクセスに対する SharePoint 権限](#Permissions)  
  
 [Excel Services での Power Pivot ブックのセキュリティに関する考慮事項](#excel)  
  
##  <a name="bkmk_auth"></a> クラシック モード サインインを使用した Windows 認証の要件  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint では、SharePoint で使用できる認証オプションを縮小したオプション セットがサポートされています。 使用可能な認証オプションのうち、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint の配置では Windows 認証のみがサポートされます。 さらに、サインインに使用する Web アプリケーションでクラシック モードが構成されている必要があります。  
  
 Windows 認証が必要なのは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint の配置の Analysis Services データ エンジンで Windows 認証のみがサポートされているためです。 Excel Services は、MSOLAP OLE DB プロバイダーを介して、NTLM または Kerberos プロトコルによって認証された Windows ユーザー ID を使用して、Analysis Services への接続を確立します。  
  
 2 番目の要件である、Web アプリケーションでのクラシック モードの認証は、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Web サービスを確実に運用できるようにするために必要です。 Web サービスは、Web フロント エンドで実行されるコンポーネントで、ファーム内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint サーバーへの HTTP リダイレクトを可能にします。 Web サービスは、サービス間の通信の要求に対応しますが、ファーム内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 共有サービスに自らがルーティングするデータ接続要求には対応しません。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを読み込む要求は、Windows ID を使用した IIS からの認証接続でのみサポートされます。 Web アプリケーションでクラシック モードでサインインすることにより、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Web サービスからファーム内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 共有サービスに接続することができます。  
  
 より一般的なデータ アクセスのシナリオ ( [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを、そのデータを表示する同じ Excel ブックから抽出する場合) にはクラシック モードのサインインは必要ありませんが、他の認証プロバイダーを使用するように構成された SharePoint Web アプリケーションでは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint を使用しないでください。 使用した場合、外部データ ソースとして [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックにユーザーが接続しようとすると、必ず接続エラーになります。  
  
 クラシック モードのサインインを使用しないと、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Web サービスによって処理される次の種類の要求は失敗します。  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データに対するファーム外からの要求 (たとえば、データ ソースが [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックへの SharePoint URL であるレポートをレポート デザイナーまたはレポート ビルダーで作成する場合)  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックを外部データ ソースとして使用するファーム内のクライアント アプリケーションまたはレポートからの要求 (たとえば、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを格納する 2 番目に公開された Excel ブックをデータ ソースとして使用し、Excel デスクトップ アプリケーションでブックを作成する場合)  
  
### <a name="how-to-check-the-authentication-provider-for-your-application"></a>アプリケーションの認証プロバイダーを確認する方法  
 新しい Web アプリケーションを作成する場合は、[新しい Web アプリケーションの作成] ページで **[クラシック モード認証]** オプションを選択する必要があります。  
  
 既存の Web アプリケーションの場合は、次の手順に従って、Windows 認証を使用するように Web アプリケーションが構成されていることを確認します。  
  
1.  サーバーの全体管理で、[アプリケーション構成の管理] の **[Web アプリケーションの管理]**をクリックします。  
  
2.  Web アプリケーションを選択します。  
  
3.  **[認証プロバイダー]**をクリックします。  
  
4.  各ゾーンに 1 つのプロバイダーがあり、既定のゾーンが Windows に設定されていることを確認します。  
  
##  <a name="UserConnections"></a> ユーザーの承認を必要とする Power Pivot の操作  
 SharePoint の承認は、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] のクエリおよびデータ処理に対するすべてのレベルのアクセスに排他的に使用されます。  
  
 Analysis Services のロールベースの承認モデルはサポートされていません。 セル、行、テーブル レベルの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データのロールベースの承認はありません。 ブックのさまざまな部分をセキュリティで保護することによって、ブック内にある機密データへのアクセスを特定のユーザーについて許可したり、拒否したりすることはできません。 SharePoint ライブラリの Excel ブックに対する表示権限を持つユーザーは、埋め込まれた [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データをすべて使用できます。  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint は、次の場合に SharePoint のユーザーの権限を借用します。  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データベースへのデータ接続があるピボットテーブルまたはピボットグラフへのクエリ。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションは、データを処理する特定の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 共有サービス インスタンスに対して、ユーザーに代わって接続を確立します。  
  
-   キャッシュまたはライブラリからの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データの読み込み (それ以外の方法ではデータを利用できない場合)。 システムにまだ読み込まれていない [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データに対してデータ接続要求が行われた場合、 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] インスタンスでは、SharePoint ユーザー ID を使用して、データ ソースをコンテンツ ライブラリから取得し、メモリに読み込みます。  
  
-   データ ソースの更新されたコピーをコンテンツ ライブラリのブックに保存するデータ更新操作。 この場合、実際のログオン操作は、Secure Store Service の対象アプリケーションから取得したユーザー名とパスワードを使用して実行されます。 資格情報には、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 自動データ更新アカウント、またはデータ更新スケジュールの作成時に一緒に保存された資格情報を使用できます。 詳細については、「 [Power Pivot データ更新用の保存された資格情報の構成 (Power Pivot for SharePoint)](http://msdn.microsoft.com/en-us/987eff0f-bcfe-4bbd-81e0-9aca993a2a75) 」および「 [Power Pivot 自動データ更新アカウントの構成 (Power Pivot for SharePoint)](http://msdn.microsoft.com/en-us/81401eac-c619-4fad-ad3e-599e7a6f8493)」を参照してください。  
  
##  <a name="Permissions"></a> Power Pivot データ アクセスに対する SharePoint 権限  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックのパブリッシュ、管理、およびセキュリティ保護は、SharePoint 統合を通じてのみサポートされます。 SharePoint サーバーは、データへの正当なアクセスを確保する認証サブシステムと承認サブシステムを提供します。 SharePoint ファーム外に [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックを安全に配置するシナリオはサポートされていません。  
  
 サーバー上では、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データへの表示権限以上のユーザー アクセスは、読み取り専用です。 投稿権限では、ファイルを追加および編集できます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを変更するには、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel がインストールされている Excel デスクトップ アプリケーションにブックをダウンロードする必要があります。 ファイルに対する投稿権限があるかどうかにより、ユーザーがファイルをローカル コンピューターにダウンロードして、変更内容を再び SharePoint に保存することができるかどうかが決まります。  
  
 つまり、投稿および表示のみのレベルの権限によって、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データへのユーザー アクセスに対する有効な権限セットが定義されます。 その他の権限レベルは、その権限レベルに投稿および表示のみと同じ権限がある場合にその範囲内で機能します (たとえば、読み取り権限には表示のみ権限が含まれるので、読み取りに割り当てられているユーザーは表示のみと同じアクセス レベルを持ちます)。  
  
 次の表に、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データやサーバー操作へのアクセスを決定する権限レベルを要約します。  
  
|権限レベル|許可されるタスク|  
|----------------------|------------------------|  
|ファームまたはサービス管理者|サービスおよびアプリケーションをインストール、有効化、および構成します。<br /><br /> [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理ダッシュボードを使用し、管理レポートを表示します。|  
|フル コントロール|サイト コレクション レベルで [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 機能統合をアクティブ化します。<br /><br /> [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリー ライブラリを作成します。<br /><br /> データ フィード ライブラリを作成します。|  
|投稿|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックを追加、編集、削除、およびダウンロードします。<br /><br /> データ更新を構成します。<br /><br /> SharePoint サイトで [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックに基づいて新しいブックやレポートを作成します。<br /><br /> データ フィード ライブラリにデータ サービス ドキュメントを作成します。|  
|読み取り|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックに外部データ ソースとしてアクセスします。ブックの URL は接続ダイアログ ボックス (たとえば、Excel のデータ接続ウィザード) で明示的に入力されます。|  
|表示のみ|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックを表示します。<br /><br /> データ更新履歴を表示します。<br /><br /> ローカル ブックを SharePoint サイト上の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックに接続し、そのデータの用途を変更します。<br /><br /> ブックのスナップショットをダウンロードします。 スナップショットは、スライサー、フィルター、式、またはデータ接続を含まない、データの静的なコピーです。 スナップショットの内容は、ブラウザー ウィンドウからのセル値のコピーに似ています。|  
  
##  <a name="excel"></a> Excel Services での Power Pivot ブックのセキュリティに関する考慮事項  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] のサーバー側クエリ処理は、Excel サービスと密接に結び付いています。 製品の統合は、ドキュメント レベルで開始されます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを含んでいるか、参照している Excel ブック (.xlsx) ファイルです。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブック用の個別のファイル拡張子はありません。  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックを SharePoint サイトで開くと、Excel Services は [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] の埋め込みデータ接続文字列を読み取り、要求をローカルの SQL Server Analysis Services OLE DB プロバイダーに転送します。 プロバイダーは、この接続情報をファーム内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバーに渡します。 要求が 2 つのサーバー間でシームレスに流れるには、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint により要求される設定を使用するように Excel Services を構成する必要があります。  
  
 Excel Services では、セキュリティ関連の構成設定は信頼できる場所、信頼できるデータ プロバイダー、および信頼できるデータ接続ライブラリで指定します。 次の表に、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ アクセスを有効化または拡張する設定について説明します。 ここに記載されていない設定は、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバー接続に影響しません。 これらの設定を指定する方法については、「 [初期構成(Power Pivot for SharePoint)](http://msdn.microsoft.com/en-us/3a0ec2eb-017a-40db-b8d4-8aa8f4cdc146)」の「Excel Services の有効化」を参照してください。  
  
> [!NOTE]  
>  ほとんどのセキュリティ関連の設定は、信頼できる場所に適用されます。 既定値を保持するか、サイトごとに異なる値を使用する場合は、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを含むサイト用に信頼できる場所を追加作成し、そのサイトにのみ以下の設定を構成できます。 詳細については、「 [Power Pivot サイト用の信頼できる場所の作成](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)」を参照してください。  
  
|領域|設定|Description|  
|----------|-------------|-----------------|  
|[Web アプリケーション]|Windows 認証プロバイダー|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] は、Excel Services から取得した要求トークンを Windows ユーザー ID に変換します。 Excel Services をリソースとして使用する Web アプリケーションは、Windows 認証プロバイダーを使用するように構成されている必要があります。|  
|信頼できる場所|場所の種類|この値は、 **[Microsoft SharePoint Foundation]**に設定されている必要があります。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバーは、.xlsx ファイルのコピーを取得して、それをファーム内の Analysis Services サーバーに読み込みます。 このサーバーはコンテンツ ライブラリから .xlsx ファイルのみを取得できます。|  
||外部データの許可|この値は、 **[信頼できるデータ接続ライブラリと、埋め込まれている接続]**に設定されている必要があります。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ接続は、ブックに埋め込まれています。 埋め込み接続を禁止した場合、ユーザーは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] キャッシュは表示できますが、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを操作することはできなくなります。|  
||更新時の警告|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーを使用してブックやレポートを格納している場合は、この値を無効にする必要があります。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ギャラリーには、[開くときに更新する] と [更新時の警告] の両方がオフになっているときに最適に動作するドキュメント プレビュー機能が含まれています。|  
|信頼できるデータ プロバイダー|MSOLAP.4<br /><br /> MSOLAP.5|既定では MSOLAP.4 が含まれますが、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ アクセスでは、MSOLAP.4 プロバイダーが SQL Server 2008 R2 バージョンである必要があります。<br /><br /> MSOLAP.5 は、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] for SharePoint の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] バージョンと共にインストールされます。<br /><br /> これらのプロバイダーは、信頼できるデータ プロバイダー一覧から削除しないでください。 場合によっては、ファーム内の別の SharePoint サーバーにもこのプロバイダーの追加のコピーをインストールすることが必要になることもあります。 詳細については、「 [SharePoint サーバーへの Analysis Services OLE DB プロバイダーのインストール](http://msdn.microsoft.com/en-us/2c62daf9-1f2d-4508-a497-af62360ee859)」を参照してください。|  
|信頼できるデータ接続ライブラリ|省略可。|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックでは、Office データ接続 (.odc) ファイルを使用できます。 .odc ファイルを使用してローカル [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックに接続情報を提供する場合、同じ .odc ファイルをこのライブラリに追加できます。|  
|ユーザー定義関数アセンブリ|該当なし。|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint では、Excel Services 用にビルドし、配置するユーザー定義関数アセンブリは無視されます。 特定の動作でユーザー定義アセンブリに依存している場合、作成したユーザー定義関数は [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] クエリ処理で使用されないことに留意してください。|  
  
## <a name="see-also"></a>参照  
 [Power Pivot サービス アカウントの構成](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md)   
 [Power Pivot の構成自動データ更新アカウント (Power Pivot for SharePoint)](http://msdn.microsoft.com/en-us/81401eac-c619-4fad-ad3e-599e7a6f8493)   
 [Power Pivot サイト用の信頼できる場所の作成](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)   
 [Power Pivot セキュリティ アーキテクチャ](http://go.microsoft.com/fwlink/?linkID=220970)  
  
  
