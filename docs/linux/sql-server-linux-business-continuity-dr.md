---
title: "Linux 上の SQL Server の災害復旧 |Microsoft ドキュメント"
description: 
author: mihaelab
ms.author: mihaelab
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: c75717c8-c677-4033-8ca6-d0ac93aee04d
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 86f41971e06efb767dde336cf93f9224a204176d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="business-continuity-and-database-recovery-sql-server-on-linux"></a>ビジネス継続性とデータベース復旧 Linux に SQL Server

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

SQL Server on Linux さまざまなさまざまなビジネス要件に対応するサービス レベル契約の目標を実現するために実行できるようにします。

最も簡単なソリューションでは、高度な障害に対する回復性ホスト レベル、ハードウェアの障害、および弾力性とリソース活用を最大化に対してフォールト トレランスを実現するために仮想化テクノロジを活用します。 これらのシステムでは、プライベートまたはパブリック クラウド、またはハイブリッド環境で、オンプレミスでを実行できます。 災害復旧と保護の最も単純な形式は、データベースのバックアップです。 SQL Server 2017 RC2 で使用できる単純なソリューションは次のとおりです。

- **VM のフェールオーバー**
    - ゲストと OS レベルの障害に対する回復力
    - 計画されていないと計画的なイベント
    - 修正プログラムとアップグレードのための最小のダウンタイム
    - 分単位で RTO


- [**データベースのバックアップと復元**](sql-server-linux-backup-and-restore-database.md) 
    - 誤ってまたは悪意のあるデータの破損に対する保護
    - 障害回復保護
    - 時間を分単位で RTO

高可用性と災害復旧のための標準的な手法は、共有記憶域の信頼性の高いインフラストラクチャと組み合わせて使用するインスタンス レベルの保護を提供します。 SQL Server 2017 RC2 には standard の高可用性が含まれます。

- [**フェールオーバー クラスター**](sql-server-linux-shared-disk-cluster-configure.md)
    - インスタンス レベルの保護
    - 障害の自動検出と自動フェールオーバー
    - OS と SQL Server の障害に対する回復力
    - 数秒数分からで RTO


## <a name="summary"></a>概要

Linux 上の SQL Server 2017 RC2 には、高可用性と災害復旧をサポートするために仮想化、バックアップと復元、およびフェールオーバー クラスターが含まれています。 
