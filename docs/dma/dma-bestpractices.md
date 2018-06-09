---
title: データ Migration Assistant (SQL Server) のベスト プラクティス |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/02/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Best Practices
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 8a1b184a6a280b328df35ea04a1ab6caf996c7c8
ms.sourcegitcommit: 6fe7b5e8818bd0d94fce693c560d63cc6883d76f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34758112"
---
# <a name="best-practices-for-running-data-migration-assistant"></a>データ移行のアシスタントを実行するためのベスト プラクティス
この記事では、インストール、評価、および移行の次のベスト プラクティス情報を提供します。

## <a name="installation"></a>インストール
インストールされず、SQL Server のホスト コンピューター上で直接データ Migration Assistant を実行します。

## <a name="assessment"></a>評価
- 実稼働データベースで非ピーク時の評価を実行します。
- 実行、**互換性の問題**と**機能の新しい推奨**評価期間を短縮するには、個別に評価します。

## <a name="migration"></a>移行
- 非ピーク時にサーバーを移行します。
- データベースを移行する場合は、移行元サーバーとターゲット サーバーによってアクセス可能な 1 つの共有場所を示し可能であれば、コピー操作を回避します。 コピー操作は、バックアップ ファイルのサイズに基づく遅延に陥る可能性もあります。 コピー操作では、余分な手順のため、移行に失敗する可能性も増加します。 1 つの場所を指定すると、データ Migration Assistant をバイパスするコピー操作します。
 
    さらに、必ず移行の失敗を回避する共有フォルダーに正しいアクセス許可を提供します。 適切なアクセス許可は、このツールで指定されます。 SQL Server インスタンスがネットワーク サービスの資格情報で実行している場合、共有フォルダーに、SQL Server インスタンスのマシン アカウントへの正しい権限を付与します。

- 有効にするは、ソースとターゲット サーバーに接続するときに、接続を暗号化します。 暗号化は SSL を使用して、データ移行アシスタントと SQL ログインを移行する場合に特に便利である SQL Server インスタンスの間のネットワーク経由で送信されるデータのセキュリティを向上します。 SSL 暗号化を使用しないネットワークが攻撃者によってセキュリティが侵害された場合は、移行中、SQL ログインはインターセプト取得でしたやの場で、攻撃者によって変更されました。

    一方、すべてのアクセスにセキュリティで保護されたイントラネット構成が使用される場合には、暗号化は必ずしも必要ありません。 暗号化を有効にすると、余分なオーバーヘッドがパケットの暗号化/暗号化解除に必要なために、パフォーマンスが低下します。 詳細についてを参照してください[SQL Server への接続の暗号化](https://go.microsoft.com/fwlink/?linkid=832513)です。
