---
title: PDW のファイアウォールの構成 - Analytics Platform System |Microsoft ドキュメント
description: SQL Server PDW 構成マネージャーの [ファイアウォール] ページでは有効にするにまたは許可するか、Analytics Platform System アプライアンス上の特定のポートにアクセスできないようにするファイアウォール規則を無効にすることができます。
aauthor: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 8ccfd60aee7647c2421870a09ab5fa9b2653b99d
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31539382"
---
# <a name="parallel-data-warehouse-firewall-configuration-in-analytics-platform-system"></a>Analytics Platform System での並列データ ウェアハウス ファイアウォール構成
**ファイアウォール**ページの SQL Server PDW 構成マネージャーでは、有効にするにまたは許可するか、Analytics Platform System アプライアンス上の特定のポートにアクセスできないようにするファイアウォール規則を無効にすることができます。  
  
## <a name="to-manage-ports-and-firewall-rules-for-appliance-nodes"></a>ポートとファイアウォールを管理するには、アプライアンス ノードのルールします。  
  
1.  構成マネージャーを起動します。 詳細については、次を参照してください。[構成マネージャーを起動&#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)です。  
  
2.  構成マネージャーの左側のウィンドウで展開**並列データ ウェアハウス トポロジ**、クリックして**ファイアウォール**です。  
  
3.  ルールを見つけ、ポートやファイアウォール構成一覧に更新し、選択するかその項目の横にあるボックスをオフにします。 SQL Server PDW の管理者が構成可能なオプションのみが、外部向けのノード上のポートを開いたり、閉じたりするを含め、この一覧に表示されます。  
  
4.  をクリックして**適用**して変更を保存します。  
  
![DWConfig アプライアンス PDW のファイアウォール](./media/pdw-firewall-configuration/SQL_Server_PDW_DWConfig_ApplPDWFirewall.png "SQL_Server_PDW_DWConfig_ApplPDWFirewall")  
  
## <a name="external-ports"></a>外部ポート  
PDW の外部からのクライアント接続については、次のポートを開きます。  
  
|用途|ポート番号|ノード|  
|-----------|-----------|---------|  
|SQL クライアント アクセス PDW (TDS)|17001|CTL|  
|ローダー クライアント アクセス (dwloader & SSIS)|8001|CTL|  
|リモート デスクトップ アクセス|3389|CTL を CMP|  
|SSIS BinaryLoaderDataChannel|16551|CTL|  
|dwloader BinaryLoaderDataChannel|16551|CMP|  
|SSL 暗号化接続が (内部通信、HDInsight クラスターのサービスにアクセスして、管理コンソールにアクセスする)|443|すべてのノード|  
|SQL Server PDW ロード制御フローの Windows 資格情報|8002|CTL|  
|_Kerberos|88|AD01 および AD02、|  
|_ldap|389|AD01 および AD02|  
  
## <a name="internal-ports"></a>内部ポート  
次のポートは、内部の通信と PDW によって使用されますの PDW アプライアンスの外部からの接続が開いていません。  
  
|用途|ポート番号|ノード|  
|-----------|-----------|---------|  
|DMS コントロール チャネルのトラフィック|16450|CTL を CMP|  
|DMS データ チャネルのトラフィック|16550|CTL を CMP|  
|内部診断|16650|CTL を CMP|  
|フェールオーバーの状態 (DM)|15000|CTL を CMP|  
|フェールオーバーの状態 (エンジン)|15001|CMP|  
|動的 (短期) ポートの範囲|20000-65535|CTL を CMP|  
|SQL Server ポート範囲 (TDS)|1433, 1500-1508|CTL を CMP|  
  
> [!NOTE]  
> 既定では TCP ポート 8020 を使用して外部のテーブルまたは外部データ ソースを作成します。 これらのステートメントは、代わりにその他のポートを構成できます。 Hortonworks JOB_TRACKER_LOCATION 既定ポートは、50300 です。 他のシステムやツールと統合すると、追加のポートが必要があります。  
  
<!-- MISSING LINKS ## See Also  
[HDInsight Firewall Configuration &#40;Analytics Platform System&#41;](hdinsight-firewall-configuration.md)  -->  
  
