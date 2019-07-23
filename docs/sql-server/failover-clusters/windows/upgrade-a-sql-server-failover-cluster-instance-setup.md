---
title: SQL Server フェールオーバー クラスター インスタンスのアップグレード (セットアップ) | Microsoft Docs
ms.custom: ''
ms.date: 01/22/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- upgrading clusters
- clusters [SQL Server], upgrading
- failover clustering [SQL Server], creating clusters
- clusters [SQL Server], creating
- failover clustering [SQL Server], upgrading
ms.assetid: ea8b7d66-e5a1-402f-9928-8f7310e84f5c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0e5232f1f8cad8ba9e6dc4ffcb9d838614a8c2c6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68044704"
---
# <a name="upgrade-a-sql-server-failover-cluster-instance-setup"></a>SQL Server フェールオーバー クラスター インスタンスのアップグレード (セットアップ)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスターを [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] フェールオーバー クラスターにアップグレードするには、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セットアップ UI またはコマンド プロンプトを使用します。  
  
 ローカルでのインストールの場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セットアップを管理者として実行する必要があります。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] をリモート共有からインストールする場合は、そのリモート共有に対する読み取り権限を持つドメイン アカウントを使用する必要があります。  
  
 アップグレードを行う前に、「 [SQL Server フェールオーバー クラスター インスタンスのアップグレード](../../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance.md)」を参照してください。  
  
##  <a name="UpgradeSteps"></a>[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスターをアップグレードするには  
  
#### <a name="to-upgrade-a-includessnoversionincludesssnoversion-mdmd-failover-cluster"></a>[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスターをアップグレードするには  
  
1.  アップグレードするエディションと一致するエディションの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インストール メディアで、ルート フォルダーの setup.exe をダブルクリックします。 必須コンポーネントがインストールされていない場合は、インストールするように求められます。  
  
2.  必須コンポーネントがインストールされると、インストール ウィザードによって [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インストール センターが起動します。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の既存のインスタンスをアップグレードするには、インスタンスを選択します。  
  
3.  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セットアップ サポート ファイルが必要な場合は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セットアップによってインストールされます。 コンピューターの再起動を求めるメッセージが表示されたら、再起動してから続行します。  
  
4.  システム構成チェッカーにより、コンピューターで検出処理が実行されます。 続行するには、 [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  [プロダクト キー] ページで、以前の製品バージョンのエディションに一致する新しいバージョンのエディション用の PID キーを入力します。 たとえば、エンタープライズ フェールオーバー クラスターをアップグレードするには、 [!INCLUDE[ssEnterprise](../../../includes/ssenterprise-md.md)]用の PID キーを入力する必要があります。 **[次へ]** をクリックして次に進みます。 フェールオーバー クラスターのアップグレードに使用する PID キーは、同じ [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス内のすべてのフェールオーバー クラスター ノードで一貫している必要があります。  
  
6.  [ライセンス条項] ページで使用許諾契約書を読み、使用許諾条件に同意する場合は対応するチェック ボックスをオンにします。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の機能向上に役立てるため、機能の使用状況オプションを有効にしてレポートを [!INCLUDE[msCoName](../../../includes/msconame-md.md)]に送信することもできます。 **[次へ]** をクリックして次に進みます。 セットアップを終了するには、 **[キャンセル]** をクリックします。  
  
7.  [インスタンスの選択] ページで、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] にアップグレードする [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]インスタンスを指定します。 **[次へ]** をクリックして次に進みます。  
  
8.  [機能の選択] ページでは、アップグレードする機能があらかじめ選択されています。 機能名を選択すると、右側のペインに各コンポーネント グループの説明が表示されます。 アップグレードする機能は変更できず、アップグレード操作中に機能を追加することもできないことに注意してください。 アップグレード操作の完了後に、アップグレードされた [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] のインスタンスに機能を追加するには、「 [SQL Server 2016 のインスタンスへの機能の追加 &#40;セットアップ&#41;](../../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md)」を参照してください。  
  
     選択した機能の必須コンポーネントが、右側のペインに表示されます。 SQL Server セットアップでは、この手順の後半で説明するインストール手順の間に、まだインストールされていない必須コンポーネントをインストールします。 時間を節約するには、各ノードにこれらの必須コンポーネントを事前にインストールしておく必要があります。  
  
9. フィールドが [インスタンスの構成] ページで以前のインスタンスから自動的に生成されます。 新しい InstanceID 値を指定することもできます。  
  
     **[インスタンス ID]** : 既定では、インスタンス名がインスタンス ID として使用されます。 これは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンスのインストール ディレクトリとレジストリ キーを識別するために使用されます。 これは、既定のインスタンスの場合も名前付きインスタンスの場合も同様です。 既定のインスタンスの場合、インスタンス名とインスタンス ID は、MSSQLSERVER になります。 既定以外のインスタンス ID を使用するには、 **[インスタンス ID]** チェック ボックスをオンにして、値を指定します。 既定値をオーバーライドする場合、すべてのフェールオーバー クラスター ノードでアップグレードされたものと同じインスタンス ID を指定する必要があります。 アップグレード済みインスタンスのインスタンス ID は、すべてのノードに一致している必要があります。  
  
     **[検出されたインスタンスと機能]** : セットアップを実行中のコンピューター上にある [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスがグリッドに表示されます。 **[次へ]** をクリックして次に進みます。  
  
10. [必要なディスク領域] ページでは、指定した機能に必要なディスク領域が計算され、セットアップを実行中のコンピューター上の空き領域と比較されます。  
  
11. [フルテキスト検索アップグレード] ページで、アップグレードするデータベースのアップグレード オプションを指定します。 詳細については、「 [フルテキスト検索アップグレード オプション](https://msdn.microsoft.com/library/16c9376b-5fbb-4495-a429-06a2493849c9)」。  
  
12. **[エラー レポート]** ページで、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] に送信する、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の機能向上に役立つ情報を指定します。 既定では、エラー レポートのオプションは有効になっています。  
  
13. アップグレード処理が開始される前に、システム構成チェッカーによって別のルール セットが実行され、コンピューターの構成と指定した [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 機能が検証されます。  
  
14. フェールオーバー クラスター インスタンス内のノードの一覧、および各ノードの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] コンポーネントのインスタンスのバージョン情報が [クラスター アップグレード レポート] ページに表示されます。 また、データベース スクリプト状態およびレプリケーション スクリプト状態が表示されます。 さらに、 **[次へ]** をクリックしたときの動作についての情報メッセージも表示されます。 アップグレード済みのフェールオーバー クラスター ノードの数とノード総数の違いに応じて、 **[次へ]** をクリックしたときの動作がセットアップにより表示されます。 必須コンポーネントをまだインストールしていない場合に生じ得る不要なダウンタイムについての警告も表示されます。  
  
15. [アップグレードの準備完了] ページには、セットアップで指定したインストール オプションのツリー ビューが表示されます。 続行するには、 **[アップグレード]** をクリックします。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] セットアップは、選択した機能の必須コンポーネントを最初にインストールし、その後で機能をインストールします。  
  
16. アップグレード中は、セットアップの進行に合わせてアップグレードの進行状況を監視できるように、[進行状況] ページに状態が表示されます。  
  
17. 現在のノードでアップグレードが終了すると、すべてのフェールオーバー クラスター ノード、各フェールオーバー クラスター ノードの機能、およびそのバージョン情報に関するアップグレード状態の情報が [クラスター アップグレード レポート] ページに表示されます。 表示されたバージョン情報を確認し、残りのノードでのアップグレードを続行します。 アップグレードしたノードでフェールオーバーが発生した場合は、状態ページを確認する作業も必要になります。 Windows クラスター アドミニストレーターのツールを使用して確認することもできます。  
  
18. アップグレードが終了すると、[完了] ページにインストールの概要ログ ファイルへのリンクと、その他の重要な注意事項が表示されます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインストール プロセスを完了するには、 **[閉じる]** をクリックします。  
  
19. コンピューターの再起動を求めるメッセージが表示されたら、再起動してください。 セットアップが完了した時点で、インストール ウィザードによるメッセージを確認することが重要です。 セットアップ ログ ファイルの詳細については、「 [SQL Server セットアップ ログ ファイルの表示と読み取り](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)」を参照してください。  
  
20. アップグレード プロセスを完了するには、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フェールオーバー クラスターの他のすべてのノードで、これらの手順を繰り返します。  
  
## <a name="to-upgrade-a-includessnoversionincludesssnoversion-mdmd-multi-subnet-failover-cluster"></a>[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] マルチサブネット フェールオーバー クラスターをアップグレードするには  
  
#### <a name="to-upgrade-to-a-includessnoversionincludesssnoversion-mdmd-multi-subnet-failover-cluster-existing-includessnoversionincludesssnoversion-mdmd-cluster-is-a-non-multi-subnet-cluster"></a>[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] マルチサブネット フェールオーバー クラスターにアップグレードするには (既存の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] クラスターがマルチサブネット クラスターでない場合)  
  
1.  前述の手順に従って、クラスターを [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]にアップグレードします。  
  
2.  AddNode セットアップ操作を使用して別のサブネット上のノードを追加し、 **[クラスター ネットワークの構成]** ページで IP アドレス リソースの依存関係が OR になっていることを確認します。 詳細については、「[SQL Server フェールオーバー クラスターでのノードの追加または削除 &#40;Setup&#41;](../../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)」を参照してください。  
  
#### <a name="to-upgrade-a-multi-subnet-cluster-currently-using-stretch-v-lan"></a>拡張 V-LAN を現在使用しているマルチサブネット クラスターをアップグレードするには  
  
1.  前述の手順に従って、クラスターを [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]にアップグレードします。  
  
2.  ネットワーク設定を変更し、リモート ノードを別のサブネットに移動します。  
  
3.  Windows フェールオーバー クラスター管理ツールを使用して、IP アドレス リソースの依存関係が OR に設定された新しいサブネットの新しい IP アドレスを追加します。  
  
## <a name="next-steps"></a>Next Steps  
 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]へのアップグレード後は、次の作業を実行します。  
  
-   [データベース エンジンのアップグレードの完了](../../../database-engine/install-windows/complete-the-database-engine-upgrade.md)  
  
-   [データベース互換性モードの変更とクエリ ストアの使用](../../../database-engine/install-windows/change-the-database-compatibility-mode-and-use-the-query-store.md)  
  
-   [SQL Server 2016 の新機能を利用する](https://msdn.microsoft.com/library/d8879659-8efa-4442-bcbb-91272647ae16)  
  
## <a name="see-also"></a>参照  
 [SQL Server フェールオーバー クラスター インスタンスのアップグレード](../../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance.md)   
 [SQL Server セットアップ ログ ファイルの表示と読み取り](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)   
 [SQL Server 2016 のインスタンスへの機能の追加 &#40;セットアップ&#41;](../../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-2016-setup.md)  
  
  
