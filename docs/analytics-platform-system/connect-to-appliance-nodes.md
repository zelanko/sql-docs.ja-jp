---
title: アプライアンス ノードと Analytics Platform System への接続 |Microsoft Docs
description: この記事では、Analytics Platform System appliance 内の各ノードに接続するさまざまな方法について説明します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: ae40d38768f081ea6c439c40059065d695ebee23
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961086"
---
# <a name="connect-to-appliance-nodes-in-analytics-platform-system"></a>Analytics Platform System でアプライアンス ノードへの接続します。
この記事では、Analytics Platform System appliance 内の各ノードに接続するさまざまな方法について説明します。  
  
## <a name="connecting-with-hadoop"></a>Hadoop との接続  
SQL Server PDW で Hadoop を使用する前に SQL Server PDW に Java ランタイム環境をインストールするには、アプライアンス管理者に問い合わせてください。 手順については、次を参照してください。[外部データへの PolyBase 接続構成&#40;Analytics Platform System&#41; ](configure-polybase-connectivity-to-external-data.md)アプライアンス操作ガイド 』 でします。  
  
## <a name="ConnectingToIndividualNodes"></a>アプライアンス ノードへの接続  
各アプライアンス ノードに直接アクセスは特定の状況下でのみ、特定のユーザーの種類。 次の表は、各アプライアンスのノードとするユーザーがそのノードに直接接続するシナリオを示します。  
  
<!-- MISSING LINKS For information on the purpose of each node, see [Understanding SQL Server PDW &#40;SQL Server PDW&#41;](../sqlpdw/understanding-sql-server-pdw-sql-server-pdw.md).  -->  

> [!WARNING]  
> 製品チームまたは AP 顧客サポート チームの明示的な同意なしのコントロールまたはコンピューティング ノード上のデータベースまたはテーブルの設定を変更すると、サポート対象外、APS アプライアンスがレンダーする可能性があります。
  
|||  
|-|-|  
|**[Node]**|**アクセスのシナリオ**|  
|制御ノード|Web ブラウザーを使用して、コントロールのノードで実行される管理コンソールにアクセスします。 詳細については、次を参照してください。[アプライアンスの監視、管理コンソールを使用して&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)します。<br /><br />すべてのクライアント アプリケーションとツールは、イーサネットまたは InfiniBand 接続が使用するかどうかに関係なく、コントロール ノードに接続します。<br /><br />制御ノードへのイーサネット接続を構成するには、制御ノードのクラスター IP アドレスとポートを使用して、 **17001**します。 たとえば、「192.168.0.1,17001」とします。<br /><br />コントロールのノードに InfiniBand 接続を構成するには使用 <strong>*appliance_domain*-SQLCTL01</strong>とポート**17001**します。 使用して <strong>*appliance_domain*-SQLCTL01</strong>、アプライアンス DNS サーバーでは、サーバーは active の InfiniBand ネットワークに接続します。 これを使用する非アプライアンス サーバーを構成するを参照してください。 [InfiniBand ネットワーク アダプターの構成](configure-infiniband-network-adapters.md)します。<br /><br />アプライアンス管理者は、管理操作を実行するコントロールのノードに接続します。 たとえば、アプライアンス管理者は、制御ノードから、次の操作を実行します。<br /><br />構成と Analytics Platform System、 **dwconfig.exe**構成ツール。|  
|コンピューティング ノード|コンピューティング ノードの接続は制御ノードに送られます。 コンピューティング ノードの IP アドレスがアプリケーションのコマンドにパラメーターとして入力ことはありません。<br /><br />読み込みの場合はバックアップ、リモート テーブルのコピー、および Hadoop、SQL Server PDW は送信または並列コンピューティング ノードと非アプライアンス ノードまたはサーバーの間で直接データを受信します。 これらのアプリケーションは、コントロール ノードに接続して SQL Server PDW に接続し、制御ノードがコンピューティング ノードと非アプライアンス サーバー間の通信を確立するために SQL Server PDW に送ります。<br /><br />たとえば、これらのデータ転送操作では、並行してコンピューティング ノードへの直接接続が行われます。<br /><br />SQL Server PDW に読み込みサーバーから読み込んでいます。<br /><br />バックアップ サーバーに SQL Server PDW からデータベースをバックアップします。<br /><br />SQL Server PDW にサーバーのバックアップからデータベースを復元します。<br /><br />SQL Server PDW から Hadoop データのクエリを実行します。<br /><br />SQL Server PDW から外部 Hadoop テーブルへのデータをエクスポートします。<br /><br />SQL Server PDW テーブルをリモートの SMP SQL Server データベースにコピーしています。|  
  
## <a name="connecting-to-the-ethernet-and-infiniband-networks"></a>イーサネット、InfiniBand ネットワークに接続します。  
リモート サーバーは、アプライアンス InfiniBand ネットワーク経由またはイーサネット ネットワーク経由で接続できます。 パフォーマンス上の理由で、サーバーを読み込んで、サーバーをバックアップするのとサーバーを使用してデータを受信**CREATE リモート TABLE AS SELECT**ステートメントでは、通常はアプライアンスの InfiniBand ネットワーク経由でデータを転送します。  
  
独自の顧客のワークグループまたはドメインに属している非アプライアンス サーバーを構成し、それらのサーバーおよびそれらへのデータの転送に接続するため、自社の顧客ネットワークを使用できます。 また、アプライアンスの InfiniBand ネットワークを介して相互にデータを転送するためのオプションのある InfiniBand アプライアンスに接続されている非アプライアンス サーバーSQL Server PDW のパフォーマンスが低下するため、これには注意します。  
  
たとえば、このステートメントは、InfiniBand IP アドレス 192.168.0.1 を持つバックアップ サーバーに InfiniBand を使用してバックアップを実行するためのネットワーク資格情報を追加します。 アプライアンスのドメインが*mypdw*、バックアップ サーバーから、ステートメントが実行されます。 このステートメントを実行する前に、独自のパラメーターを入力する必要があります。  
  
```  
sqlcmd -S "mypdw-sqlctl01,17001" -U sa -P password -I -Q "exec sp_pdw_add_network_credentials '192.168.0.1', 'mypdw\Administrator', 'password'"  
```  
  
たとえば、次のように読み込みコマンドが開始されます。  
  
```  
dwloader -S mypdw-SQLCTL01  
```  
  
<!-- MISSING LINKS ## See Also  
[Configure an External Windows System To Receive Remote Table Copies Using InfiniBand &#40;SQL Server PDW&#41;](../sqlpdw/configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband-sql-server-pdw.md)  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
