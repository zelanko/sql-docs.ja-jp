---
title: SQL Server Machine Learning サービスのファイアウォールの構成 |Microsoft Docs
description: SQL Server Machine Learning サービスのファイアウォールを構成する方法。
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: d2bf36ea9a7c7a0b193dc4613f6a36f58e66014a
ms.sourcegitcommit: 13d98701ecd681f0bce9ca5c6456e593dfd1c471
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2018
ms.locfileid: "49419057"
---
# <a name="firewall-configuration-for-sql-server-machine-learning-services"></a>SQL Server Machine Learning サービスのファイアウォールの構成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、machine learning サービスを使用する場合を考慮しておいてください管理者や設計者は、ファイアウォール構成の考慮事項を示します。

## <a name="default-firewall-rules"></a>既定のファイアウォール規則

既定では、SQL Server セットアップには、ファイアウォール ルールを作成して送信接続が無効にします。

SQL Server 2016 および 2017 では、これらの規則はセットアップがの 1 つの送信規則を作成、ローカル ユーザー アカウントに基づいて**SQLRUserGroup**そのメンバーへのネットワーク アクセスを拒否する (各ワーカー アカウントとして表示されました対象にローカルの原則規則。 SQLRUserGroup の詳細については、次を参照してください。[は、SQL Server Machine Learning Services の機能拡張フレームワークのセキュリティの概要](../../advanced-analytics/concepts/security.md#sqlrusergroup)します。

SQL Server の 2019 AppContainers への移行の一部としていくつか AppContainer Sid に基づいて、新しいファイアウォール規則: SQL Server セットアップによって作成された 20 AppContainers ごとに 1 つ。 ファイアウォール規則の名前の名前付け規則は**AppContainer 00 の SQL Server インスタンス MSSQLSERVER でネットワーク アクセスをブロック**00 (00-20 既定)、AppContainer の数には、MSSQLSERVER が、SQL の名前サーバー インスタンスです。

> [!Note]
> ネットワーク呼び出しが必要な場合は、Windows ファイアウォールの送信の規則を無効にできます。

## <a name="restrict-network-access"></a>ネットワーク アクセスを制限します。

既定のインストールでは、外部のランタイム プロセスからのすべての発信ネットワーク アクセスをブロックする Windows ファイアウォールの規則を使用します。 パッケージのダウンロード、および悪意のある可能性があるその他のネットワーク呼び出しは、外部のランタイム プロセスを防ぐためにファイアウォール規則を作成する必要があります。

別のファイアウォール プログラムを使用している場合のローカル ユーザー アカウントまたはユーザー アカウント プールによって表されるグループのルールを設定して、ランタイムの外部の送信ネットワーク接続をブロックするルールを作成することもできます。

R または Python ランタイムで無制限のネットワーク アクセスを防ぐために Windows ファイアウォール (または別のファイアウォール) を有効にすることを強くお勧めします。

## <a name="next-steps"></a>次の手順

[Windows ファイアウォールの着信接続を構成します。](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)