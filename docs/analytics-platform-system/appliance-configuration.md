---
title: 構成のチェックリスト - Analytics Platform System |Microsoft Docs
description: Analytics Platform System を独自の環境の構成に必要なタスクのチェックリストを提供します。 これらの構成タスクは、アプライアンスを使用する前に必要です。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 9977ac8ea73e37afef85a46d6794ea5136357b44
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961597"
---
# <a name="appliance-configuration-checklists-for-analytics-platform-system"></a>Analytics Platform System のアプライアンス構成のチェックリスト
Analytics Platform System を独自の環境の構成に必要なタスクのチェックリストを提供します。 これらの構成タスクは、アプライアンスを使用する前に必要です。  
  
> [!WARNING]  
> Analytics Platform System を使用して**Configuration Manager**最善の方法は、唯一サポートされているツールで使用可能なタスクを実行する方法。  
  
## <a name="BeforeTasks"></a>はじめに  
  
### <a name="prerequisites"></a>前提条件  
  
1.  アプライアンスをデータ センターにインストールされ、電源をオンにする必要があります。  
  
2.  IHV によって提供される、次の情報を確認してください。  
  
    -   PDW 管理ノードの外部 IP アドレス (*PDW_region-* CTL01)  
  
    -   アプライアンスのドメイン名  
  
    -   アプライアンスのドメイン管理者のユーザー名とパスワード  
  
3.  信頼された証明書を取得します。 接続を許可し、後の手順ではインポート、 **Admin Console**セキュリティで保護された接続を使用します。 証明書をパスワードで保護された PFX ファイル内の管理ノードに保存します。  
  
4.  起動、 **Configuration Manager**、次の手順を使用します。  
  
    1.  使用**リモート デスクトップ**PDW 管理ノードに接続する (*PDW_region*-CTL01)。 (CTL01 の外部 IP アドレスに接続する必要があります)。  
  
    2.  起動、 **Configuration Manager**から、**開始**PDW 管理ノードのメニュー。 Configuration Manager の最初の画面には、IHV によって作成されたアプライアンス トポロジが表示されます。 ご使用のアプライアンスの一部として、SQL Server PDW ソフトウェアによって認識されるハードウェア ノードの一覧になります。 アプライアンス トポロジ画面上のすべての設定を変更する必要はありません。  
  
## <a name="CMTasks"></a>Configuration Manager のタスクを実行します。  
SQL Server の PDW**Configuration Manager** (PDWCM) は、SQL Server PDW のシステム管理者は、アプライアンス レベルの操作を実行して、アプライアンス レベルの設定を変更するを使用するアプライアンスの管理ツールです。 たとえば、PDWCM を使用して、パスワードをリセット、タイム ゾーンの設定、IP アドレスを変更、SSL 証明書を構成、ファイアウォール経由のリモート アクセスを有効にする、起動またはアプライアンスを停止し、ファイルの瞬時初期化を設定します。  
  
使用**Configuration Manager**次の構成タスクを実行します。  
  
|構成タスク|説明|  
|----------------------|---------------|  
|コンポーネントの物理名を持つについて理解を深める|[PDW およびアプライアンス ファブリックの物理的なコンポーネント&#40;Analytics Platform System&#41;](pdw-and-appliance-fabric-physical-components.md)|  
|SQL Server PDW 構成マネージャーを起動します。|[Configuration Manager の起動&#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)|  
|ドメイン管理者のパスワードを変更します。|アプライアンスをプライベート Windows Active Directory Domain Services、アプライアンス内のノードを認証するために使用します。<br /><br />IHV は、アプライアンスの既定のドメイン管理者のパスワードを設定します。 これには、セキュリティで保護されたパスワードを変更する必要があります。<br /><br />**Configuration Manager**が、唯一サポートされているドメイン管理者のパスワードを変更する方法。<br /><br />詳細については、次を参照してください。[パスワードのリセット&#40;Analytics Platform System&#41;](password-reset.md)します。|  
|パスワードを変更、 **sa**ログオン|SQL Server PDW がという名前のシステム管理者のログオン**sa**します。 **Sa**ログオンは、すべての特権を持っています。 許可、拒否、または権限を取り消すことできます。 すべてのシステム ビューを表示することもできます。<br /><br />詳細については、次を参照してください。[パスワードのリセット&#40;Analytics Platform System&#41;](password-reset.md)します。|  
|アプライアンスのタイム ゾーンを設定します。|アプライアンスのすべてのノードの時間 (ローカルまたはその他の目的の時間) を設定します。<br /><br />詳細については、次を参照してください。[アプライアンスのタイム ゾーン構成&#40;Analytics Platform System&#41;](appliance-time-zone-configuration.md)します。|  
|SQL Server PDW アプライアンスの外部に公開されたネットワーク設定を指定します。|[アプライアンスのネットワーク構成&#40;Analytics Platform System&#41;](appliance-network-configuration.md)|  
|管理コンソールのセキュリティ証明書をインポートします。|証明書を HTTPS 経由で Secure Sockets Layer (SSL) 接続を提供できます、[アプライアンスの監視、管理コンソールを使用して&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)します。 既定で、 **Admin Console**プライバシーがないサーバーの認証を提供する自己署名証明書が含まれています。 この証明書には、という内容の Internet Explorer のエラーも返されます。「この web サイトのセキュリティ証明書に問題がある」ユーザーが接続したときにします。 この接続は、クライアントとサーバー間のインフライトのデータを暗号化が攻撃者からのリスクのままでの接続です。<br /><br />SQL Server PDW の管理者は、セキュリティで保護された接続があり、Internet Explorer でレポートされるエラーを削除するには、クライアントによって認識される信頼された証明機関にチェーンされている証明書をすぐに取得する必要があります。 (推奨) 制御ノードの仮想 IP アドレスをマップする完全修飾ドメイン名が必要です、または管理者コンソールにアクセスするバーは、ブラウザーのアドレスに入力された値に一致する証明書の名前。<br /><br />使用して、 **Configuration Manager**を追加または信頼された証明書を削除します。 Microsoft Windows HTTP サービス証明書の構成ツールを使用して直接 (`winHttpCertCfg.exe`) 証明書の管理はサポートされていません。<br /><br />詳細については、次を参照してください。 [PDW 証明書のプロビジョニング&#40;Analytics Platform System&#41;](pdw-certificate-provisioning.md)します。|
|機能スイッチ|Analytics Platform System AU7 で導入された機能スイッチについての情報を表示します。 このページを使用して、更新、または Analytics Platform System の機能と設定の有効/無効にします。 機能スイッチの値を変更するには、サービスの再起動が必要です。<br /><br />詳細については、次を参照してください。 [PDW 機能スイッチ&#40;Analytics Platform System&#41;](appliance-feature-switch.md)します。|
|有効またはを許可または SQL Server PDW アプライアンス上の特定のポートにアクセスできないようにする Windows ファイアウォール ルールを無効にします。|IHV は構成し、正常に動作するアプライアンスに必要なファイアウォール規則を有効にします。 ほとんどの場合いないを有効にするか、ファイアウォール規則を無効にするは。<br /><br />詳細については、次を参照してください。 [PDW のファイアウォール構成&#40;Analytics Platform System&#41;](pdw-firewall-configuration.md)します。|  
|開始し、停止、SQL Server PDW アプライアンス|停止または SQL Server PDW アプライアンスを開始します。 詳細については、次を参照してください。 [PDW のサービス状態&#40;Analytics Platform System&#41;](pdw-services-status.md)します。|  
|使用してファイルの瞬時初期化オプションの確認、**特権** ダイアログ ボックス|ファイルの瞬時初期化より迅速に実行するデータ ファイルの操作を許可する SQL Server 機能です。 SQL Server PDW では、Network Service アカウントに SE_MANAGE_VOLUME_NAME 特権が付与されている場合にのみ有効です。 既定でオフにされています。<br /><br />詳細については、次を参照してください。[インスタント ファイル初期化構成&#40;Analytics Platform System&#41;](instant-file-initialization-configuration.md)します。|  
|Master データベースのバックアップから復元します。|現在の削除**マスター**データベースし、バックアップに置き換えられます。 詳細については、次を参照してください。 [Master データベースの復元&#40;Analytics Platform System&#41;](restore-the-master-database.md)します。|  
  
## <a name="AddTasks"></a>追加の構成タスクを実行します。  
実行した後、 **Configuration Manager**のタスクは、次の追加の構成タスクの一覧を実行します。 これらのタスクの一部は省略可能です。  
  
|構成タスク|説明|  
|----------------------|---------------|  
|サード パーティ製のウイルス対策ソフトウェアをインストールして、外部からのノードに接続するための SQL Server PDW アプライアンス上で構成できます。<br /><br />(オプション)|詳細については、次を参照してください。[ウイルス対策ソフトウェア&#40;Analytics Platform System&#41;](antivirus-software.md)します。|  
|DSRM のパスワードを変更できます。<br /><br />(オプション)|詳細については、次を参照してください。[ディレクトリ サービス復元モードで AD ノードにログオンするための管理者パスワードの設定&#40;DSRM&#41; &#40;Analytics Platform System&#41;](set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode.md)します。|  
|ソフトウェア更新プログラムを受信するアプライアンスを構成します。<br /><br />(推奨)|アプライアンスは、SQL Server PDW と基になるソフトウェアの更新プログラムを受信するように構成する必要があります。<br /><br />詳細については、次を参照してください。 [Windows Server Update Services の構成&#40;WSUS&#41; &#40;Analytics Platform System&#41;](configure-windows-server-update-services-wsus.md)します。 WSUS の詳細については、次を参照してください。[ソフトウェア サービス&#40;Analytics Platform System&#41;](software-servicing.md)します。|  
|Hadoop または Azure blob ストレージなどの外部データへの接続を構成します。<br /><br />(オプション)|詳細については、次を参照してください。[外部データへの PolyBase 接続構成&#40;Analytics Platform System&#41;](configure-polybase-connectivity-to-external-data.md)します。|  
|ウイルス対策ソフトウェアを構成します。<br /><br />(オプション)|サード パーティ製のウイルス対策ソリューションでは、外部に公開されたノードを保護するために使用できますが、必須ではありません。 ガイドラインに従います。|  
|バックアップおよびサーバーの読み込みの InfiniBand ネットワーク アダプターを構成します。<br /><br />(オプション)|InfiniBand ネットワークを使用して SQL Server PDW に接続するバックアップおよびサーバーを読み込んで構成するには、現在アクティブな InfiniBand ネットワークに、InfiniBand 接続を解決するのには DNS アプライアンスを許可するネットワーク アダプターを構成する必要があります。|  
|テレメトリ データを Microsoft に送信する構成します。<br /><br />(オプション)|テレメトリ データを Microsoft に送信する Analytics Platform System を構成するには、コントロールのノードで PowerShell スクリプトを実行する必要があります。 具体的な手順については、次を参照してください。[を Microsoft に製品利用統計情報 フィードバックの送信&#40;SQL Server PDW&#41;](send-telemetry-feedback-to-microsoft-sql-server-pdw.md)します。|  
  
## <a name="see-also"></a>参照  
[ウイルス対策ソフトウェア&#40;Analytics Platform System&#41;](antivirus-software.md)  
[InfiniBand ネットワーク アダプターの構成&#40;SQL Server PDW&#41;](configure-infiniband-network-adapters.md)  
  
