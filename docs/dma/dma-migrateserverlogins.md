---
title: Data Migration Assistant で SQL Server ログインの移行 |Microsoft Docs
description: Data Migration Assistant で SQL Server ログインを移行する方法について説明します
ms.custom: ''
ms.date: 08/29/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, login migration
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: rajpo
manager: craigg
ms.openlocfilehash: 271cb804b63b7adc400f21e6ccbe8e95eb0de307
ms.sourcegitcommit: fb269accc3786715c78f8b6e2ec38783a6eb63e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/29/2018
ms.locfileid: "43152713"
---
# <a name="migrate-sql-server-logins-with-data-migration-assistant"></a>Data Migration Assistant で SQL Server ログインを移行します。

この記事では、Data Migration Assistant を使用して SQL Server ログインの移行の概要を示します。 

## <a name="which-logins-are-migrated"></a>ログインを移行します。

- (ドメイン ユーザーまたは Windows ドメイン グループ) などの Windows プリンシパル上に基づいてログインを移行することができます。 SQL Server ログインとも呼ばれる、SQL 認証に基づいて作成されたログインを移行することもできます。

- Data Migration Assistant 現在サポートしていません (証明書にマップされたログイン) のスタンドアロン セキュリティ証明書、スタンドアロン非対称キー (非対称キーにマップされるログイン) および資格情報にマップされたログインに関連付けられているログインします。

- Data Migration Assistant が動かない、 **sa**ダブル ハッシュ記号で囲まれた名前を持つログインとサーバーの原則 (\#\#)、内部使用のみであります。

- 既定では、Data Migration Assistant は、移行するすべての修飾ログインを選択します。 必要に応じて、移行する特定のログインを選択できます。 Data Migration Assistant は、修飾のすべてのログインを移行、する場合は、移行されるデータベースでユーザーのログイン マッピングが残ります。 

  特定のログインを移行する場合は、必ずを移行用に選択されたデータベース内の 1 つまたは複数のユーザーにマップされるログインを選択します。

- ログインの移行の一環として、Data Migration Assistant もユーザー定義サーバー ロールに移動し、サーバー レベルのアクセス許可をユーザー定義サーバー ロールに追加します。 ロールの所有者に設定する**sa**プリンシパル。

## <a name="during-and-after-migration"></a>移行の前後に

- ログインの移行の一環として、Data Migration Assistant、アクセス許可に割り当てます、ターゲット SQL Server でセキュリティ保護可能なソース SQL Server 上に存在します。 

  ターゲット SQL Server で、ログインが既に存在する場合は、Data Migration Assistant セキュリティ保護可能リソースに割り当てられた権限のみを移行および全体のログインを再作成することはできません。

- Data Migration Assistant は、対象サーバーで、ログインが既に存在する場合は、データベース ユーザーにログインをマップするベスト エフォートです。

- ログインの移行と推奨される移行後のアクションの全体的な状態を把握する移行の結果を確認することをお勧めします。

## <a name="resources"></a>リソース

[Data Migration Assistant (DMA)](../dma/dma-overview.md)

[Data Migration Assistant: 構成の設定](../dma/dma-configurationsettings.md)
