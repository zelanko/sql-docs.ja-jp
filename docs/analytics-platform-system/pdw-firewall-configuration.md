---
title: PDW のファイアウォールの構成 - Analytics Platform System |Microsoft Docs
description: SQL Server PDW 構成マネージャーの [ファイアウォール] ページでは有効にまたはを許可または Analytics Platform System appliance の特定のポートにアクセスできないようにするファイアウォール規則を無効にすることができます。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 6f650aac34e3a5299cabae500a8ee73250c3974d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960419"
---
# <a name="parallel-data-warehouse-firewall-configuration-in-analytics-platform-system"></a>Analytics Platform System の parallel Data Warehouse ファイアウォールの構成

**ファイアウォール**の SQL Server PDW 構成マネージャー ページでは、有効にまたはを許可または Analytics Platform System appliance の特定のポートにアクセスできないようにするファイアウォール規則を無効にすることができます。  
  
## <a name="to-manage-ports-and-firewall-rules-for-appliance-nodes"></a>ポートとファイアウォールを管理するには、アプライアンス ノードのルールします。  
  
1.  Configuration Manager を起動します。 詳細については、次を参照してください。 [Configuration Manager の起動&#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)します。  
  
2.  Configuration Manager の左側のウィンドウで展開**並列データ ウェアハウスのトポロジ**、 をクリックし、**ファイアウォール**します。  
  
3.  構成の一覧を更新し選択するか、その項目の横にあるボックスをオフにするポートまたはファイアウォールのルールを探します。 SQL Server PDW の管理者が構成可能なオプションだけが、外部向けのノード上のポートを開いたり、閉じたりするなど、この一覧に表示されます。  
  
4.  クリックして**適用**変更を保存します。  
  
![DWConfig アプライアンス PDW のファイアウォール](./media/pdw-firewall-configuration/SQL_Server_PDW_DWConfig_ApplPDWFirewall.png "SQL_Server_PDW_DWConfig_ApplPDWFirewall")  
  
## <a name="external-ports"></a>外部ポート  
PDW の外部からのクライアント接続は、次のポートが開かれます。  
  
|用途|ポート番号|ノード|  
|-----------|-----------|---------|  
|SQL クライアント アクセスの PDW (TDS)|17001|CTL|  
|ローダーのクライアント アクセス (dwloader & SSIS)|8001|CTL|  
|リモート デスクトップ アクセス|3389|CMP、CTL|  
|SSIS BinaryLoaderDataChannel|16551|CTL|  
|dwloader BinaryLoaderDataChannel|16551|CMP|  
|SSL 暗号化 (管理者コンソールにアクセスする内部通信) の接続|443|すべてのノード|  
|SQL Server PDW ロード制御フローの Windows 資格情報|8002|CTL|  
|(_K)|88|AD01 と AD02、|  
|_ldap|389|AD01 と AD02|  
| &nbsp; | &nbsp; | &nbsp; |
  
## <a name="internal-ports"></a>内部ポート  
次のポートは、社内コミュニケーションの PDW で使用されますが、PDW アプライアンスの外部からの接続が開かれていません。  
  
|用途|ポート番号|ノード|  
|-----------|-----------|---------|  
|DMS のコントロール チャネルのトラフィック|16450|CMP、CTL|  
|DMS データ チャネルのトラフィック|16550|CMP、CTL|  
|内部診断|16650|CMP、CTL|  
|フェールオーバーの状態 (DMS)|15000|CMP、CTL|  
|フェールオーバーの状態 (エンジン)|15001|CMP|  
|動的な (短期) ポート範囲|20000-65535|CMP、CTL|  
|SQL Server のポート範囲 (TDS)|1433, 1500-1508|CMP、CTL|  
| &nbsp; | &nbsp; | &nbsp; |
  
> [!NOTE]  
> 外部テーブルまたは外部データ ソースを作成するには、既定で TCP ポート 8020 が使用されます。 これらのステートメントは、代わりに他のポートを構成できます。 Hortonworks JOB_TRACKER_LOCATION の既定のポートは、50300 です。 その他のシステムおよびツールと統合すると、追加のポートが必要があります。  
  
<!-- MISSING LINKS ## See Also  
[HDInsight Firewall Configuration &#40;Analytics Platform System&#41;](hdinsight-firewall-configuration.md)
-->
  
