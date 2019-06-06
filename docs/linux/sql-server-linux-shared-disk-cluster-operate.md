---
title: Linux 上の SQL Server のフェールオーバー クラスター インスタンスの動作 |Microsoft Docs
description: この記事では、Linux 上の SQL Server のフェールオーバー クラスター インスタンス (FCI) を運用する方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 86ba2672ee1ddb7d7c801556c817d93e6d2e0ceb
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66712912"
---
# <a name="operate-failover-cluster-instance---sql-server-on-linux"></a>フェールオーバー クラスター インスタンスの操作 - SQL Server on Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Linux 上の SQL Server のフェールオーバー クラスター インスタンス (FCI) を運用する方法について説明します。 Linux 上の SQL Server FCI を作成していない、表示[構成フェールオーバー クラスター インスタンス - SQL Server on Linux](sql-server-linux-shared-disk-cluster-configure.md)します。 

## <a name="failover"></a>[フェールオーバー]

Fci のフェールオーバーは、Windows Server フェールオーバー クラスター (WSFC) に似ています。 FCI をホストしているクラスター ノードに何らかのエラーが発生した場合、FCI はする必要がありますを別のノードで自動的にフェールオーバーします。 WSFC の場合とは異なりは、Pacemaker は、FCI の新しいホストとなるノードを取得するように、優先所有者を設定する方法はありません。

別のノードに FCI を手動で失敗することがあります。 プロセスは、WSFC 上の Fci の場合と同じではありません。 Wsfc では、ロール レベルでリソースをフェールオーバーします。 Pacemaker を移動するリソースを選択して、すべての制約が正しいと仮定すると、他のすべてが移動も。 

フェールオーバーする方法は、Linux ディストリビューションによって異なります。 Linux ディストリビューションの手順を実行します。

- [RHEL または Ubuntu](#-manual-failover-rhel-or-ubuntu)
- [SLES](#-manual-failover-sles)

## <a name = "#-manual-failover-rhel-or-ubuntu"></a> 手動フェールオーバー (RHEL または Ubuntu)

バイ サイドの Red Hat Enterprise Linux (RHEL) または Ubuntu サーバーは、手動フェールオーバーを実行するには、次の手順を実行します。
1.  次のコマンドを発行します。 

   ```bash
   sudo pcs resource move <FCIResourceName> <NewHostNode> 
   ```

   \<FCIResourceName > は、SQL Server FCI の Pacemaker リソース名です。

   \<NewHostNode >、FCI をホストするクラスター ノードの名前を指定します。 

   すべての受信確認は利用できません。

2.  手動のフェールオーバー中には、Pacemaker は、手動で移動する選択されたリソースの場所の制約を作成します。 この制約で参照する実行`sudo pcs constraint`します。

3.  フェールオーバーが完了したら、発行することによって、制約の削除`sudo pcs resource clear <FCIResourceName>`します。 

\<FCIResourceName > は、FCI の Pacemaker リソース名です。 

## <a name = "#-manual-failover-sles"></a> 手動フェールオーバー (SLES)


Suse Linux Enterprise Server (SLES) で使用して、 `migrate` SQL Server FCI を手動でフェールオーバー コマンドします。 例 :

```bash
crm resource migrate <FCIResourceName> <NewHostNode>
```

\<FCIResourceName > は、フェールオーバー クラスター インスタンスのリソースの名前です。 

\<NewHostNode > 新しい移行先ホストの名前を指定します。 


<!---

|Distribution |Topic 
|----- |-----
|**Red Hat Enterprise Linux with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Operate](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-sles-configure.md)

--->

## <a name="next-steps"></a>次の手順

- [Linux 上の SQL Server のフェールオーバー クラスター インスタンスを構成します。](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
