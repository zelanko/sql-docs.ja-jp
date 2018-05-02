---
title: PolyBase のインストール | Microsoft Docs
ms.custom: ''
ms.date: 02/23/2018
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: polybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine-polybase
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PolyBase, installation
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: fbb861dda4b837bc3f3003edf357c89efaa4eb88
ms.sourcegitcommit: f3aa02a0f27cc1d3d5450f65cc114d6228dd9d49
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2018
---
# <a name="polybase-installation"></a>PolyBase のインストール
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  SQL Server の試用版をインストールするには、「 [SQL Server 評価版ソフトウェア](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) 
  
## <a name="prerequisites"></a>Prerequisites  
  
- 64 ビット SQL Server 評価版。  
  
- Microsoft .NET Framework 4.5。  

- Oracle Java SE Runtime Environment (JRE). バージョン 7 (7.51 以降) と 8 がサポートされています ([JRE](http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html) または [Server JRE](http://www.oracle.com/technetwork/java/javase/downloads/server-jre8-downloads-2133154.html) が機能します)。 [Java SE ダウンロード](http://www.oracle.com/technetwork/java/javase/downloads/index.html)に移動します。 JRE が存在しない場合、インストーラーは失敗します。 JRE9 と JRE10 はサポートされていません。
    
- 最小メモリ: 4 GB。  
  
- 最小ハード ディスク容量: 2 GB。  
  
- Polybase が正常に機能するは、TCP/IP を有効にする必要があります。 TCP/IP は、Developer Edition と Express Edition を除く SQL Server のすべてのエディションで、既定で有効です。 Developer Edition および Express Edition で Polybase が正常に機能するためには、TCP/IP 接続を有効にする必要があります (「[Enable or Disable a Server Network Protocol](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)」 (サーバー ネットワーク プロトコルを有効または無効にする) を参照してください)。

- Azure blob または Hadoop クラスターのいずれかである外部データ ソース。 Hadoop のサポートされているバージョンについては、「[PolyBase を構成する](#supported)」を参照してください。  


> [!NOTE]
>   Hadoop に対して計算プッシュダウン機能を使用する予定の場合、ターゲットの Hadoop クラスターに HDFS のコア コンポーネントの Yarn/MapReduce があり、Jobhistory サーバーが有効であることを確認する必要があります。 PolyBase から MapReduce 経由でプッシュダウン クエリを送信し、JobHistory Server からステータスをプルします。 いずれかのコンポーネントがない場合、クエリは失敗します。 
  
 **注**  
  
 PolyBase は各マシンで 1 つの SQL Server インスタンスにのみインストールできます。  
  
## <a name="single-node-or-polybase-scaleout-group"></a>シングル ノードまたは PolyBase スケールアウト グループ
SQL Server インスタンスに PolyBase をインストールする前に、シングル ノード インストールが必要なのか、PolyBase スケールアウト グループが必要なのか検討することが推奨されます。 PolyBase スケールアウト グループの場合、次のように手配する必要があります。 
- すべてのマシンが同じドメインにある。
- インストール時、同じサービス アカウントとパスワードを使用する。
- SQL Server インスタンスがネットワーク経由で互いと通信できる。
- SQL Server インスタンスがすべて同じバージョンの SQL Server である。

PolyBase をスタンドアロンとスケールアウト グループのいずれかでインストールした後、変更することはできません。 この設定を変更するには、この機能をアンインストールし、再インストールする必要があります。

## <a name="install-using-the-installation-wizard"></a>インストール ウィザードを使用したインストール  
  
1.  **SQL Server インストール センター**を実行します。 SQL Server インストール メディアを挿入し、 **Setup.exe**をダブルクリックします。  
  
2.  **[インストール]** をクリックし、 **[SQL Server の新規スタンドアロン インストールを実行するか、既存のインストールに機能を追加します]** をクリックします。  
  
3.  [機能の選択] ページで、 **[外部データ用 PolyBase クエリ サービス]** を選択します。  
  
4.  [Server の構成] ページで、 **SQL Server PolyBase エンジン サービス** と SQL Server PolyBase データ移動サービスを同じアカウントで実行するように構成します。  
  
    > **重要:** PolyBase スケールアウト グループで、すべてのノード上の PolyBase エンジンおよび PolyBase データ移動サービスを、同じドメイン アカウントで実行する必要があります。  
    > PolyBase のスケール アウトを参照してください。  
  
5.  **[PolyBase の構成]** ページで、次の 2 つのオプションのいずれかを選択します。 詳細については、「 [PolyBase スケールアウト グループ](../../relational-databases/polybase/polybase-scale-out-groups.md) 」を参照してください。  
  
    -   スタンドアロンの PolyBase 対応インスタンスとして、 SQL Server インスタンスを使用します  
  
         SQL Server インスタンスをスタンドアロンのヘッド ノードとして使用するには、このオプションを選択します。  
  
    -   PolyBase スケールアウト グループの一部として、SQL Server インスタンスを使用します  このオプションを選択すると、ファイアウォールが開かれ、SQL Server データベース エンジン、SQL Server PolyBase エンジン、SQL Server PolyBase データ移動サービス、および SQL ブラウザーへの着信接続が許可されます。 ファイアウォールが開かれて、PolyBase スケールアウト グループ内の他のノードからの着信接続が許可されます。  
  
         このオプションを選択すると、Microsoft Distributed Transaction Coordinator (MSDTC) ファイアウォール接続も有効になり、MSDTC レジストリの設定が変更されます。  
  
6.  **[PolyBase の構成]** ページで、少なくとも 6 つのポートを含むポート範囲を指定します。 SQL Server セットアップにより、この範囲の最初の 6 つの利用可能なポートが割り当てられます。  
  
##  <a name="installing"></a> コマンド プロンプトを使用してインストールする  
 次の表の値を使用して、インストール スクリプトを作成します。 **SQL Server PolyBase エンジン** と **SQL Server PolyBase データ移動サービス** の 2 つのサービスは、同じアカウントで実行する必要があります。 PolyBase スケールアウト グループで、すべてのノード上の PolyBase サービスを、同じドメイン アカウントで実行する必要があります。  
  
|SQL Server のコンポーネント (SQL Server component)|パラメーターおよび値|Description|  
|--------------------------|--------------------------|-----------------|  
|SQL Server セットアップ コントロール|**必須**<br /><br /> /FEATURES=PolyBase|PolyBase 機能を選択します。|  
|SQL Server PolyBase エンジン|**省略可**<br /><br /> /PBENGSVCACCOUNT|エンジン サービスのアカウントを指定します。 既定値は、 **NT Authority\NETWORK SERVICE**です。|  
|SQL Server PolyBase エンジン|**省略可**<br /><br /> /PBENGSVCPASSWORD|エンジン サービス アカウントのパスワードを指定します。|  
|SQL Server PolyBase エンジン|**省略可**<br /><br /> /PBENGSVCSTARTUPTYPE|PolyBase エンジン サービスのスタートアップ モードを指定します (Automatic (既定)、Disabled、Manual)。|  
|SQL Server PolyBase データ移動サービス|**省略可**<br /><br /> /PBDMSSVCACCOUNT|データ移動サービスのアカウントを指定します。 既定値は、 **NT Authority\NETWORK SERVICE**です。|  
|SQL Server PolyBase Data Movement Service|**省略可**<br /><br /> /PBDMSSVCPASSWORD|データ移動アカウントのパスワードを指定します。|  
|SQL Server PolyBase Data Movement Service|**省略可**<br /><br /> /PBDMSSVCSTARTUPTYPE|データ移動サービスのスタートアップ モードを指定します (Automatic (既定)、Disabled、Manual)。|  
|PolyBase|**省略可**<br /><br /> /PBSCALEOUT|PolyBase スケールアウト計算グループの一部として SQL Server インスタンスを使用するかどうかを指定します。 <br />サポートされる値: **True**、 **False**|  
|PolyBase|**省略可**<br /><br /> /PBPORTRANGE|PolyBase サービスのポート範囲 (6 ポート以上) を指定します。 例:<br /><br /> `/PBPORTRANGE=16450-16460`|  
  
 **例**  
  
 セットアップ スクリプトの例を次に示します。  
  
```  
  
Setup.exe /Q /ACTION=INSTALL /IACCEPTSQLSERVERLICENSETERMS /FEATURES=SQLEngine,Polybase   
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="\<fabric-domain>\Administrator"   
/INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /PBSCALEOUT=TRUE   
/PBPORTRANGE=16450-16460 /SECURITYMODE=SQL /SAPWD="<StrongPassword>"   
/PBENGSVCACCOUNT="<DomainName>\<UserName>" /PBENGSVCPASSWORD="<StrongPassword>"   
/PBDMSSVCACCOUNT="<DomainName>\<UserName>" /PBDMSSVCPASSWORD="<StrongPassword>"  
  
```  
  
## <a name="post-installation-notes"></a>インストール後の注意  
 PolyBase は、DWConfiguration、DWDiagnostics、および DWQueue の 3 つのユーザー データベースをインストールします。   これらは PolyBase で使用するためのものであり、変更したり、削除したりできません。  
  
### <a name="how-to-confirm-installation"></a>インストールの確認方法  
 次のコマンドを実行します。 PolyBase がインストールされている場合は 1 を返し、それ以外の場合は 0 を返します。  
  
```sql  
SELECT SERVERPROPERTY ('IsPolybaseInstalled') AS IsPolybaseInstalled;  
```  
  
### <a name="firewall-rules"></a>ファイアウォール規則  
 SQL Server PolyBase のセットアップでは、コンピューターに次のファイアウォール規則が作成されます。  
  
-   SQL Server PolyBase – Database Engine - \<SQLServerInstanceName> (TCP-In)  
  
-   SQL Server PolyBase – PolyBase Services - \<SQLServerInstanceName> (TCP-In)  
  
-   SQL Server PolyBase - SQL Browser - (UDP-In)  
  
 インストール時に、PolyBase スケールアウト グループの一部として SQL Server インスタンスを使用することを選択した場合、これらの規則が有効になり、ファイアウォールが開かれて、SQL Server データベース エンジン、SQL Server PolyBase エンジン、SQL Server PolyBase Data Movement サービス、SQL Browser への着信接続が許可されます。 ただし、インストール中にコンピューターでファイアウォール サービスが実行していない場合、SQL Server セットアップはこれらの規則を有効にできません。 その場合は、コンピューターでファイアウォール サービスを開始し、これらの規則をインストール後に有効にする必要があります。  
  
#### <a name="to-enable-the-firewall-rules"></a>ファイアウォール規則を有効にするには  
  
-   **[コントロール パネル]** を開きます。  
  
-   **[システムとセキュリティ]** をクリックし、 **[Windows ファイアウォール]** をクリックします。  
  
-   **[詳細設定]** をクリックして、 **[受信の規則]** をクリックします。  
  
-   無効になっている規則を右クリックして、**[規則の有効化]** をクリックします。  
  
### <a name="polybase-service-accounts"></a>PolyBase サービス アカウント
PolyBase エンジンと PolyBase データ移動サービスのサービス アカウントを変更するには、PolyBase 機能をアンインストールし、再インストールします。
   
## <a name="next-steps"></a>次の手順  
 「 [PolyBase configuration](../../relational-databases/polybase/polybase-configuration.md)」を参照してください。  
  
  
