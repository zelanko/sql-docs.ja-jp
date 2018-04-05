---
title: SQL Server ログイン (データ Migration Assistant) の移行 |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/31/2017
ms.prod: sql-non-specified
ms.prod_service: dma
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-dma
ms.tgt_pltfrm: ''
ms.topic: article
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, login migration
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5d3347eb2aff8e14c3938880dde6fe1879eb910d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="migrating-sql-server-logins-using-data-migration-assistant"></a>データ Migration Assistant を使用して SQL Server ログインを移行します。

この記事では、データ Migration Assistant を使用して移行の SQL Server ログインの概要を示します。 

## <a name="key-concepts"></a>主要な概念
主要な概念を次に示します。

- (ドメイン ユーザーまたは Windows ドメイン グループ) などの Windows プリンシパル上に基づいてログインを移行することができます。 SQL Server ログインとも呼ばれる SQL 認証を基に作成されたログインを移行することもできます。

- データ Migration Assistant 現在サポートされていません (証明書にマップされているログイン) スタンドアロン セキュリティ証明書、スタンドアロン非対称キー (非対称キーにマップされたログイン) および資格情報にマップされているログインに関連付けられているログイン。

- データ Migration Assistant は移動せず、 **sa**ダブル ハッシュ記号で囲まれた名前を持つログインとサーバーの原則 (\#\#)、これは内部使用のみ。

- 既定では、データ移行 Assistatn は移行する修飾すべてのログインを選択します。 必要に応じて、移行する特定のログインを選択できます。 移行する場合のデータ Migration Assistant 修飾のすべてのログインは、移行されるデータベースでログイン ユーザーのマッピングが残ります。 

  特定のログインを移行する場合は、移行用に選択されたデータベースの 1 つまたは複数のユーザーにマップされるログインを選択することを確認してください。

- ログインの移行の一環として、データ Migration Assistant もユーザー定義サーバー ロールに移動し、サーバー レベルの権限をユーザー定義サーバー ロールに追加します。 ロールの所有者に設定されます**sa**プリンシパル。

- ログインの移行の一環として、データ Migration Assistant に権限を割り当てます、ターゲット SQL Server でセキュリティ保護可能なソース SQL Server 上に存在するとします。 

  対象の SQL Server にログインが既に存在する場合データ Migration Assistant 保護可能なリソースに割り当てられた権限のみを移行し、全体のログインを再作成することはできません。

- データ移行アシスタントは、対象サーバーにログインが既に存在する場合は、データベース ユーザーにログインをマップする最善の努力を使用します。

- ログインの移行と推奨される移行後アクションの全体的な状態を理解する移行の結果を確認することをお勧めします。

## <a name="resources"></a>リソース

[データ Migration Assistant (DMA)](../dma/dma-overview.md)

[データ移行のアシスタント: 構成の設定](../dma/dma-configurationsettings.md)
