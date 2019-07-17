---
title: Linux 上のスナップショット フォルダーの共有 SQL Server レプリケーションの構成します。
description: この記事では、Linux でのスナップショット フォルダーの共有 SQL Server レプリケーションを構成する方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6959b2073871f70fb33823b50419c208a23df2dd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093181"
---
# <a name="configure-replication-with-non-default-ports"></a>既定以外のポートでレプリケーションを構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Network.tcpport mssql conf の設定で構成した任意のポートでリッスンしている Linux インスタンスで SQL server レプリケーションを構成できます。 ポートは、次の条件に該当する場合の構成時に、サーバー名に付加する必要があります。

1. Linux 上の SQL Server のインスタンスは、レプリケーションのセットアップ
2. 任意のインスタンス (Windows または Linux) は、既定以外のポートでリッスンします。 

インスタンスのサーバー名は @ を実行して確認できます@servernameインスタンス。

## <a name="examples"></a>使用例

'Server1' は、Linux 上のポート 1500 でリッスンします。 'Server1' は、配布用に構成するには、実行`sp_adddistributor`で`@distributor`します。 例: 

```sql
exec sp_adddistributor @distributor = 'Server1,1500'
```

'Server1' は、Linux 上のポート 1500 でリッスンします。 ディストリビューターのパブリッシャーを構成するには、次のように実行します。`sp_adddistpublisher`で`@publisher`します。 以下に例を示します。

```sql
exec sp_adddistpublisher @publisher = 'Server1,1500' ,  ,  
```

'Server2' は、Linux 上のポート 6549 でリッスンします。 サブスクライバーとして 'Server2' を構成するには実行`sp_addsubscription`で`@subscriber`します。 例:

```sql
exec sp_addsubscription @subscriber = 'Server2,6549' ,  ,  
```

'Server3' は、Server3 のサーバー名とインスタンス名 MSSQL2017 の Windows 上のポート 6549 でリッスンします。 'Server3' をサブスクライバーとして構成するには、実行、`sp_addsubscription`で`@subscriber`します。 以下に例を示します。

```sql
exec sp_addsubscription @subscriber = 'Server3/MSSQL2017,6549',  ,  
```

## <a name="next-steps"></a>次の手順

[概念:Linux 上の SQL Server レプリケーション](sql-server-linux-replication.md)

[レプリケーション ストアド プロシージャ](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)します。

