---
title: リモート テーブルのコピー (SQL Server PDW) の SQL Server PDW の構成します。
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 496b4214-5891-404c-8237-c2a1e09db6d5
caps.latest.revision: 11
ms.openlocfilehash: 46fdb88ce3a244946b89f14320229905793564ac
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="configure-sql-server-pdw-for-remote-table-copies"></a>リモート テーブルのコピーの SQL Server PDW を構成します。
SQL Server PDW アプライアンス以外のサーバー上の SMP SQL Server データベースにテーブルをコピーするリモート テーブルのコピー機能を使用するを構成する方法について説明します。  
  
このトピックでは、リモート テーブルのコピーを構成するための構成手順のいずれかについて説明します。 すべての構成手順の一覧は、次を参照してください。[リモート テーブルのコピー](remote-table-copy.md)です。  
  
## <a name="before-you-begin"></a>はじめに  
リモート テーブルのコピーを使用する SQL Server PDW を構成するのには、次の操作を行います。  
  
-   直接ログオンする権限を持つ分析プラットフォーム システム管理者アカウントがある、***appliance_domain *-AD01**と ***appliance_domain *-AD02**ノード。  
  
-   ホスト名または移行先サーバーの IP 名を知っています。  
  
## <a name="HowToPDW"></a>リモート テーブルのコピーの SQL Server PDW の構成: DNS のホスト名を更新  
**CREATE REMOTE TABLE**リモート テーブルのコピーを使用するステートメントは、IP アドレスまたは SMP Windows システムの IP 名を使用して、移行先サーバーを指定します。 IP 名を使用するのには、DNS サーバーに名前解決の成功のエントリを追加する必要があります。  
  
次の手順では、DNS サーバーを更新する方法を説明します。  
  
1.  作業中の AD ノードにログオン (通常 ***appliance_domain *-AD01**)。  
  
2.  DNS マネージャーを開きます。 これは、下にある **管理ツール**で、**開始**メニュー。  
  
3.  IP 名を追加するのにには、DNS マネージャーを使用します。  
  
## <a name="see-also"></a>参照  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[非アプライアンスの DNS 名を解決するのには、DNS フォワーダーを使用します。](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
<!-- MISSING LINKS 
[Security - Configure Domain Trusts &#40;SQL Server PDW&#41;](../sqlpdw/security-configure-domain-trusts-sql-server-pdw.md)  
-->
  
