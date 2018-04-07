---
title: アプライアンスのノード (Analytics Platform System) に接続します。
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f975aa91-c816-4b29-89bf-923ab5b4abb4
caps.latest.revision: 19
ms.openlocfilehash: 9b95bc8285625170c9c9b4a91eeae99dcd3907a5
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="connect-to-appliance-nodes"></a>アプライアンスのノードに接続します。
このトピックでは、Analytics Platform System アプライアンス内の各ノードに接続するさまざまな方法について説明します。  
  
## <a name="connecting-with-hadoop"></a>Hadoop を使用した接続  
SQL Server PDW の Hadoop を使用して、前に SQL Server PDW に Java ランタイム環境をインストールする、アプライアンス管理者に問い合わせてください。 手順については、次を参照してください。[外部データへの PolyBase 接続を構成する&#40;Analytics Platform System&#41; ](configure-polybase-connectivity-to-external-data.md)アプライアンス Operations guide の「にします。  
  
## <a name="ConnectingToIndividualNodes"></a>アプライアンスのノードに接続します。  
各アプライアンスのノードに直接アクセスし、特定のユーザーの種類によって特定の使用シナリオでのみです。 次の表は、各アプライアンスのノードとするユーザーがそのノードに直接接続のシナリオを示します。  
  
<!-- MISSING LINKS For information on the purpose of each node, see [Understanding SQL Server PDW &#40;SQL Server PDW&#41;](../sqlpdw/understanding-sql-server-pdw-sql-server-pdw.md).  -->  
  
|||  
|-|-|  
|**[Node]**|**アクセスのシナリオ**|  
|コントロールのノード|Web ブラウザーを使用して、アクセス管理コンソールで、[管理] ノードで実行されます。 詳細については、次を参照してください。[アプライアンスを管理コンソールを使用して監視&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)です。<br /><br />すべてのクライアント アプリケーションおよびツールは、イーサネットまたは InfiniBand 接続で使用するかどうかに関係なく、コントロールのノードに接続します。<br /><br />コントロールのノードへのイーサネット接続を構成するのに、コントロールのノードのクラスター IP アドレスとポートを使用して**17001**です。 たとえば、「192.168.0.1,17001」とします。<br /><br />コントロールのノードへの InfiniBand 接続を構成するのには、使用 ***appliance_domain *-SQLCTL01**とポート**17001**です。 使用して ***appliance_domain *-SQLCTL01**アプライアンスの DNS サーバーは、サーバーをアクティブの InfiniBand ネットワークに接続します。 これを使用する、非アプライアンス サーバーを構成するのを参照してください。 [InfiniBand ネットワーク アダプターの構成](configure-infiniband-network-adapters.md)です。<br /><br />アプライアンスの管理者は、管理操作を実行するコントロールのノードに接続します。 たとえば、アプライアンスの管理者は、コントロールのノードから、次の操作を実行します。<br /><br />Analytics Platform System での構成、 **dwconfig.exe**構成ツール。|  
|コンピューティング ノード|コンピューティング ノードの接続は、[管理] ノードで送られます。 コンピューティング ノードの IP アドレスは、パラメーターとしてしないでアプリケーション コマンドに入力されます。<br /><br />読み込みのバックアップ、リモート テーブルのコピー、および Hadoop、SQL Server PDW は送信または、並列コンピューティング ノードと非アプライアンスのノードまたはサーバーの間で直接データを受信します。 これらのアプリケーションがコントロールのノードに接続して SQL Server PDW に接続し、コントロールのノード、コンピューティング ノードと非アプライアンス サーバー間の通信を確立するために SQL Server PDW します。<br /><br />たとえば、これらのデータ転送操作と並行してコンピューティング ノードへの直接接続が行われます。<br /><br />SQL Server PDW にサーバーを読み込んでから読み込んでいます。<br /><br />バックアップ サーバーに SQL Server PDW からデータベースをバックアップします。<br /><br />サーバーのバックアップからデータベースを復元する、SQL Server PDW にします。<br /><br />SQL Server PDW から Hadoop のデータのクエリを実行します。<br /><br />SQL Server PDW から外部の Hadoop テーブルへのデータをエクスポートします。<br /><br />SQL Server PDW のテーブルをリモートの SMP SQL Server データベースにコピーしています。|  
  
## <a name="connecting-to-the-ethernet-and-infiniband-networks"></a>Ethernet、InfiniBand ネットワークに接続します。  
リモート サーバーは、アプライアンス InfiniBand ネットワーク経由またはイーサネット ネットワーク経由で接続できます。 パフォーマンス上の理由から、サーバーの読み込みが、サーバーをバックアップおよびサーバーを使用してデータを受信**CREATE リモート TABLE AS SELECT**ステートメントが通常アプライアンス InfiniBand ネットワーク経由でデータを転送します。  
  
独自の顧客のワークグループまたはドメインに属しているアプライアンス以外のサーバーを構成し、カスタマー ネットワークを使用して、それらのサーバーおよびそれらにデータを転送に接続できます。 また、アプライアンスの InfiniBand ネットワーク経由で相互にデータを転送するためのオプションのある InfiniBand アプライアンスに接続されている非アプライアンス サーバーSQL Server PDW のパフォーマンスが低下するため、これには注意します。  
  
たとえば、このステートメントは、InfiniBand を使用してバックアップには、InfiniBand IP アドレス 192.168.0.1 をサーバーのバックアップを実行するためのネットワーク資格情報を追加します。 アプライアンス ドメインは*mypdw*サーバーのバックアップから、ステートメントが実行されるとします。 このステートメントを実行する前に、独自のパラメーターを入力する必要があります。  
  
```  
sqlcmd -S "mypdw-sqlctl01,17001" -U sa -P password -I -Q "exec sp_pdw_add_network_credentials '192.168.0.1', 'mypdw\Administrator', 'password'"  
```  
  
たとえば、読み込みコマンドは、次のように開始されます。  
  
```  
dwloader –S mypdw-SQLCTL01  
```  
  
<!-- MISSING LINKS ## See Also  
[Configure an External Windows System To Receive Remote Table Copies Using InfiniBand &#40;SQL Server PDW&#41;](../sqlpdw/configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband-sql-server-pdw.md)  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
