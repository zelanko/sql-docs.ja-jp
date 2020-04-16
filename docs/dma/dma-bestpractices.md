---
title: Data Migration Assistant のベスト プラクティス
description: データ移行アシスタントを使用して SQL Server データベースを移行するためのベスト プラクティスを学習します。
ms.custom: seo-lt-2019
ms.date: 03/12/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Best Practices
ms.assetid: ''
author: HJToland3
ms.author: rajpo
ms.openlocfilehash: f2bfbb79a8a4803bb56e3dce85f575e8cf257b4a
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388151"
---
# <a name="best-practices-for-running-data-migration-assistant"></a>Data Migration Assistant を実行するためのベスト プラクティス
この記事では、インストール、評価、および移行に関するベスト プラクティスの情報を提供します。

## <a name="installation"></a>インストール
SQL Server ホスト マシンに直接データ移行アシスタントをインストールして実行しないでください。

## <a name="assessment"></a>評価
- 非ピーク時に、運用データベースに対して評価を実行します。
- **[互換性の問題**] と **[新機能の推奨事項]** 評価を個別に実行して、評価期間を短縮します。

## <a name="migration"></a>移行
- ピーク時以外の時間帯にサーバーを移行します。

- データベースを移行する場合は、ソース サーバーと移行先サーバーからアクセスできる単一の共有場所を指定し、可能であればコピー操作を回避します。 コピー操作では、バックアップ ファイルのサイズに基づいて遅延が発生する場合があります。 コピー操作を行うと、追加の手順のために移行が失敗する可能性も高くなります。 1 つの場所が指定されている場合、データ移行アシスタントはコピー操作をバイパスします。
 
    また、移行の失敗を避けるために、共有フォルダに適切なアクセス許可を与えるようにしてください。 ツールで正しいアクセス許可が指定されています。 SQL Server インスタンスがネットワーク サービスの資格情報で実行されている場合は、SQL Server インスタンスのコンピューター アカウントに共有フォルダーに対する適切なアクセス許可を与えます。

- ソースサーバーとターゲットサーバーに接続する際に、暗号化接続を有効にします。 TLS 暗号化を使用すると、データ移行アシスタントと SQL Server インスタンス間のネットワーク間で送信されるデータのセキュリティが向上します。 TLS 暗号化が使用されず、ネットワークが攻撃者によって侵害された場合、移行される SQL ログインが攻撃者によって傍受されたり、その場で変更されたりする可能性があります。

    一方、すべてのアクセスにセキュリティで保護されたイントラネット構成が使用される場合には、暗号化は必ずしも必要ありません。 暗号化を有効にすると、パケットの暗号化と復号化に必要な余分なオーバーヘッドが発生するため、パフォーマンスが低下します。 詳細については、「 [SQL Server への接続の暗号化](https://go.microsoft.com/fwlink/?linkid=832513)」を参照してください。
    
- データを移行する前に、ソース データベースとターゲット データベースの両方で信頼できない制約を確認してください。 移行後、ターゲット データベースを再度分析し、データ移動の一部として制約が信頼されなくなったかどうかを確認します。 信頼できない制約を必要に応じて修正します。 制約を信頼できないままにしておくと、実行プランが不十分になり、パフォーマンスに影響を与える可能性があります。
