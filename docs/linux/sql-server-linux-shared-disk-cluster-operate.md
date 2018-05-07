---
title: 'フェールオーバー クラスター インスタンス: Linux 上の SQL Server の動作 |Microsoft ドキュメント'
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.openlocfilehash: 663bf4969d949f03368fbb66d608c4f6292afd7c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="operate-failover-cluster-instance---sql-server-on-linux"></a>フェールオーバー クラスター インスタンス: Linux 上の SQL Server の動作します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Linux 上の SQL Server のフェールオーバー クラスター インスタンス (FCI) を運用する方法について説明します。 Linux に SQL Server の FCI を作成していない、表示[構成のフェールオーバー クラスター インスタンス: SQL Server on Linux](sql-server-linux-shared-disk-cluster-configure.md)です。 

## <a name="failover"></a>[フェールオーバー]

Fci のフェールオーバーは、Windows Server フェールオーバー クラスター (WSFC) に似ています。 FCI をホストしているクラスター ノードに何らかの障害が発生した場合、FCI は必要がありますを別のノードで自動的にフェールオーバーします。 WSFC とは異なりペース、FCI の新しいホストとなるノードを選択するようにするために、優先所有者を設定する方法はありません。

別のノードに FCI を手動でフェールオーバーすることがあります。 プロセスは、WSFC で Fci の場合と同じです。 WSFC では、ロール レベルでリソースをフェールオーバーします。 ペース、内を移動するリソースを選択して、すべての制約が正しいと仮定すると、他のすべて移動されますも。 

フェールオーバーするための方法は、Linux ディストリビューションに依存します。 Linux ディストリビューションの手順に従います。

- [RHEL または Ubuntu](#rhelFailover)
- [SLES](#slesFailover)

## <a name = "#rhelFailover"></a> 手動フェールオーバー (RHEL または Ubuntu)

Red Hat Enterprise Linux (RHEL) バイ サイドまたは Ubuntu サーバーは、手動フェールオーバーを実行するには、次の手順を実行します。
1.  次のコマンドを発行します。 

   ```bash
   sudo pcs resource move <FCIResourceName> <NewHostNode> 
   ```

   \<FCIResourceName > SQL Server の FCI のペース リソースの名前です。

   \<NewHostNode >、FCI をホストするクラスター ノードの名前を指定します。 

   受信確認は取得しません。

2.  手動フェールオーバーでペースを手動で移動するように選択されたリソースの場所の制約を作成します。 この制約で参照する実行`sudo pcs constraint`です。

3.  フェールオーバーが完了したら、発行して制約を削除`sudo pcs resource clear <FCIResourceName>`です。 

\<FCIResourceName >、FCI のペース リソース名を指定します。 

## <a name = "#slesFailover"></a> 手動フェールオーバー (SLES)


Suse Linux Enterprise Server (SLES) で使用して、 `migrate` SQL Server の FCI を手動でフェールオーバーするコマンドします。 以下に例を示します。

```bash
crm resource migrate <FCIResourceName> <NewHostNode>
```

\<FCIResourceName > フェールオーバー クラスター インスタンスに名前を指定します。 

\<NewHostNode > 新しい移行先ホストの名前を指定します。 


<!---
|Distribution |Topic 
|----- |-----
|**Red Hat Enterprise Linux with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Operate](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-sles-configure.md)
--->

## <a name="next-steps"></a>次の手順

- [フェールオーバー クラスター インスタンス: Linux 上の SQL Server を構成します。](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
