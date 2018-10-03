---
title: クラスター ネットワークの構成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- cluster network selection, Setup
- cluster network selection
ms.assetid: 579482ef-a023-45b2-9176-b4a4188adf9d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3cd117a9f873de13938d8a6946faf4f1c00d522d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48163035"
---
# <a name="cluster-network-configuration"></a>クラスター ネットワークの構成
  フェールオーバー クラスター インスタンスのネットワーク リソースを指定するには、 **[クラスター ネットワークの選択]** ページを使用します。  
  
## <a name="options"></a>および  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターのネットワーク名** - ネットワーク上でフェールオーバー クラスター インスタンスを識別するために使用される名前です。  
  
 **[ネットワークの設定]** - フェールオーバー クラスター インスタンスの IP の種類と IP アドレスを指定します。  
  
 ノードの追加またはノードの削除を実行すると、その操作が進行している間、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターの既存の IP アドレスを示した読み取り専用の一覧が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって表示されます。  
  
-   統合インストール:  
  
    -   追加しようとしているノードが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターの既存のノードとまったく同じ一連のネットワーク サブネットをサポートする場合、他の IP アドレスは追加できません。 依存関係の設定は変更されません。  
  
    -   追加しようとしているノードが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターの既存のノードがサポートしているサブネットの一部のみをサポートする場合、他の IP アドレス リソースは追加できません。 指定された IP アドレスが一部のクラスター ノードでは無効であるという事実を反映するために、IP アドレス リソースの依存関係は [OR] に設定されます。  
  
    -   追加しようとしているノードが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターの既存のノードによって既にサポートされている以外のサブネットもサポートする場合、新しい有効な IP アドレスを追加することを選択できます。 新しい IP アドレスが指定された場合、指定された IP アドレスが一部のクラスター ノードでは無効であるという事実を反映するために、IP アドレス リソースの依存関係は [OR] に設定されます。  
  
    -   追加しようとしているノードが、他のネットワーク サブネットをサポートしている場合で、なおかつ、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターの既存のノードによってサポートされたサブネットは一切サポートしないという場合、別途 IP アドレスを追加する必要があります。 指定された IP アドレスが一部のクラスター ノードでは無効であるという事実を反映するために、IP アドレス リソースの依存関係は [OR] に設定されます。  
  
-   詳細設定インストール: インストールの完了手順で、フェールオーバー クラスター インスタンスのすべてのノードおよびサブネットについて、対応する IP アドレスを指定します。 マルチサブネット フェールオーバー クラスターの場合は複数の IP アドレスを指定できますが、サポートされる IP アドレスは、1 つのサブネットにつき 1 つだけです。 準備の対象となるすべてのノードは、少なくとも 1 つの IP アドレスを所有している必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスター内に複数のサブネットが存在する場合、IP アドレス リソースの依存関係を [OR] に設定するように求められます。ノードの削除:  
  
    -   残りの IP アドレスが、残りのすべてのノードでサポートされている場合は、IP アドレス リソースの依存関係を [AND] に設定するように求められます。  
  
    -   残りの IP アドレスが、残りのすべてのノードでサポートされていない場合は、IP アドレス リソースの依存関係は [OR] のままとなります。  
  
  
