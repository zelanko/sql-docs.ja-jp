---
title: '[サブスクリプションのプロパティ - サブスクライバー] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.subproperties.subscriber.f1
helpviewer_keywords:
- Subscription Properties dialog box
ms.assetid: bef66929-3234-4a45-8ec4-3b271519d07a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f9fa0e53e7bccdadf6d1aefdde9b716ad0a75c22
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52761670"
---
# <a name="subscription-properties---subscriber"></a>[サブスクリプションのプロパティ - サブスクライバー]
  サブスクライバーの **[サブスクリプションのプロパティ]** ダイアログ ボックスを使用すると、プル サブスクリプションのプロパティを表示したり設定したりできます。  
  
 **[サブスクリプションのプロパティ]** ダイアログ ボックスの各プロパティには説明が含まれています。 プロパティをクリックすると、ダイアログ ボックスの一番下に説明が表示されます。 このトピックでは、いくつかのプロパティについて追加情報を示します。 プロパティは次のように分類されます。  
  
-   すべてのサブスクリプションに適用されるプロパティ。  
  
-   トランザクション サブスクリプションに適用されるプロパティ。  
  
-   マージ サブスクリプションに適用されるプロパティ。  
  
 読み取り専用として表示されているオプションの場合、サブスクリプションが作成されている場合にのみ設定できます。 サブスクリプションの新規作成ウィザードで使用することのできないオプションを設定する場合は、サブスクリプションをストアド プロシージャで作成します。 詳細については、「 [Create a Pull Subscription](create-a-pull-subscription.md) 」および「 [Create a Push Subscription](create-a-push-subscription.md)」を参照してください。  
  
> [!NOTE]  
>  ディストリビューション エージェントまたはマージ エージェントのジョブがサブスクリプションに対してまだ作成されていない場合、ほとんどのサブスクリプション プロパティは表示されません。 プル サブスクリプションのエージェント ジョブを作成するには、[sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql) (スナップショットまたはトランザクション パブリケーションへのサブスクリプションの場合) または [sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql) (マージ パブリケーションへのサブスクリプションの場合) を実行します。  
  
## <a name="options-for-all-subscriptions"></a>すべてのサブスクリプションに対するオプション  
 **[スナップショットからパブリッシュされたデータを初期化]**  
 サブスクリプションがスナップショットで初期化されるか (既定)、別の方法で初期化されるかを決定します。 サブスクリプションの初期化の詳細については、「[サブスクリプションの初期化](initialize-a-subscription.md)」を参照してください。  
  
 **[スナップショットの場所]**  
 初期化または再初期化の際にアクセスするスナップショット ファイルの場所を決定します。 場所は次の値のいずれかです。  
  
-   **[既定の場所]**: ディストリビューターの構成時に定義される既定の場所です。 詳細については、「[既定のスナップショットの場所の指定 &#40;SQL Server Management Studio&#41;](specify-the-default-snapshot-location-sql-server-management-studio.md)」を参照してください。  
  
-   **[代替フォルダー]**: **[パブリケーションのプロパティ]** ダイアログ ボックスで指定することができる代替の場所です。 詳細については、「 [Alternate Snapshot Folder Locations](alternate-snapshot-folder-locations.md)」を参照してください。  
  
-   **[動的スナップショット フォルダー]**: パラメーター化された行フィルターを使用するマージ パブリケーションのスナップショットの場所です。 詳しくは、「 [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md)」をご覧ください。  
  
-   **[FTP フォルダー]**: FTP (ファイル転送プロトコル) サーバーにアクセスできるフォルダーです。 詳細については、「[FTP によるスナップショットの転送](transfer-snapshots-through-ftp.md)」を参照してください。  
  
 **[スナップショット フォルダー]**  
 **[スナップショットの場所]** オプションに対して **[既定の場所]** 以外の値を選択した場合、そのスナップショット フォルダーへのパスを指定する必要があります。  
  
 **[Windows 同期マネージャーを使用]**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 同期マネージャーを使用して、サブスクリプションを同期化できるかどうかを決定します。  
  
 **Security**  
 **[エージェント プロセス アカウント]** 行をクリックしてプロパティ ボタン (**[...]**) をクリックし、ディストリビューション エージェントまたはマージ エージェントがサブスクライバーで実行されるアカウントを変更します。 接続に関するセキュリティ オプションは、サブスクリプションの種類によって異なります。  
  
-   トランザクション パブリケーションへのサブスクリプションの場合、ディストリビューション エージェントがディストリビューターへの接続を作成するアカウントを変更するには、 **[ディストリビューター接続]** をクリックしてプロパティ ボタン (**[...]**) をクリックします。  
  
-   トランザクション パブリケーションへの即時更新サブスクリプションの場合、上記のディストリビューター接続に加え、サブスクライバーからパブリッシャーに変更を伝達するのに使用する方法を変更することができます。これを行うには、 **[パブリッシャー接続]** をクリックしてプロパティ ボタン (**[...]**) をクリックします。  
  
-   マージ パブリケーションへのサブスクリプションの場合、 **[パブリッシャー接続]** をクリックしてプロパティ ボタン (**[...]**) をクリックします。  
  
 各エージェントに必要な権限の詳細については、「 [Replication Agent Security Model](security/replication-agent-security-model.md)」を参照してください。  
  
## <a name="options-for-transactional-subscriptions"></a>トランザクション サブスクリプションに対するオプション  
 **[更新可能なサブスクリプション]**  
 サブスクライバーの変更がパブリッシャーにレプリケートされるかどうかを決定します。 変更は、キュー更新または即時更新を使用してレプリケートすることができます。 **[サブスクライバーの更新方法]** オプションでは、どの方法を使用するかを決定します。 詳細については、「 [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md)」を参照してください。  
  
## <a name="options-for-merge-subscriptions"></a>マージ サブスクリプションに対するオプション  
 **[パーティション定義 (HOST_NAME)]**  
 パラメーター化されたフィルターを使用するパブリケーションで、マージ レプリケーションは、2 つのシステム関数 (または両方のフィルターが両方の関数を参照している場合) のいずれかをサブスクライバーが受け取るデータを決定する同期中に評価します。**SUSER_SNAME()** または**HOST_NAME()** します。 既定では、**HOST_NAME()** は、マージ エージェントが実行されているコンピューターの名前を返しますが、この値はサブスクリプションの新規作成ウィザードでオーバーライドすることができます。 パラメーター化されたフィルターと **HOST_NAME()** のオーバーライドの詳細については、「[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md)」を参照してください。  
  
 **[サブスクリプションの種類]** と **[優先度]**  
 サブスクリプションがクライアント サブスクリプションまたはサーバー サブスクリプションであるかどうかを表示します (これは、サブスクリプションが作成された後では変更できません)。 サーバー サブスクリプションは、他のサブスクライバーへのデータの再パブリッシュと、競合解決方法の優先度の割り当てができます。  
  
 サブスクリプションの新規作成ウィザードでサーバーのサブスクリプションの種類を選択した場合、サブスクライバーには競合解決方法で使用される優先度が割り当てられます。  
  
 **[競合を対話的に解決する (対話的な解決をサポートするアーティクルに対してのみ適用されます)]**  
 インタラクティブ競合回避モジュールのユーザー インターフェイスを使用して、マージ同期中の競合を回避するかどうかを決定します。 これを行うには、 **[Windows 同期マネージャーを使用]** に **[有効化]** の値を設定する必要があります。 詳細については、「 [Interactive Conflict Resolution](merge/advanced-merge-replication-conflict-interactive-resolution.md)」を参照してください。  
  
 **[Web 同期]**  
 **[Web 同期を使用]** では、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] インターネット インフォメーション サービス (IIS) サーバーに接続してサブスクリプションを同期するかどうかを決定します。 このオプションは、パブリケーションに対して Web 同期が有効である場合のみ有効です。 詳細については、「 [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md)」を参照してください。  
  
 **[Web 同期を使用]** に **[True]** を選択した場合、次の手順に従います。  
  
-   **[Web サーバー アドレス]** に IIS サーバーのフル アドレスを入力します。  
  
-   サブスクライバーが IIS サーバーに接続されるアカウントを設定または変更するには、 **[Web サーバー接続]** 行をクリックしてプロパティ ボタン (**[...]**) をクリックします。  
  
-   必要であれば、 **[Web サーバーのタイムアウト]** を変更します。 タイムアウトは Web 同期要求の期限が切れるまでの期間 (秒単位) です。  
  
 構成の詳細については、「 [Configure Web Synchronization](configure-web-synchronization.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [プル サブスクリプションのプロパティの表示または変更](view-and-modify-pull-subscription-properties.md)   
 [プッシュ サブスクリプションのプロパティの表示または変更](view-and-modify-push-subscription-properties.md)   
 [パブリケーションのサブスクライブ](subscribe-to-publications.md)  
  
  
