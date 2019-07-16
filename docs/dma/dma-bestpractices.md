---
title: Data Migration Assistant (SQL Server) のベスト プラクティス |Microsoft Docs
description: Data Migration Assistant で SQL Server データベースを移行するためのベスト プラクティスについて説明します
ms.custom: ''
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
ms.openlocfilehash: 5a717c47163e03e6430272ca44d2120c7328289e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68061785"
---
# <a name="best-practices-for-running-data-migration-assistant"></a>Data Migration Assistant を実行するためのベスト プラクティス
この記事では、インストール、評価、および移行のベスト プラクティスについてはいくつか提供します。

## <a name="installation"></a>インストール
インストールして、SQL Server のホスト コンピューターで直接 Data Migration Assistant を実行しないでください。

## <a name="assessment"></a>Assessment
- 実稼働データベースで非ピーク時の評価を実行します。
- 実行、**互換性の問題**と**新機能のお勧め**評価期間を短縮するには、個別に評価します。

## <a name="migration"></a>移行
- 非ピーク時にサーバーを移行します。

- データベースを移行する場合は、移行元サーバーとターゲット サーバーからアクセスできる 1 つの共有場所を提供し、可能であればコピー操作を回避します。 コピー操作は、バックアップ ファイルのサイズに基づいての遅延を生じる可能性があります。 コピー操作では、余分な手順のため、移行が失敗する可能性も高くなります。 1 つの場所を指定すると、バイパス、Data Migration Assistant、コピー操作でします。
 
    さらに、必ず移行の失敗を回避するために共有フォルダーに正しいアクセス許可を提供します。 適切なアクセス許可は、このツールで指定されます。 SQL Server インスタンスは、ネットワーク サービスの資格情報で実行する場合、共有フォルダーの SQL Server インスタンスのマシン アカウントへの適切な権限を付与します。

- 有効にするは、ソースとターゲット サーバーに接続するときに、接続を暗号化します。 SSL を使用して暗号化は、Data Migration Assistant と SQL ログインを移行する場合に特に有益である SQL Server インスタンスの間のネットワークを介して転送されるデータのセキュリティを向上します。 SSL 暗号化が使用されていないネットワークが攻撃者によって侵害された場合は、SQL ログインの移行中でしたインターセプトを取得または変更その場で、攻撃者によってを。

    一方、すべてのアクセスにセキュリティで保護されたイントラネット構成が使用される場合には、暗号化は必ずしも必要ありません。 暗号化を有効にすると、余分なオーバーヘッドは暗号化し、パケットを暗号化解除に必要なために、パフォーマンスが低下します。 詳細についてを参照してください [SQL Server への接続の暗号化](https://go.microsoft.com/fwlink/?linkid=832513)します。
