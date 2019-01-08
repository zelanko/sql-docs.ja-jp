---
title: Azure の仮想マシンの SQL Server Machine Learning Services での R 言語と Python の機能をインストールします。
description: R と Python のデータ サイエンスと機械学習、Azure クラウドで SQL Server 仮想マシンでソリューションを実行します。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/09/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6216142708a201a1ad720ab4e1e659c507744195
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432305"
---
# <a name="install-sql-server-machine-learning-services-with-r-and-python-on-an-azure-virtual-machine"></a>SQL Server Machine Learning サービスを Azure の仮想マシンで R と Python のインストールします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Azure では、インストールおよび構成タスクを排除することで SQL Server 仮想マシンで、Machine Learning サービスで R と Python の統合をインストールできます。 仮想マシンをデプロイすると、機能が使用する準備ができます。
 
ステップ バイ ステップの手順については、次を参照してください。 [、Azure portal で Windows SQL Server 仮想マシンのプロビジョニング方法](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision)します。

[構成の SQL server の設定](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision#4-configure-sql-server-settings)の手順では、インスタンスに machine learning を追加します。

<a name="firewall"></a>

## <a name="unblock-the-firewall"></a>ファイアウォールのブロックを解除します。

既定では、Azure の仮想マシン上のファイアウォールには、ネットワークのローカル ユーザー アカウントのアクセスをブロックするルールが含まれます。

アクセスできることを確認するには、このルールを無効にする必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]リモート データ サイエンス クライアントからのインスタンス。  それ以外の場合、仮想マシンのワークスペースを使用して、計算コンテキストで、機械学習のコードを実行できません。

リモート データ サイエンス クライアントからのアクセスを有効にします。

1. 仮想マシン で、[セキュリティが強化された Windows ファイアウォール] を開きます。
2. **[送信の規則]** を選択します
3. 次の規則を無効にします。
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`
  
## <a name="enable-odbc-callbacks-for-remote-clients"></a>リモート クライアントの ODBC コールバックを有効にする

サーバーを呼び出すクライアントが、機械学習ソリューションの一部として ODBC クエリを実行する必要があることを期待する場合は、スタート パッドがリモート クライアントの代理としての ODBC 呼び出しを実行できることを確認します必要があります。 

これを行うには、スタート パッドによって使用される SQL ワーカー アカウントがインスタンスにログインするできるようにする必要があります。 詳細については、次を参照してください。[データベース ユーザーとしての SQLRUserGroup の追加](../security/add-sqlrusergroup-to-database.md)します。

<a name="network"></a>

## <a name="add-network-protocols"></a>ネットワーク プロトコルを追加します。

+ 名前付きパイプを有効にする
  
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] では、クライアントとサーバー コンピューター間の接続 (および一部の内部接続) に、名前付きパイプ プロトコルが使用されます。 名前付きパイプが有効になっていない場合は、Azure 仮想マシンと、サーバーに接続するデータ サイエンス クライアントの両方に名前付きパイプをインストールし、有効化する必要があります。
  
+ TCP/IP を有効にする

  TCP/IP は、ループバック接続に必要です。 "DBNETLIB; のエラーが発生する場合SQL Server が存在しないかアクセスが拒否されました"、インスタンスをサポートする仮想マシンで TCP/IP を有効にします。