---
title: "作成し、CA での Power Pivot サービス アプリケーションの構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2e5693e-4af3-453f-83f3-07481ab1ac6a
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 343e3ed597e892e7b9e332d35acb6719e5b27aee
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-and-configure-power-pivot-service-application-in-ca"></a>作成し、CA で Power Pivot サービス アプリケーションを構成します。
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスの共有サービス インスタンスです。 各サービス アプリケーションは、固有のアプリケーション ID、構成設定、プロパティ、および内部データ ストレージを備えています。  
  
 このトピックには、次のセクションが含まれます。  
  
 [新しい Power Pivot サービス アプリケーションを作成するかどうかの決定](#determine)  
  
 [Power Pivot サービス アプリケーションの作成](#CreateApp)  
  
 [Power Pivot サービス アプリケーションの構成](#ConfigApp)  
  
 [Power Pivot サービス アプリケーションの Web アプリケーションへの割り当て](#AssignGSA)  
  
 [サービス アプリケーションのプロパティの編集](#EditGSA)  
  
##  <a name="determine"></a> 新しい Power Pivot サービス アプリケーションを作成するかどうかの決定  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint のインストールでは、ファーム内に少なくとも 1 つの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションが必要になります。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 構成ツールを使用してサーバーを構成した場合は、サービス アプリケーションが自動的に作成されます。 そうでない場合は、サーバーの全体管理で [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを手動で作成する必要があります。  
  
 サービス アプリケーションを作成すると、サービスが使用可能になり、サービス アプリケーション データベースが生成されます。 また、サービス アプリケーションの作成時に選択したオプションによっては、既定のサービス接続のグループに [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス接続が追加されます。 これにより、既定のサービス接続のグループにサブスクライブしているすべての SharePoint Web アプリケーションが、自動的かつ直ちに [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションにアクセスできるようになります。  
  
 複数の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを作成することもできます。 ほとんどの配置シナリオでは 1 つで十分ですが、次のようなビジネスの要件がある場合は、追加の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを作成することを検討する必要があります。  
  
-   アプリケーションごとに異なる自動 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ更新アカウントを使用する場合。  
  
-   異なるタイムアウト、使用状況履歴、およびクエリ応答レポートのしきい値を使用する場合。  
  
-   サービスの管理を別のユーザーに委任する場合。 管理者は、自分が管理しているアプリケーションについてのみ、データ更新の履歴や使用状況データなどのプロパティを表示できます。 SharePoint Web アプリケーションを分離する必要がある場合 (顧客ごとの SharePoint Web アプリケーションのデータの分離を保証するホスティング サービスを提供している場合など) は、別の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを作成して、各サービス管理者に自分が管理しているアプリケーションの構成設定とプロパティしか表示されないようにすることで、分離の要件を満たすことができます。  
  
 追加のサービス アプリケーションを作成する場合は、サービスの関連付けの管理に関する新たな要件として、 サービス アプリケーションを追加するたびにカスタム サービス関連付けリストを作成して使用する必要があります。  
  
 追加の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを作成する理由が特にない場合は、ファーム内のすべての Web アプリケーションに対して 1 つのサービス アプリケーションを使用してください。  
  
##  <a name="CreateApp"></a> Power Pivot サービス アプリケーションの作成  
  
1.  サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]**をクリックします。  
  
2.  **[サービス アプリケーション]** リボンで、 **[新規作成]**をクリックします。  
  
3.  **[SQL Server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション]** を選択します。 この項目が一覧に表示されない場合は、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint がインストールされていないか、正しく構成されていません。  
  
4.  **[新しい [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションの作成]** ページで、アプリケーションの名前を入力します。 既定値は PowerPivotServiceApplication\<番号 >。 複数の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを作成する場合は、それぞれの用途を明確に示す名前を付けると他の管理者にわかりやすくなります。  
  
5.  [アプリケーション プール] で、このアプリケーションのための新しいアプリケーション プールを作成し (推奨)、 そのアプリケーション プールのマネージ アカウントを選択または作成します。 必ずドメイン ユーザー アカウントを指定してください。 ドメイン ユーザー アカウントにより、パスワードやアカウント情報をまとめて更新できる SharePoint のマネージ アカウント機能を使用できるようになります。 ドメイン アカウントは、配置をスケールアウトして、同じ ID で実行されるサービス インスタンスを追加する場合にも必要です。  
  
6.  **[データベース サーバー]**の既定値は、ファーム構成データベースをホストする SQL Server データベース エンジン インスタンスです。 このサーバーを使用することも、別の SQL Server を選択することもできます。  
  
7.  **データベース名**、既定値は PowerPivotServiceApplication1_\<guid > です。 各 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションに固有のデータベースを作成する必要があります。 既定のデータベース名は、既定のサービス アプリケーション名に対応しています。 独自のサービス アプリケーション名を入力した場合は、サービス アプリケーションとデータベースを一緒に管理できるように、データベース名に対しても同様の命名規則を使用してください。  
  
8.  **[データベース認証]**の既定値は、"Windows 認証" です。 **[SQL 認証]**を選択する場合は、SharePoint 管理者ガイドを参照して、SharePoint 配置でその認証の種類を使用するためのベスト プラクティスを確認してください。  
  
9. 必要に応じて、**[この [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションのプロキシをファームの既定のプロキシ グループに追加します]** のチェック ボックスをオンにします。 のチェック ボックスをオンにします。これにより、このサービス アプリケーション接続が既定のサービス接続のグループに追加されます。  
  
     最初の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを作成する場合は、このチェック ボックスをオンにする必要があります。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理ダッシュボードが正しく機能するには、既定の接続グループに [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションが 1 つ存在している必要があります。  
  
     既定の接続グループに既に [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションが存在している場合は、それ以上追加しないでください。 同じ型のサービス アプリケーションのエントリを複数追加する構成はサポートされていないため、エラーが発生する可能性があります。 追加のサービス アプリケーションを作成する場合は、既定の接続グループには含めずに、カスタム リストに追加してください。  
  
     サービスの関連付けの詳細については、「 [サーバーの全体管理での SharePoint Web アプリケーションへの PowerPivot サービス アプリケーションの接続](../../analysis-services/power-pivot-sharepoint/connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md)」を参照してください。  
  
10. クリックして **OK.** 作成したサービスが、他のマネージ サービスと共にファームのサービス アプリケーションの一覧に表示されます。  
  
##  <a name="ConfigApp"></a> Power Pivot サービス アプリケーションの構成  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションは、既定の構成を使用して作成されます。 既定の設定は、ほとんどのシナリオで推奨されます。 既定の設定を変更するのは、応答の遅延や接続の切断などの問題が発生した場合や、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービスの構成を特定の SharePoint Web アプリケーションに対して変更する場合だけにしてください。  
  
1.  サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]**をクリックします。  
  
     サービス アプリケーションの一覧に、先ほど作成したサービス アプリケーションの名前が表示されます。 既定の名前は、 **"PowerPivotServiceApplication1"**です。  
  
2.  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションをクリックします。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理ダッシュボードが開きます。  
  
3.  ダッシュボードの右上隅にある **[アクション]** ボックスの一覧で、 **[サービス アプリケーションの設定の構成]**をクリックします。  
  
4.  **[データベース読み込みのタイムアウト]**の値を増減させて、データの読み込み要求を転送した SQL Server Analysis Services ( [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ) インスタンスからの応答を[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]サービスが待機する時間を変更します。 非常に大規模なデータセットには、ネットワーク上で移動する時間がかかるための十分な時間を許可する必要があります、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Excel ブックを取得し、移動するサービス インスタンス、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] クエリ処理の Analysis Services インスタンスへのデータです。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データは一般に大きいため、既定値は 30 分に設定されています。  
  
5.  **[接続プールのタイムアウト]**の値を増減させて、アイドル状態のデータ接続を開いたままにする時間 (分) を変更します。 既定値は 30 分です。 この期間に、同じ SharePoint ユーザーから同じ [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データに対する読み取り専用の要求が送られた場合、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービスはアイドル状態のデータ接続を再利用します。 指定した期間にそのデータに対する要求がそれ以上受信されなかった場合は、接続がプールから削除されます。 有効値は 1 ～ 3600 秒です。 接続プールの詳細については、「[構成設定のリファレンス &#40;Power Pivot for SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configuration-setting-reference-power-pivot-for-sharepoint.md)」を参照してください。  
  
6.  **[ユーザー接続プールの最大サイズ]**の値を増減させて、各 SharePoint ユーザー、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データセット、およびバージョンの組み合わせに関する個々の接続プールに [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービスが作成するアイドル接続の最大数を変更します。  
  
     既定値は 1000 です。 有効値は、-1 (無制限)、0 (ユーザー接続プールを無効にする)、または 1 ～ 10000 です。  
  
     これらの接続プールを使用すると、同じユーザーによる同じ読み取り専用データに対する継続的な接続を、サービスでより効率的にサポートできます。 接続プールを無効にすると、すべての接続が新しく作成されます。  
  
     接続プール サイズの制限を変更しても (値を 0 に設定した場合も)、接続が切断されることはありません。 接続プールは、データに接続するときの待ち時間を短縮するためのものです。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービスは、接続プールの設定に基づいて接続を拒否することはありません。  
  
7.  **[管理接続プールの最大サイズ]**の値を増減させて、Analysis Services への [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス接続用に作成された接続プール内の開いている接続の数を変更します。 各 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス インスタンスが同じコンピューター上の Analysis Services インスタンスに独立した管理接続を開きます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービスでは、アイドル状態の接続を確認し、サーバーのヘルスを監視するために管理接続を再利用する、独立したプールを作成します。 接続数の既定値は 200 です。 有効値は、-1 (無制限)、0 (管理接続プールを無効にする)、または 1 ～ 10000 です。 0 を選択すると、すべての接続が新しく作成されます。  
  
8.  **[割り当て方法]**では、負荷分散方式を指定できます。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスでは、最初の要求の負荷を分散するために、この方法を使用して特定の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションが選択されます。 既定値は **[ヘルス ベース]**で、使用可能なメモリとプロセッサ使用率によって評価されるサーバーの状態に基づいて要求を割り当てることができます。 また、 **[ラウンド ロビン]** を選択すると、サーバーがビジー状態かアイドル状態かに関係なく、要求を同じ順序でサーバーに割り当てることができます。  
  
9. [データ更新] の **[営業時間]**では、営業時間を定義する時間の範囲を指定できます。 データ更新スケジュールを営業時間後に実行すると、通常の営業時間中に生成されたトランザクション データを取得できます。  
  
10. **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 自動データ更新アカウント**で、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ更新ジョブを実行するための定義済みアカウントを保存する Secure Store Service の定義済みの対象アプリケーションを指定できます。 ID ではなく、必ず対象アプリケーション名を指定してください。 自動データ更新の対象アプリケーションは、SQL Server セットアップで [新しいサーバー] オプションを使用して [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint をインストールした場合は自動的に作成されます。 それ以外の場合は、対象アプリケーションを手動で作成する必要があります。 アカウントを構成する方法については、「 [Power Pivot 自動データ更新アカウントの構成 (Power Pivot for SharePoint)](http://msdn.microsoft.com/en-us/81401eac-c619-4fad-ad3e-599e7a6f8493)」を参照してください。  
  
11. **[ユーザーによるカスタムの Windows 資格情報の入力を許可する]**チェック ボックスをオンまたはオフにして、スケジュールの所有者が任意の Windows 資格情報を入力してデータ更新スケジュールを実行できるようにするかどうかを指定します。 このチェック ボックスを選択した場合 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションは作成され、保存された資格情報のセットごとに対象アプリケーションを管理します。 詳細については、「 [PowerPivot データ更新用の保存された資格情報の構成 (PowerPivot for SharePoint)](http://msdn.microsoft.com/en-us/987eff0f-bcfe-4bbd-81e0-9aca993a2a75)」を参照してください。  
  
12. **[処理履歴の最大の長さ]**では、データ更新処理の履歴レコードを保持する期間を指定できます。 この情報は、データ更新を使用するブックごとに保持されるデータ更新の履歴ページに表示されます。 表示されます、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理ダッシュ ボード。  
  
13. [使用状況データ収集] の **[クエリをレポートする間隔]**で、クエリ統計を報告する間隔を指定します。 クエリ統計は、サーバー間の通信を最小限に抑えるために単一のイベントとして報告されます。  
  
14. [使用状況データの履歴] で、使用状況データの履歴レコードを保持する期間を指定します。 使用状況情報は [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理ダッシュボードに表示されます。 指定した使用状況データ履歴の値が小さすぎると、レポートの効果が下がります。  
  
15. [使用状況データ収集] の各クエリ応答のしきい値で、カテゴリとカテゴリの境界を決定する上限を指定します。 これらのカテゴリによって、クエリの動作の評価基準が設定されます。 また、これらのカテゴリを使用して、システムのクエリ応答時間の傾向を監視できます。 この情報は [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 管理ダッシュボードに表示されます。  
  
16. **[OK]** をクリックして変更を保存します。  
  
     読み込みのタイムアウトや割り当て方法の変更は、新たに受信した要求に対してのみ適用されます。 既に進行中の要求に対しては、要求の受信時に有効だった値が適用されます。  
  
##  <a name="AssignGSA"></a> Power Pivot サービス アプリケーションの Web アプリケーションへの割り当て  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションの構成が完了したら、Web アプリケーションに関連するサービス アプリケーションの接続リストに追加することによって、サービス アプリケーションを Web アプリケーションに割り当てることができます。 これには 2 つの方法があります。  
  
-   "既定" **** の接続グループに追加します。 *既定の接続グループ* とは、そのグループを参照する任意の Web アプリケーションで使用できるサービス アプリケーション接続のコレクションです。 このリストに [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを 1 つ追加する必要があります。  
  
-   特定の Web アプリケーションの "カスタム" **** 接続リストを作成します。 複数の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを作成した場合は、カスタム リストで選択することによって、使用するサービス アプリケーションを選択できます。  
  
 既定の接続グループに同じ型のサービス アプリケーションを複数含めることもできますが、 このリストに複数の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを追加する構成はサポートされていません。  
  
1.  サーバーの全体管理で、 **[アプリケーション構成の管理]**の **[Web アプリケーションの管理]**をクリックします。  
  
2.  接続を割り当てるアプリケーションを選択します ("SharePoint -80" など)。  
  
3.  **[サービス接続]**をクリックします。  
  
4.  **[次の関連付けのグループを編集する]**で、 **[既定]** または **[カスタム]**を選択します。  
  
5.  **[カスタム]**を選択した場合は、使用する各サービス アプリケーション接続の横のチェック ボックスをオンにします。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション ([型] が **Power Pivot Service Application Proxy**に設定されているアプリケーション) が複数ある場合は、そのうちの 1 つだけを選択してください。  
  
6.  **[OK]**をクリックします。  
  
##  <a name="EditGSA"></a> サービス アプリケーションのプロパティの編集  
 サービス アプリケーションの名前、アプリケーション プール、データベース設定、およびサービスの関連付けを指定するプロパティ ページを再び開くには、次の手順に従ってください。  
  
1.  サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]**をクリックします。  
  
2.  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを選択します (クリックはしないでください)。 型の名前をクリックすると行全体を選択できます。  
  
3.  リボンの **[プロパティ]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [サーバーの全体管理での Power Pivot サーバーの管理と構成](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
  
