---
title: 失敗したクラスター ノードの Analytics Platform System を決める |Microsoft Docs
description: この記事では、クラスター フェールオーバーが発生した後にクラスター フェールオーバーの警告が発生しましたが失敗した Analytics Platform System (APS) ノードの名前を確認する方法について説明します。 クラスターのフェイル オーバーのトラブルシューティングの一環として、問題を解決するために Microsoft に連絡する前に失敗したノードの名前を決定する必要があります。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 2c17fde577b71382cd3ee63b8c6f50818184eab0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961056"
---
# <a name="determine-which-cluster-node-failed-for-analytics-platform-system"></a>どのクラスター決定 Analytics Platform System のノードに失敗しました
このトピックでは、クラスター フェールオーバーが発生した後にクラスター フェールオーバーの警告が発生しましたが失敗した Analytics Platform System (APS) ノードの名前を確認する方法について説明します。 クラスターのフェイル オーバーのトラブルシューティングの一環として、問題を解決するために Microsoft に連絡する前に失敗したノードの名前を決定する必要があります。  
  
## <a name="Background"></a>バック グラウンド  
SQL Server PDW の高可用性の管理 ノードとコンピューティング ノードは、Windows フェールオーバー クラスターのアクティブまたはパッシブのコンポーネントとして構成されます。 アクティブなサーバーは、重要なシステムの要求に応答する失敗した場合、パッシブ サーバーがフェールオーバーし、失敗したサーバーの機能を実行します。  
  
クラスターのフェールオーバー後に SQL Server PDW は、ノードの状態を報告したときにパッシブのサーバーが、失敗した状態にします。 ただし、ない明白などのサーバーまたはノードが失敗しました、失敗したサーバーがオンラインのままである場合に特にです。 クラスターの障害をトラブルシューティングするには、するには、フェールオーバー ノードの名前を特定する必要があります。  
  
## <a name="AdminConsoleSolution"></a>管理コンソールのソリューション  
  
#### <a name="to-find-the-name-of-the-node-that-failed"></a>失敗したノードの名前を検索するには  
  
1.  管理者コンソールを開きます。 管理コンソールの詳細については、次を参照してください。[アプライアンスの監視、管理コンソールを使用して&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)します。 アラートの数でフェールオーバー イベントが含まれるフェールオーバーが発生した後、**ヘルス**ページ。 **ヘルス**PDW リージョン、およびアプライアンスの fabric 領域のページ。 各正常性ページには、**アラート**タブ。アラートについての詳細については、正常性 ページの アラート タブをクリックし、アラートをクリックします。  
  
## <a name="SystemView"></a>システム ビューのソリューション  
次の SQL ステートメントを使用する方法を示しています、 [sys.dm_pdw_component_health_active_alerts](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-active-alerts-transact-sql.md)失敗したサーバーの名前を検索するシステム ビュー。  
  
```sql  
SELECT  
SUBSTRING( component_instance_id, 2, charindex(' ', component_instance_id, 1)-2) AS failed_node_name,  
create_time AS failover_time  
FROM sys.dm_pdw_component_health_active_alerts  
WHERE alert_id = 500139  
ORDER BY failed_node_name;  
```  
  
